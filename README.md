# youbytes
youbytes.com

开发者
--

1. 使用提供搜索页
2. 嵌入HTML页面到网站
3. API接口

-----

## 1. 使用提供搜索页

* 参数

| 参数名称 | 是否可空 | 说明 | 备注 |
| -------- | -------- | -------- | -------- |
| c     | 否     | 连接集名称     |  无   | 
| q     | 是     | 搜索关键字     |   无  | 

[示例](http://www.youbytes.com/public/search.html?c=bookstack%E7%94%B5%E5%AD%90%E4%B9%A6) http://www.youbytes.com/public/search.html?c=bookstack电子书

-----


## 2. 嵌入HTML页面到网站

基于API应用程序接口 jsonp格式 实现编写HTML页面，上传到站点可访问的位置。
--
示例代码: https://github.com/yongpeixu/youbytes

-----

## 3. API接口

API以json或jsonp格式返回结构化数据。

如果此API可以帮助您，请在您的网站上添加 https://www.youbytes.com

### 搜索

返回搜索结果, [示例](https://www.youbytes.com/api/query?c=bookstack%E7%94%B5%E5%AD%90%E4%B9%A6&q=vue) https://www.youbytes.com/api/query?c=bookstack电子书&q=vue

* 接口地址
https://www.youbytes.com/api/query

* 参数

| 参数名称 | 是否可空 | 说明 | 备注 |
| -------- | -------- | -------- | -------- |
| c     | 否     | 连接集名称     |  无   | 
| q     | 否     | 搜索关键字     |   无  | 


* 返回示例
```
{
    "data":{
        "items":[
            {
                "description":"...使用 <strong>vue</strong>-cli 我们还可以使用 <strong>vue</strong>-cli 初始化项目，命令如下： > npm i -g <strong>vue</strong>-cli> mkdir my-project && cd my-project> <strong>vue</strong> init webpack> npm i && npm i element-ui 引入 Element...",
                "link":"http://www.bookstack.cn/read/element-ui/quickstart",
                "title":"1.2 快速上手 - 《Element-UI使用手册》 - 书栈网(BookStack.CN)"
            },
            {
                "description":"...<strong>Vue</strong> <strong>Vue</strong>.js 基础 可重用的组件 <strong>Vue</strong>.js 指令 Tip <strong>Vue</strong>.js 中的插件 Tip 练习 方程式状态和 Vuex Tip <strong>vue</strong>-cli IDEs 的 <strong>Vue</strong> 插件 安装， 使用， 调试 <strong>Vue</strong>.js 方程式 安装 <strong>Vue</strong>.js...",
                "link":"http://www.bookstack.cn/read/Learning-Vuejs-2-zh_CN/chapter-2-Fundamentals.md",
                "title":"基础 - 《Learning Vue.js 2 中文版》 - 书栈网(BookStack.CN)Vue.js - CSP-compliantVue.js - NPM Installation"
            },
            {
                "description":"...<strong>Vue</strong> 的入口 <strong>Vue</strong> 的定义 initGlobalAPI 总结 从入口开始 我们之前提到过 <strong>Vue</strong>.js 构建过程，在 web 应用下，我们来分析 Runtime + Compiler 构建出来的 <strong>Vue</strong>.js...",
                "link":"http://www.bookstack.cn/read/vue-analysis/4.md",
                "title":"从入口开始 - 《Vue.js 技术揭秘》 - 书栈网(BookStack.CN)"
            }
            {
                "description":"",
                "link":null,
                "title":null
            }
        ],
        "itemsPerPage":50,
        "startIndex":1,
        "total":47118,
        "totalResults":2219
    },
    "msg":"OK",
    "result":0
}
```
