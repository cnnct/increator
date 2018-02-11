# 接口名称

```
/**
扫码支付
@paramjson
*  body 商品描述
*  out_trade_no 订单号
*  tr_amt金额(单位分)
@returncode_url二维码链接
*/
publicstaticJSONObject sendWebPrepay(JSONObject json)throwsException;
```

# **调用示例：**

```
JSONObject json =newJSONObject();
json.put("body","充值");
json.put("out_trade_no ","123");
json.put("tr_amt","1");
JSONObject ret = AlipayService.sendWebPrepay(json);
System.out.println(ret);
```



