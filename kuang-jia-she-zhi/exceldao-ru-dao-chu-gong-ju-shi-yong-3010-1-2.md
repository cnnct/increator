# excel导入导出工具使用

### 1.导出工具使用示例：
#### (1).前台调用：

    function doTest(obj){
    	window.location.href ='${base}/sys/auth/brch/exportExcelTest?brchId='+getFirstInputId(obj);
    	
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
            @Override
         	public String exportExcelTest(HttpServletRequest request, HttpServletResponse response) {
         		String brchId=request.getParameter("brchId").toString();
         		List<SysBranchCust> brchs = brchMapper.getBrchInfoForDel(brchId);
         		List<SysBranchModul> moduls = new ArrayList<>();
         		for(SysBranchCust brchCust:brchs){
         			//将需导出的数据转换为公共模型
         			SysBranchModul m = (SysBranchModul)ExportExcelUtil.ToParentClass(brchCust, SysBranchModul.class);
         			moduls.add(m);
         		}
         		//模板文件名
         		String templateFileName="branch.xlsx";
         		//导出文件
         		String fileName=ExportExcelUtil.exportExcel(response,moduls,templateFileName);
         		return fileName;
         	}