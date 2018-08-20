#### listview的优化
1，包括利用好 ConvertView
目的：减少layout去inflate填充的次数，因为每次填充都会解析布局，很消耗资源；

2，利用好viewholder，而且最好static，避免内存泄漏；
目的；主要是减少findviewbyid的次数
3，采用分页加载；如果有bitmap图片，使用软引用包裹一下；

3；利用好展示不同类型的viewtype，两个方法，getitemViewType（）和getViewTypecount（）；
第一个方法是告诉 ListView 当前 position 对应哪种 ViewType ，第二个方法是告诉 ListView 一共有多少中 ViewType 

4；减少item中view的绘制时间；即避免item视图过于复杂
android系统每隔16.7ms就会给主线程发起一个渲染信号，让主线程去绘制ui，当我们把listview添加到布局，并不断刷新，listview会不断调用
getview方法，如果视图过于复杂，需要不断的measure和draw的话，有可能导致时间超过了16.7ms，就会出现掉帧的情况；

5；使用自定义布局；（自己和自定义组合控件类似）
自定义布局有个好处就是可以省略ViewHolder；并且也不需要findviewbyid，因为自定义布局的构造方法已经findviewbyid了，并且自定义布局只需要提供
对外暴露设置属性的方法就可以了；比如里面有个textview，直接搞个方法setitemText（），完事

6；保证每个item高度不要太高；
尽量小于屏幕的四分之三；这样方便view的回收；facebook出了一套完整的方案，但是我现在记不太清了；

7；getview（）方法尽量少做事；
因为getview方法会不断被调用，内容太多，影响性能；

8；使用硬件加速等；