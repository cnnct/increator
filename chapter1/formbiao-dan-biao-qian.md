# **Form标签**

#### ** form标签有4个属性分别为id、class、name、action,其中id属性为必填项；**

#### form标签的引入方式如下：

```
&lt;@form  id="demoform"  name="demoform"  action="userLogin.do" &gt;
```

```java
 &lt;@form\_group class="row"&gt;

      &lt;@input label="姓名;true" id="name" name="name1"  type="text" size="3"  /&gt;

      &lt;@input label="邮箱;true" id="email1" name="email"  type="email" size="3" /&gt;

      &lt;@input label="邮编;true" id="name1" name="name"  type="text" size="3"  /&gt;

 &lt;/@form\_group&gt;
```

```
 &lt;@form\_group class="row"&gt;

           &lt;@date\_time  label="时间框1;false" id="date1" name="start\_time3" size="3"/&gt;

           &lt;@date\_time  label="时间框2;false" id="date2" name="start\_time4" size="3"/&gt;

           &lt;@date\_time  label="时间框3;false" id="date3" name="start\_time5" size="3"/&gt;

 &lt;/@form\_group&gt;
```

```
 &lt;@form\_group &gt;

                   &lt;@button id="submit" type="submit"   value="提交" icon="search"/&gt;

                   &lt;@button id="repeat3" type="button"   value="重置" icon="repeat"/&gt;

  &lt;/@form\_group&gt;
```

&lt;/@form&gt;

