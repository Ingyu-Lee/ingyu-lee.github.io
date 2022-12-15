---
title: "시스템의 특성에 관해"
excerpt: "Linearity, static, dynamic, time-invariant, causal 등의 다양한 시스템의 특성에 관해 알아보도록 한다."
use_math: true
toc: true
categories:
  - Studies
tags:
  - Control Systems Engineering
  - Digital Signal Process
  - Linear System Theory

last_modified_at: 2021-03-17T20:52:00
---

# 1. Linear system

가장 자주 나오고 흔히 쓰이는 선형 시스템이다. 선형 시스템은 다음과 같은 조건을 만족한다.

\begin{align\*}
  \text{A relaxed system is linear iff}
\end{align\*}

\begin{align\*}
  f\left( A x_1 + B x_2 \right)
  = A f \left( x_1 \right) + B f \left( x_2 \right)
\end{align\*}

\begin{align\*}
  \displaylines
    {
      \text{where } A \text{ and } B \text{ are constants, } f \text{ is a system,}
      \\\ \text{and } x_1 \text{ and } x_2 \text{ are system inputs.}
    }
\end{align\*}

이는 두 특성, additivity 와 homogeneity 가 같이 있는 것으로 볼 수 있다. 이러한 성질 때문에 다양한 linear operations 에 적용할 수 있어 계산이 용이하여 system design에 있어 linear 한 설계가 선호된다.

## 1-1. Additivity
Additivity 는 system input 이 여러 값의 합일 때, system output 이 각각의 input의 output의 합으로 나타내지는 특성이다. 수식으로 표현하면 다음과 같다.
\begin{align\*}
  f \left( x_1 + x_2 \right) = f \left( x_1 \right) + f \left( x_2 \right)
\end{align\*}

## 1-2. Homogeneity
Homogeneity 는 system input 에 constant 가 곱해졌을 때 그 output 도 constant 배가 되는 특성이다. 수식으로 표현하면 다음과 같다.

\begin{align\*}
  f \left( A x \right) = A f \left( x \right)
\end{align\*}

# 2. Dynamic, Memory
System output 이 오직 현재의 input 에만 dependent 하다면 static system, 또는 memoryless system 이라 하며, 그렇지 않을 경우 dynamic system, 또는 memory system 이라 한다. 각각의 예시는 다음과 같다.

Static system / memoryless system
\begin{align\*}
  y \left( t \right) = f \left( x \left( t \right) \right)
\end{align\*}

Dynamic system / memory system
\begin{align\*}
  \displaylines
  {
    y \left( t \right) = f \left( x \left( t \right), x \left( t-1 \right) \right)
    \\\ \dot{y} \left( t \right) = x \left( t \right)
    \\\ y \left( t \right) = \frac{d}{dt} x \left( t \right)
    \\\ y \left( t \right) = x \left( t - t_0 \right)
    \\\ y \left( t \right) = x \left( 3t \right)
  }
\end{align\*}

# 3. Time-invariant
Time-invariant system 은 system input 의 time shift 또는 delay 가 그 output 에도 같은 time shift 또는 delay 를 야기하는 시스템이다. 이를 수식으로 표현하면 다음과 같다.

\begin{align\*}
  y \left( t - t_0 \right) = f \left( x\left( t - t_0\right) \right)
\end{align\*}

앞서 소개한 linearity 까지 만족하는 system 을 linear time-invariant system, 줄여서 LTI system 이라 하고, 시스템 설계에 주로 사용된다. 흔히 사용되는 linear time-invariant operation 에는 matrix 연산, integration/derivative, 그리고 Fourier transform 등이 있다.


# 4. Causality

# 5. Relaxedness

# 6. Stability
