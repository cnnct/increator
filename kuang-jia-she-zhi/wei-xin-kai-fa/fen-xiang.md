# 微信分享

说明：微信分享给朋友、分享到朋友圈等主要是web前端的工作，这里我主要说明下调用微信JS-SDK所需要后台反悔的配置信息及签名信息

所有需要使用JS-SDK的页面必须先注入配置信息，否则将无法调用，如下图

![](/assets/微信图片_20180116143856.png)图中所示appId，timestamp，nonceStr，signature这些参数需要后台返回，下面主要说明下签名的生成步骤

#### 1.获取access\_token

请求地址：https://api.weixin.qq.com/cgi-bin/token?grant\_type=client\_credential&appid=APPID&secret=APPSECRET

#### 2.获取jsapi\_ticket

用第一步拿到的access\_token 采用http GET方式请求获得jsapi\_ticket（有效期7200秒，开发者必须在自己的服务全局缓存jsapi\_ticket）

请求地址：[https://api.weixin.qq.com/cgi-bin/ticket/getticket?access\_token=ACCESS\_TOKEN&type=jsapi](https://api.weixin.qq.com/cgi-bin/ticket/getticket?access_token=ACCESS_TOKEN&type=jsapi)

#### 3.生成签名

生成签名所需参数

noncestr ：随机字符串

jsapi\_ticket ：第二步获取

timestamp：时间戳

url ： 当前网页的URL，不包含\#及其后面部分 建议使用：location.href.split\('\#'\)\[0\]获取,而且需要encodeURIComponent

生成步骤1：

对所有待签名参数按照字段名的ASCII 码从小到大排序（字典序）后，使用URL键值对的格式（即key1=value1&key2=value2…）拼接成字符串string1

示例：jsapi\_ticket=sM4AOVdWfPE4DxkXGEs8VMCPGGVi4C3VM0P37wVUCFvkVAy\_90u5h9nbSlYy3-Sl-HhTdfl2fzFy1AOcHKP7qg&noncestr=Wm3WZYTPz0wzccnW×tamp=1414587457&url=http://mp.weixin.qq.com?params=value

生成步骤2.：

对string1进行sha1签名，得到signature

#### 注意 ：

1.这里签名用的随机字符串noncestr和时间戳timestamp 需原样返给页面

2.url建议使用location.href.split\('\#'\)\[0\]获取,而且需要encodeURIComponent

以上签名完成之后即可在页面进行分享

#### 注意：分享链接的域名或路径必须与当前页面对应的公众号JS安全域名一致

js安全域名配置见下图

#### ![](/assets/微信图片_20180116143733.png)强调 ：

#### 实际开发中分享时因为手机系统的问题、多次分享的问题，发现当该分享地址动态获取时容易出现分享的页面与期望不一致，因此建议该分享地址写死，即写上带域名的全路径



