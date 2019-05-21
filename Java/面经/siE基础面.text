面试问题总结如下：
1.StringBuilder和StringBuffer的区别？
    其实这道题面试官还可以继续问，string，stringBuilder，stringBuffer的区别。
    待我慢慢道来：
    首先string是一个常量，每次对String的对象进行改变时，就等同于生成了一个新的对象，指针会指向新的对象。
    所以在经常进行转换值的对象时，最好不使用String类型，消耗内存。
    其次StringBuffer是一个线程安全的可变字符序列，一个类似于String字符串的缓冲区。
    每次更改StringBuffer对象都是对此对象本身进行操作，而不是生成新的对象。建议对于频繁操作的字符串对象使用StringBuffer。
    最后StringBuilder是一个线程非安全的可变字符序列，他提供了一个与StringBuffer兼容的Api，所以在一般的实现上效率要高于StringBuffer。

2.各集合的区别？
    集合包含set map  List
    List包含：LinkedList / ArrayList /vetor/statck
    Set包含：HashSet / LinkedHashSet / TreeSet / EnumSet
    Map包含：HashMap / Hashtable / LinkedHashMap / TreeMap / WeakHashMap /ConcurrentHashMap
    当然这么多，全说出来，面试官揪住几个往深了问，你就傻眼了。你就说几个你常用的：
    LinkedList  ArrayList   HashSet  LinkedHashSet  HashMap  Hashtable LinkedHashMap
    就可以了。

    好了，话不多说，看看这些集合的不同吧：
    LinkedList和ArrayList首先他们都是可以随机访问的，是线程不安全的，按元素进入先后（有下标）保持所以是有序的并且不关心元素是否重复。
    其次LinkedList底层是链表实现的，而ArrayList底层是数组实现的。
    HashSet  LinkedHashSet  HashMap HashTable
    HashSet，inkedHashSet实现了Set接口，HashMap,HashTable实现了map接口。
    其中linkedHashSet继承自HashSet,其中HashSet内部实现是HashMap,LinkedHashSet内部实现是LinkedHashMap，
    所有HashSet和HashMap都是无序的，但似乎LinkedHashSet和LinkedHashMap都是有序的（为何有序，用了指针，元素之间维持着一条总的链表数据结构）。
    HashMap和HashTable的不同：HashMap是继承自AbstractMap类，而HashTable是继承自Dictionary类，
    其中HashMap允许key值为null,HashTable既不允许key为null值也不允许value值为null.其中HashTable是线程安全的（它的每个方法中都加入了Synchronize方法），
    HashMap不是线程安全的，所以效率上HashMap的比HashTable更高
    （当需要多线程操作的时候可以使用线程安全的ConcurrentHashMap,ConcurrentHashMap虽然也是线程安全的，
    但是它的效率比Hashtable要高好多倍。因为ConcurrentHashMap使用了分段锁，并不对整个数据进行锁定）

 

3.谈谈你对Spring的理解？
    Spring实现了工厂模式的工厂类，这个类名为BeanFactory(接口)，
    在程序中通常用他的子类ApplicationContext。
    Spring相当于一个大的工厂类，在其配置文件中通过<bean>元素配置用于
    创建实例对象的类名和实例对象的属性。其中Spring最重要的两个实现是IOC和AOP

4.AOP和IOC的理解？
    IOC也是一种编程思想，是一种架构艺术，利用这种思想可以很好地实现模块之间的解耦。 IOC就是对对象的创建、维护、销毁等生命周期的控制，
    这个过程一般是由我们的程序去主动控制。
    DI也是IOC的重要实现。一个对象的创建往往会涉及到其他对象的创建，这就是依赖。IOC机制既然负责了对象的创建，
    那么这个依赖关系也就必须由IOC容器负责起来。负责的方式就是DI——依赖注入，通过将依赖关系写入配置文件，然后在创建有依赖关系的对象时，
    由IOC容器注入依赖的对象。如在创建A时，检查到有依赖关系，IOC容器就把A依赖的对象B创建后注入到A中（组装，通过反射机制实现），
    然后把A返回给对象请求者，完成工作。
    AOP称为面向切面编程，就是系统中有很多各不相干的类的方法，在这些众多方法中要加入某种系统功能的代码，如加入日志，权限判断，异常处理，
    这种应用称为AOP。实现AOP功能采用的是代理技术，客户端程序不再调用目标，而调用代理类，代理类与目标类对外具有相同的方法声明。
    有两种方式可以实现相同的方法声明，一是实现相同的接口，二是作为目标的子类。在JDK中采用Proxy类，产生动态代理的方式为某个接口生成实现类，
    如果要为某个类生成子类，则采用CGLIB。
    系统功能的代理以Advice对象进行提供，要创建出代理对象，至少需要目标类和Advice类。Spring提供了这种支持，
    只需要在Spring配置文件中配置这两个元素即可实现代理和AOP功能。

