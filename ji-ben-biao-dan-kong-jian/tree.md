#
tree标签

#### tree**标签的属性 :**

> tree标签属性分别如下：
**其中id、tree\_id、sql\_key为必填项**
>
> > **\* id ：** id属性
> >
> > **name ：** name属性
> >
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",默认size为5
> >
> > **checkbox\_have ：** 为是否有复选框，默认false
> >
> > **\* tree\_id ：** tree树对象的id
> >
> > **\* sql\_key ：** sql\_key属性为select标签后台执行的sql的key值
> >
> > **sql\_condition :** sql\_condition属性用于配合sql\_key属性，当对应的后台sql需要传入参数替换“？”占位符时填写，也可以用登录用户的id替换占位符如sql\_condition="ACC\_RECHG\_TYPE,session.operId",其中‘ACC\_RECHG\_TYPE’会用来替换第一个占位符，登录用户的id会用来替换第二个占位符；
注意：【1.4】版本后分隔符由“，”替换成为“&&&”
> >
> > **edit_flag【1.9】：** tree树的可编辑开关，默认false，开启时节点支持编辑功能，包括（新增节点，修改节点，删除节点，移动节点等编辑功能）
> >
> > **nav_flag【1.9】：** tree的支持用于含有导航页功能开发的开关，默认false，edit_flagb必须为true时开启有效，开启时节点支持编辑功能且需要绑定加载页面的url，节点编辑功能包括（新增节点，修改节点，删除节点，移动节点等编辑功能）
> >
> > **cust_get_data_clazz【1.9】：** 该功能用于支持自定义加载tree的初始化数据，如果该项存在，则将屏蔽sql_key的加载数据功能，指定加载类和静态方法,规则示例将在下面展示；
> >
> > **cust_get_data_param【1.9】：** 该功能用于支持自定义加载tree的初始化数据，如果该项存在，则将屏蔽sql_key的加载数据功能，指定加载类和静态方法的参数（现阶段只支持单个参数且为string类型）,规则示例将在下面展示；
> >
> > **url【1.9.1】：** 由于1.9版本的tree编辑功能存在异步加载问题，所以【1.9.1】作为【1.9】版本的修复版，注意，当edit_flag功能开启时，必须要配合url属性来加载数据，其他两种方式将不支持
> >


#### tree标签的引入方式 :

```
<@tree size="12" id="but2" tree_id="tree2" name="valuetree2" sql_key="sysfunc8" checkbox_have="true" sql_condition="session.operId"/>

```

#### 对应sql语句 :

![](/assets/tree_sql.png)

```
SELECT
sf.FUNC_ID AS id,
sf.PARENT_ID AS pId,
sf.TITLE AS name,
(
CASE
WHEN sf.FUNC_ID IN (
SELECT
srf.FUNC_ID
FROM
sys_role_func srf,
sys_role sr,
sys_oper_role sor
WHERE
srf.ROLE_ID = sr.ROLE_ID
AND
sor.ROLE_ID = sr.ROLE_ID
AND
sor.OPER_ID = ?
) THEN
'true'
ELSE
'false'
END
) AS checked
FROM
sys_func sf
```

**上图中红色别名必须有，且区分大小，分别对应 : 树节点的id，父级id，和显示的text名**

#### 显示结果 :

![](/assets/tree.png)

#### tree的数据重新加载方法 :

```
treeReload(treeId,treeData);//js代码
```

#### tree获取被勾选的节点的id的方法 :

```
getCheckedNodesIds(treeId);//js代码，返回数组
```

#### tree获取被勾选的节点的text的方法 :

```
getCheckedNodesText(treeId);//js代码，返回字符串，以","分割
```

#### tree的可编辑功能和自定义获取数据的示例【1.9】：
* 1.加载标签：
        <@tree  size="12" 
                id="but2"
                tree_id="tree2"
                name="valuetree2"
                sql_key="sysfunc12"
                checkbox_have="true"
                sql_condition="session.operId&&&010602"
                nav_flag="true"
                edit_flag="true"
                cust_get_data_clazz="com.cnnct.utils.CustRepSysTagDataUtils[getTreeDataList]"
		        cust_get_data_param="${base}"
                />
