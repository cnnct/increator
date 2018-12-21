#### DateUtil公共方法

##### DateUtil中公共方法有很多，不一一赘述，下面说一些常用的：

checkDate\(String dateStr\)：判断日期合法性。

parse\(String date, String pattern\)：转化日期字符串为Date，转化错误返回null。

formatDate\(Date date, String format\)：格式化日期，转为字符串。

formatDate\(Date date\)：以默认的格式格式化日期。

daysBetween\(DateUtil du\)：取两个日期之间的天数。

getNowDate\(\)：获取当前年月日字符串。

getNowTime\(\)：获取当前年月日时分秒字符串。

getYearsFromTwoDate\(Date startDate, Date endDate\)：计算两个日期的间隔年数。

getMonthsFromTwoDate\(Date startDate, Date endDate\)：计算两个日期的间隔月数。

getDaysFromTwoDate\(Date startDate, Date endDate\)：计算两个日期的间隔天数。

getHoursFromTwoDate\(Date startDate, Date endDate\)：计算两个日期的间隔小时数。

getMinutesFromTwoDate\(Date startDate, Date endDate\)：计算两个日期的间隔分钟数。

getSecondsFromTwoDate\(Date startDate, Date endDate\)：计算两个日期的间隔秒数。

processDateAddYear\(String inputDate, int i\)：日期加减i年。

processDateAddMonth\(String inputDate, int i\)：日期加减i月。

processDateAddDay\(String inputDate, int i\)：日期加减i天。

