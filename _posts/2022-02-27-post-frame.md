---
title: "框架"
date: 2022-02-27 19:51:28-23:00
last_modified_at: 2023-04-20 20:36:41-23:00
categories:
  - 学习
---

框架：

	Spring
		ioc
			控制反转 依赖注入
		AOP(面向切面编程)
		事务
			@Transactional注解只能应用到 public 可见度的方法，主事务-子事务
			事务传播机制，7个机制：required(默认，支持当前事务)，requires_new(创建一个新的事务并挂起当前事务)，nested(如果存在事务则嵌套事务内执行，不存在事务则相当于required)
	SpringMvc
		执行流程：前端控制器DispatcherServlet-->处理器映射器HandlerMapping-->Handler-->处理器适配器HandlerAdaper-->视图解析器ViewResolver-->View
	SpringBoot
		简化Spring应用程序的创建和开发过程
		抛弃了xml文件匹配文件，采用默认配置以及反射和注解
		内嵌了Tomcat服务器运行程序，不需要部署war包文件
	SpringCloud
		多个模块组件、接口feign调用http的rest风格，比较灵活
			Eureka:服务治理组件
			Hystrix:服务容错组件(通过线程池隔离资源)
			GateWay:API网关组件
	阿里热部署Arthas（阿尔萨斯）
		#### 获取arthas全量包 并 启动arthas

		sc -d cn.ffcs.controller.GroupController | grep classLoader
retransform /home/ctffview/GroupController.class
		查看 dashboard  thread 1 查具体线程信息；thread -b 查堵塞线程；jad *** 反编译代码cn.ffcs.controller.GroupController；打印类的详细信息 sc -d demo.MathGame；用ognl查看修改内存中变量的值 watch com.taobao.container.Test test "params[0]" 、watch com.taobao.container.Test test "{params}" "params[0].{? #this.name == null }.size()>0" -x 2
	dubbo
		服务注册中心Zookeeper、服务治理、服务之间的通信用的RPC(接口强依赖性，但是采用Netty的nio速度快)、客户端和服务器是JAVA接口之间的调用
	Zookeeper
		原子广播
		谁先启动谁当Leader，需要超过半数
		事务id号(zxid)，最大的当选Leader