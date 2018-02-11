# 接口**：**

```
/**
*支付宝查询订单
* @param out_trade_no 订单号
* @return JSONObject
*  issuccess成功true,失败false
*  tradeno支付宝交易流水号--成功时返回
*  sendpaydate支付成功时间--成功时返回
*  submsg失败原因--失败时返回
*/
publicstatic JSONObject sendOrderQuery(String pay_Id);
```

# **调用示例：**

JSONObject ret = AlipayService.sendOrderQuery\("1"\);

System.out.println\(ret\);

