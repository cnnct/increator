

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

### 2.导入工具的使用示例：
#### (1).前台页面及调用：
    <@modal_body id="modal_import" modal_title="导入部门">
        <@form id="import_form">
            <@form_group class="row">
                <@file_upload label="待上传文件,,2" id="myfile" name="myfile" size="8"/>
                <@button icon="saved" value="获取sheet" onclick="getExcelSheets()"/>
            </@form_group>
        </@form>
     	 <@form id="sheet_form">
            <@form_group class="row">
                <@select  label="sheet列表,,2" id="sheet_list"  name="index"  choice_have="true" size="10"/>
            </@form_group>
        </@form>
    </@modal_body>
    <@modal_foot>
    <@button size="2" icon="saved" value="提交" onclick="fileImport()"/>
    </@modal_foot>
    <script>
    <#-- 获取sheet的list -->
    function getExcelSheets() {
        //表单验证
       // if (!$("#add_form").valid()) return;
        $("#import_form").ajaxSubmit({
            url: "${base}/sys/auth/file/getExcelSheets",
            type: "post",
            dataType: "json",
            success: function (data) {
            	//设置sheetlist
            	setSheetList("sheet_list",data.sheetList);
            }
        });
    }
    <#-- 设置sheetList -->
    function setSheetList(id,sheetList){
    	$("#"+id).html("<option >"+"--请选择--"+"</option>");
    	for(var i=0 ;i<sheetList.length;i++){
    		$("#"+id).append("<option value='"+i+"'>"+sheetList[i]+"</option>");
    	}
    }
    
    function fileImport(){
    	$("#sheet_form").ajaxSubmit({
            url: "${base}/sys/auth/brch/importExcel",
            type: "post",
            dataType: "json",
            success: function (data) {
            	alert("ok");
            }
        });
    }
    </script>

![](/assets/sxcel6.png)
####(2).后台调用 ：

     controller调用：
                 /**
            	 * 导入excel数据
            	 * @param model
            	 * @param funcId
            	 * @return
            	 */
            	@RequestMapping("/importExcel")
            	@ResponseBody
                public ResultData importExcel(HttpServletRequest request) {
            		ResultData resultData=brchServ.importExcelTest(request);
                    return resultData;
                    
                }
        
                        
    service调用：
                public ResultData importExcelTest(HttpServletRequest request) {
            		//获取excel中的数据包含title和错误信息msg
            		ResultData resultData=ImportUtil.getDataList(request, SysBranchModul.class);
            		//excel数据
            		List<Map<String,Object>> excelDataList=(List<Map<String,Object>>)resultData.get("excelDataList");
            		//错误数据
            		List<SImportErrorMessage> msg=(List<SImportErrorMessage>)resultData.get("importErrorMsg");
            		for(int i=1;i<excelDataList.size();i++){
            			//获取数据
            			Map<String,Object> map=excelDataList.get(i);
            			SysBranchCust brch=new SysBranchCust();
            			brch.setBrchId(map.get("brchId").toString());
            			brch.setBrchName(map.get("brchName").toString());
            			brchMapper.insert(brch);
            		}
            		if(msg!=null && msg.size()>0){
            			resultData.setResultCode(Result_Code.BRCH_ADD_ERR);
            		}
            		return resultData;
            	}