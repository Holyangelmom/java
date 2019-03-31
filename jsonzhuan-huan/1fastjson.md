# fastjson

### 1、参考文档

[https://www.cnblogs.com/peak911/p/9158060.html](https://www.cnblogs.com/peak911/p/9158060.html)

### 2、fastjson概述

fastJson是阿里提供的快速解析json包，对于json格式的字符串的解析主要用到了一下三个类：

* JSON：fastJson的解析器，用于将JSON格式字符串转换为JSON对象、JSON数组、JavaBean。
* JSONObject：fastJson提供的json对象。
* JSONArray：fastJson提供json数组对象。

JSON类。抽象类，实现了JSONStreamAware和JSONAware接口，这俩接口都只有一个方法。

![](/assets/JSON类.png)

