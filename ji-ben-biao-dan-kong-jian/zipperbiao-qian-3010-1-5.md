# zipper**拉链标签**

* 注意:该标签现阶段只用于首页面，用于控制首界面的面板布局 

#### zipper**标签的属性 :**

> zipper标签属性分别如下：
>
> > ***id ：** id属性
> >
> > ***items ：** name属性
> >

#### button标签的引入方式 :

```
   <@zipper id="layout_controller" items={"box1":"标题1","box2":"标题2","box3":"标题3","box4":"标题4","box5":"标题5"}/>
	 <#-- 首页右侧功能模块 -->
	<div class="index-contain" id="main-widget-container">
			<div class="row">
				<@panel id="box1" title="标题1" position="center" size="12">
					<@echarts 
						id="echarts_post" 
						size="6" 
						option_url="${base}/tag/echarts" 
						position="center"
						/>
				</@panel>
		    </div>
		    
		    
		    <div class="row">
		    	<@panel id="box2" title="标题2" position="left" size="4">
					放置内容区域2
				</@panel>
				<@panel id="box3" title="标题3" position="left" size="4">
					放置内容区域3
				</@panel>
				<@panel id="box4" title="标题4" position="left" size="4">
					放置内容区域4
				</@panel>
		    </div>
		    <div class="row">
				<@panel id="box5" title="标题5" position="center" size="12">
					放置内容区域5
				</@panel>
		    </div>
			
		</div>
```

#### button标签的显示结果 :

![](/assets/button.png)

