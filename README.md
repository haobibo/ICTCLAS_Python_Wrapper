#ICTCLAS_Python_Warpper
Python warpper for ICTCLAS 2014 (or NLPIR 2014).


## ICTCLAS Python 接口
本项目提供了一个利用Python调用ICTCLAS（NLPIR）的便捷的接口，可以通过一个函数调用返回分词后的结果。
具体使用方法示例参见nlpir.py文件当中的main函数。

##常见问题
* 使用之前，请在nlpir.py文件当中，通过参数“libFile”设置正确的库文件，根据操作系统（Linux/Windows）和操作系统位数（32/64 bit），配置正确的库文件（dll/so）。
* 库文件放在项目的nlpir目录下，dll是Windows所需动态链接库，so是Linux所需的动态库，文件名当中的32/64表示操作系统bit数。
* 建议通过Linux调用，如果在Windows下使用，建议使用Pycharm或其他IDE，以正常输出中文。 在Windows CMD下，如果基于Python 2.x，可能会输出乱码，解决方案参见：[这篇文章](http://apoo.bokee.com/7028948.html)。
* 关于利用Python 3.x 进行调用，代码文件当中说明了需要修改的配置，主要的区别是返回值需要从bytes进行类型转换后再使用。
* 关于证书问题：
a. 如果日志文件中出现“License not for system”错误，则是库文件与Data文件的证书文件不匹配；
b. 如果日志文件中出现其他的证书相关的错误，则可能是证书过期。
* 关于证书问题的解决方案是：
a. 移步至[ICTCLAS网站](http://ictclas.nlpir.org/)下载最新的库文件和数据文件；
b. 将下载包当中的库文件（dll/so）更新至nlpir目录下；
c. 将下载包当中的Data文件夹替换掉当前目录下的Data文件夹。
* 当前项目下的库文件是ICTCLAS网站2014-3-24发布的库。
* 当前项目在 Windows 8.1 64bit + [Anaconda](https://store.continuum.io/cshop/anaconda/) 1.9 (Python 2.7.6) + [PyCharm](http://www.jetbrains.com/pycharm/) 3.1.2下测试通过。

## Acknowledgments
* This is just a warpper for the binary distribution of [ICTCLAS](http://ictclas.nlpir.org/).
* This project is released as an open source software by Hao Bibo.

## If you want to:
* Report bug or contribute to project: report an issue through GitHub.
* Know more about the author or contacts: see his [CV](http://en.wikipedia.org/wiki/User:Haobibo) or browse his [Sina Weibo](http://weibo.com/peteraeon).
