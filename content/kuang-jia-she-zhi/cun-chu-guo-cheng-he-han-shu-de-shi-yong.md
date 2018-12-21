# 存储过程和函数的使用

这两个使用方法一致，都有如下两种：

1、

```
<select id="callProcedure" parameterType="map" statementType="CALLABLE">
    call prg_add(
        #{inParam,mode=IN,jdbcType=VARCHAR},
        #{outParam1,mode=OUT,jdbcType=INTEGER},
        #{outParam2,mode=OUT,jdbcType=VARCHAR}
    )
</select>
```

2、

```
<select id="callProcedure" parameterMap="params" statementType="CALLABLE">
    call prg_add(?,?,?)
</select>
<parameterMap type="java.util.Map" id="params">
    <parameter property="inParam" mode="IN" jdbcType="VARCHAR"/>
    <parameter property="outParam1" mode="OUT" jdbcType="INTEGER"/>
    <parameter property="outParam2" mode="OUT" jdbcType="VARCHAR"/>
</parameterMap>
```



