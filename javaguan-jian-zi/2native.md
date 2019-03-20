# native

### 1、认识native

类似 public native int hashCode\(\);一个Native Method就是一个Java调用非Java代码的接口。我们把这类接口称为JNI（Java Native Interface），它提供了若干的API实现了Java和其他语言的通信（主要是C&C++），它允许Java代码和其他语言写的代码进行交互。

![](/assets/JNI为桥梁.png)

2、JNI技术用来做什么 

当一个程序无法完全使用Java编写时,开发者可以通过JNI来编写本地方法,比如标准Java类库并不支持的依赖于平台的特色或者程序库。JNI还可以用于修改现有的使用其它语言编写的程序,使它们可以通过Java编写的程序来访问。

很多基本类库都依赖JNI来为开发者和用户提供服务,比如文件的输入/输出和音频功能。在基本类库中包含的对于性能和平台敏感的API可以允许所有的Java程序以安全和平台无关的方式来使用这些功能。

