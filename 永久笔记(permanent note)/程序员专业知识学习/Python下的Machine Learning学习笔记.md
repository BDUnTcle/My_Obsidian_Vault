#CS/Python #CS/编程语言/Python #程序员 #CS/MachineLearning

---
# 一些事前环境准备和相关工具软件安装
## 安装Jupyter工具
一个用来写程序并实时可视化的编辑器，用来做开发
1. Jupyterlab
2. Jupyter notebook
## 嫌麻烦可以直接安装Anaconda Distribution
这是一个集成平台，各种工具和库都有，一键安装傻瓜式
不过软件有点卡，用起来感觉一般。而且我第一次安装就遇到过各种问题。感觉兼容性一般般。第一印象不太好
**但是省事**
PS：我浪费了两个小时时间都没弄好环境，已经放弃了。我选择手动安装三方库。。。
# Libraries（ML相关库）
- Numpy
- Pandas
- MatPlotLib
- Scikit-Learn
### pandas库（用来处理输入数据）
1. read_csv(): 读取一个csv文件
	1. *usecols*：参数可以指定读取csv文件中的哪些列
2. shape()：返回行列数
3. describ()
4. drop()：去掉所给数据集中的指定数据（比如某一列），返回去掉后的新列
#### 检查和处理数据中的NaN
[[Python Pandas库学习笔记及示例代码合集#Deal with NaN in the original data（处理原始数据中的NaN）]]
#### iloc\[\]和loc\[\]
用来根据输入，处理原始数据，并返回一个Series，或者DataFrame（返回依据据input格式不同）
(https://pandas.pydata.org/docs/reference/api/pandas.Series.iloc.html#pandas.Series.iloc)

```python
>>> mydict = [{'a': 1, 'b': 2, 'c': 3, 'd': 4},
...           {'a': 100, 'b': 200, 'c': 300, 'd': 400},
...           {'a': 1000, 'b': 2000, 'c': 3000, 'd': 4000}]
>>> df = pd.DataFrame(mydict)
>>> df
      a     b     c     d
0     1     2     3     4
1   100   200   300   400
2  1000  2000  3000  4000

>>> type(df.iloc[0])#返回指定行，竖着排列
<class 'pandas.core.series.Series'>
>>> df.iloc[0]
a    1
b    2
c    3
d    4
Name: 0, dtype: int64

>>> df.iloc[[0]]#返回指定行，横着排列
   a  b  c  d
0  1  2  3  4
>>> type(df.iloc[[0]])
<class 'pandas.core.frame.DataFrame'>

>>> df.iloc[[0, 1]]#返回数组里的所有行
     a    b    c    d
0    1    2    3    4
1  100  200  300  400

>>> df.iloc[:3]#返回集合里的所有列
      a     b     c     d
0     1     2     3     4
1   100   200   300   400
2  1000  2000  3000  4000

>>> df.iloc[0, 1]#返回第0行第1列
2
>>> df.iloc[[0, 2], [1, 3]]#返回[第0行+第2行] 交 [第1列+第3列]
      b     d
0     2     4
2  2000  4000
```

### sklearn库（ML Model）
#### sklearn.tree Module
- tree.export_graphviz()：将模型生成为.dot类型的文件
##### DecisionTreeClassifier Class

#### sklearn.model_selection Module
##### train_test_split
*train_test_split()*：负责将输入的数据分开成train数据和test数据，可以调整比例，返回一个tuple包含各个数据
#### sklearn.matrics
##### accuracy_score
*accuracy_score()*：计算给定两组数据数据的精确度

```python
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score

X_train, X_test, Y_train, Y_test = train_test_split(X,Y,test_size=0.2)

model.fit(X_train,Y_train)
predictions_2 = model.predict(X_test)

m_accuracy = accuracy_score(Y_test,predictions_2)

m_accuracy
```

### joblib库
- *joblib.dump()/load()*：保存和加载已经训练好的模型

### Numpy（）
# Jupyter 的使用(VS Code插件环境)
## 快捷键
- ESC/Enter：切换到控制模式/切换到编辑模式
- X/C/V：剪切代码块/复制代码块/粘贴代码块
- D D：删除代码块
- M：切换代码块至markdown块
- Ctrl+Alt+Enter：运行当前块
- A / Ctrl+Ship+Enter：在上方插入代码块
- B：在下方插入代码块
- Shift+Win+Alt+J：将本代码块和上一个代码块合并
- Win+Alt+J：将本代码块和后一个代码块合并
- Ctrl+Shift+ - ：切分代码块