<bookstore> 根元素
<book category="COOKING" id="000">
  <title lang="en">Everyday Italian</title>
  <author>Giada De Laurentiis</author>
  <year>2005</year>
  <price>30.00</price>
</book>
<book category="CHILDREN" id="111">
  <title lang="en">Harry Potter</title>
  <author>J K. Rowling</author>
  <year>2005</year>
  <price>29.99</price>
</book>
<book category="WEB" id="222">
  <title lang="en">Learning XML</title>
  <author>Erik T. Ray</author>
  <year>2003</year>
  <price>39.95</price>
</book>
</bookstore>


大小写敏感

实体引用（特殊符号转义）
&lt;	<	小于
&gt;	>	大于
&amp;	&	和号
&apos;	'	单引号
&quot;	"	引号


HTML 会把多个连续的空格字符裁减（合并）为一个，在 XML 中，文档中的空格不会被删节

元数据（有关数据的数据）应当存储为属性，而数据本身应当存储为元素
