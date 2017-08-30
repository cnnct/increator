# HttpClient的使用示例

#### 1.调用HttpClientUtil代码示例：

```
MD5使用示例：
public static void main(String args[]) {
		MD5 m = new MD5();
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
	

SHA1使用示例：
public static void main(String[] args) throws Exception {  
        String key = "123";  
        System.out.println(SHA1Utils.encryptSHA(key));  
 }  
 
BASE64编码图片示例：Base64Image
public static void main(String[] args) {
	    String imgStr = Base64Image.imageToBase64("G:\\img.jpg");
	    System.out.println(imgStr);
	    base64ToImage(imgStr, "G:\\img1.jpg");
	}
	
	
DES加解密使用示例: DESUtils
 public static void main(String[] args) throws Exception {
        String source = "amigoxie";
        System.out.println("原文: " + source);
        String key = "A1B2C3D4E5F60708";
        String encryptData = encrypt(source, key);
        System.out.println("加密后: " + encryptData);
        String decryptData = decrypt(encryptData, key);
        System.out.println("解密后: " + decryptData);
    }
    
 DES3加解密使用示例: DES3Utils
  public static void main(String[] args) throws Exception {
        byte[] key = "6C4E60E55552386C759569836DC0F83869836DC0F838C0F7".getBytes();
        byte[] keyiv = { 1, 2, 3, 4, 5, 6, 7, 8 };
        byte[] data = "amigoxie".getBytes("UTF-8");
        System.out.println("data.length=" + data.length);
        System.out.println("CBC加密解密");
        byte[] str5 = des3EncodeCBC(key, keyiv, data);
        System.out.println(new sun.misc.BASE64Encoder().encode(str5));

        byte[] str6 = des3DecodeCBC(key, keyiv, str5);
        System.out.println(new String(str6, "UTF-8"));
    }
```

