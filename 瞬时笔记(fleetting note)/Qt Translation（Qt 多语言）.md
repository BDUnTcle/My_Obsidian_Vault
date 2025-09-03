#QT/QT5 #QT/QT第三方开发 #QT/QT跨平台编程
# 对所有的文本使用 tr()

# 官方接口学习笔记
## translate(const char *context, const char *sourceText, const char *disambiguation = nullptr, int n = -1)

这个接口用来在代码中实现基于qm文件的翻译，用于编写实际代码时需要翻译的情况。**由于使用Qt 语言家生成的翻译文件只能涵盖UI界面中的翻译**
### 对于参数一：context的理解
*”context“* 顾名思义，即为上下文的意思。那么，在这里其上下文具体指的是什么呢？
要知道，这个接口是通过qm文件来执行翻译的。而qm文件又由工程中的.ts文件生成。打开一个.ts文件可以看到，其中每一个具体翻译的message节点，都有其context的name。
因此要想成功调用translate，就要使用对应.ts文件内的信息才行
![[微信图片_20230314165114.png]]
### 使用示例
```C++
QTanslator* m_translator = new QTranslator();
m_translator->load(":/translator_file.qm"); //进行翻译之前，需要加载翻译文件
QString name = m_translator->translate("epicPointCloudTransfer","message");//如果成功，会根据qm文件内的翻译返回。如果失败，返回空
```
