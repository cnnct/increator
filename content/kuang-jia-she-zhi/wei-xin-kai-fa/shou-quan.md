# 微信网页授权开发说明

微信官方网页授权文档地址

[https://mp.weixin.qq.com/wiki?t=resource/res\_main&id=mp1421140842](https://mp.weixin.qq.com/wiki?t=resource/res_main&id=mp1421140842)

注：在进行微信网页授权开发前建议先仔细阅读上述文档，下文所述说明亦是根据官方文档结合实际开发中的问题所进行的讲解

## 微信网页授权参考链接

```
https://open.weixin.qq.com/connect/oauth2/authorize?appid=wxf0e81c3bee622d60&redirect_uri=http%3A%2F%2Fnba.bluewebgame.com%2Foauth_response.php&response_type=code&scope=snsapi_userinfo&state=STATE#wechat_redirect
```

注：该链接是需要用户手动同意授权的参考链接，若不需要用户手动授权则将连接中的参数scope设为snsapi\_base

### 链接详解

appid ：公众号的唯一标识（可进入一微信公众号，点击左下角 基本配置，即可看到 开发者ID

\(AppID\)）

redirect\_uri ：授权后重定向的回调链接地址（用户同意授权后跳转到的服务器即我们的代码地址，用户同意后微信会在该地址后拼接一个参数code）

response\_type ：返回类型，请填写code

scope ：应用授权作用域，snsapi\_base （不弹出授权页面，直接跳转，只能获取用户openid），snsapi\_userinfo （弹出授权页面，可通过openid拿到昵称、性别、所在地。并且， 即使在未关注的情况下，只要用户授权，也能获取其信息 ）

state ： 重定向后会带上state参数 （可以填写你想要传入的值，最多128字节）

wechat\_redirect ： 必须带此参数

### 授权流程

#### 1.**用户同意授权后，获取code**

说明 ：用户同意授权后，微信会在重定向的地址后拼接一个参数code,可通过request.getParameter\("code"\)获取code值

每次授权的code值都不一样，且code只能使用一次，过期时间5分钟

注：重定向地址需要使用域名，该域名需要在微信公众号中进行配置，配置地址如下：

![](/assets/微信图片_20180124145547.png)

#### 2.**通过code换取网页授权access\_token**

说明：获取code后，请求以下链接获取access\_token：  https://api.weixin.qq.com/sns/oauth2/access\_token?appid=APPID&secret=SECRET&code=CODE&grant\_type=authorization\_code

这里appid和secret的值是每个公众号的唯一标识 （可进入一微信公众号，点击左下角 基本配置，即可看到）

![](/assets/微信图片_20180124145656.png)

#### 3.**刷新access\_token（如果需要）**

说明：第二步获取到的token过期时间为7200s，刷新token可获得更长的有效期，获取第二步的refresh\_token后请求链接，

```
https://api.weixin.qq.com/sns/oauth2/refresh_token?appid=APPID&grant_type=refresh_token&refresh_token=REFRESH_TOKEN
```

#### 4.**拉取用户信息\(需scope为 snsapi\_userinfo\)**

说明：根据第二步或第三步获取到的access\_token和openid请求链接;

```
 https://api.weixin.qq.com/sns/userinfo?access_token=ACCESS_TOKEN&openid=OPENID&lang=zh_CN
```

即可获取微信用户基本信息