5.JaveBean的作用域？
    首先什么叫javaBean，按我的理解就是一个可复用的java类，在mvc设计模式中又是model数据层。
    使用useBean的scope属性可以用来指定javabean的作用范围
    1.page:仅在当前页面有效
    2.request  请求范围,可以通过HttpRequest.getAttribute()方法获取JavaBean对象
    3.session  会话范围,可以通过HttpSession.getAttribute()方法获取JavaBean对象
    4.application 全局范围, 可以通过application.getAttribute()方法获取JavaBean对象


6.线程和线程池的区别？
    线程是一个程序执行流中的最小单位，由于程序运行往往是多线程运行的，而为了管理这些线程和减少内存的消耗就有了线程池的概念。
    扩展：
    创建线程的三种方法: 1.继承Thread类， new thread类对象调用start就产出新的线程。
    2.实现Ruanable接口(注意调用run方法不会产生新的线程)  
    3.通过Callable和Future创建线程。（第三种方式可以获取线程的返回值）
    常用的线程池有：1.newFixedThreadPool：创建固定大小的线程池
                   2 .newSingleThreadExecutor：创建一个单线程的线程池
                   3.newCachedThreadPool：创建带有缓存的线程池
                   4.newScheduledThreadPool：创建定时和周期性执行的线程池
 具体可见[https://mp.weixin.qq.com/s/mA59X7bOotyWwvf2V6zMIA?](https://mp.weixin.qq.com/s/mA59X7bOotyWwvf2V6zMIA?)

7.Oracle常用函数？
    1.MOD(x,y)返回 x 除以 y 的余数
    2.Concat()连接两个字符串
    3.avg()求平均值
    4.length()长度 lower()转小写 upper()转大写
    5.SUBSTR(X,start[,length]) 返回X的字串，从start处开始，截取length个字符，缺省length，默认到结尾
    6.round() 四舍五入

 8.varchar和varchar2的区别？
    varchar 对于汉字占两个字节，对于英文是一个字节，占的内存小，varchar2都是占两个字节
    varchar 对空串不处理，varchar2将空串当做null来处理
    varchar存放固定长度的字符串，最大长度是2000，varchar2是存放可变长度的字符串，最大长度是4000.

9.==和equals的区别？
    == 比较的是变量(栈)内存中存放的对象的(堆)内存地址，用来判断两个对象的地址是否相同，即是否是指相同一个对象。比较的是真正意义上的指针操作
    equals用来比较的是两个对象的内容是否相等

10.怎么形象的解释堆和栈？
    栈：stack,它是java运行的单位 
    堆：heap是存储的单位 
    代码程序计算需要空间，就比如小学算题需要演算纸一样。
    堆呢？就相当于没算出一个值将值写到作业本上，用于存储值。
    相当于你做的作业，劳动成果的体现，而草稿纸就是这些值的来源存储了值的来源初始位置。

11.数据查询的优化有哪些？
    1.减少不必要的表连接
    2.将函数运算放到逻辑代码层
    3.减少不必要的查询条件，尽量避免全表扫描
    4.用exists代替in like时，采用like 'a%' 半模糊查询而非全模糊查询
    5.对于查询条件使用频繁的采用建索引的方式
    6.限制结果集的数量
    7.创建临时表暂存中间结果
    8.注意order by语句后字段最好都是索引列
    9.表关联时取别名
    10.升级硬件，提高服务器内存，配置序列内存，增加服务器cpu数

12.缓存 cookie和session有用过吗，说一下各自的特点？
    Cookie数据保存在客户端（cookie的内容主要包括：名字，值，过期时间，路径和域），Session数据保存在服务器端
    Cookies也是属于Session对象的一种。Cookies不会占服务器资源，是存在客服端本地内存或者一个Cookie的文本文件中；而Session则会占用服务器资源。
    当我们访问一个网站时，服务器会在请求头中加入一个set-Cookie,并将cookie信息存储在响应头里。
    但是session和cookie是有关联的，当我们的请求到达服务器时，服务器为了鉴别是哪个客户端的请求，
    会在客户端传到服务端的地址url中获取对应的sessionId（sessionId如何生成的呢？服务器收到客户打端的请求后会读取cookie中的地址信息，
    调用response.encodeURL(url)解析地址方法，该方法会在解析的地址后面带上sessionId参数并放回给客户端，这样客户端在每次请求的时候带上这个sessionId）

13.redis缓存怎么样？
    回答这个问题，要考虑到应用场景：
    一般的应用场景是——请求过来，redis里面有没有？有就给用户，没有查询数据库
    数据库里面有没有？没有告诉用户没有有就查询出来，给用户，并且存放到redis。
    它有什么特点？
    （1）Redis数据库完全在内存中，使用磁盘仅用于持久性。
    （2）相比许多键值数据存储，Redis拥有一套较为丰富的数据类型。
    （3）Redis可以将数据复制到任意数量的从服务器。
Redis 优势？
     （1）异常快速：Redis的速度非常快，每秒能执行约11万集合，每秒约81000+条记录。
     （2）支持丰富的数据类型：Redis支持最大多数开发人员已经知道像列表，集合，有序集合，散列数据类型。这使得它非常容易解决各种各样的问题，因为我们知道哪些问题是可以处理通过它的数据类型更好。
     （3）操作都是原子性：所有Redis操作是原子的，这保证了如果两个客户端同时访问的Redis服务器将获得更新后的值。
     （4）多功能实用工具：Redis是一个多实用的工具，可以在多个用例如缓存，消息，队列使用(Redis原生支持发布/订阅)，任何短暂的数据，应用程序，如Web应用程序会话，网页命中计数等。
Redis 缺点？
    （1）单线程
    （2）耗内存
  具体可参考：[http://www.cnblogs.com/linkstar/p/5970354.html](http://www.cnblogs.com/linkstar/p/5970354.html)

14.什么叫接口？
    接口是一系列方特征的集合，例如实际生活中，电饭煲就是一个做饭的接口，我们只需要提供适量的米和水插上电，
    它就可以完成一系列的加工过程得到我们想要的结果。我们并不需要知道其内部实现，这样便丰富了java面向对象的思想，也使得程序变得规范简单，
    提高了可维护性和扩展性，使得程序更安全。在和前端的数据交互中，ajax调用的数据源返回数据的也可以称谓一个接口。

15.什么叫注解？
    Java注解是附加在代码中的一些元信息，用于一些工具在编译、运行时进行解析和使用，起到说明、配置的功能。
    注解不会也不能影响代码的实际逻辑，仅仅起到辅助性的作用。包含在 java.lang.annotation 包中.

    注解的用处：
      1、生成文档。这是最常见的，也是java 最早提供的注解。常用的有@param @return 等
      2、跟踪代码依赖性，实现替代配置文件功能。比如Dagger 2依赖注入，未来java开发，将大量注解配置，具有很大用处;
      3、在编译时进行格式检查。如@override 放在方法前，如果你这个方法并不是覆盖了超类方法，则编译时就能检查出。
   注解的原理：
　　  注解本质是一个继承了Annotation的特殊接口，其具体实现类是Java运行时生成的动态代理类。而我们通过反射获取注解时，返回的是Java运行时生成的动态代理对象$Proxy1。通过代理对象调用自定义注解（接口）的方法，会最终调用AnnotationInvocationHandler的invoke方法。该方法会从memberValues这个Map中索引出对应的值。而memberValues的来源是Java常量池。
      具体可参考：[https://www.cnblogs.com/jpfss/p/8126049.html](https://www.cnblogs.com/jpfss/p/8126049.html)
