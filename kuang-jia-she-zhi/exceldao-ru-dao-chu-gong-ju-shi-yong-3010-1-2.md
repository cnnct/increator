# excel导入导出工具使用

### 1.导出工具使用示例：
#### (1).前台调用：
    注意这里不能使用ajax请求，必须用普通请求
    function doTest(obj){
    	window.location.href ='${base}/sys/auth/brch/exportExcelTest?brchId='+getFirstInputId(obj);
    	
    }
    