# HttpClient的使用示例

#### 1.调用HttpClientUtil代码示例：

```
@Test
public void testHttpClientJson() { // json格式参数
    SysRole role = new SysRole();
    role.setRoleId(1L);
    role.setRoleDesc("管理员");
    JSONObject json = JSONObject.fromObject(role);
    String ret = HttpClientUtil.doPost("http://localhost:8080/manageplat/HttpClient", json.toString());
    System.out.println(ret);
}
	
@Test
public void testHttpClientXml() { // xml格式参数
    String para = "<root> <id>1</id> <name>张三</name> </root>";
    String ret = HttpClientUtil.doPost("http://localhost:8080/manageplat/HttpClient", para);
    System.out.println(ret);
}

@Test
public void testHttpClientFile() { // 文本文件格式参数.json.xml等
    File file = new File("D:\\test.xml");
    String ret = HttpClientUtil.doPost("http://localhost:8080/manageplat/HttpClient", file);
    System.out.println(ret);
}
```

