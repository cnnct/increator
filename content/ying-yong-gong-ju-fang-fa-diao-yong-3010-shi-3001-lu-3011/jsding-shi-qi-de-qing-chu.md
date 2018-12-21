#### JS定时器的清除

如果页面导入了global.js , 执行：

```
putTimerToCookie(定时器返回值);
```

否则，执行：

```
document.cookie=定时器返回值+'Timer='+escape(定时器返回值)+';path=/';
```



