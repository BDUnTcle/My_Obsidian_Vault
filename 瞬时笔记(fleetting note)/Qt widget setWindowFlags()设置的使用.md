#QT/QT5 #QT/QT控件 #QT/QT第三方开发 
# 使用setWindowFlag()方法disable对话框的默认关闭按钮

## QWidget::setWindowFlag(Qt::WindowType flag , bool on = true)
**参数一**：Qt的窗口flag类型
**参数二**：true-启用这个flag，false-禁用这个flag
```c++
QWidget::setWindowFlag(Qt::WindowCloseButtonHint , false);
show()//设置flag后，必须重新调用show 才能让窗口重新显示
```
