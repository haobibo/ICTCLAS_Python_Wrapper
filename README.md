#ICTCLAS Python Warpper
Python warpper for ICTCLAS 2014 (or NLPIR 2014).

NLPIR（ICTCLAS）中文分词系统Python接口。

## ICTCLAS Python 接口
本项目提供了一个利用Python调用ICTCLAS（NLPIR）的便捷的接口，可以通过一个函数调用返回分词后的结果。
具体使用方法示例参见nlpir.py文件当中的main函数。

## 使用说明 ##
* 温馨提示：如果您是Python初学者请您特别留意（非初学者跳过）：
	* 您的操作系统位数与Python程序的位数是否匹配（因为64bit Windows下是可以运行32bit的Python程序的），如果不匹配，请您正确安装位数匹配的Python程序。
	* 您使用的Python版本，目前Python存在2.x和3.x两类主流版本，这两个版本存在着较大的差异，如果您还不确定您要使用哪个版本，请您使用Python2.7.x，并且可以直接考虑下载安装集成了诸多科学计算包的[Anaconda](https://store.continuum.io/cshop/anaconda/) 2.0 (Python 2.7.6)。除非你有确切的技术理由，否则不建议为了“追新”使用Python3.x。

* 使用之前，请在nlpir.py文件当中，通过参数“libFile”设置正确的库文件，根据操作系统（Linux/Windows）和操作系统位数（32/64 bit），配置正确的库文件（dll/so）。

* 库文件放在项目的nlpir目录下，dll是Windows所需动态链接库，so是Linux所需的动态库，文件名当中的32/64表示操作系统bit数。


* 建议通过Linux调用，如果在Windows下使用，建议使用Pycharm或其他IDE，以正常输出中文。 在Windows CMD下，如果基于Python 2.x，可能会输出乱码，解决方案参见：[这篇文章](http://apoo.bokee.com/7028948.html)。
 当前项目在 Windows 10(TechPreview) 64bit + [Anaconda](https://store.continuum.io/cshop/anaconda/) 2.1 (Python 2.7.8) + [PyCharm](http://www.jetbrains.com/pycharm/) 4.0下测试通过。

* 目前的代码针对Python2.7.x设计，如果您要用Python 3.x进行调用，代码文件当中说明了需要修改的配置，主要的区别是返回值需要从bytes进行类型转换后再使用，细节在代码文件当中有描述，或者您也可以参照“常见问题”中关于Python3.x调用的说明部分。

##常见问题
**当系统不能正常运行时，请您首先仔细耐心查看程序的错误栈或者系统的错误日志，然后参照下面的提示进行解决。下面列出的几个常见问题，涵盖了截止到目前为止作者通过邮件、微博私信等所有方式得到的使用者的反馈。请尊重他人的时间，确认下面列出的方法无法解决您的问题之后再向作者发信息提问。**

###调用分词程序时系统初始化出错的问题：
* 问题表现：在Python弄程序当中，进行初始化或分词时候，代码抛出“Initialization failed!”等异常。

* 出错原因：本Python程序只是一个接口程序，当出现上述问题时，绝大多数情况都是由于NLPIR（ICTCLAS）组件分词出错导致的。当您看到这样的错误时，请首先到程序的Data目录下，查看是否有文件名为“YYYYMMDD.err”（YYYYMMDD为日期）的错误输出文件，该文件由NLPIR（ICTCLAS）组件生成，具体指明了错误原因。错误原因一般包括：

* 原因一» 数据文件未正确配置的问题：如果日志文件中出现“Cannot Open Configure file”，则是因为您的Data文件未正确配置导致的。解决方案为：	请确认您再代码中调用Init函数的第一个参数（数据文件路径），与Data存放的目录相匹配，如果您传入的该参数为空字符串，则默认为当前python代码的路径。

* 原因二» 关于证书与程序不匹配、过期、无效的问题：如果日志文件中出现“License not for system”错误，则是库文件与Data文件的证书文件不匹配；如果日志文件中出现“Not valid license or your license expired”错误，则是证书文件到期、损坏、或不存在等；关于证书问题的解决方案如下：
	* 移步至[ICTCLAS网站](http://ictclas.nlpir.org/)下载最新的库文件和数据文件；
	* 将下载包当中的库文件（dll/so）更新至nlpir目录下，替换时注意您的操作系统、操作系统位数、Python程序位数(32/64bit)、程序库(dll/so)位数的匹配；
	* 将下载包当中的Data文件夹替换掉当前目录下的Data文件夹。

### **【证书问题特别说明】** ###
* 在2014年6月上旬，ICTCLAS证书出现使用问题，表现为：2014-3-24发布的版本、2014-4-28（百度网盘）共享的版本，运行时均出现证书过期的问题。该问题是由于ICTCLAS本身的问题导致的，最佳解决方案是与ICTCLAS原作者取得联系提示其更新证书。

* 当前项目下的库文件是ICTCLAS网站2014-09-26发布的程序库及数据文件，经测试，到目前仍可正常使用。
您可以自行更新到其他时间的发布包以满足您的需求。不同时间发布的程序库，在本项目代码中以“Patch_YYYYMMDD.zip”的形式命名，下载后将原来代码中的nlpir目录和Data目录替换，

* 经测试，20131219发布的程序版本截止可用，改版本为2013年底推出的2014测试版，可以正常进行分词，但分词模型可能较旧。

* 如果出现了其他关于证书的问题，在您尝试了更新ICTCLAS程序包后仍不能解决的，这样的证书问题不属于Python接口能解决的范畴，请联系ICTCLAS原作者解决证书问题。

###关于Python3.x调用的问题
代码文件当中说明了需要修改的配置，主要的区别是返回值需要从bytes进行类型转换后再使用，请从代码中搜索以“###”开始的行，这些用“###”注释掉的行是针对Python3.x的，而这些代码前一行或者后一行的代码是Python2.7.x调用需要的代码，如果您确认您要用Python3.x调用，修改这三四行代码就可以解决问题。

## Acknowledgments
* This is just a warpper for the binary distribution of [ICTCLAS](http://ictclas.nlpir.org/).
* This project is released as an open source software by Hao Bibo.
* To know more about the author or contacts: see his [CV](http://en.wikipedia.org/wiki/User:Haobibo) or browse his [Sina Weibo](http://weibo.com/peteraeon).
    > **OFFER DESIRE**: the author is now eager for a PhD or job offer from top univeristies or research institutions, top IT companies as well. If you have interests after you read my CV, please feel free to contact me.

## If you want to:
* Report bug or contribute to project: report an issue through GitHub.

* If you like this program, please Start it on its GitHub Page.

* Donate to the author: the author will be grateful if you dontae through his ZhiFuBao(AliPay) account, scan the QR code with you Alipay Cellphone APP.

![](https://raw.githubusercontent.com/haobibo/ICTCLAS_Python_Warpper/master/AliPay-Peter_Howe.png)