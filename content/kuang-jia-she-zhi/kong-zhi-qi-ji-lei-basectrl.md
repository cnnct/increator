#### BaseCtrl公共方法

##### BaseCtrl中公共方法有很多，不一一赘述，下面说一些常用的：

nofuncSessionJudge\(HttpServletRequest request\)：判断session是否已失效。

getSessionMap\(\)：得到当前登录用户的sessionMap。

getOper\(\)：得到当前登录用户。

getOperId\(\)：得到当前登录用户的operId。

getOperName\(\)：得到当前登录用户的operName。

getSysBranch\(\)：得到当前登录用户的部门。

getOperOrgan\(\)：得到当前登录用户的机构。

downloadFile\(HttpServletResponse response, String filePath\)：从FTP下载文件公共方法。

downloadFile\(HttpServletResponse response, List&lt;InputStream&gt; iss, List&lt;String&gt; fileNames, String zipName\)：压缩并下载文件公共方法。



