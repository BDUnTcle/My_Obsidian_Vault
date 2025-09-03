#Linux/命令 #Linux/sed命令 
[具体讨论地址](https://qastack.cn/programming/148451/how-to-use-sed-to-replace-only-the-first-occurrence-in-a-file)

```
sed '0,/pattern/s/pattern/replacement/' filename
```