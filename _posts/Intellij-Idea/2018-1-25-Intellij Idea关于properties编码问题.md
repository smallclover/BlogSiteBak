---
layout: post
title: Intellij Idea properties前台显示乱码
categories: Intellij Idea
description: Intellij Idea properties前台显示乱码
keywords: Intellij-Idea, jebarin, properties, UTF-8, 乱码, 编码
---
# Intellij Idea properties前台显示乱码

## 问题

+ 测试代码

测试源代码

```java
public class PropertiesTest {

    @Test
    public void testLanguage(){
        ResourceBundle bundle = ResourceBundle.getBundle("globalMessages_zh_CN");
        Assert.assertEquals("用户名", bundle.getString("username"));
    }
}

```

测试properties(格式是UTF-8)

```properties
check=请选择语言
chinese=中文
english=英文
login=登录
password=密码
title=欢迎来到本站
username=用户名
```

+ 测试结果

![乱码](/images/posts/Intellij-Idea/luanma.png)

## 描述

在笔者使用properties配置文件做国际化的时候，遇到了一个很常见的问题，properties文件中的中文在前台读取到之后，就变成了乱码。前台页面显示乱码的原因在笔者所接触的范围内大概有两个，一个是前台的JSP页面设置的编码格式不正确，这里具体指如下两个变量:

```java

pageEncoding="UTF-8" 
contentType="text/html; UTF-8"

```

这两个变量如果设置了与浏览器格式不相符的编码格式可能会造成问题,当然这两个变量之间也有区别：

+ pageEncoding是jsp文件本身的编码

+ contentType的charset是指服务器发送给客户端时的内容编码

这第二个原因就是properties本身文件的编码格式与前台不匹配。比如说properties文件是GBK，而前台（浏览器）是UTF-8,就会造成乱码问题。然而，笔者的Intelij Idea文件编码设置有确实是UTF-8

+ Intellij Idea 文件编码设置界面

File->Settings->Editor->File Encodings

![编码设置](/images/posts/Intellij-Idea/intellijidea-file-encoding-setting.png)


至于这里为何即使采用UTF-8也会出现乱码，网上一说是由于Java解析properties文件是采用字节流读取，所以导致了会将汉字根据字节流读取，具体笔者也没有仔细去深究。_(:з)∠)_

这里提供如下解决方法：

解决方法的原则就是在properties中使用unicode来表示中文

+ 如果你是使用的是Intellij Idea。打开如上图所示编码设置的文件，在Transparent native-to-ascii conversion选择框上点上对号即可。Intellij Idea 会在你输入中文的时候自动将它转成Unicode格式，同时你看到的仍然是中文（当你把刚才点上的对号取消后就可以看到Unicode了），另外需要注意的一点是，如果你在选项没有点上对号的时候输入中文的话，解析出来仍然是乱码。

+ 如果你是其他IDE或者工具的用户，可以选择使用jdk自带的工具native2ascii.exe，该文件在jdk的bin目录中，使用方式请自行google。