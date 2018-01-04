#### BaseServImpl公共方法

##### BaseServImpl中公共方法有很多，不一一赘述，下面说一些常用的：

getDataBaseDate\(\)：获取当前数据库时间。

setActionLog\(HttpServletRequest request, Integer trCode\)：业务操作将trCode设置到缓存中的SysActionLog对象中。

selectList\(String sql\)：直接执行sql语句查询结果为Map集合\(多条记录\)。

selectOne\(String sql\)：直接执行sql语句查询结果为Map\(一条记录\)。

getSequenceByName\(String sequenceName\)：根据序列名称获取序列\(用于oracle\)。

各种入参的uploadFile方法：上传文件到FTP。

zipUploadFile\(Map&lt;String, Object&gt; map, String zipPath\)：压缩多个文件并上传到FTP

