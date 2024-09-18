#一、代理和翻墙设置
- 翻墙工具自己搞定
- 代理设置，端口可自己设置（一定要在WIN+R CMD进去终端设置代理）
- 然后打开谷歌网址测试一下[Google](https://www.google.com/)

Windows
~~~
set http_proxy=127.0.0.1:7890
set https_proxy=127.0.0.1:7890
~~~
Mac
~~~
export http_proxy=127.0.0.1:7890
export https_proxy=127.0.0.1:7890
~~~
测试是否翻墙
~~~
curl accounts.google.com
~~~
返回下面代码信息就是表示成功

![](https://upload-images.jianshu.io/upload_images/4369261-e89f4ea2dfb601ea.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#二、检查项目
~~~
flutter pub publish --dry-run
~~~
- CHANGELOG 版本记录
- LINCENSE 开源文件
- READNE 使用说明

#三、项目配置
pubspec文件
~~~
version: 版本号
homepage: GitHub项目地址
~~~

#四、发布
测试是否翻墙
~~~
curl accounts.google.com
~~~
复制下面命令直接运行
~~~
flutter packages pub publish --server=https://pub.dartlang.org
~~~
####会有一下几个步骤
1. 检查项目
2. 询问是否发布 y就行
3. 授权：把地址复制到浏览器打开就行
4. 等待上传
5. 恭喜你，发布成功，过一会就可以在[Dart packages](https://pub.dev/)
   搜索到了

#五、注意
- 第一点最为重要
### 问题一
~~~
It looks like accounts.google.com is having some trouble.
Pub will wait for a while before trying to connect again. 
OS Error: Operation timed out, errno = 60, 
address = accounts.google.com, port = 53481 
pub finished with exit code 69
~~~
原因：
1. 国内墙
2. flutter环境配置添加了国内镜像

解决方式：
1. 翻墙
2. 屏蔽环境变量里关于flutter的国内镜像
   屏蔽方式如下：
~~~
export PUB_HOSTED_URL=https://pub.flutter-io.cn
~~~
~~~
export FLUTTER_STORAGE_BASE_URL=https://storage.flutter-io.cn
~~~
3. 设置终端（CMD）代理命令(第一点)