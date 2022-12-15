---
title: "Optimal State Estimation Ch.01 Linear Systems Theory"
excerpt: "Optimal State Estimation Ch.01 Linear Systems Theory"
thumbnail: 999999_category_DanSimon_OptimalStateEstimation_00.jpg
banner: 999999_home_image_banner_textbook.jpg
banner_caption: Optiman State Estimation
use_math: true
toc: true
toc_sticky: true
categories:
  - Studies
last_modified_at: 2022-04-21T20:20:00
sidebar:
  title: "Optimal State Estimation"
  nav: sidebar-dynamics
---

# 1 Linear Systems Theory

Matrix algebra와 matrix inversion lemma는 각각 그 내용이 너무 기초적이고, 그 내용이 외우기에는 다소 복잡하여 기록에 남기기보다는 추후 다시 본문을 찾아보는 것으로 한다.

## 1.1 Matrix Calculus

* Matrix 의 미분과 적분은 각 element에 대한 연산이다.
\begin{equation}
    \displaylines
    {
        \frac{d}{dt}\text{A}\left( t \right) &=& \begin{bmatrix}
                                                 \tfrac{d}{dt}\text{A}\_{11} & \tfrac{d}{dt}\text{A}\_{12} & \\dots \\\
                                                 \\vdots & \\ddots & \\\
                                                 \tfrac{d}{dt}\text{A}\_{n1} & & \tfrac{d}{dt}\text{A}\_{nn}
                                                 \end{bmatrix} \\\
        \int \text{A}\left( t \right) dt &=& \begin{bmatrix}
                                    \int \text{A}\_{11} dt & \int \text{A}\_{12} dt & \\dots \\\
                                    \\vdots & \\ddots & \\\
                                    \int \text{A}\_{n1} dt & & \int \text{A}\_{nn} dt
                                    \end{bmatrix}
    }
\end{equation}

<!-- * Derivative of Inverse Matrix
\begin{equation}
    \displaylines
    {
        \frac{d}{dt}\left( \text{A}\text{A}^{-1} \right) &=& \frac{d\text{A}}{dt}\text{A}^{-1} - \text{A}\frac{d}{dt}\left( \text{A}^{-1} \right) \\\
        0 &=& \frac{d\text{A}}{dt}\text{A}^{-1} - \text{A}\frac{d}{dt}\left( \text{A}^{-1} \right) \\\
        \text{A}\frac{d}{dt}\left( \text{A}^{-1} \right) &=& \frac{d\text{A}}{dt}\text{A}^{-1} \\\
        \therefore \frac{d}{dt}\left( \text{A}^{-1} \right) &=& \text{A}^{-1}\frac{d\text{A}}{dt}\text{A}^{-1}
    }
\end{equation}

* \begin{math} f \left( x \right) \end{math} 는 scalar function, \begin{math} x \end{math} 는 \begin{math} \left( n \times 1 \right) \end{math} vector 일 때,

\begin{equation}
    \frac{\partial f}{\partial x} = \left[ \frac{\partial f}{\partial x\_1} \frac{\partial f}{\partial x\_2} \\dots \frac{\partial f}{\partial x\_n} \right]
\end{equation} -->


- - -
# 참고문헌
