#CS/Python #CS/编程语言/Python #CS/编程语言 #程序员 

---
# 第三方库的安装
## 使用pip 命令
pip is the [package installer](https://packaging.python.org/guides/tool-recommendations/) for Python. You can use pip to install packages from the [Python Package Index](https://pypi.org/) and other indexes

---
# 学习资料
[Github:100 天Python](https://github.com/jackfrued/Python-100-Days/blob/master/Day01-15/02.%E8%AF%AD%E8%A8%80%E5%85%83%E7%B4%A0.md)
[[Python summary notes.pdf]]
《Fluent Python》Luciano Ramalho
《Python Crash Course》Eric Marks
《High Performance Python》Micha Gorelick Ozsvald
《Automate The Boring Stuff With Python》
《Python Playground》Mahesh Venkitachalam
《A Smarter Way to Learn Python》
《Machine Learning for Absolute Beginners: [https://amzn.to/2Gs0koL](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbjQ5aDBVaWpJWkdFNnZCWEpPTmY0RW1GNTlMd3xBQ3Jtc0tucVZuY2ZoMzdWc3AtdVNEZGxXN25KOFh5ZnVjTGM4a0xCeEhJaFNxVmtJcHR3WDQ4T2N6d3NSMlJrUUdvSlVqRFhxWGp3TTZKWDFiV1c2T1JzYVBiZFFCeVBCSmUxUGt5aHByUXd4TE80WGg0T3BwRQ&q=https%3A%2F%2Famzn.to%2F2Gs0koL&v=_uQrJ0TkZlc)》
《Hands-on Machine Learning with scikit-learn and TensorFlow: [https://amzn.to/2IdUuJy](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbk1wdHM1Q2czMnFfM3l0WDRyRzZiT0lxcGpNZ3xBQ3Jtc0tuMzRlQl9Pd29VMkpHQllIUE5hX0xyWGE3dGhzSTFMOUpzNW1PM2RyXzk2QjNHRXNFMW1pSzhVQXlRX2ZBZy1odEt6SE1EQnB0MVhrZ1RPWXVaTlo5U19yN0pzYS14S3laMUZid0dQYk1XVzhrb3k3dw&q=https%3A%2F%2Famzn.to%2F2IdUuJy&v=_uQrJ0TkZlc)》

---
# 零散的知识
`__name__` 和 `__main__` 是 python 中隐含的变量
- `__name__` 代表模块的名字
- `__main__` 代表当前执行的模块名
在涉及模块时，如果包含了非函数的执行代码，应该保证模块被调用时这部分代码不要被执行。所以可以使用这两个隐含变量来判断
```python
if __name__ == '__main__':
    print('call foo()')
    foo()
    print('call bar()')
    bar()
```


---
# Dictionaries 
We use dictionaries to store key/value pairs. 

```python
customer = { “name”: “John Smith”, “age”: 30, “is_verified”: True }
customer[“name”] # returns “John Smith” 
customer[“type”] # throws an error 
customer.get(“type”, “silver”) # returns “silver” 
customer[“name”] = “new name”
```

```python
# 创建映射字典
gender_mapping = {'male': 0, 'female': 1}

# 使用 map 函数进行映射转换
df['gender'] = df['gender'].map(gender_mapping)
# 使用 replace 函数替换值
df['gender'].replace({'male': 0, 'female': 1}, inplace=True)

```

 We can use strings or numbers to define keys. They should be unique. We can use any types for the values. 