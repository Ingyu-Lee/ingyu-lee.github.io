---
title: "ROS Basics: URDF and Xacro"
excerpt: "ROS Basics: URDF and Xacro"
thumbnail: 999999_category_research_paper_memo_00.jpg
banner: 999999_home_image_banner_textbook.jpg
banner_caption: Research Memo
use_math: true
toc: true
toc_sticky: true
categories:
  - Studies
tags:
  - ROS
---

# 요약

기초적인 object spawn을 하던 중 아래 방법들의 차이가 궁금해져 정리를 하려 한다.

<div class="tex2jax_ignore">
1. World 파일에 object 삽입
2. URDF를 활용한 object creating and spawning[1]
3. 기존 연구실 방식인, xacro 파일을 사용해 spawn
</div>

# 내용 정리

## World 파일에 object 삽입

아래 접기 글은 world에 구체를 삽입하기 위해 사용한 코드로, model 객체에 properties를 적용한다.

<details>
```
<model name='unit_sphere_0'>
  <static>true</static>
  <pose>29.09  -4.6  -88.20 0 0 0</pose>
  <link name='link'>
    <inertial>
      <mass>1</mass>
      <inertia>
        <ixx>0.1</ixx>
        <ixy>0</ixy>
        <ixz>0</ixz>
        <iyy>0.1</iyy>
        <iyz>0</iyz>
        <izz>0.1</izz>
      </inertia>
      <pose>0 0 0 0 0 0</pose>
    </inertial>
    <collision name='collision'>
      <geometry>
        <sphere>
          <radius>0.5</radius>
        </sphere>
      </geometry>
      <max_contacts>10</max_contacts>
      <surface>
        <contact>
          <ode/>
        </contact>
        <bounce/>
        <friction>
          <torsional>
            <ode/>
          </torsional>
          <ode/>
        </friction>
      </surface>
    </collision>
    <visual name='visual'>
      <geometry>
        <sphere>
          <radius>0.5</radius>
        </sphere>
      </geometry>
      <material>
        <script>
          <name>Gazebo/Grey</name>
          <uri>file://media/materials/scripts/gazebo.material</uri>
        </script>
      </material>
    </visual>
    <self_collide>0</self_collide>
    <enable_wind>0</enable_wind>
    <kinematic>0</kinematic>
  </link>
</model>
```
</details>

## URDF 를 활용한 object creating and spawning

ROS 튜토리얼을 참조했다. 아래 접기 글의 코드는 object.urdf 로 저장된다.

위 world 파일에서의 코드와 비교하면, model이 아닌 robot 객체이지만 inertial, mass 등의 properties는 그대로 적용한다.

이후 아래 코드를 입력하여 gazebo에서 spawn한다.
```
rosrun gazebo_ros spawn_model -file `pwd`/object.urdf -urdf -z 1 -model my_object
```

<details>
```
<robot name="simple_box">
  <link name="my_box">
    <inertial>
      <origin xyz="2 0 0" />
      <mass value="1.0" />
      <inertia  ixx="1.0" ixy="0.0"  ixz="0.0"  iyy="100.0"  iyz="0.0"  izz="1.0" />
    </inertial>
    <visual>
      <origin xyz="2 0 1"/>
      <geometry>
        <box size="1 1 2" />
      </geometry>
    </visual>
    <collision>
      <origin xyz="2 0 1"/>
      <geometry>
        <box size="1 1 2" />
      </geometry>
    </collision>
  </link>
  <gazebo reference="my_box">
    <material>Gazebo/Blue</material>
  </gazebo>
</robot>
```
</details>

<div class="tex2jax_ignore">
dae 파일을 mesh로 불러오기 위해서는 아래와 같은 예시를 참조하면 될 것 같다.[2]
</div>

```
<link name="left_gripper">
  <visual>
    <geometry>
      <mesh filename="package://pr2_description/meshes/gripper_v0/l_finger.dae"/>
    </geometry>
  </visual>
</link>
```

## xacro 파일을 사용해 spawn

아래 launch 파일을 거쳐 xacro_1 파일을 불러오고, 다시 한번 그 안에서 xacro_2 파일을 불러 와 spawn하는 방식이다.

launch 파일에서 xacro_2 파일을 바로 불러오는 방식으로는 spawn이 되지 않는다. namespace 때문인지, 또는 어떤 property가 선언이 되지 않아서인 것으로 생각되는데 확실친 않다.

