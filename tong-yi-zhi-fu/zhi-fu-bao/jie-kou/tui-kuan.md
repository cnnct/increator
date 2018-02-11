/\*\*

退款申请

**@param**json

\*  out\_trade\_no 订单号

\* refund\_order\_id 退款订单号

\*  refund\_amt退款总金额（分）

**@return**JSONObject

\*  issuccess成功true,失败false

\*  tradeno支付宝交易流水号

\*/

**publicstatic**JSONObject sendRefund\(JSONObject json\);

# **调用示例：**

JSONObject json = new JSONObject\(\);

json.put\("out\_trade\_no", "123"\);

json.put\("refund\_order\_id", "1"\);

json.put\("refund\_amt", "1"\);

JSONObject ret = AlipayService.sendRefund\(json\);

System.out.println\(ret\);

