### Handler原理

Android的线程间通信就靠Handler、Looper、Message、MessageQueue这四个麻瓜兄弟了

1，首先我们从looper开始分析

在Looper中，维持一个Thread对象以及MessageQueue，通过Looper的构造函数我们可以知道:

    private Looper(boolean quitAllowed) {
        mQueue = new MessageQueue(quitAllowed);//传入的参数代表这个Queue是否能够被退出
        mThread = Thread.currentThread();
    }

Looper在构造函数里干了两件事情：  
 1. 将自己维持的线程对象指向了创建Looper的线程  
 2. 创建了一个新的MessageQueue消息队列  

所以我们先来分析Handler的构造方法

空参数的构造方法与之对应，这里只给出主要的代码，具体大家可以到源码中查看  

    public Handler(Callback callback, boolean async) {
    	//打印内存泄露提醒log
   	 ....
    
   	 //获取与创建Handler线程绑定的Looper
   	 mLooper = Looper.myLooper();
   		 if (mLooper == null) {
    		throw new RuntimeException( "Can't create handler inside thread that has not called Looper.prepare()");
   		 }
   		 //获取与Looper绑定的MessageQueue
   		 //因为一个Looper就只有一个MessageQueue，也就是与当前线程绑定的MessageQueue
   		 mQueue = mLooper.mQueue;
   		 mCallback = callback;
   		 mAsynchronous = async;
    }  
    

    public static @Nullable Looper myLooper() {
    	return sThreadLocal.get();
    }

looper.prepare()（在当前线程关联一个Looper对象）

     private static void prepare(boolean quitAllowed) {
    	if (sThreadLocal.get() != null) {
    		throw new RuntimeException("Only one Looper may be created per thread");
    	}
    	//在当前线程绑定一个Looper
    	sThreadLocal.set(new Looper(quitAllowed));
    }
以上代码只做了两件事情：  
 1. 判断当前线程有木有Looper，如果有则抛出异常（在这里我们就可以知道，Android规定一个线程只能够拥有一个与自己关联的Looper）。   
 2. 如果没有的话，那么就设置一个新的Looper到当前线程。





