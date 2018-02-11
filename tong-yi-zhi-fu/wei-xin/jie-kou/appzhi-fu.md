/\*\*

\*公共方法：微信预支付

\* **@param** request

\* **@param** response

\* **@param** json

\*  body 商品描述

\*  pay\_id商户系统支付订单号

\*  tr\_amt订单结算金额

\*  limit\_pay no\_credit--指定不能使用信用卡支付

\* **@return** JSONObject

\*/

**publicstatic**String sendPrepay\(HttpServletRequest request,HttpServletResponse response,JSONObject json\)**throws**Exception;



