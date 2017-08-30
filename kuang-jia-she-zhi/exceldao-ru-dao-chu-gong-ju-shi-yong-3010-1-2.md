# excel导入导出工具使用

### 1.导出工具使用示例：
#### (1).前台调用：

    function doTest(obj){
    	window.location.href ='${base}/sys/auth/brch/exportExcelTest?brchId='+getFirstInputId(obj);
    	
    }
    注意这里不能使用ajax请求，必须用普通请求

 ####(2).后台调用 ：
     /**
     * 测试导出
     * @param request
     * @param response
     * @return
     * @throws Exception
     */
    @RequestMapping("/exportExcelTest")
    @ResponseBody 
    public ResultData exportExcelTest(HttpServletRequest request,HttpServletResponse response) throws Exception {
    	String fileName=brchServ.exportExcelTest(request, response);
    	ResultData resultData = new ResultData(Result_Code.SUCCESS);
    	resultData.put("fileName", fileName);
        return resultData;
    }  