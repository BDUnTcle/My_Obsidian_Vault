#MachineLearning/pandas #CS/Python #CS/编程语言/Python #CS/MachineLearning 

---
# Data Preprocessing Before using model（预处理数据）
## Deal with NaN in the original data（处理原始数据中的NaN）
[[Python下的Machine Learning学习笔记#检查和处理数据中的NaN]]
1. Using `isna()` or  `isnull()` 。这两个方法的作用是相同的，都用于检测缺失值。这会输出一个布尔值的 DataFrame，其中 True 表示对应位置的值是 NaN，False 表示不是 NaN。这样你就可以看到哪些位置有缺失值了。
2. Also can use `isna().any()` or `isnull().any()` 来检查是否有任何列包含 NaN 值。这将返回一个布尔值的 Series，其中每个值表示对应列是否包含 NaN 值。True 表示该列包含 NaN，False 表示该列不包含 NaN。
处理 DataFrame 中包含 NaN 值的方法通常取决于你的数据以及你希望如何处理缺失值。以下是一些常见的处理方法：
1. **删除包含 NaN 的行或列**：
    - `dropna()` 方法可以删除包含 NaN 值的行或列。你可以通过指定 `axis` 参数来选择删除行（`axis=0`）还是删除列（`axis=1`）。
    - 但是要注意，删除 NaN 值可能会导致数据丢失过多，因此应该在确保不会丢失重要信息的情况下使用。
2. **填充缺失值**：
	- `fillna()` 方法可以用指定的值填充 NaN 值。
	- 填充可以使用单个值（如常数）、列的平均值、中位数或者前后值等。

---
# DataFrame操作
## 构造
```python
import pandas as pd # 假设你有一个包含数据的二维数组 
data = [ [1, 'A', True], [2, 'B', False], [3, 'C', True] ] 
# 为每一列指定表头 
columns = ['column1', 'column2', 'column3'] 
# 使用数组构建 DataFrame，并指定表头 
df = pd.DataFrame(data, columns=columns)
```
## 插入行列（insertion）

```python
# Create a DataFrame 
df = pd.DataFrame({'col1': [1, 2, 3], 'col2': ['A', 'B', 'C']}) 
# Insert a new column at a specific position with a specified name 
df.insert(loc=1, column='new_column', value=[4, 5, 6])
```
