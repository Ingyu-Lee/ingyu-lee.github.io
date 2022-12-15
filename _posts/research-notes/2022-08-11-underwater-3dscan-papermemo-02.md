---
title: "An autonomous integrated system for 3-D underwater terrain map reconstruction"
excerpt: "An autonomous integrated system for 3-D underwater terrain map reconstruction"
thumbnail: 999999_category_research_paper_memo_00.jpg
banner: 999999_home_image_banner_textbook.jpg
banner_caption: Research Memo
use_math: true
toc: true
toc_sticky: true
categories:
  - Studies
tags:
  - Paper Reviews
sidebar:
  title: "Underwater 3D Scan<br>Literature Study"
  nav: aaa
---

<figure style="width: 100%" class="align-center">
  <a href="{{ site.url }}{{ site.baseurl }}/assets/images/220811_underwater_3drecon_paperreview_02.png">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/220811_underwater_3drecon_paperreview_02.png" alt="">
  </a>
  <figcaption>
  Fig.1 Paper title and author
  </figcaption>
</figure>

# 요약

이 논문은 2016 년 11 월 OCEANS 학회에 실린 paper로, 해저 지형 3D reconstruction을 자동 경로 설정을 통해 수행한 논문이다. LBL, PID와 칼만 필터를 활용하여 자함의 localization을, multi-resolution partitioning과 global navigation으로 자함의 이동 경로를 자동으로 설정하고, 그리고 multi-beam sonar sensor로 alpha-shape를 활용해 3D-map reconstruction을 수행한 논문이다.

## Navigation Controller

Multi-resolution partitioning은 탐사 지역을 여러 해상도의 map으로 나누어, 각 element마다 4 개의 label을, explored, unexplored, obstacle, 그리고 buffer를 붙인다. 맨 처음엔 모든 지역의 label이 unexplored로 시작하여, 같은 row엔 같은 potential value를, 그리고 서로 다른 columns에는 점점 감소하는 potential value를 부여한다. Obstacle 및 buffer label 에는 minus infinity potential energy를 부여한다. 현재 AUV의 위치와 unexplored 의 위치를 비교하여, distance와 turning angle에 따른 travel cost를 계산하여 최종적인 potential field를 계산하여 AUV의 경로를 결정한다. 하지만 이 경우 local neighborhood에 unexplored cell이 없을 경우 local minimum에 갇히게 된다.

## Global Navigation

Local minimum에 갇힌 경우 수행된다. Multi-resolution partition 된 map의 coarser level map을 사용하여 다시 새로운 목표goal을 찾고, Bug2 알고리즘을 사용하여 새 목표로 향한다.

# Note

Path planning 알고리즘이 대단히 흥미롭다. 논문에서는 map의 구석에만 obstacle이 있어 zigzag path가 쭉 이어지는 형태로 되는데, map 한가운데와 같은 path에 대해선 보이지 않아서 아쉬운 부분이 있다.

- - -
# 참고문헌

L. Mazzei, L. Corgnati, S. Marini, E. Ottaviani and B. Isoppo, "Low cost stereo system for imaging and 3D reconstruction of underwater organisms," OCEANS 2015 - Genova, 2015, pp. 1-4, doi: 10.1109/OCEANS-Genova.2015.7271554.
