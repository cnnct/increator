# panel_container**标签**

#### panel_container**标签的属性 :**

> panel_container标签，主要用来布局card主页的panel面板，可以对多个panel面板进行布局，属性分别如下：

> > **layout：** 布局属性，该属性有内置属性：colspan(布局占用的列数，总共支持12列，默认1列)，rowspan(行属性，默认1行)
>>




#### panel_container标签的引入方式 :

```
   <@panel_container layout=[
									[
										{"colspan":"5","rowspan":"2"},
										{"colspan":"4","rowspan":"1"},
										{"colspan":"3","rowspan":"1"}
									],
									[
										{"colspan":"7","rowspan":"1"}
									],
									[
										{"colspan":"12","rowspan":"1"}
									]
								]>
								<@panel id="box1" title="标题1" position="left"  style_type="classical">
													<@echarts 
														id="echarts_post" 
														size="6" 
														option_url="${base}/demo/tag/echarts" 
														position="left"
														/>
												</@panel>

								<@panel id="box2" title="标题2" position="left" ></@panel>
								<@panel id="box3" title="标题3" position="left" ></@panel>
								<@panel id="box4" title="标题4" position="left" ></@panel>
								<@panel id="box5" title="标题5" position="left" >

								</@panel>

							</@panel_container>
```

#### panel_container标签的显示结果 :

![](/assets/button_group1.png)

