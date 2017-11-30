

# Documentation

## `@Log4j public class CacheUtil`

缓存管理工具类

## `private CacheUtil()`

缺省构造方法

## `public static void putOperSes(Object key,Object value)`

用户session放入缓存

 * **Parameters:**
   * `key` — 当前sessionId
   * `value` — 当前用户operId

## `public static Object getOperSes(Object key)`

通过sessionId得到operId

 * **Parameters:** `key` — sessionId
 * **Returns:** 

## `public static void removeOperSes(Object key)`

通过sessionId删除OperId

 * **Parameters:** `key` — sessionId

## `public static void putSession(Object key,Map value)`

根据operId存放用户session相关数据map，支持redis和ehcache

 * **Parameters:**
   * `key` — operId
   * `value` — session相关的数据map

## `public static void removeSession(Object key)`

根据operId移除用户session相关数据map，支持redis和ehcache

 * **Parameters:** `key` — operId

## `public static Map getSession(Object key)`

根据operId获取用户session相关数据map，支持redis和ehcache

 * **Parameters:** `key` — operId

## `public static void putErrCode(Object key,Object value)`

errCode存放单个对象

 * **Parameters:**
   * `key` — errCode错误码
   * `value` — Sys_Code_Err对象

## `public static Object getErrCode(Object key)`

根据errCode值

 * **Parameters:** `key` — errCode错误码
 * **Returns:** Sys_Code_Err对象

## `public static String getErrMsgByErrCode(Object key)`

根据错误码获取错误描述

 * **Parameters:** `key` — errCode错误码
 * **Returns:** 错误码对应的描述

## `public static void putMapValue(HttpServletRequest request,Map<String,Object> map)`

 * **Deprecated**
 * **Parameters:**
   * `key` — 当前请求url等信息拼接作为key
   * `value` — 存放对象

## `public static Object getMapValue(Object key)`

取出map缓存

 * **Parameters:** `key` — 当前请求url等信息拼接作为key
 * **Returns:** 返回map对象

## `public static Map<String,Object> getMapValue(HttpServletRequest request)`

取出map缓存

 * **Parameters:** `key` — 当前请求url等信息拼接作为key
 * **Returns:** 返回map对象

## `public static void removeMapValue(HttpServletRequest request)`

移除map缓存

 * **Parameters:** `request` — 当前请求request

## `public static void putActionLog(Object key,Object value)`

将actionLog放入缓存

 * **Parameters:**
   * `key` — 当前请求url等信息拼接作为key
   * `value` — SysActionLogCust对象

## `public static void putActionLog(HttpServletRequest request,SysActionLogCust value)`

将actionLog放入缓存

 * **Parameters:**
   * `request` — 当前请求request
   * `value` — SysActionLogCust对象

## `public static Object getActionLog(Object key)`

取出actionLog缓存

 * **Parameters:** `key` — 当前请求url等信息拼接作为key
 * **Returns:** SysActionLogCust对象

## `public static SysActionLogCust getActionLog(HttpServletRequest request)`

取出actionLog缓存

 * **Parameters:** `key` — 当前请求url等信息拼接作为key
 * **Returns:** SysActionLogCust对象

## `public static void removeActionLog(HttpServletRequest request)`

移除actionLog缓存

 * **Parameters:** `key` — 当前请求url等信息拼接作为key

## `public static void putInterfaceLog(HttpServletRequest request,Map<String,Object> map)`

 * **Deprecated**
 * **Parameters:**
   * `key` — 当前请求url等信息拼接作为key
   * `value` — Sys_Interface_log

## `public static String getCodeNameBySysCode(String codeType,String codeValue)throws CustomException`

根据SYS_CODE表的code_Type和code_Value字段,获得code_Name的值，否则返回空字符串

 * **Parameters:**
   * `codeType` — code_Type名称，如SEX
   * `codeValue` — code_Value值
 * **Returns:** code_Name值

## `public static String getFieldNameBySysCode(String codeType,String codeValue)throws CustomException`

根据SYS_CODE表的code_Type和code_Value字段,获得field_Name的值，否则返回空字符串

 * **Parameters:**
   * `codeType` — code_Type名称，如SEX
   * `codeValue` — code_Value值
 * **Returns:** field_Name值

## `public static String getCodeValueBySysCode(String codeType,String codeName)throws CustomException`

根据SYS_CODE表的code_Type和code_Name字段,获得code_Value的值，否则返回空字符串

 * **Parameters:**
   * `codeType` — code_Type名称，如SEX
   * `codeName` — code_Name名称，如男
 * **Returns:** code_Value值

## `public static SysParaCust getSysParaByCode(String paraCode)throws CustomException`

根据para_Code返回SysParaCust对象

 * **Parameters:** `paraCode` — para_Code名称，如LOGIN_TIME_OUT
 * **Returns:** SysParaCust对象

## `public static String getParaValueByCode(String paraCode)throws CustomException`

根据para_Code返回Sys_Para.para_Value值

 * **Parameters:** `paraCode` — para_Code名称，如LOGIN_TIME_OUT
 * **Returns:** Sys_Para.para_Value值，如30

## `public static SysCodeTrCust getSysCodeTrByTrCode(Object trCode)throws CustomException`

根据tr_Code返回SysCodeTrCust对象

 * **Parameters:** `trCode` — 交易代码，如110013
 * **Returns:** SysCodeTrCust交易代码对象

## `public static String getTrCodeNameByTrCode(Object trCode)throws CustomException`

根据交易代码tr_Code返回Sys_Code_Tr.code_Name值

 * **Parameters:** `trCode` — 交易代码，如110013
 * **Returns:** Sys_Code_Tr.code_Name值

## `public static String getChineseByTypeDetailState(Object orderType, Object orderTypeDetail, Object orderState) throws CustomException`

根据orderType+orderTypeDetail+orderState返回orderStateChinese

 * **Parameters:**
   * `orderType` — 订单类型
   * `orderTypeDetail` — 订单子类型
   * `orderState` — 订单状态值
 * **Returns:** Sys_Code_Tr.code_Name值

## `public static boolean getRedisFlag()`

判断是否启用了redis

## `public static SysInterfaceReqcodeCust getReqCodeTrByReqCode(Object reqCode)throws CustomException`

根据reqCode返回SysInterfaceReqcodeCust对象

 * **Parameters:** `reqCode` — 接口请求码，如U001
 * **Returns:** SysInterfaceReqcodeCust对象

## `public static Boolean checkReqCode(Object reqCode)throws CustomException`

判断reqCode对象是否存在

 * **Parameters:** `reqCode` — 接口请求码，如U001
 * **Returns:** 是否存在
 * **Exceptions:** `CustomException` — 