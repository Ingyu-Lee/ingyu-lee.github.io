---
title: "수식입력연습"
excerpt: "수식입력연습"
thumbnail: 999999_category_research_paper_memo_00.jpg
banner: 999999_home_image_banner_textbook.jpg
banner_caption: Research Memo
use_math: true
last_modified_at: 2021-08-20T18:30:00
---

\begin{equation}
  \displaylines
  {
    Q &=& \frac{\text{Displace amplitude at resonance}}
    {\text{Static deflection due to force amplitude}}
    \\\ &=& \frac{m\omega\_0}{R\_m} = \frac{1}{2\zeta} =
    \frac{\omega\_0}{\text{Half-power bandwidth}}
  }
\end{equation}


\begin{equation}
  \displaylines
  {
    f\left( x-ct \right) \\ \\ \\ \text{and} \\ \\ \\ g\left( x+ct \right)
    \\\ \text{where f, and g are arbitrary functions}
  }
\end{equation}


\begin{equation}
  \nabla ^2f = \sum^{n}\_{i=1}\frac{\partial ^2 f}{\partial x^2\_i}
\end{equation}

\begin{equation\*}
  \displaylines
  {
    J &=& \Vert A\theta - y \Vert^2\_2 + \lambda \Vert \theta \Vert^2\_2
    \\\ &=& \left( A\theta - y \right)^T \left( A\theta - y \right) + \lambda \left( \theta^T \theta \right)
    \\\ &=& \left( \theta^TA^T - y^T \right)^T \left( A\theta - y \right) + \lambda \left( \theta^T \theta \right)
    \\\ &=& \theta^T A^T A \theta - \theta^T A^T y - y^T A \theta + y^T y + \lambda \left( \theta^T \theta \right)
    \\\ \Rightarrow \frac{\partial J}{\partial \theta} &=& A^T A \theta + \left( A^T A \right)^T \theta - A^T y - \left( y^T A \right)^T + 2 \lambda \theta
    \\\ &=& 2 A^T A \theta - 2 A^T y + 2 \lambda \theta = 0
    \\\ \Rightarrow \left( A^T A + \lambda I\_n \right) \theta &=& A^T y
    \\\ \Rightarrow \hat{\theta} &=& \left( A^TA + \lambda I\_n \right)^{-1} A^T y
  }
\end{equation\*}


\begin{equation\*}
  \displaylines
  {
    \theta \leftarrow \theta - \eta \frac{\partial J}{\partial \theta}
    \\\ \theta \leftarrow \theta - 2 \eta \left( A^T A \theta - A^T y + \lambda \theta \right)
  }
\end{equation\*}
