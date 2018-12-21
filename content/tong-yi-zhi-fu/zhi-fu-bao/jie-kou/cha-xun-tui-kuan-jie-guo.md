# 接口：

```
/**
查询订单退款
@paramjson
*  out_trade_no 订单号
* refund_order_id退卡订单号
@returnJSONObject
*  issuccess成功true,失败false
*  tradeno支付宝交易流水号
*/
publicstaticJSONObject sendOrderRefundQuery(JSONObject json);
```

# **调用示例：**

```
JSONObject json = new JSONObject();
json.put("out_trade_no", "123");
json.put("refund_order_id", "1");
JSONObject ret = AlipayService.sendOrderRefundQuery (json);
System.out.println(ret);
```



