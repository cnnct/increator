

### 1.导出工具使用示例：
#### (1).前台调用：

    function doTest(obj){
    	window.location.href ='${base}/sys/auth/brch/exportExcelTest;
    	
    }
    注意这里不能使用ajax请求，必须用普通请求

 ####(2).后台调用 ：
     controller调用：
             /**
             * 测试导出
             * @param request
             * @param response
             * @return
             * @throws Exception
             */
            @RequestMapping("/exportExcelTest")
            @ResponseBody 
            public ResultData exportExcelTest(HttpServletRequest request,HttpServletResponse response) {
            	String fileName=brchServ.exportExcelTest(request, response);
            	ResultData resultData = new ResultData(Result_Code.SUCCESS);
            	resultData.put("fileName", fileName);
                return resultData;
            }  
            
            
    service调用：
            /**
             * 测试导出
             * @param request
             * @param response
             * @return
             * @throws Exception
             */
            @Override
         	public String exportExcelTest(HttpServletRequest request, HttpServletResponse response) {
         		List<SysBranchCust> brchs = brchMapper.getBrchInfo();
         		List<SysBranchModul> moduls = new ArrayList<>();
         		for(SysBranchCust brchCust:brchs){
         			//将需导出的数据转换为相应的模型
         			SysBranchModul m = (SysBranchModul)ExportExcelUtil.ToParentClass(brchCust, SysBranchModul.class);
         			moduls.add(m);
         		}
         		//获取模板文件名
         		String templateFileName="branch.xlsx";
         		//导出文件
         		String fileName=ExportExcelUtil.exportExcel(response,moduls,templateFileName);
         		return fileName;
         	}
####(3).模板存放位置： 
![](/assets/excel1.png)
![](/assets/excel5.png)
####(3).模型存放位置： 
![](/assets/excel2.png)
![](/assets/excel3.png)

### 2.导入工具使用示例：