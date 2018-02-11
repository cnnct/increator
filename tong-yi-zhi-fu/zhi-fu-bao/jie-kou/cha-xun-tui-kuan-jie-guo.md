/\*\*

查询订单退款

**@param**json

\*  out\_trade\_no 订单号

\* refund\_order\_id退卡订单号

**@return**JSONObject

\*  issuccess成功true,失败false

\*  tradeno支付宝交易流水号

\*/

**publicstatic**JSONObject sendOrderRefundQuery\(JSONObject json\);

# **调用示例：**

JSONObject json = new JSONObject\(\);

json.put\("out\_trade\_no", "123"\);

json.put\("refund\_order\_id", "1"\);

JSONObject ret = AlipayService.sendOrderRefundQuery \(json\);

System.out.println\(ret\);

