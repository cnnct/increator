# **Form标签**

#### ** form标签有4个属性分别为id、class、name、action,其中id属性为必填项；**

#### form标签的引入方式如下：

&lt;@form id="demoform" name="demoform" action="userLogin.do" &gt;

			&lt;@form\_group class="row"&gt;

				 	&lt;@input label="姓名：;true" id="name" name="name1"  type="text" size="3"  /&gt;

				    &lt;@input label="邮箱：;true" id="email1" name="email"  type="email" size="3" /&gt;

				 	&lt;@input label="邮编：;true" id="name1" name="name"  type="text" size="3"  /&gt;

			  &lt;/@form\_group&gt;

			  &lt;@form\_group class="row form-group-select"&gt;

					 &lt;@select label="选择框1：;true" id="jskd" sql\_key="syscode1"  name="sle" show\_field="CODE\_NAME" value\_field="CODE\_VALUE" default\_val="2" choice\_have="true" size="3"/&gt;

					 &lt;@code\_select label="选择框2：;true" id="select-11" name="sle" code\_type="AREA\_TYPE" default\_val="2"  no\_show="1"  size="3" choice\_have="true" select\_more="" /&gt;

					 &lt;@code\_select label="选择框3：;true" id="select-111" name="sle" code\_type="AREA\_TYPE" default\_val="2"  no\_show="1"  size="3" choice\_have="true" select\_more="" /&gt;		

			  &lt;/@form\_group&gt;

			  &lt;@form\_group class="row"&gt;

					 &lt;@input\_tree  label="input树1：;false" size="3" id="but6" tree\_id="tree6" name="valuetree6" sql\_key="sysfunc7" checkbox\_have="true"/&gt;

					 &lt;@input\_tree  label="input树2：;false" size="3" id="but7" tree\_id="tree7" name="valuetree7" sql\_key="sysfunc7" checkbox\_have="true"/&gt;

					 &lt;@input\_tree  label="input树3：;false" size="3" id="but5" tree\_id="tree5" name="valuetree5" sql\_key="sysfunc7" checkbox\_have="true"/&gt;

			  &lt;/@form\_group&gt;

			  &lt;@form\_group class="row"&gt;

					 &lt;@date\_time  label="时间框1：;false" id="date1" name="start\_time3" size="3"/&gt;

					 &lt;@date\_time  label="时间框2：;false" id="date2" name="start\_time4" size="3"/&gt;

					 &lt;@date\_time  label="时间框3：;false" id="date3" name="start\_time5" size="3"/&gt;

 			  &lt;/@form\_group&gt;

			  &lt;@form\_group class="row"&gt;

					 &lt;@search\_input  label="search框1：;false" id="search1" name="searchOrgName" sql\_key="org\_name1" show\_item="item.org\_id + ' \_ ' + item.org\_name" show\_value="org\_name" hidden\_value="org\_id" size="3"/&gt;

					 &lt;@search\_input   label="search框2：;false" id="search2" name="searchOrgName" sql\_key="org\_name1" show\_item="item.org\_id + ' \_ ' + item.org\_name" show\_value="org\_name" hidden\_value="org\_id" size="3"/&gt;

					 &lt;@search\_input   label="search框3：;false" id="search3" name="searchOrgName" sql\_key="org\_name1" show\_item="item.org\_id + ' \_ ' + item.org\_name" show\_value="org\_name" hidden\_value="org\_id" size="3"/&gt;

 			  &lt;/@form\_group&gt;

			  &lt;@form\_group class="row"&gt;

					&lt;@text\_area label="文本域1：;false" id="username1" name="ntextame" value="name"  size="5" /&gt; 

 			  &lt;/@form\_group&gt;

			  &lt;@form\_group class="row"&gt;

				 	&lt;@code\_radio name="code\_type2" code\_type="AREA\_TYPE" default\_val="28" readonly="true"/&gt;

			  &lt;/@form\_group&gt;

			  &lt;@form\_group class="row"&gt;

				 	&lt;@code\_checkbox name="code\_type1" code\_type="AREA\_TYPE" default\_val="09,28,58" readonly="true" /&gt;

			  &lt;/@form\_group&gt;

			  &lt;@form\_group &gt;

				 	&lt;@button id="submit" type="submit"   value="提交" icon="search"/&gt;

					&lt;@button id="repeat3" type="button"   value="重置" icon="repeat"/&gt;

			 &lt;/@form\_group&gt;

		&lt;/@form&gt;



