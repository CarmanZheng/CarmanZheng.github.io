---
title: flask终结篇整体结构
layout: post
tags: web开发
categories: ''
---

## 1.  COVID-19数据可视化项目

[基于Python+Flask+Echarts]

https://blog.csdn.net/hxxjxw/article/details/105336981?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.channel_param&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.channel_param

b站参考：https://www.bilibili.com/video/BV177411j7qJ?from=search&seid=10787152272334148270

<img src="D:\04_Tianchi\Tianchi_task\HonorZheng.github.io\_posts\images\image-20210302105928578.png" alt="image-20210302105928578" style="zoom:50%;" />

### 1.1爬取数据

爬虫，就是给网站发起请求，并从响应中提取需要的数据。

1.发起请求，获取响应

​		通过http库，对目标站点进行请求。等同于自己打开浏览器，输入网址。 常用库：**urllib，urllib3，requests**

​		服务器会返回请求的内容，一般为：html，二进制文件（视频，音频），文档，json字符串等等。

2.解析内容

​		寻找自己需要的信息，就是利用正则表达式或者其他库提取目标信息。常用库：**re, beautifulsoup4**

3.保存数据

​		将解析到的数据持久化到文件或者数据库中

​	

```python
import requests
url = "http://www.baidu.com"
res = requests.get(url)
print(res.encoding)

print(res.headers) # 里面编码方式为ISO-8859-1，就会出现中文乱码，需要使用utf-8编码才能解析
print(res.url)
print(res.status_code)
```



### 1.2 正则表达式

re是python自带的正则表达式

### 1.3 数据存储到数据库

此处主要在于数据库的设计，难点在于关系型数据库的设计

### 1.4开发项目部署



## 2. echarts+flask+mysql数据可视化多图超实用!!!

https://blog.csdn.net/qq_45032715/article/details/102642762?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-5.channel_param&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-5.channel_param





## 3. 数据可视化：基于 Echarts + Python 实现的动态实时大屏范例二

https://blog.csdn.net/lildkdkdkjf/article/details/106783264?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-6.channel_param&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-6.channel_param

## 4.echarts必看必看！！

https://www.bilibili.com/video/BV12i4y1x71R?from=search&seid=15116136014653105293
