---
create date: 2024-09-09
tags:
  - review
  - "#程序员"
  - "#Math/Manim"
modification date: 
type: LearningNote
---

>[!summary] Review List
>>

---
# Background & Materials
---
# 介绍/安装 Manim 库

Manim 是一个用于制作数学动画的开源 Python 库，最早由 3Blue1Brown（Grant Sanderson）为他的 YouTube 频道开发。Manim 的全称是 **Mathematical Animation Engine**，它允许用户通过 Python 代码创建精美的动画，特别适合演示数学概念。

Manim 的强大之处在于它可以通过编程控制动画的每个细节，这使得它非常灵活，尤其是对于需要展示复杂数学公式、几何图形和动态过程时。比如，你可以使用它来展示线性代数中的向量变换、微积分中的函数图像，甚至是各种抽象的数学概念。

## 安装 manim 和 ffmpeg（视频渲染支持）

---
# 使用例子
一个简单的 manim 脚本
```python
from manim import *
class CreateCircle(Scene):

    def construct(self):
        circle = Circle()  # 创建一个圆
        circle.set_fill(PINK, opacity=0.5)  # 设置填充颜色和透明度
        self.play(Create(circle))  # 动画地绘制圆

  
class MathFormula(Scene):
    def construct(self):
        formula = MathTex(r"(x+y)^2=x^2+2xy+y^2")  # LaTeX 公式
        self.play(Write(formula))  # 动画地写出公式
```

使用此命令可以用 manim 运行并渲染出视频 `manim -pql example.py CreateCircle` ，这里的 `-pql` 表示 "预览"（preview）和 "低质量"（low quality），这有助于快速渲染和查看结果。