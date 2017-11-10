优先使用Mybatis默认方式操作数据库。

如果Mybatis默认方式无法实现想要的效果时，可以使用动态sql。

使用方法：在需要调用的类中自动注入BaseMapper，即可使用。

示例如下：

```
    @Autowired
    private BaseMapper baseMapper;
```

```
List<Map<String, Object>> list = baseMapper.selectList("select * from sys_func");
```

可以使用增删改查等方法。

