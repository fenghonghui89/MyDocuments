
<a href="http://www.w3school.com.cn">xxxxx</a>
<a></a> - 标签
xxxxx - 元素
href="http://www.w3school.com.cn" - 属性 大小写不敏感 要加引号

字符实体
如果希望正确地显示预留字符，我们必须在 HTML 源代码中使用字符实体（character entities）。如需显示小于号，我们必须这样写：&lt; 或 &#60;
&nbsp;或者&#160; - 半角的不断行的空白格
&ensp; - 半角的空格
&emsp;  - 全角的空格
%20用于url


URL 编码
URL 只能使用 ASCII 字符集来通过因特网进行发送。
由于 URL 常常会包含 ASCII 集合之外的字符，URL 必须转换为有效的 ASCII 格式。
URL 编码使用 "%" 其后跟随两位的十六进制数来替换非 ASCII 字符。
URL 不能包含空格。URL 编码通常使用 + 来替换空格。


颜色值
颜色由一个十六进制符号来定义，这个符号由红色、绿色和蓝色的值组成（RGB）。
每种颜色的最小值是0（十六进制：#00）。最大值是255（十六进制：#FF）。
例如#00FF00对应rgb(0,255,0)


标签
被包含的div的宽度会累加,当宽度和超过父div的宽度,会另起一行

<div id="header">     <h1>Main Title of Web Page</h1> </div>

<style type="text/css">     div#container{width:500px}     div#header {background-color:#99bbbb;}     div#menu {background-color:#ffff99; height:200px; width:100px; float:left;}     div#content {background-color:#EEEEEE; height:200px; width:400px; float:left;}     div#footer {background-color:#99bbbb; clear:both; text-align:center;}     h1 {margin-bottom:0;}     h2 {margin-bottom:0; font-size:14px;}     ul {margin:0;}     li {list-style:none;} </style>


html dom
DOM 处理中的常见错误是希望元素节点包含文本。
在本例中：<title>DOM 教程</title>，元素节点 <title>，包含值为 "DOM 教程" 的文本节点。
可通过节点的 innerHTML 属性来访问文本节点的值。


默认情况下，所有 HTML 元素的位置都是静态的，并且无法移动。如需对位置进行操作，记得首先把元素的 CSS position 属性设置为 relative、fixed 或 absolute
