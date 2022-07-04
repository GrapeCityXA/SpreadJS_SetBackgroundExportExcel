# SpreadJS_SetBackgroundExportExcel
在纯前端在线表格中实现设置背景导出 Excel功能
# SpreadJS_SetBackgroundExportExcel
在纯前端在线表格中实现设置背景导出 Excel功能

### SpreadJS 示例，单元格设置图片后导出到Excel
该示例包括使用 SpreadJS API 的演示脚本，可用于实现单元格设置图片后导出到Excel
有关 SpreadJS API 的更多信息，请参阅[SpreadJS API指南]( https://demo.grapecity.com.cn/spreadjs/help/api/) 和[帮助手册]( https://help.grapecity.com.cn/pages/viewpage.action?pageId=5963808)。



### 运行步骤
1、在开始之前，请确保您已满足以下先决条件：
要运行 SpreadJS，浏览器必须支持 HTML5，客户端导入和导出 Excel 需要 IE10及以上。
请先了解 [SpreadJS 的产品使用环境]( https://www.grapecity.com.cn/developer/spreadjs/selection-guide/product-use-environment)，并申请临时部署授权激活
安装并更新NodeJS和NPM
2、克隆或下载此代码库
3、初始化控件，并运行示例脚本
#### 控件初始化
首先，创建一个新页面，并在页面上输入以下代码：
```
<!DOCTYPE html>
    <html>
    <head>
        <title>SpreadJS HTML Test Page</title>
```
2、在页面中添加对 SpreadJS 的引用。代码如下。需要注意的是，SpreadJS 提供压缩过
```
//（minified）的 JavaScript 文件和和用于调试的文件：
<script src="[Your_Scripts_Path]/gc.spread.sheets.all.xxxx.min.js" type="text/javascript"></script>
```
3、添加 CSS 文件以改变Spread.JS 的外观。默认的CSS文件名为： 
gc.spread.sheets.xxxx.css，里面包含了所有的默认样式。该 CSS 文件将会影响滚动条，筛选框及其子元素，单元格和下方标签栏的样式。引入 CSS 的代码如下：
```
//<link href="[Your_CSS_Path]/gc.spread.sheets.xxxx.css" rel="stylesheet" type="text/css"/>
```
4、添加产品授权，代码为（本地测试可以不添加）：
```
GC.Spread.Sheets.LicenseKey = "xxx";
```
5. 添加控件初始化代码。本例会在一个 id 为 “ss” 的 DOM 元素上初始化 SpreadJS：
```
<script type="text/javascript">
// Add your license
// If run this in local for testing, remove or comment below code
 GC.Spread.Sheets.LicenseKey = "xxx";

// Add your code
 window.onload = function(){
var spread = new GC.Spread.Sheets.Workbook(document.getElementById("ss"),{sheetCount:3});
var sheet = spread.getActiveSheet();
 }
</script>
</head>
<body>
```
6、 创建一个 id 为 “ss” 的元素，SpreadJS 将在该 DOM 中初始化：
```
<div id="ss" style="height: 500px; width: 800px"></div>
</body>
</html>
```
#### 示例代码
```
HTML：
<p>单元格设置图片后导出到Excel</p>
<input type="button" id="saveExcel" value="export" class="button">
<div id='ss'></div>

CSS：
#ss {
    height: 400px;
    width: 100%
}
p{
    color: #336699;
    text-align: center;
}
.button{
    margin-bottom: 10px;
}

JavaScript：
GC.Spread.Common.CultureManager.culture('zh-cn');

$(document).ready(function() {
    var picture = 'data:img/jpg;base64,iVBORw0KGgoAAAANSUhEUgAAACUAAAAlCAIAAABK/LdUAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAJcEhZcwAAEnQAABJ0Ad5mH3gAAAKWSURBVFhH7ZX7T5JRGMf9v1przZZdt66T1DDnWlNnkYvyMkHUZvNCmoWJiOQQoeUFzVJwEVoaLi+zqExns5qXFBTLJATXkzyzt+flvGOzH/zh/ez7C+f5fs/Le97znBMjIiKy6/nlDwy9cNdXdZRkG65frE6XlF5LrSqW62vLW/vso77lH+jbOcGNYJvpefIx1Yk9cpYksXmNmi7fCvOpP9f8MA/+EGBs6OOlMyVkdpYS4xS2Dhcmt1hdWXN0D6tVpqRDiqoiM46ycPaMkBmj0UND77c5b3/vWGVhc0Jc/vZ4fGwuzhuR8deT21auTu/LVlyuLVc2Fcn1SYeVpCosV99bnJ2P5EAecYNMuh7Pog8dW18FFvDs/hxiY6ks34hJgrneRqygNyNTWP6XhVnv+SPRvihmCAkH/657WNZmJ9YiAX+F+PnKz7xv0dsxwGXCPUOsF44XYo1NbrqGpECn9t7ISbvX3T44P+tBHx+njW5L2NBYY/O0dYCklDLt4sIylgWAc4Qka8pasMYG+oykjNpurLH4NDkL3SOTqkkyL6MGHWweaLpIqqG6E2uEqQ9fWoyOK9IKEuBq2bOKbgb8LQYdjDUu0LzEF1HCr1h3u5344SjAGqHgah2xslShbFr7vo4xDvCdiBNkNfdhmTDqmiBWAUFfP2p8Bof4zPS8e2z6ScvLzMRy4gHJktU4O59gMAS3CQmkniy+c9OSlVJJxqMRnMsCF9MfVFm6sFV6tEBf3Tk8+D4UCsH4Zmgz+tUOK+Nc6dzXpfC0TCbffdaq22CV/OsBHOLQanTwFyCiDHcfBwIbGNsJ3iWfpcHO78uw0uJv6Sqt0FTo/o/AVeDqd8MdBDvFZn014BiHjYM1ERGR3U1MzG/dmjY5fcSQGwAAAABJRU5ErkJggg==';
    var excelIo = new GC.Spread.Excel.IO();
    var spread = new GC.Spread.Sheets.Workbook(document.getElementById("ss"), {
        sheetCount: 3
    });
    var sheet = spread.getActiveSheet();
    var picture = sheet.pictures.add("f2", picture, 20, 20, 37, 37);
    picture.startRow(0);
    picture.startColumn(0);
    picture.startRowOffset(0);
    picture.startColumnOffset(0);
    picture.endRow(1);
    picture.endColumn(1);
    picture.endRowOffset(0);
    picture.endColumnOffset(0);
    picture.allowMove(false);
    //picture.fixedPosition(true);
    $("#saveExcel").click(function() {
        fileName = 'picture.xlsx';

        var json = spread.toJSON();

        // here is excel IO API
        excelIo.save(json, function(blob) {
            saveAs(blob, fileName);
        }, function(e) {
            // process error
            console.log(e);
        });

    });

});
```
#### 关于 SpreadJS
[SpreadJS]( https://www.grapecity.com.cn/developer/spreadjs) 是一款基于 HTML5 的纯前端表格控件，兼容 450 多种 Excel 公式，具备“高性能、跨平台、与 Excel 高度兼容”的产品特性。使用 SpreadJS，可直接在 Angular、 React、 Vue 等前端框架中实现高效的模板设计、在线编辑和数据绑定等功能，为最终用户提供高度类似 Excel 的使用体验。

