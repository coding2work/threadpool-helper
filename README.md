## threadpool-helper(线程池助手)

* 该项目是对JDK线程池功能衍生，例如参数调整、监控等。 
* 该项目参考 dynamic-tp,hippo4j开源项目

>一个不是在造轮子，就是在造轮子路上的程序员  

## 使用痛点 

使用线程池 ThreadPoolExecutor过程中你是否有以下痛点？
1. 使用JDK ThreadPoolExecutor线程池，但不知道参数设置多少合适，例如初识线程数，队列大小等等。
2. 线程数、队列设置不合理容易删除任务拒绝，那如何根据实际情况动态调整线程池参数
3. 监控，及时了解线程池运行状况
4. 提供自定义线程池功能，当线程池达到核心线程数时，先创建新线程，直到线程数达到最大线程数之后再放入队列等优化，适合低延迟场景。


##

dynamic-tp:无配置中心应用接入（将配置放在本地配置文件中，无动态调参功能，但有监控告警功能）



### 迭代计划

1.0-SNAPSHOT(2023-03-16 start)

线程池
* 支持JDK ThreadPoolExecutor 动态参数调整
  可更改参数包含以下：
    1. corePoolSize (可以通过 setCorePoolSize() 方法来动态调整线程池的核心线程数量)
    2. maximumPoolSize (可以通过 setMaximumPoolSize() 方法来动态调整线程池的最大线程数量)
    3. keepAliveTime (可以通过 setKeepAliveTime() 和 allowCoreThreadTimeOut() 方法来动态调整线程池中空闲线程的最大存活时间)
    4. workQueue (可以通过设置不同类型的队列，动态调整任务队列的大小和类型。)
    5. handler：(可以通过 setRejectedExecutionHandler() 方法来动态设置拒绝策略，以处理超出线程池容量的任务)

* 提供REST API 修改以上参数值

监控
* Logging 支持线程池指标数据会以Json格式输出到指定的日志文件里
* Internal_loggin 支持线程池指标数据会以Json格式输出到项目日志文件里
* EndPoint 暴露Endpoint端点，可以通过http方式实时获取指标数据