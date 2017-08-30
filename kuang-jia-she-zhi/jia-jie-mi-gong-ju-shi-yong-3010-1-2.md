# HttpClient的使用示例

#### 1.调用HttpClientUtil代码示例：

```
**MD5使用：**
public static void main(String args[]) {
		MD5Utils m = new MD5Utils();
		System.out.println(m.getMD5ofStr(m.getMD5ofStr("a")));
		if (Array.getLength(args) == 0) { // 如果没有参数，执行标准的Test Suite
			System.out.println("MD5 Test suite:");
			System.out.println("MD5(\"\"):" + m.getMD5ofStr(""));
			System.out.println("MD5(\"a\"):" + m.getMD5ofStr("a"));
			System.out.println("MD5(\"abc\"):" + m.getMD5ofStr("abc"));
			System.out.println("MD5(\"message digest\"):" + m.getMD5ofStr("message digest"));
			System.out.println("MD5(\"abcdefghijklmnopqrstuvwxyz\"):" + m.getMD5ofStr("abcdefghijklmnopqrstuvwxyz"));
			System.out.println("MD5(\"ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789\"):"
					+ m.getMD5ofStr("ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789"));
		} else
			System.out.println("MD5(" + args[0] + ")=" + m.getMD5ofStr(args[0]));

	}
	

SHA1使用：


@Test
public void testHttpClientFile() { // 文本文件格式参数.json.xml等
    File file = new File("D:\\test.xml");
    String ret = HttpClientUtil.doPost("http://localhost:8080/manageplat/HttpClient", file);
    System.out.println(ret);
}
```

