# echarts3**标签**

#### echarts3**标签的属性 :**
#### 注意echarts3标签是在echarts的基础上升级到的3.0版本，标签的属性功能和echarts标签一致，但图表的渲染效果和后台封装的属性api有所差别，且引用echarts3时必须切换ECharts-3.0.0.3.jar的包，前台init_page配套属性需要调整，注意两个 版本不可以混用
> echarts3标签属性如下：
>
> **其中id,option_url为必填项,下面必填项加上了\*号**；
>
> > **\*id ：** id属性
> >
> > **name ：** name属性
> >
> > **size ：** size为尺寸标签,可以填的数值范围为（1-12）,如size="6",button标签的默认size为4
> >
> > **class：** class属性
> >
> > **style:** style属性
> >
> > **\*option_url:** 为后台发送ajax去加载echarts的option数据
> >
> > **position:** 为位置，可以填写的值为left，center，right，默认left
> >
> > **interval_time:** 为定时器刷新时间，单位毫秒，如果有值则实时刷新图表


#### echarts3标签的引入方式 :

```
 <@init_page title="公交公司在线车辆数展示" echarts_version="3">
    <@echarts3
        id="echarts_pie"
        size="12"
        option_url="${base}/term/busInfo/queryOnline"
        position="center"
    />
</@init_page>
```

#### echarts3标签的显示结果 :

![](/assets/echart3_1.png)

#### echarts3标签后台加载option数据：
![](/assets/echart3_2.png)
```
Ctrl写法：
    @RequestMapping("/queryOnline")
    @ResponseBody
    public ResultData queryOnline(Model model) {
        ResultData resultData = new ResultData(Result_Code.SUCCESS);
        String option = busInfoServ.queryOnline();
        resultData.put("option", option);
        return resultData;
    }

Service写法：
 public String queryOnline() {		
        Option basic = new Option();
        basic.title().text("公交公司配车数量对比").x("center").y("top");
        basic.tooltip().trigger(Trigger.item).formatter("{a} <br/>{b} : {c} ({d}%)");
        //获取配车数据
        List<Map<String,Object>> childMerchList=mapper.getChildMerchData();
        List<String> legendList=new ArrayList<>();
        List<PieData> pieDataList=new ArrayList<>();
        for(int i=0;i<childMerchList.size();i++){
        	Map<String,Object> childMerchMap=childMerchList.get(i);
        	legendList.add(Tools.processNull(childMerchMap.get("MERCH_NAME")));
        	pieDataList.add(new PieData(Tools.processNull(childMerchMap.get("MERCH_NAME")),Tools.processNull(childMerchMap.get("BUS_COUNT"))));
        }
        //抬头
        basic.legend().data(legendList.toArray()).x("left").orient(Orient.vertical);

        basic.series(new Pie().name("配车数").data(pieDataList.toArray()).center("50%", "55%").radius("50%"));
       
       Gson gson = new Gson();
      return  gson.toJson(basic);
	}
```


后台写法参照
平台demo示例或
https://oss.sonatype.org/content/repositories/releases/com/github/abel533/ECharts/3.0.0/


