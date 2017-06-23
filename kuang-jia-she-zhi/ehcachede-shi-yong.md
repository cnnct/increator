在config下的

ehcache.xml

该配置文件是对Ehcache缓存的配置，具体用法如下

```
name:缓存名称。

maxElementsInMemory：缓存最大个数。


eternal:对象是否永久有效，一但设置了，timeout将不起作用。


timeToIdleSeconds：设置对象在失效前的允许闲置时间（单位：秒）。仅当eternal=false对象不是永久有效时使用，可选属性，默认值是0，也就是可闲置时间无穷大。


timeToLiveSeconds：设置对象在失效前允许存活时间（单位：秒）。最大时间介于创建时间和失效时间之间。仅当eternal=false对象不是永久有效时使用，默认是0.，也就是对象存活时间无穷大。


overflowToDisk：当内存中对象数量达到maxElementsInMemory时，Ehcache将会对象写到磁盘中。


diskSpoolBufferSizeMB：这个参数设置DiskStore（磁盘缓存）的缓存区大小。默认是30MB。每个Cache都应该有自己的一个缓冲区。


maxElementsOnDisk：硬盘最大缓存个数。


diskPersistent：是否缓存虚拟机重启期数据
Whether
the
disk
store
persists
between
restarts
of
the
Virtual
Machine.
The
default
value
is
false.


diskExpiryThreadIntervalSeconds：磁盘失效线程运行时间间隔，默认是120秒。


memoryStoreEvictionPolicy：当达到maxElementsInMemory限制时，Ehcache将会根据指定的策略去清理内存。默认策略是LRU（最近最少使用）。你可以设置为FIFO（先进先出）或是LFU（较少使用）。


clearOnFlush：内存数量最大时是否清除。
```

例：

![](/assets/ehcache.png)

name不能重复，用于Ehcache的缓存名称。一般memoryStoreEvictionPolicy都设置为LRU（最少使用），以session为例

```
timeToIdleSeconds="1800" --闲置30分钟失效
timeToLiveSeconds="0"    --默认对象只要在使用就永不失效
```

程序中使用：

在src.com.cnnct.base.cache.factory目录下

创建以ehcache.xml配置文件中配置的name 名称开头，CacheFactory结尾的缓存工厂类，实现CacheFactory接口，

![](/assets/errCodeCacheFactory.png)

重写getCache方法，manager.getCache\(""\)中写入ehcache.xml中对应的cache的name，如果需要初始化的时候在cache中加入值，name需要在cache目录下创建Product结尾的文件

例如：

![](/assets/product.png)

并实现Product接口，重写create方法。并在application-service.xml中配置service

例（红框的是重点）：

![](/assets/service-eache.png)

并在对应的cache工厂类方法中提供对应的set方法，在set方法中，赋值给静态对象。

例：

![](/assets/service-cachefactory.png)

因为， Ehcache的使用需要创建 Element，对Element对象进行操作，在程序中操作不是很方便。name在utils下的CacheUtil中，可以添加get，put，remove等方法

例：

![](/assets/cacheUtil.png)

