# 接口：

```
/**
查询账单地址
@parambill_date yyyy-mm-dd
@return
*/
publicstaticString sendOrderQueryBillUrl(String bill_date);
```

# **调用示例：**

```
System.out.println(AlipayService.sendOrderQueryBillUrl("2016-11-24"));
```

