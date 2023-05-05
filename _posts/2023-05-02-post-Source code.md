---
title: "源码"
date: 2023-05-02 14:30:55-23:00
last_modified_at: 2023-05-05 22:30:55-23:00
categories:
  - JAVA
---

源码:

	ArrayList
		无参构造，初始容量为0，第一次扩容为10，后续也为前一次容量的1.5倍
		有参构造，入参为初始容量，扩容一次为初始容量的1.5倍
		线程不安全，可以使用CopyOnWriteArrayList
	LinkedList
		前驱后继节点 双向链表
	HashMap
		数组+单向链表+红黑树 线程不安全，可以使用ConcurrentHashMap
		key的hashCode值决定,(n-1)&hash，n必须为2的幂数，扩容会引起元素位置的改变
		初始容量为16，阈值16*0.75=12，达到阈值后，每次扩容为前一次容量的2倍
		有参构造时的容量为入参最近的2的幂数
		Node<k,v>[] table，存的可能是节点-链表-红黑树(TreeNode<k,v>)
		链表长度超过8，hash桶的容量达到64，就会转为红黑树(容量达不到64时会调用扩容方法，进行扩容)
		红黑树的长度小于6时会转换为链表
	LinkedHashMap
		继承HashMap，实现Map，双向链表 前驱后继节点
	TreeMap
		构造函数-comparator比较器-红黑树排序(小的节点在左边，大的节点在右边)
	线程
		优先使用实现Runnable接口去创建子线程，方便线程间共享数据
		run方法是开启主线程，start才是开启一个子线程，线程默认优先级为5，从1到10
		jvisualvm.exe
			 daemon 守护线程-finalizer 垃圾回收线程；可以看是否有死锁
		实现Callable(可以返回值，抛异常) ，要等到call方法执行完成才能执行主线程
			FutureTask<String> fts = new FutureTask<String>(new Callable<String>() {}）
		ThreadLocal保证每个线程都创建一个对象，保证线程安全(通过System.identityHashCode(obj) 获得标识哈希码)
			底层实现：Thread对象里面的ThreadLocalMap集合，key存threadloocal；value存对象
	