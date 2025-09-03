
#LaTex，Latex #Math #计算机工具学习

---
# 常用网站
[lists of mathematical symbols](https://oeis.org/wiki/List_of_LaTeX_mathematical_symbols)
[LaTex Wiki](https://en.wikibooks.org/wiki/LaTeX/Basics)

**overleaf 是一个线上云latex编辑器平台**
[overleaf document:Learn Latex in 30 minutes](https://www.overleaf.com/learn/latex/Learn_LaTeX_in_30_minutes)

---
## 常见符号
- **文字上加横线**：\overline{asdA}
- **文字上加箭头**：\overrightarrow{AB}
- **文字上加波浪**：\tilde{x}
- **~**：\sim
- **正负无穷**$\infty$：$\infty$ +- \infty
- **括号**：\left ( \right), \left[ \right] 
- **约等于号**$\approx$：\approx
- **不等于号**$\neq$：neq
- **集合关系**：($\in$)\in, 
- **加减号**：$\pm$ pm
![[Pasted image 20240317171653.png]]
## 全局设定：
```latex
\usepackage{latexsym}
\usepackage{amssymb}
\usepackage{amsmath}
\usepackage{graphicx}        
\usepackage{moreverb}
\usepackage[mathscr]{eucal}  
\usepackage[sans]{dsfont} 
\usepackage{fancyhdr}    
\usepackage{algorithm2e} 
\usepackage{ragged2e}
\usepackage{xcolor}
\usepackage{pgfplots}
\pagestyle{fancy}

\\[9pt]\textbf{A:}\color{teal}\\

\color{black}
```

## 各种不同的字体和排版
```Latex
\huge{} %大写
\bf{} %Bold
\it{} % italic

% 左，右，中心对齐
\raggedright 
\raggedleft
\raggedcenter
```
## 如何插入图片
```latex
//适用于overleaf在线编辑器
\includegraphics[width=1.0\columnwidth]{Homework02/Graphs/scatterplot_2.png}
```
## 列表（list）
```Latex
%create a number list
\begin{enumerate}
	\item
\end{enumerate}

%create a item list
\begin{itemize}
\item 1
\end{itemize}
```

## 数学表示
- permutation & combination：$P_{{a},{b}}$ , $\binom{a}{b}$
- 分数的写法：$\frac{1}{2}$
>积分的写法
![[Pasted image 20240317171753.png|500]]
```Latex
\int_{a}^{b}f(x)dx
```
>微分的写法
$\frac{\partial y}{\partial x}$
### 写一个竖着的等式
```latex
\begin{equation}
        \begin{split}
        &=......\\
        \end{split}
\end{equation}
```

### 概率和统计中的数学符号
- 交并补符号（$\cap,\cup$）：\cap 和 \cup
### PMF table的画法
```latex
\[ \begin{array}{c|c} x & p(x) \\ \hline -1 & 0.1 \\ 0 & 0.3 \\ 1 & 0.2 
\\ 3 & 0.4 \end{array} \]
```
![[Pasted image 20240423181449.png|500]]
```latex
\[ Y \quad \begin{array}{r|c|c|c|l}
 \multicolumn{5}{c}{X} \\[3pt]
   & 0    & 1    & 2    &  \quad \\ \hline
-1 & 0.30 & 0.10 & 0.05 &  \\ \hline
 1 & 0.05 & 0.30 & 0.20 &  \\ \hline
   &      &      &     &  \end{array} \]
```
### PMF 坐标系的画法
```latex
\usepackage{pgfplots}
\begin{tikzpicture}
\begin{axis}[
    ybar, % Bar plot
    bar width=1, % Width of the bars
    axis lines=middle,
    ymin=0, ymax=0.8, % Minimum value of y-axis
    xlabel={$x$}, % Label for the x-axis
    ylabel={$p(x)$}, % Label for the y-axis
    xtick={-2,-1,0,1,2,3,4}, % The symbolic coordinates on the x-axis
    ytick={0,0.1,0.2,0.3,0.4,0.5},
    clip=false,
]

% Add the plot data
\addplot coordinates {(-1,0.1) (0,0.3) (1,0.2) (3,0.4)};
\draw [->, thick] (axis cs:3,0)--(axis cs:4,0);
\draw [-, thick] (axis cs:-2,0)--(axis cs:-1,0);

\end{axis}
\end{tikzpicture}
```
### CDF 坐标系的画法
```latx
\usepackage{pgfplots}
\begin{tikzpicture}
\begin{axis}[
    axis lines=middle,
    xlabel=$x$,
    ylabel={$F(x)$},
    ymin=0, ymax=1.2,
    xtick={-2,-1,0,1,2,3,4},
    ytick={0,0.2,0.4,0.6,1,1.2},
    clip=false,
]
% Stepwise function
\addplot+[const plot,no marks, color=black,thick] coordinates {(-2,0) };
\addplot+[const plot,no marks, color=black,thick] coordinates { (-1,0.1) (0,0.1)};
\addplot+[const plot,no marks, color=black,thick] coordinates { (0,0.4) (1,0.4)};
\addplot+[const plot,no marks, color=black,thick] coordinates { (1,0.6) (3,0.6)};
\addplot+[const plot,no marks, color=black,thick] coordinates { (3,1) (4,1)};
% Solid dots
\addplot+[only marks, mark=*, color=black,fill=black] coordinates {(-1,0.1) (0,0.4) (1,0.6) (3,1)};
% Open dots
\addplot+[only marks, mark=o, color=black,fill=white] coordinates {(-1,0)(0,0.1) (1,0.4) (3,0.6)};
% Extend the x-axis line
\draw [->, thick] (axis cs:4,0)--(axis cs:5,0);
\end{axis}
\end{tikzpicture}
```
### 条件函数的写法
```latex
P(X = x) = 
\begin{cases}  
p_1 & \text{for } x = x_1, \\   
p_2 & \text{for } x = x_2,  \\
\vdots & \\  \\
p_n & \text{for } x = x_n,  \\
\end{cases}
```
>[!Note] 绘制一个函数
>> ![[Pasted image 20240320195933.png|300]]
```
\usepackage{pgfplots}
\begin{tikzpicture}
\begin{axis}[
    axis lines=middle,
    xlabel=$x$,
    ylabel={$f(x)$},
    xtick={-2,-1,0,1,2,3},
    ytick={0,1,2},
    clip=false,
]
% 绘制 f(x) = |x|
\addplot[
    domain=-1:1,
    samples=100,
    color=red,
] {abs(x)};
\addplot[
    domain=-2:-1,
    samples=100,
    color=red,
] {0};
\addplot[
    domain=1:3,
    samples=100,
    color=red,
] {0};
% Extend the x-axis line
\draw [->, thick] (axis cs:3,0)--(axis cs:4,0);
\draw[dashed] (axis cs:-1,0) -- (axis cs:-1,1);
\draw[dashed] (axis cs:1,0) -- (axis cs:1,1);
\end{axis}
\end{tikzpicture}
```

```
\usepackage{pgfplots}
\usepgfplotslibrary{fillbetween}
\begin{tikzpicture}
  \begin{axis}[
      axis lines = middle, % 坐标轴设置为中线
      xlabel = $x$, % x 轴标签
      ylabel = {$y$}, % y 轴标签
      samples=100, % 增加采样点来使图像更加平滑
      ymin=0, ymax=70, % y 轴范围
      xmin=0, xmax=70, % x 轴范围
      xtick={5,15,30,45,60},
      ytick={5,10,20,40,50,60},
      width=5cm, % 图像宽度
      height=5cm % 图像高度
    ]
    \addplot[name path=A,domain=5:60, thick, color=blue]{x-5};
    \addplot[name path=B, domain=0:60,thick, color=blue]{x+5};
    \addplot[name path=C, domain=0:60,thick, color=black]{x};
    \draw[dashed] (axis cs:15,0) -- (axis cs:15,60);
    \draw[dashed] (axis cs:45,0) -- (axis cs:45,60);
    \draw[dashed] (axis cs:15,60) -- (axis cs:45,60);
    \draw[dashed] (axis cs:15,10) -- (axis cs:0,10);
    \draw[dashed] (axis cs:15,20) -- (axis cs:0,20);
    \draw[dashed] (axis cs:45,40) -- (axis cs:0,40);
    \draw[dashed] (axis cs:45,50) -- (axis cs:0,50);
    \addplot [
        thick,
        color=blue,
        fill=black!20, % 20% 蓝色阴影
    ]
    fill between[
        of=A and C,
        soft clip={domain=15:45}, % 限制阴影范围
     ];
     \addplot [
        thick,
        color=blue,
        fill=red!20, % 20% 蓝色阴影
    ]
    fill between[
        of=B and C,
        soft clip={domain=15:45}, % 限制阴影范围
     ];
  \end{axis}
\end{tikzpicture}
```
### 正态函数曲线
![[Pasted image 20240510195045.png|500]]
```
\begin{tikzpicture}
\begin{axis}[
    axis lines=middle,
    enlargelimits=true,
    xlabel=$x$,
    ylabel=$y$,
    domain=-3:3,
    samples=100,
    ytick=\empty,
    xtick={-2.00},
    xticklabels={$t=-1.5$}
]
    % 正态分布曲线
    \addplot [smooth, thick] {exp(-x^2/2)/sqrt(2*pi)};
    % 高亮t右侧区域
    \addplot [smooth, thick, fill=red, domain=-3:-2.00] {exp(-x^2/2)/sqrt(2*pi)} \closedcycle;
    % 标记点t
    \node[label={270:{}},circle,fill,inner sep=2pt] at (axis cs:2.00,0) {};
\end{axis}
\end{tikzpicture}
```
## 插入图片 **