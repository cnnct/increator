# 接口名称

```
/**
web支付
@paramjson
*  body 商品描述
*  out_trade_no 订单号
*  tr_amt金额(单位分)
*  enable_paymethod 可用渠道---可空，与disable_paymethod互斥，
比如可用余额、网银、借记卡快捷，，则传入directPay^bankPay^debitCardExpress
*  disable_paymethod禁用渠道---可空，与enable_paymethod互斥，
比如禁用信用卡快捷，，则传入creditCardExpress
@returncode_url web支付form
*/
publicstaticJSONObject sendWebPay(JSONObject json)throwsException;
```

# **调用示例：**

```
JSONObject json =newJSONObject();
json.put("body","充值");
json.put("out_trade_no ","123");
json.put("tr_amt","1");
json.put("enable_paymethod", "directPay^bankPay^debitCardExpress^cash");
JSONObject ret = AlipayService.sendWebPay(json);
System.out.println(ret);
```



