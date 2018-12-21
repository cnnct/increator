#### Tools公共方法

##### Tools中公共方法有很多，不一一赘述，下面说一些常用的：

各种入参出参的processNull方法：处理对象null，返回空字符串、0等。

processInt\(String str\)：String转int------如果异常,返回-1。

processLong\(String str\)：String转Long------如果异常,返回-1。

processFloat\(String str\)：String转Long------如果异常,返回0。

leftTrim\(String str\)：去左空格。

rightTrim\(String str\)：去右空格。

getMoney\(double money\)：double转String\(钱币\)。

getvalueByObject\(Object o, String str\)：获取未知类型对象的特定属性值。

两种入参的convertToSearch：Map中key转换为search.xxx，用于将使用表格时所写的sql复用化。

camelToUnderline\(String param\)：驼峰转下划线。

underlineToCamel\(String param\)：下划线转驼峰。

underlineToClass\(String param\)：下划线转类名。

checkNull\(String str\)：检查string是不是null。

isNumber\(String str\)：判断字符串是否为纯数字构成。

getParameterMap\(HttpServletRequest request\)：将request中的数据分装成map。

