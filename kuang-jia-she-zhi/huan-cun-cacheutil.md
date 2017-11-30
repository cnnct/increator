\`\`CacheUtil

com.cnnct.utils

## 类 CacheUtil

* java.lang.Object
* * com.cnnct.utils.CacheUtil

* ---

```
  public class 
  CacheUtil

  extends java.lang.Object
```

缓存管理工具类

* ### 字段概要

  |  |  |
  | :--- | :--- |
  | 限定符和类型 | 字段和说明 |
  | `static net.sf.ehcache.Cache` | [`actionLogCache`](#actionlogcache) |
  | `static net.sf.ehcache.Cache` | [`errCodeCache`](../../../com/cnnct/utils/CacheUtil.html#errCodeCache) |
  | `static net.sf.ehcache.Cache` | [`mapValueCache`](../../../com/cnnct/utils/CacheUtil.html#mapValueCache) |
  | `static net.sf.ehcache.Cache` | [`operSesCache`](../../../com/cnnct/utils/CacheUtil.html#operSesCache) |
  | `static net.sf.ehcache.Cache` | [`reqCodeCache`](../../../com/cnnct/utils/CacheUtil.html#reqCodeCache) |
  | `static net.sf.ehcache.Cache` | [`sessionCache`](../../../com/cnnct/utils/CacheUtil.html#sessionCache) |
  | `static net.sf.ehcache.Cache` | [`sysCodeCache`](../../../com/cnnct/utils/CacheUtil.html#sysCodeCache) |
  | `static net.sf.ehcache.Cache` | [`sysParaCache`](../../../com/cnnct/utils/CacheUtil.html#sysParaCache) |
  | `static net.sf.ehcache.Cache` | [`trCodeCache`](../../../com/cnnct/utils/CacheUtil.html#trCodeCache) |
  | `static net.sf.ehcache.Cache` | [`trOrderCache`](../../../com/cnnct/utils/CacheUtil.html#trOrderCache) |

  * ### 方法概要

    |  |  |
    | :--- | :--- |
    |  |  |
    | 限定符和类型 | 方法和说明 |
    | `static java.lang.Boolean` | [`checkReqCode`](../../../com/cnnct/utils/CacheUtil.html#checkReqCode-java.lang.Object-)`(java.lang.Object reqCode)`判断reqCode对象是否存在 |
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

    * ### 从类继承的方法 java.lang.Object

    `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`
* * ### 字段详细资料
* #### sessionCache

  ```
  public static net.sf.ehcache.Cache sessionCache
  ```
* #### errCodeCache

  ```
  public static net.sf.ehcache.Cache errCodeCache
  ```
* #### actionLogCache

  ```
  public static net.sf.ehcache.Cache actionLogCache
  ```
* #### operSesCache

  ```
  public static net.sf.ehcache.Cache operSesCache
  ```
* #### sysCodeCache

  ```
  public static net.sf.ehcache.Cache sysCodeCache
  ```
* #### sysParaCache

  ```
  public static net.sf.ehcache.Cache sysParaCache
  ```
* #### trCodeCache

  ```
  public static net.sf.ehcache.Cache trCodeCache
  ```
* #### mapValueCache

  ```
  public static net.sf.ehcache.Cache mapValueCache
  ```
* #### reqCodeCache

  ```
  public static net.sf.ehcache.Cache reqCodeCache
  ```
* #### trOrderCache

  ```
  public static net.sf.ehcache.Cache trOrderCache
  ```

  * ### 方法详细资料
* #### putOperSes

  ```
  public static void putOperSes(java.lang.Object key,
                                java.lang.Object value)
  ```

  用户session放入缓存  
  参数:  
  `key`

  * 当前sessionId
    `value`
  * 当前用户operId

* #### getOperSes

  ```
  public static java.lang.Object getOperSes(java.lang.Object key)
  ```

  通过sessionId得到operId  
  参数:  
  `key`

  * sessionId
    返回:

* #### removeOperSes

  ```
  public static void removeOperSes(java.lang.Object key)
  ```

  通过sessionId删除OperId  
  参数:  
  `key`

  * sessionId

* #### putSession

  ```
  public static void putSession(java.lang.Object key,
                                java.util.Map value)
  ```

  根据operId存放用户session相关数据map，支持redis和ehcache  
  参数:  
  `key`

  * operId
    `value`
  * session相关的数据map

* #### removeSession

  ```
  public static void removeSession(java.lang.Object key)
  ```

  根据operId移除用户session相关数据map，支持redis和ehcache  
  参数:  
  `key`

  * operId

* #### getSession

  ```
  public static java.util.Map getSession(java.lang.Object key)
  ```

  根据operId获取用户session相关数据map，支持redis和ehcache  
  参数:  
  `key`

  * operId

* #### putErrCode

  ```
  public static void putErrCode(java.lang.Object key,
                                java.lang.Object value)
  ```

  errCode存放单个对象  
  参数:  
  `key`

  * errCode错误码
    `value`
  * Sys\_Code\_Err对象

* #### getErrCode

  ```
  public static java.lang.Object getErrCode(java.lang.Object key)
  ```

  根据errCode值  
  参数:  
  `key`

  * errCode错误码
    返回:
    Sys\_Code\_Err对象

* #### getErrMsgByErrCode

  ```
  public static java.lang.String getErrMsgByErrCode(java.lang.Object key)
  ```

  根据错误码获取错误描述  
  参数:  
  `key`

  * errCode错误码
    返回:
    错误码对应的描述

* #### putMapValue

  ```
  public static void putMapValue(javax.servlet.http.HttpServletRequest request,
                                 java.util.Map
  <
  java.lang.String,java.lang.Object
  >
   map)
  ```

  已过时。  
  暂未使用 将map放入缓存  
  参数:  
  `key`

  * 当前请求url等信息拼接作为key
    `value`
  * 存放对象

* #### getMapValue

  ```
  public static java.lang.Object getMapValue(java.lang.Object key)
  ```

  取出map缓存  
  参数:  
  `key`

  * 当前请求url等信息拼接作为key
    返回:
    返回map对象

* #### getMapValue

  ```
  public static java.util.Map
  <
  java.lang.String,java.lang.Object
  >
   getMapValue(javax.servlet.http.HttpServletRequest request)
  ```

  取出map缓存  
  参数:  
  `key`

  * 当前请求url等信息拼接作为key
    返回:
    返回map对象

* #### removeMapValue

  ```
  public static void removeMapValue(javax.servlet.http.HttpServletRequest request)
  ```

  移除map缓存  
  参数:  
  `request`

  * 当前请求request

* #### putActionLog

  ```
  public static void putActionLog(java.lang.Object key,
                                  java.lang.Object value)
  ```

  将actionLog放入缓存  
  参数:  
  `key`

  * 当前请求url等信息拼接作为key
    `value`
  * SysActionLogCust对象

* #### putActionLog

  ```
  public static void putActionLog(javax.servlet.http.HttpServletRequest request,
                                  com.cnnct.po.custom.SysActionLogCust value)
  ```

  将actionLog放入缓存  
  参数:  
  `request`

  * 当前请求request
    `value`
  * SysActionLogCust对象

* #### getActionLog

  ```
  public static java.lang.Object getActionLog(java.lang.Object key)
  ```

  取出actionLog缓存  
  参数:  
  `key`

  * 当前请求url等信息拼接作为key
    返回:
    SysActionLogCust对象

* #### getActionLog

  ```
  public static com.cnnct.po.custom.SysActionLogCust getActionLog(javax.servlet.http.HttpServletRequest request)
  ```

  取出actionLog缓存  
  参数:  
  `key`

  * 当前请求url等信息拼接作为key
    返回:
    SysActionLogCust对象

* #### removeActionLog

  ```
  public static void removeActionLog(javax.servlet.http.HttpServletRequest request)
  ```

  移除actionLog缓存  
  参数:  
  `key`

  * 当前请求url等信息拼接作为key

* #### putInterfaceLog

  ```
  public static void putInterfaceLog(javax.servlet.http.HttpServletRequest request,
                                     java.util.Map
  <
  java.lang.String,java.lang.Object
  >
   map)
  ```

  已过时。  
  暂未使用 将interfaceLog放入缓存  
  参数:  
  `key`

  * 当前请求url等信息拼接作为key
    `value`
  * Sys\_Interface\_log

* #### getCodeNameBySysCode

  ```
  public static java.lang.String getCodeNameBySysCode(java.lang.String codeType,
                                                      java.lang.String codeValue)
                                               throws increator.base.exception.CustomException
  ```

  根据SYS\_CODE表的code\_Type和code\_Value字段,获得code\_Name的值，否则返回空字符串  
  参数:  
  `codeType`

  * code\_Type名称，如SEX
    `codeValue`
  * code\_Value值
    返回:
    code\_Name值
    抛出:
    `increator.base.exception.CustomException`

* #### getFieldNameBySysCode

  ```
  public static java.lang.String getFieldNameBySysCode(java.lang.String codeType,
                                                       java.lang.String codeValue)
                                                throws increator.base.exception.CustomException
  ```

  根据SYS\_CODE表的code\_Type和code\_Value字段,获得field\_Name的值，否则返回空字符串  
  参数:  
  `codeType`

  * code\_Type名称，如SEX
    `codeValue`
  * code\_Value值
    返回:
    field\_Name值
    抛出:
    `increator.base.exception.CustomException`

* #### getCodeValueBySysCode

  ```
  public static java.lang.String getCodeValueBySysCode(java.lang.String codeType,
                                                       java.lang.String codeName)
                                                throws increator.base.exception.CustomException
  ```

  根据SYS\_CODE表的code\_Type和code\_Name字段,获得code\_Value的值，否则返回空字符串  
  参数:  
  `codeType`

  * code\_Type名称，如SEX
    `codeName`
  * code\_Name名称，如男
    返回:
    code\_Value值
    抛出:
    `increator.base.exception.CustomException`

* #### getSysParaByCode

  ```
  public static com.cnnct.po.custom.SysParaCust getSysParaByCode(java.lang.String paraCode)
                                                          throws increator.base.exception.CustomException
  ```

  根据para\_Code返回SysParaCust对象  
  参数:  
  `paraCode`

  * para\_Code名称，如LOGIN\_TIME\_OUT
    返回:
    SysParaCust对象
    抛出:
    `increator.base.exception.CustomException`

* #### getParaValueByCode

  ```
  public static java.lang.String getParaValueByCode(java.lang.String paraCode)
                                             throws increator.base.exception.CustomException
  ```

  根据para\_Code返回Sys\_Para.para\_Value值  
  参数:  
  `paraCode`

  * para\_Code名称，如LOGIN\_TIME\_OUT
    返回:
    Sys\_Para.para\_Value值，如30
    抛出:
    `increator.base.exception.CustomException`

* #### getSysCodeTrByTrCode

  ```
  public static com.cnnct.po.custom.SysCodeTrCust getSysCodeTrByTrCode(java.lang.Object trCode)
                                                                throws increator.base.exception.CustomException
  ```

  根据tr\_Code返回SysCodeTrCust对象  
  参数:  
  `trCode`

  * 交易代码，如110013
    返回:
    SysCodeTrCust交易代码对象
    抛出:
    `increator.base.exception.CustomException`

* #### getTrCodeNameByTrCode

  ```
  public static java.lang.String getTrCodeNameByTrCode(java.lang.Object trCode)
                                                throws increator.base.exception.CustomException
  ```

  根据交易代码tr\_Code返回Sys\_Code\_Tr.code\_Name值  
  参数:  
  `trCode`

  * 交易代码，如110013
    返回:
    Sys\_Code\_Tr.code\_Name值
    抛出:
    `increator.base.exception.CustomException`

* #### getChineseByTypeDetailState

  ```
  public static java.lang.String getChineseByTypeDetailState(java.lang.Object orderType,
                                                             java.lang.Object orderTypeDetail,
                                                             java.lang.Object orderState)
                                                      throws increator.base.exception.CustomException
  ```

  根据orderType+orderTypeDetail+orderState返回orderStateChinese  
  参数:  
  `orderType`

  * 订单类型
    `orderTypeDetail`
  * 订单子类型
    `orderState`
  * 订单状态值
    返回:
    Sys\_Code\_Tr.code\_Name值
    抛出:
    `increator.base.exception.CustomException`

* #### getRedisFlag

  ```
  public static boolean getRedisFlag()
  ```

  判断是否启用了redis

* #### getReqCodeTrByReqCode

  ```
  public static com.cnnct.po.custom.SysInterfaceReqcodeCust getReqCodeTrByReqCode(java.lang.Object reqCode)
                                                                           throws increator.base.exception.CustomException
  ```

  根据reqCode返回SysInterfaceReqcodeCust对象  
  参数:  
  `reqCode`

  * 接口请求码，如U001
    返回:
    SysInterfaceReqcodeCust对象
    抛出:
    `increator.base.exception.CustomException`

* #### checkReqCode

  ```
  public static java.lang.Boolean checkReqCode(java.lang.Object reqCode)
                                        throws increator.base.exception.CustomException
  ```

  判断reqCode对象是否存在  
  参数:  
  `reqCode`

  * 接口请求码，如U001
    返回:
    是否存在
    抛出:
    `increator.base.exception.CustomException`