<details>
```
<launch>
    <!-- Debug flag -->
    <arg name="debug" default="0" />
    <!-- Vehicle's initial pose -->
    <arg name="x" default="0" />
    <arg name="y" default="0" />
    <arg name="z" default="-50" />
    <arg name="roll" default="0.0" />
    <arg name="pitch" default="0.0" />
    <arg name="yaw" default="0.0" />
    <!--
	Mode to open different robot configurations as set the in file
	nomenclature standard for the files in /robots
	/robots/<mode>.xacro
	-->
    <arg name="mode" default="default" />
    <!-- Vehicle's namespace -->
    <arg name="namespace" default="object" />
    <!-- World Frame -->
    <arg name="world_frame" default="world" />
    <!-- <arg name="use_simplified_mesh" default="false"/> -->
    <!-- <arg name="use_ned_frame" default="false"/> -->
    <group ns="$(arg namespace)">
       
        <param name="robot_description" command="$(find xacro)/xacro '$(find hero_agent_description)/robots/obj_test_00.xacro' --inorder
                    debug:=$(arg debug)
					namespace:=$(arg namespace)" />
        <!--<node name="joint_state_publisher" pkg="joint_state_publisher" type="joint_state_publisher"></node>
		-->
        <!-- use_simplified_mesh:=$(arg use_simplified_mesh) -->
        <!-- inertial_reference_frame:=world_ned -->
        <!-- Run a python script to the send a service call to gazebo_ros to spawn a URDF robot -->
        <node name="urdf_spawner" pkg="gazebo_ros" type="spawn_model" respawn="false" output="screen" args="-urdf -x $(arg x) -y $(arg y) -z $(arg z) -R $(arg roll) -P $(arg pitch) -Y $(arg yaw) -model $(arg namespace) -param /$(arg namespace)/robot_description" />
        <!-- A joint state publisher plugin already is started with the model, no need to use the default joint state publisher -->
        <!-- Publish robot model for ROS -->
       
    </group>
    <!-- Publish state and tf for in relation to the world frame -->
    <include file="$(find uuv_descriptions)/launch/message_to_tf.launch">
        <arg name="namespace" value="$(arg namespace)" />
    </include>

</launch>
```
</details>

<details>
```
<?xml version="1.0"?>
<robot name="obj_test_00"
    xmlns:xacro="http://www.ros.org/wiki/xacro">
    <xacro:arg name="debug" default="0" />
    <xacro:arg name="namespace" default="obj_test_00" />
    <!-- Include the ROV macro file xacro:hero_agent_base -->
    <xacro:include filename="$(find hero_agent_description)/urdf/obj_test_00.xacro" />
    <!-- Hydrodynamic and hydrostatic parameters for the vehicle xacro:macro hero_agent_hydro_model -->
    <xacro:include filename="$(find hero_agent_description)/urdf/gazebo.xacro" />
    <!-- Create the hero_agent -->
    <xacro:hero_agent_base namespace="$(arg namespace)">
        <!--
		The underwater object plugin is given as an input block parameter to
		allow the addition of external models of manipulator units
        1001.651
		-->


        <gazebo>
            <plugin name="uuv_plugin" filename="libuuv_underwater_object_ros_plugin.so">
                <fluid_density>
					1010.651
                </fluid_density>
                <flow_velocity_topic>
					hydrodynamics/current_velocity
                </flow_velocity_topic>
                <debug>
					$(arg debug)
                </debug>
                <!-- Adding the hydrodynamic and hydrostatic parameters for the vehicle -->
                <xacro:hero_agent_hydro_model namespace="$(arg namespace)" />
                <!--
				In case other modules are added to the vehicle (such as a manipulator)
				that also have link running with the underwater object plugin, they
				should also be added in this block. For this, this new module should
				have a file similar to gazebo.xacro above with the description of the
				parameter necessary for the underwater object plugin to be initialized.
				-->
            </plugin>
        </gazebo>
    </xacro:hero_agent_base>
    <!-- Joint state publisher plugin -->
    <xacro:default_joint_state_publisher namespace="$(arg namespace)" update_rate="10" />

  
    <gazebo>
        <plugin name="fix_agent_roll_pitch" filename="libfix_agent_roll_pitch.so"></plugin>
    </gazebo>
    <gazebo><plugin name="model_push" filename="libmodel_push.so"></plugin></gazebo>
    
</robot>
```
</details>

