---
title: '[Markdown] MD에 LyX 수식 적용하기'
date: '2020-03-07 22:59:00 +0800'
categories:
  - Markdown
  - LyX
tags:
  - Markdown
  - LyX
  - 수식 입력
toc: true
comments: true
use_math: true

---

## 본격적인 통계학 포스팅에 앞서 수식 입력 트레이닝을 선행한다.

***

&nbsp;&nbsp;&nbsp;&nbsp; LyX으로 입력한 내용을 tex로 export한 뒤, pandoc을 이용하여 markdown으로 바로 만들 수 있었다. 수식은 mathjax를 통해 잘 작동하지만 LyX에서 쓰던 매크로가 그대로 작동하지 않으므로 이를 그나마 사용할 수 있게 방법들을 찾아보고, 정리해보았다.

***

- 매크로 지정  

```  
$$
   \def\RR{\bf R}

   \def\bold#1{\bf #1}
   
   \def\df#1#2{\dfrac{#1}{#2}}
   
   \def\si{\sigma}
   
   \def\dt{\cdot}
   
   \def\inf{\infty}
$$
```
&nbsp;이렇게 지정하니 아래와 같이 매크로가 잘 작동하는 것을 확인할 수 있다. 
$$
\def\RR{\bf R}
\def\bold#1{\bf #1}
\def\df#1#2{\dfrac{#1}{#2}}
\def\si{\sigma}
\def\dt{\cdot}
\def\inf{\infty}
$$


```
$\RR$ and $\bold{base}$
```
  * output:

   &nbsp;&nbsp;&nbsp;&nbsp;$\RR$ and $\bold{base}$

***

+ /df1 space 2 가능  
  
```
$\df1 2$
```

  * output: 

  &nbsp;&nbsp;&nbsp;&nbsp;$\df1 2$

***

- {} 없이도 가능

```
$f_X(x)$ 
$\si^2$ 
```

&nbsp;&nbsp;&nbsp;&nbsp;이건 참 다행이다

  * output: 

&nbsp;&nbsp;&nbsp;&nbsp;   $f_X(x)$

  &nbsp;&nbsp;&nbsp;&nbsp; $\si^2$  

   &nbsp;&nbsp;&nbsp;&nbsp;$\sqrt{2\pi\si^2}$

***

- align은 \\$ 한번만. 가운데로 몰려면 \\$$ 없이. (입력은 \\\\\\\\ = 출력은 \\\\)
  
```
$
\begin{aligned} 
2x - 4 & = 6 \\\\ 2x &= 10 \\\\ x &= 5 
\end{aligned}

\begin{aligned} 
2x - 4 & = 6 \\\\ 2x &= 10 \\\\ x &= 5 
\end{aligned} 
```

  * output: 

  &nbsp;&nbsp;&nbsp;&nbsp;$
  \begin{aligned} 
  2x - 4 & = 6 \\\\ 2x &= 10 \\\\ x &= 5 
  \end{aligned}
  $

  \begin{aligned} 
  2x - 4 & = 6 \\\\ 2x &= 10 \\\\ x &= 5 
  \end{aligned}

&nbsp;&nbsp;&nbsp;&nbsp; 수식을 줄줄이 쓸 수 있는 align이 작동하지 않아 애먹었다.

***

- **연습문제:**  

  확률변수 X가 평균이 $\mu$이고, 분산이 $\si^{2}$인 정규분포를 따른다고 할 때,  

  
  
  $X$의 확률밀도함수는 다음과 같다.

<br/>

\begin{aligned}
\text{if} \,\, X & \sim N(\mu,\si^2), \\\\ \\\\ f_X(x) & = \df1 {\sqrt{2\pi\si^2}} e^{ - \df1 2 \left(  \df{x-\mu} \si \right)^2} \, \, \, \text{for} -\inf<x<\inf
\end{aligned}


- **input:**  
```
\begin{aligned}
\text{if} \,\, X & \sim N(\mu,\si^2), 
\\\\ \\\\ 
f_X(x) & = \df1 {\sqrt{2\pi\si^2}} e^{ - \df1 2 \left(  \df{x-\mu} \si^2 \right)} 
\, \, \, \text{for} -\inf<x<\inf
\end{aligned}
```

***

## 결론


&nbsp;&nbsp;&nbsp;&nbsp;마크다운은 어색해...



