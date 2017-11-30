# com.cnnct.utils.CacheUtil    缓存管理工具类

| `static java.lang.Boolean` | [`checkReqCode`](../../../com/cnnct/utils/CacheUtil.html#checkReqCode-java.lang.Object-)`(java.lang.Object reqCode)`判断reqCode对象是否存在 |
| :--- | :--- |
| `static com.cnnct.po.custom.SysActionLogCust` | [`getActionLog`](../../../com/cnnct/utils/CacheUtil.html#getActionLog-javax.servlet.http.HttpServletRequest-)`(javax.servlet.http.HttpServletRequest request)`取出actionLog缓存 |
| `static java.lang.Object` | [`getActionLog`](../../../com/cnnct/utils/CacheUtil.html#getActionLog-java.lang.Object-)`(java.lang.Object key)`取出actionLog缓存 |
| `static java.lang.String` | [`getChineseByTypeDetailState`](../../../com/cnnct/utils/CacheUtil.html#getChineseByTypeDetailState-java.lang.Object-java.lang.Object-java.lang.Object-)`(java.lang.Object orderType, java.lang.Object orderTypeDetail, java.lang.Object orderState)`根据orderType+orderTypeDetail+orderState返回orderStateChinese |
| `static java.lang.String` | [`getCodeNameBySysCode`](../../../com/cnnct/utils/CacheUtil.html#getCodeNameBySysCode-java.lang.String-java.lang.String-)`(java.lang.String codeType, java.lang.String codeValue)`根据SYS\_CODE表的code\_Type和code\_Value字段,获得code\_Name的值，否则返回空字符串 |
| `static java.lang.String` | [`getCodeValueBySysCode`](../../../com/cnnct/utils/CacheUtil.html#getCodeValueBySysCode-java.lang.String-java.lang.String-)`(java.lang.String codeType, java.lang.String codeName)`根据SYS\_CODE表的code\_Type和code\_Name字段,获得code\_Value的值，否则返回空字符串 |
| `static java.lang.Object` | [`getErrCode`](../../../com/cnnct/utils/CacheUtil.html#getErrCode-java.lang.Object-)`(java.lang.Object key)`根据errCode值 |
| `static java.lang.String` | [`getErrMsgByErrCode`](../../../com/cnnct/utils/CacheUtil.html#getErrMsgByErrCode-java.lang.Object-)`(java.lang.Object key)`根据错误码获取错误描述 |
| `static java.lang.String` | [`getFieldNameBySysCode`](../../../com/cnnct/utils/CacheUtil.html#getFieldNameBySysCode-java.lang.String-java.lang.String-)`(java.lang.String codeType, java.lang.String codeValue)`根据SYS\_CODE表的code\_Type和code\_Value字段,获得field\_Name的值，否则返回空字符串 |
| `static java.util.Map<java.lang.String,java.lang.Object>` | [`getMapValue`](../../../com/cnnct/utils/CacheUtil.html#getMapValue-javax.servlet.http.HttpServletRequest-)`(javax.servlet.http.HttpServletRequest request)`取出map缓存 |
| `static java.lang.Object` | [`getMapValue`](../../../com/cnnct/utils/CacheUtil.html#getMapValue-java.lang.Object-)`(java.lang.Object key)`取出map缓存 |
| `static java.lang.Object` | [`getOperSes`](../../../com/cnnct/utils/CacheUtil.html#getOperSes-java.lang.Object-)`(java.lang.Object key)`通过sessionId得到operId |
| `static java.lang.String` | [`getParaValueByCode`](../../../com/cnnct/utils/CacheUtil.html#getParaValueByCode-java.lang.String-)`(java.lang.String paraCode)`根据para\_Code返回Sys\_Para.para\_Value值 |
| `static boolean` | [`getRedisFlag`](../../../com/cnnct/utils/CacheUtil.html#getRedisFlag--)`()`判断是否启用了redis |
| `static com.cnnct.po.custom.SysInterfaceReqcodeCust` | [`getReqCodeTrByReqCode`](../../../com/cnnct/utils/CacheUtil.html#getReqCodeTrByReqCode-java.lang.Object-)`(java.lang.Object reqCode)`根据reqCode返回SysInterfaceReqcodeCust对象 |
| `static java.util.Map` | [`getSession`](../../../com/cnnct/utils/CacheUtil.html#getSession-java.lang.Object-)`(java.lang.Object key)`根据operId获取用户session相关数据map，支持redis和ehcache |
| `static com.cnnct.po.custom.SysCodeTrCust` | [`getSysCodeTrByTrCode`](../../../com/cnnct/utils/CacheUtil.html#getSysCodeTrByTrCode-java.lang.Object-)`(java.lang.Object trCode)`根据tr\_Code返回SysCodeTrCust对象 |
| `static com.cnnct.po.custom.SysParaCust` | [`getSysParaByCode`](../../../com/cnnct/utils/CacheUtil.html#getSysParaByCode-java.lang.String-)`(java.lang.String paraCode)`根据para\_Code返回SysParaCust对象 |
| `static java.lang.String` | [`getTrCodeNameByTrCode`](../../../com/cnnct/utils/CacheUtil.html#getTrCodeNameByTrCode-java.lang.Object-)`(java.lang.Object trCode)`根据交易代码tr\_Code返回Sys\_Code\_Tr.code\_Name值 |
| `static void` | [`putActionLog`](../../../com/cnnct/utils/CacheUtil.html#putActionLog-javax.servlet.http.HttpServletRequest-com.cnnct.po.custom.SysActionLogCust-)`(javax.servlet.http.HttpServletRequest request, com.cnnct.po.custom.SysActionLogCust value)`将actionLog放入缓存 |
| `static void` | [`putActionLog`](../../../com/cnnct/utils/CacheUtil.html#putActionLog-java.lang.Object-java.lang.Object-)`(java.lang.Object key, java.lang.Object value)`将actionLog放入缓存 |
| `static void` | [`putErrCode`](../../../com/cnnct/utils/CacheUtil.html#putErrCode-java.lang.Object-java.lang.Object-)`(java.lang.Object key, java.lang.Object value)`errCode存放单个对象 |
| `static void` | [`putInterfaceLog`](../../../com/cnnct/utils/CacheUtil.html#putInterfaceLog-javax.servlet.http.HttpServletRequest-java.util.Map-)`(javax.servlet.http.HttpServletRequest request, java.util.Map<java.lang.String,java.lang.Object> map)`已过时。暂未使用 将interfaceLog放入缓存 |
| `static void` | [`putMapValue`](../../../com/cnnct/utils/CacheUtil.html#putMapValue-javax.servlet.http.HttpServletRequest-java.util.Map-)`(javax.servlet.http.HttpServletRequest request, java.util.Map<java.lang.String,java.lang.Object> map)`已过时。暂未使用 将map放入缓存 |
| `static void` | [`putOperSes`](../../../com/cnnct/utils/CacheUtil.html#putOperSes-java.lang.Object-java.lang.Object-)`(java.lang.Object key, java.lang.Object value)`用户session放入缓存 |
| `static void` | [`putSession`](../../../com/cnnct/utils/CacheUtil.html#putSession-java.lang.Object-java.util.Map-)`(java.lang.Object key, java.util.Map value)`根据operId存放用户session相关数据map，支持redis和ehcache |
| `static void` | [`removeActionLog`](../../../com/cnnct/utils/CacheUtil.html#removeActionLog-javax.servlet.http.HttpServletRequest-)`(javax.servlet.http.HttpServletRequest request)`移除actionLog缓存 |
| `static void` | [`removeMapValue`](../../../com/cnnct/utils/CacheUtil.html#removeMapValue-javax.servlet.http.HttpServletRequest-)`(javax.servlet.http.HttpServletRequest request)`移除map缓存 |
| `static void` | [`removeOperSes`](../../../com/cnnct/utils/CacheUtil.html#removeOperSes-java.lang.Object-)`(java.lang.Object key)`通过sessionId删除OperId |
| `static void` | [`removeSession`](../../../com/cnnct/utils/CacheUtil.html#removeSession-java.lang.Object-)`(java.lang.Object key)`根据operId移除用户session相关数据map，支持redis和ehcache |