<details>
```
<?xml version="1.0"?>
<robot name = "test_00"
    xmlns:xacro="http://www.ros.org/wiki/xacro">
    <!-- Loading some constants -->
    <xacro:include filename="$(find uuv_descriptions)/urdf/common.urdf.xacro" />
    <!-- Loading file with sensor macros -->
    <xacro:include filename="$(find uuv_sensor_ros_plugins)/urdf/sensor_snippets.xacro" />
    <xacro:include filename="$(find hero_agent_description)/urdf/snippets.xacro" />
    <!-- ADDED -->
    <xacro:include filename="$(find uuv_gazebo_ros_plugins)/urdf/snippets.xacro" />
    <!-- Vehicle's parameters (remember to enter the model parameters below) -->
    <!-- Mass -->
    <xacro:property name="mass" value="9.18" />
    <!-- Describing the dimensions of the vehicle's bounding box: width, length, height -->
    <xacro:property name="x_size" value="0.38" />
    <xacro:property name="y_size" value="0.38" />
    <xacro:property name="z_size" value="0.35" />
    <xacro:property name="radius" value="0.0825" />
    <xacro:property name="length" value="0.35" />
    <xacro:property name="rho" value="1028" />
    <!-- minion_usv_height is not really! It's just for run... We need first calculate the Fossen parameters -->
    <!-- Volume -->
    <xacro:property name="volume" value="0.0078" /> <!-- default agent buoy -->
    <xacro:property name="volume2" value="0.00135" /> <!-- active buoy volume -->
    <xacro:property name="volume3" value="0.0095" />
    <!-- Center of gravity -->
    <xacro:property name="cog" value="0 0 0" />
    <!--
	Center of buoyancy according to eq. (3.1) p. 28 in Berg2012.
	The original values, [0.0822, -0.00773, 0.3872] however, seem to
	assume NWU (otherwise cob is below cog?). 0.155
	-->
    <xacro:property name="cob" value="0 0 0" />
    <!-- Fluid density -->
    <xacro:property name="rho" value="1028" />
    <!--1028
	Visual mesh file for the vehicle, usually in DAE (Collada) format. Be sure to store the
	mesh with the origin of the mesh on the same position of the center of mass, otherwise
	the mesh pose will have to be corrected below in the <visual> block.
	Open the meshes for the RexROV vehicle in Blender to see an example on the mesh placement.
	-->
    <xacro:property name="visual_mesh_file" value="file://$(find hero_agent_description)/meshes/dojagi_.dae" />
    <!--
	Collision geometry mesh, usually in STL format (it is recommended to keep
	this geometry as simple as possible to improve the performance the physics engine
	regarding the computation of collision forces)
	-->
    <xacro:property name="collision_mesh_file" value="file://$(find hero_agent_description)/meshes/dojagi_.dae" />
    <!-- Vehicle macro -->
    <!-- <xacro:macro name="hero_agent_base" params="namespace debug *gazebo"> -->
    <xacro:macro name="hero_agent_base" params="namespace *gazebo">
        <!-- Rigid body description of the base link -->

        <link name="${namespace}/base_link">
            <!--
			Be careful to setup the coefficients for the inertial tensor,
			otherwise your model will become unstable on Gazebo
			-->
            <inertial>
                <mass value="${mass}" />
                <origin xyz="${cog}" rpy="0 0 0" />
                <!-- <inertia ixx="525.39" ixy="1.44" ixz="33.41" iyy="794.20" iyz="2.6" izz="691.23"/> -->
                <inertia ixx="${mass*radius*radius / 4  + mass*length*length / 12}" ixy="0.0" ixz="0.0" iyy="${mass*radius*radius / 4  + mass*length*length / 12}" iyz="0.0" izz="${mass*radius*radius / 2}" />
            </inertial>
            <!--
			This visual geometry representation can be used when running
			tasks in which you need Gazebo to start quickly
			-->
            <visual>
                <origin xyz="0 0 0" rpy="3.141593 0 0" />
                <geometry>
                    <mesh filename="${visual_mesh_file}" scale="1 1 1" />
                </geometry>
            </visual>

            <collision>
                <origin xyz="0 0 0" rpy="0 0 0"/>
                <geometry>
                    <box size="0.25 0.25 0.3"/>
                </geometry>
            </collision>
            <!-- In rexrov2_base they made collision planes to minize the GPU load -->
            <!-- <collision><origin xyz="0 0 0" rpy="0 0 0"/><geometry><mesh filename="${collision_mesh_file}" scale="1 1 1" /></geometry></collision> -->
        </link>

    </xacro:macro>

    
</robot>
```
</details>

- - -
# 참고문헌

<div class="tex2jax_ignore">

[1] https://wiki.ros.org/simulator_gazebo/Tutorials/SpawningObjectInSimulation

[2] https://answers.ros.org/question/35819/using-dae-file-in-gazebo/

</div>
