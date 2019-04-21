#  github引入的原因说明：

本来是使用公司的svn版本管理进行手册版本管理的，但最后发现git和svn还是存在冲突，没找到共存的方案，因此转到github上。

gitbook官网：[www.gitbook.com](/www.gitbook.com)

github官网：[https://github.com/](https://github.com/)

github仓库地址：[https://github.com/cnnct/increator.git](https://github.com/iceaugust/increator.git)

gitbook在线手册地址：[https://increator.gitbooks.io/dev\_guide/content](https://increator.gitbooks.io/dev_guide/content)

公司在线手册地址： [http://soeasycn.com/dev\_guide/content/](http://soeasycn.com/dev_guide/content/)  **（注意：手动更新部署，可能不是最新版本）**

# 使用方法：

* 1、注册github账号，并在gitbook中使用此账号登录，不登录也可，但在同步项目时还是会提示登录。
* 2、在gitbook中选择工作区，比如e:\gitbook\_work，并创建新book，待生成一个新手册。![](/assets/import.png)

* 3、gitbook中设置仓库目录，为上面指定的仓库目录，确定。再点pull（相当于check out）表示从仓库中获取项目文件，及开发手册源文件，等待同步完成即可。这中间可能会提示输入github账号密码。

* 4、日常编辑修改，保存完本地文件后，会在右上角显示待同步的文件数量，如下图所示，需要上传到github仓库时，点击这个按钮即相当于check in或commit的操作，应该也是等同于菜单中的“push”。

![](/assets/push.png)

# 在线编辑gitbook

编辑gitbook除了本地客户端安装gitbook外，也可以直接在浏览器中使用。

使用gitgub账号，直接访问官网：ww.gitbook.com。

将账号与仓库进行绑定，已验证，多个账号都可以在gitbook上与同一个仓库地址绑定。

![](/assets/creatbook_fromgit.png)

# 发布gitbook

发布手册如下：

### 方式一：使用离线工具发布成本地的html的web目录手册。\(2018-12彭敏验证会报错，废弃\)

使用老版本的gitbook打开，直接在本地发布，发布成功能，会在项目同目录下生成一个名为“\_book”的目录，此目录即为对源文件md文件编辑后的html目录完整目录，详见下图

![](/assets/publish4.png)![](/assets/publish5.png)

### 方式二：全用在线的发布功能，发布，详见下图：

![](/assets/publish2.png)![](/assets/publish3.png)

### 方式三：本地命令行发布（2018-12，测试可用）：

* 本地安装notejs，百度下载安装。

* 安装成功后，在命令行中执行npm install gitbook-cli -g，安装gitbook编译工具包，待完成。

* 再 再到gitbook的源文件目录，如\increator\dev\_guide下，执行命令：gitbook serve，等提示启动成功，再CTRL+C结束服务。会在本地当前目录中生成一个\_book的目录，即为编译后的静态手册文件。

**注意：执行gitbook serve命令时，若提示Error: EPERM: operation not permitted, mkdir 错误，可尝试使用管理员运行命令行解决此问题。**

* 可把这个目录作为静态web资源发布，使用nginx，配置如下，根据实际情况修改目录名称

```
    location /book {
        #alias  E:\work\_book\;
        #index index.html;        
     }
```

# 

# gitbook的组织管理

可通过gitbook的组织将手册进行管理，且与github进行关联，目的是再发布手册时通过这个组织进行发布即可，在线手册访问地址为：[https://increator.gitbooks.io/dev\_guide/content](https://increator.gitbooks.io/dev_guide/content)

详见下图说明![](/assets/gitbook_org01.png)![](/assets/gitbook_members.png)

# gitbook如何删除已存在的book

个人book和组织级的book类似操作，详见下图所示

![](/assets/delete_book_01.png)![](/assets/delete_book_02.png)![](/assets/delete_book_03.png)