* 2.在edit_flag和nav_flag开启时需要实现的配套js方法：
                                
                                /**
                                *【2.1】版本后加入删除节点前的方法，非必要方法，方法名为treeId+"BeforeRemove",参数为对象object,
                                *含有属性id,parentId,name,需要返回标志位true(通过，继续执行)和false(阻止通过)
                                */
                                function tree2BeforeRemove(obj){
                                alert("删除成功:"+obj.id+";"+obj.parentId+";"+obj.name);
                                }
                                /**
                                *删除节点的方法，必要方法，方法名为treeId+"OnRemove",参数为对象object,
                                *含有属性id,parentId,name,需要使用者返回后台删除对应的数据记录
                                */
                                function tree2OnRemove(obj){
                                alert("删除成功:"+obj.id+";"+obj.parentId+";"+obj.name);
                                }
                                /**
                                *修改节点名的方法，必要方法，方法名为treeId+"OnRename",参数为对象object,
                                *含有属性id,parentId,name,需要使用者返回后台修改对应的数据记录
                                */
                                function tree2OnRename(obj){
                                alert("修改成功:"+obj.id+";"+obj.parentId+";"+obj.name);
                                }
                                /**
                                                                *移动节点的方法，必要方法，方法名为treeId+"OnMove",参数为对象object,
                                                                *含有属性treeNodeArray为对象数组,需要使用者返回后台修改对应的数据记录
                                                                */
                                function tree2OnMove(obj){
                                var arr=obj.treeNodeArray;
                                //alert("移动成功:"+obj.id+";"+obj.parentId+";"+obj.name);
                                }
                                /**
                                *新增节点的方法，必要方法，方法名为treeId+"BeforeAdd",参数为对象object,
                                *含有属性parentId,需要使用者返回后台新增数据记录，返回必要参数id,name,url(对应该节点绑定跳转的url),【2.1】版本后加入resultCode(当值为0时，表示后台新增成功)，新增时不可调用refreshTreeNodes(treeId)刷新节点方法
                                */
                                function tree2BeforeAdd(obj){
                                obj.id="1001001005";
                                obj.name="测试ssy";
                                obj.url="sys/auth/role/index";
                                return obj;
                                }
                                /**
                                *右侧内容切换调用方法，该项方法在nav_flag开启时，需要实现，其他上面的方法，在edit_fag开启时必须实现
                                *参数obj包含属性：节点的id,name,url
                                */
                                function tree2GetNavContext(obj){
                                var context='<iframe src="' + '${base}/'+obj.url + '" width="100%" height="500px" frameborder="no" border="0" marginwidth="0" marginheight="0" scrolling="yes" allowtransparency="yes"></iframe>'
                                $(".maincontent").html(context);
                                }  
                                                        
                                /**
                                	 *【2.1】版本后加入复制节点的方法，必要方法，方法名为treeId+"BeforeCopy",参数为对象object,
                                	 *含有属性parentId,id（被复制节点的id）需要使用者返回后台新增数据记录，返回必要参数id,name,url(对应该节点绑定跳转的url),resultCode(当值为0时，表示后台新增成功)
                                	 */
                                	function tree2BeforeCopy(obj){
                                		obj.id="1001001005";
                                		obj.name="测试ssy";
                                		obj.url="sys/auth/role/index";
                                		obj.resultCode=0;
                                		return obj;
                                	}
                                
* 3.后台自定义加载数据的方法：
![](/assets/tree_2.png)
![](/assets/tree_3.png)
* 4.sql数据，当然cust_get_data_list属性存在时，sql执行被屏蔽：

![](/assets/tree_4.png)

* 5.展示结果：

![](/assets/tree_5.png)