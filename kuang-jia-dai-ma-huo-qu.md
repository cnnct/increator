### 下载地址：

> svn：[https://183.129.148.83:8843/svn/IPM/互联网产品部/项目/管理平台2.0/4-版本发布](https://183.129.148.83:8843/svn/IPM/互联网产品部/项目/管理平台2.0/4-版本发布)
>
> 用户名密码：manageplat2/manageplat2![](/assets/code_download.png)

### 使用介绍：

> * db目录：基础数据库脚本，包含oracle版本和mysql版本，适用于新项目开始使用；其中数据库脚本也分为全量all和增量increment
> * war目录：增量更新代码目录，适用于已在用的系统，后期升级使用。更新覆盖前先仔细核对或咨询再更新。
> * zip目录：全量框架代码目录，适用于新项目开始使用。
> * 从V1.2.3版本开始，版本发布目录结构作了调整，调整后的目录层次示例如下：
>
> > 1.2【版本分支目录】
> > ```  
> >db【数据库脚本目录】
> >-----mysql_x.y.z【mysql数据库脚本目录】
> >--------all【全量数据库脚本目录】
> >------------mysql_structure_Vx.y.z.sql【mysql全量库结构脚本】
> >------------mysqle_data_Vx.y.z.sql【mysql全量库数据脚本】
> >--------increment【增量数据库脚本目录】
> >------------mysqle_increment__Vx.y.z.sql【oracle增量库数脚本（相对前一版本全量库基础之上）】
> >----oracle_x.y.z【oracle数据库脚本目录】
> >--------all【全量数据库脚本目录】
> >------------oracle_structure_Vx.y.z.sql【oralce全量库结构脚本】
> >------------oracle_data_Vx.y.z.sql【oralce全量库数据脚本】
> >--------increment【增量数据库脚本目录】
> >------------oracle_increment__Vx.y.z.sql【oracle增量库数脚本（相对前一版本全量库基础之上）】
> >code
> > ```

### 框架开发库地址（内网）

> mysql：
>
> > jdbc.url=jdbc:mysql://172.16.200.200:3306/manageplat?useUnicode=true&characterEncoding=utf-8
> >
> > jdbc.username=root
> >
> > jdbc.password=123456
>
> oralce：
>
> > jdbc.url=jdbc:oracle:thin:@172.16.200.117:1521:ORCL
> >
> > jdbc.username=manageplat
> >
> > jdbc.password=nct

### 更新升级必读！！！！

> * 代码包分为全量包和增量包。
> * 全量包直接使用。
> * 增量包是相对于上一全量版本基础上的增量包。因此若当前使用的版本较旧，则请逐一分批次使用每次的增量更新包更新。



