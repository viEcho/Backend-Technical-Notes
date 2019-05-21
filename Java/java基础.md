——JAVA基础部分
===
###1. 我们能不能声明main()方法为非静态？√


        不能，main()方法必须声明为静态的，这样JVM才可以调用main()方法而无需实例化它的类。

        如果从main()方法去掉“static”这个声明，虽然编译依然可以成功，但在运行时会导致程序失败。

 

###2.不用main方法如何运行一个类？√

        不行，没有main方法我们不能运行Java类。

        在Java 7之前，你可以通过使用静态初始化运行Java类。但是，从Java 7开始就行不通了。

 

###3. String类为什么是final的。√

        主要是为了“效率”和“安全性”的缘故。若 String允许被继承, 由于它的高度被使用率,可能会降低程序的性能，所以String被定义成final;

 

###4.使用final 关键字修饰一个变量时，是引用不能变，还是引用的对象不能变？√

        使用final 关键字修饰一个变量时，是指引用不能变，引用变量所指向的对象中的内容还是可以改变的。

 

###5. string、stringbuilder、stringbuffer区别√

        a.可变与不可变 
        
            String类中使用字符数组保存字符串，如下就是，因为有“final”修饰符，所以可以知道string对象是不可变的。private final char value[];
        
            StringBuilder与StringBuffer都继承自AbstractStringBuilder类，在AbstractStringBuilder中也是使用字符数组保存字符串，如下就是，可知这两种对象都是可变的。char[] value;
        
        b. 是否多线程安全
        
        　　String中的对象是不可变的，也就可以理解为常量，显然线程安全。
        
        　　AbstractStringBuilder是StringBuilder与StringBuffer的公共父类，定义了一些字符串的基本操作，如expandCapacity、append、insert、indexOf等公共方法。
        
        　　StringBuffer对方法加了同步锁或者对调用的方法加了同步锁，所以是线程安全的 StringBuilder并没有对方法进行加同步锁，所以是非线程安全的
        
        c. StringBuilder与StringBuffer共同点
        
        　　StringBuilder与StringBuffer有公共父类AbstractStringBuilder(抽象类)。
        
        　　抽象类与接口的其中一个区别是：抽象类中可以定义一些子类的公共方法，子类只需要增加新的功能，不需要重复写已经存在的方法；而接口中只是对方法的申明和常量的定义。
        
        　　StringBuilder、StringBuffer的方法都会调用AbstractStringBuilder中的公共方法，如super.append(...)。只是StringBuffer会在方法上加synchronized关键字，进行同步。
        
        　　最后，如果程序不是多线程的，那么使用StringBuilder效率高于StringBuffer。

 

###6. 抽象类和接口的区别√

        1).抽象类可以有构造方法，接口中不能有构造方法。
        
        2).抽象类中可以有普通成员变量，接口中没有普通成员变量
        
        3).抽象类中可以包含非抽象的普通方法，接口中的所有方法必须都是抽象的，不能有非抽象的普通方法。
        
        4). 抽象类中的抽象方法的访问类型可以是public，protected 和（默认类型,虽然
        
        eclipse 下不报错，但应该也不行），但接口中的抽象方法只能是public 类型的，并且默认即为public abstract 类型。
        
        5). 抽象类中可以包含静态方法，接口中不能包含静态方法
        
        6). 抽象类和接口中都可以包含静态成员变量，抽象类中的静态成员变量的访问类型可以任意，
        
        但接口中定义的变量只能是public static final 类型，并且默认即为public static final 类型。
        
        7). 一个类可以实现多个接口，但只能继承一个抽象类。

 

###7. Java 中应该使用什么数据类型来代表价格？√

        如果不是特别关心内存和性能的话，使用BigDecimal，否则使用预定义精度的 double 类型。

 

###8. 静态变量和实例变量的区别？√

        在语法定义上的区别：
        
        静态变量前要加static 关键字，而实例变量前则不加。
        
        在程序运行时的区别：
        
        实例变量属于某个对象的属性，必须创建了实例对象，其中的实例变量才会被分配空间，才能使用这个实例变量。静态变量不属于某个实例对象，而是属于类，所以也称为类变量，只要程序加载了类的字节码，不用创建任何实例对象，静态变量就会被分配空间，静态变量就可以被使用了。总之，实例变量必须创建对象后才可以通过这个对象来使用，静态变量则可以直接使用类名来引用。

 

###9. final, finally, finalize 的区别。√

        final 用于声明属性，方法和类，分别表示属性不可变，方法不可覆盖，类不可继承。
        
        内部类要访问局部变量，局部变量必须定义成final 类型，例如，一段代码……
        
        finally 是异常处理语句结构的一部分，表示总是执行。
        
        finalize 是Object 类的一个方法，在垃圾收集器执行的时候会调用被回收对象的此方法，可以覆盖此方法提供垃圾收集时的其他资源回收，例如关闭文件等。JVM 不保证此方法总被调用

 

###10. sleep() 和wait() 有什么区别?√

        sleep 就是正在执行的线程主动让出cpu，cpu 去执行其他线程，在sleep 指定的时间过后，cpu才会回到这个线程上继续往下执行，如果当前线程进入了同步锁，sleep 方法并不会释放锁，即使当前线程使用sleep 方法让出了cpu，但其他被同步锁挡住了的线程也无法得到执行。
        
        wait 是指在一个已经进入了同步锁的线程内，让自己暂时让出同步锁，以便其他正在等待此锁的线程可以得到同步锁并运行，只有其他线程调用了notify 方法（notify 并不释放锁，只是告诉调用过wait 方法的线程可以去参与获得锁的竞争了，但不是马上得到锁，因为锁还在别人手里，别人还没释放。如果notify 方法后面的代码还有很多，需要这些代码执行完后才会释放锁，可以在notfiy 方法后增加一个等待和一些代码，看看效果），调用wait 方法的线程就会解除wait 状态和程序可以再次得到锁后继续向下运行。

 

###11. HashMap 和Hashtable 的区别√

        HashMap 是Hashtable 的轻量级实现（非线程安全的实现），他们都完成了Map 接口，主要区别在于HashMap 允许空（null）键值（key）,由于非线程安全，在只有一个线程访问的情况下，效率要高于Hashtable。
        
        HashMap 允许将null 作为一个entry 的key 或者value，而Hashtable 不允许。
        
        HashMap 把Hashtable 的contains 方法去掉了，改成containsvalue 和containsKey。因为contains方法容易让人引起误解。
        
        Hashtable 继承自Dictionary 类，而HashMap 是Java1.2 引进的Map interface 的一个实现。
        
        最大的不同是，Hashtable 的方法是Synchronize 的，而HashMap 不是，在多个线程访问Hashtable时，不需要自己为它的方法实现同步，而HashMap 就必须为之提供外同步。
        
        Hashtable 和HashMap 采用的hash/rehash 算法都大概一样，所以性能不会有很大的差异。
        
        就HashMap 与HashTable 主要从三方面来说。
        
        一.历史原因:Hashtable 是基于陈旧的Dictionary 类的，HashMap 是Java 1.2 引进的Map 接口的一个实现
        
        二.同步性:Hashtable 是线程安全的，也就是说是同步的，而HashMap 是线程序不安全的，不是同步的
        
        三.值：只有HashMap 可以让你将空值作为一个表的条目的key 或value

 

###12. jsp 有哪些内置对象?作用分别是什么? 分别有什么方法？√

    JSP 共有以下9 个内置的对象：
        
        request 用户端请求，此请求会包含来自GET/POST 请求的参数
        
        response 网页传回用户端的回应
        
        pageContext 网页的属性是在这里管理
        
        session 与请求有关的会话期
        
        application servlet 正在执行的内容
        
        out 用来传送回应的输出
        
        config servlet 的构架部件
        
        page JSP 网页本身
        
        exception 针对错误网页，未捕捉的例外

 

###13. JSP 和Servlet 有哪些相同点和不同点，他们之间的联系是什么？√

        JSP 是Servlet 技术的扩展，本质上是Servlet 的简易方式，更强调应用的外表表达。JSP 编译后是"类servlet"。Servlet 和JSP 最主要的不同点在于，Servlet 的应用逻辑是在Java 文件中，并且完全从表示层中的HTML 里分离开来。而JSP 的情况是Java 和HTML 可以组合成一个扩展名为.jsp 的文件。JSP 侧重于视图，Servlet 主要用于控制逻辑。

 

###14. get与post之间的区别：√

    1>请求参数的存放位置：
    
    get: 在url后面用?拼接
    
    post:  参数放在请求数据包请求实体部分。
    
    2>参数的数据量大小：
    
        get:  传递数据量大小有限制
    
        post:  理论上没有限制, 存放在实体部分
    
    3>安全性：
    
    get: 相对不安全
    
    post: 相对安全
    
    4>编码相关：
    
        get:  不适合传递中文参数
    
        post:  适合传递中文参数

 

###15. 同步和异步有何异同，在什么情况下分别使用他们？举例说明√

        如果数据将在线程间共享。例如正在写的数据以后可能被另一个线程读到，或者正在读的数据可能已经被另一个线程写过了，那么这些数据就是共享数据，必须进行同步存取。当应用程序在对象上调用了一个需要花费很长时间来执行的方法，并且不希望让程序等待方法的返回时，就应该使用异步编程，在很多情况下采用异步途径往往更有效率。

 

###16.说说你写程序时经常碰到那些异常，什么原因产生的？你是怎么解决的！√

    常见的异常有：
        
        java.lang.nullpointerexception 解释是"程序遇上了空指针",就是调用了未经初始化的对象或者是不存在。
        
        java.lang.classnotfoundexception 解释是"指定的类不存在"，这里主要考虑一下类的名称和路径是否正确即可。
        
        java.lang.arrayindexoutofboundsexception 解释是"数组下标越界"，现在程序中大多都有对数组的操作，因此在调用数组的时候一定要认真检查，看自己调用的下标是不是超出了数组的范围。
        
        FileNotFoundException 解释是“文件未找到异常”。
        
        IOException 解释是”输入输出流异常“。
        
        NoSuchMethodException 解释是"方法未找到异常"。

 

 

###17. Servlet当中如何获取到jsp的9个隐含对象！√

        JspFactory jf=JspFactory.getDefaultFactory();
        
        // PageContext pageContext=jf.getPageContext(
        
        // this, request, response,null,false,
        
        // JspWriter.DEFAULT_BUFFER, true);

 

###18. 问题：Servlet是如何工作的？Servlet 如何实例化、共享变量、并进行多线程处理？√

        假设我有一个运行了大量 Servlet 的 web 服务器。通过 Servlet 之间传输信息得到 Servlet 上下文，并设置 session 变量。
        
        现在，如果有两名或更多使用者向这个服务发送请求，接下来 session 变量会发生什么变化？究竟是所有用户都是用共同的变量？还是不同的用户使用的变量都不一样？如果是后者，服务器如何区分不同用户？
        
        另一个相似的问题，如果有 n名用户访问一个特定的 Servlet，那么该 Servlet 是仅在第一个用户首次访问的时候实例化，还是分别为每个用户实例化？
        
        回答（BalusC）：
        
        ServletContext√
        
        当 Servlet 容器（比如 Apache Tomcat）启动后，会部署和加载所有 web 应用。当web 应用被加载，Servlet 容器会创建一次 ServletContext，然后将其保存在服务器的内存中。web 应用的 web.xml 被解析，找到其中所有 servlet、filter 和 Listener 或 @WebServlet、@WebFilter 和@WebListener 注解的内容，创建一次并保存到服务器的内存中。对于所有过滤器会立即调用 init()。当 Servlet 容器停止，将卸载所有 web 应用，调用所有初始化的 Servlet 和过滤器的 destroy() 方法，最后回收 ServletContext 和所有 Servlet、Filter 与 Listener 实例。
        
        当问题中的 Servlet 配置的 load-on-startup 或者 @WebServlet(loadOnStartup) 设置了一个大于 0 的值，则同样会在启动的时候立即调用 init() 方法。“load-on-startup”中的值表示那些 Servlet 会以相同顺序初始化。如果配置的值相同，会遵循 web.xml 中指定的顺序或 @WebServlet 类加载的顺序。另外，如果不设置 “load-on-startup” 值，init() 方法只在第一次 HTTP 请求命中问题中的 Servlet 时才被调用。
        
        HttpServletRequest 与 HttpServletResponse√
        
        Servlet 容器附加在一个 web 服务上，这个 web 服务会在某个端口号上监听 HTTP 请求，在开发环境中这个端口通常为 8080，生产环境中通常为 80。当客户端（web 浏览器）发送了一个 HTTP 请求，Servlet 容器会创建新的 HttpServletRequest 和 HttpServletResponse 对象，传递给已创建好并且请求的 URL 匹配 url-pattern 的 Filter 和 Servlet 实例中的方法，所有工作都在同一个线程中处理。
        
        request 对象可以访问所有该 HTTP 请求中的信息，例如 request header 和 request body。response 对象为你提供需要的控制和发送 HTTP 响应方法，例如设置 header 和 body（通常会带有 JSP 文件中的 HTML 内容）。提交并完成HTTP 响应后，将回收 request 和 response 对象。
        
        HttpSession√
        
        当用户第一次访问该 web 应用时，会通过 request.getSession() 第一次获得 HttpSession。之后 Servlet 容器将会创建 HttpSession，生成一个唯一的 ID（可以通过 session.getId() 获取）并储存在服务器内存中。然后 Servlet 容器在该次 HTTP 响应的 Set-Cookie 头部设置一个 Cookie，以 JSESSIONID 作为 Cookie 名字，那个唯一的 session ID 作为 Cookie 的值。
        
        按照 HTTP cookie 规则（正常 web 浏览器和 web 服务端必须遵循的标准），当 cookie 有效时，要求客户端（浏览器）在后续请求的 Cookie 头中返回这个 cookie。使用浏览器内置的 HTTP 流量监控器，你可以查看它们（在 Chrome、Firefox23+、IE9+ 中按 F12，然后查看 Net/Network 标签）。Servlet 容器将会确定每个进入的 HTTP 请求的 Cookie 头中是否存在名为JSESSIONID 的 cookie，然后用它的值（session ID）从服务端内存中找到关联的 HttpSession。
        
        你可以在 web.xml 中设置 session-timeout ，默认值为 30 分钟。超时到达之前 HttpSession 会一直存活。所以当客户端不再访问该 web 应用超过 30 分钟后，Servlet 容器就会回收这个 session。后续每个请求，即使指定 cookie 名称也不能再访问到相同的 session。Servlet 容器会创建一个新的 Cookie。
        
        另一方面，客户端上的 session cookie 有一个默认存活时间，该事件和该浏览器实例运行时间一样长。所以，当客户端关闭该浏览器实例（所有标签和窗口）后，这个 session 就会被客户端回收。新浏览器实例不再发送与该 session 关联的 cookie。一个新的 request.getSession() 将会返回新的 HttpSession 并设置一个拥有新 session ID 的 cookie。
        
        概述√
        
        ServletContext 与 web 应用存活时间一样长。它被所有 session 中的所有请求共享。
        
        只要客户端一直与相同浏览器实例的web应用交互并且没有超时，HttpSession就会存在。
        
        HttpServletRequest 和 HttpServletResponse 的存活时间为客户端发送完成到完整的响应（web 页面）到达的这段时间。不会被其他地方共享。
        
        所有 Servlet、Filter 和 Listener 对象在 web 应用运行时都是活跃的。它们被所有 session 中的请求共享。
        
        你设置在 HttpServletRequest、HttpServletResponse 和 HttpSession 中的所有属性在问题中的对象存活时都会一直保持存活。
        
        线程安全√
        
        即便如此，你最关心的可能是线程安全。你现在应该学习到 Servlet 和 filter 被所有请求共享。那是 Java 的一个优点，使得多个不同线程（读取 HTTP 请求）可以使用同一个实例。否则为每个请求重新创建线程的开销实在过于昂贵。
        
        但你应该也意识到永远不要将任何 request 或 session 域中的数据赋值给 servlet 或 filter 的实例变量。它将会被所有其他 session 中的所有请求共享。那是非线程安全的！

 

###19.LinkedList和ArrayList的区别√

        LinkedeList和ArrayList都实现了List接口，但是它们的工作原理却不一样。它们之间最主要的区别在于ArrayList是可改变大小的数组，而LinkedList是双向链接串列(doubly LinkedList)。ArrayList更受欢迎，很多场景下ArrayList比LinkedList更为适用。这篇文章中我们将会看看LinkedeList和ArrayList的不同，而且我们试图来看看什么场景下更适宜使用LinkedList，而不用ArrayList。
        
        LinkedList和ArrayList的区别（linkedList基于链表的操作，所以增删快，但是查询慢，对内存的开销大。ArrayList基于数组（下标）的操作，所以查询快，如果要执行删除操作会涉及数组下标的重现排列所以内存开销大。）√
        
        LinkedList和ArrayList的差别主要来自于Array和LinkedList数据结构的不同。如果你很熟悉Array和LinkedList，你很容易得出下面的结论：
        
        1) 因为Array是基于索引(index)的数据结构，它使用索引在数组中搜索和读取数据是很快的。Array获取数据的时间复杂度是O(1),但是要删除数据却是开销很大的，因为这需要重排数组中的所有数据。
        
        2) 相对于ArrayList，LinkedList插入是更快的。因为LinkedList不像ArrayList一样，不需要改变数组的大小，也不需要在数组装满的时候要将所有的数据重新装入一个新的数组，这是ArrayList最坏的一种情况，时间复杂度是O(n)，而LinkedList中插入或删除的时间复杂度仅为O(1)。ArrayList在插入数据时还需要更新索引（除了插入数组的尾部）。
        
        3) 类似于插入数据，删除数据时，LinkedList也优于ArrayList。
        
        4) LinkedList需要更多的内存，因为ArrayList的每个索引的位置是实际的数据，而LinkedList中的每个节点中存储的是实际的数据和前后节点的位置。
        
        什么场景下更适宜使用LinkedList，而不用ArrayList√
        
        我前面已经提到，很多场景下ArrayList更受欢迎，但是还有些情况下LinkedList更为合适。譬如：
        
        1) 你的应用不会随机访问数据。因为如果你需要LinkedList中的第n个元素的时候，你需要从第一个元素顺序数到第n个数据，然后读取数据。
        
        2) 你的应用更多的插入和删除元素，更少的读取数据。因为插入和删除元素不涉及重排数据，所以它要比ArrayList要快。
        
        以上就是关于ArrayList和LinkedList的差别。你需要一个不同步的基于索引的数据访问时，请尽量使用ArrayList。ArrayList很快，也很容易使用。但是要记得要给定一个合适的初始大小，尽可能的减少更改数组的大小。

 

###20. 为什么接口要规定成员变量必须是public static final的呢?√

        首先接口是一种高度抽象的"模版"，,而接口中的属性也就是’模版’的成员，就应当是所有实现"模版"的实现类的共有特性，所以它是public static的 ,是所有实现类共有的 .假如可以是非static的话，因一个类可以继承多个接口，出现重名的变量，如何区分呢？
        
        其次,接口中如果可能定义非final的变量的话，而方法又都是abstract的，这就自相矛盾了，有可变成员变量但对应的方法却无法操作这些变量，虽然可以直接修改这些静态成员变量的值，但所有实现类对应的值都被修改了，这跟抽象类有何区别? 并且接口是一种更高层面的抽象，是一种规范、功能定义的声明，所有可变的东西都应该归属到实现类中，这样接口才能起到标准化、规范化的作用。所以接口中的属性必然是final的。
        
        最后，接口只是对事物的属性和行为更高层次的抽象 。对修改关闭，对扩展（不同的实现implements）开放，接口是对开闭原则（Open-Closed  Principle）的一种体现。

 

###21. 遍历一个List有哪些不同的方式？使用哪种方式更加线程安全？√

        1）for-each(增强for循环)
        
        2）迭代器遍历（线程更加安全）

 

###22. Array和ArrayList有何区别？什么时候更适合用Array？√

        Array可以容纳基本类型和对象，而ArrayList只能容纳对象。
        
        Array是指定大小的，而ArrayList大小是固定的。
        
        Array没有提供ArrayList那么多功能，比如addAll、removeAll和iterator（迭代器）等。尽管ArrayList明显是更好的选择，但也有些时候Array比较好用。
        
        （1）如果列表的大小已经指定，大部分情况下是存储和遍历它们。
        
        （2）对于遍历基本数据类型，尽管Collections使用自动装箱来减轻编码任务，在指定大小的基本类型的列表上工作也会变得很慢。
        
        （3）如果你要使用多维数组，使用[][]比List<List<>>更容易。

 

###23. 创建线程有几种不同的方式？你喜欢哪一种？为什么？√

        有三种方式可以用来创建线程：
        
        继承Thread类
        
        实现Runnable接口
        
        应用程序可以使用Executor框架来创建线程池
        
        实现Runnable接口这种方式更受欢迎，因为这不需要继承Thread类。在应用设计中已经继承了别的对象的情况下，这需要多继承（而Java不支持多继承），只能实现接口。同时，线程池也是非常高效的，很容易实现和使用。

 

###24. 什么是死锁(deadlock)？如何避免deadlock？---->//循序锁√

        两个进程都在等待对方执行完毕才能继续往下执行的时候就发生了死锁。结果就是两个进程都陷入了无限的等待中。
        
        使用多线程的时候，一种非常简单的避免死锁的方式就是：指定获取锁的顺序，并强制线程按照指定的顺序获取锁。因此，如果所有的线程都是以同样的顺序加锁和释放锁，就不会出现死锁了。

 

###25. 在System.out.println()里面,System, out, println分别是什么?√

        System是系统提供的预定义的final类，out是一个PrintStream对象，println是out对象里面一个重载的方法。

 

###26. JAVA源文件中是否可以包括多个类，有什么限制？√
        
        答：一个java源文件中可以包含多个类，但每个源文件中只允许一个public类，
        
        如果源文件中没有public类，则源文件用什么名字都可以。

 

###27. 类有哪三个基本特性？各特性的优点？（缺省，即系统默认状态，意思与“默认”相同）√

        类具有封装性、继承性和多态性。
        
        封装性：类的封装性为类的成员提供公有、缺省、保护和私有等多级访问权限，目的是隐藏类中的私有变量和类中方法的实现细节。
        
        继承性：类的继承提供从已存在的类创建新类的机智，继承使一个新类自动拥有继承类（父类）的全部可继承的成员。
        
        多态性：类的多态性提供类中方法执行的多样性，多态性有两种表示形式：重载和覆盖。

 

###28. 列出你常用的JDK包？√

        java.io：这里面是所有输入输出有关的类，都是基于这个包下；比如文件操作等
    
        java.net：这里面是与网络有关的类，比如URL,URLConnection等。
    
        java.util：这个是系统辅助类，特别是集合类Collection，List，Map等。
    
        Java.sql：这个是数据库操作的类，Connection，Statemenmt，ResultSet等。  

 

###29. JavaScript如何定义数组？√

        var arrTest = new Array();

 

###30.JavaScript能否操作cookie和session？√

        JavaScript可以操作cookie，但是不能操作session。
        
        //JS是客户端的操作，是servlet组件功能的扩展。而session是用于在服务端的数据储存。

 

###31.请写出JavaScript中常用的三种事件？√

        onclick（鼠标单击事件），onblur（鼠标失去焦点触发的事件），onChange（内容改变时触发的事件）

 

###32.JS中的三种弹出式消息提醒的命令是什么？√

        alert，
        
        confirm（自定义弹出框的内容   并且ok 和cancle单击后会各自返回true和false，依据此机制可以在页面输出不同的内容）
        
        Prompt（（prompt（“1”，“2”）单击事件后弹出一个输入框，1是输入框的标题，2是输入框的文本输入区，此方法会返回一个dom对象）

 

###33. 请说出5种常见的runtime exception？√

        NullPointerException：当操作一个空引用时会出现此错误。
        
        NumnerFormatException：数据格式转换出现问题时出现此异常。
        
        ClassCastException：强制类型转换类型不匹配时出现此异常。
        
        ArrayIndexOutOfBoundsException：数组下标越界，当使用一个不存在的数组下标时出现此异常。
        
        ClassNotFoundException：定义类找不到

 

###34. 数组有没有length()这个方法？String有没有length()这个方法？√

        数组没有length()这个方法,但有这个属性；String有length()方法。

 

###35. JSP页面之间传递参数的方式有哪些？√

        request、session、application、提交表单（submit）、超链接（<a></a>）

 

###36. Oracle 对象有哪些？并分别说明下用途？√

        视图，序列，存储函数，同义词，索引，表。
    
        约束条件：保证数据完整性
        
        试图：虚表，命名的查询语句
        
        索引：加速查询的速度
        
        序列：一串连续递增或递减的数字，步长相同，(代理键)。
        
        同义词：一个对象的另外一个叫法(对象的别名)。
        
        存储过程：用于操作。
        
        函数：用作复杂运算的。用于计算。
        
        触发器：由事件触发的存储过程。

 

###37.一般内连接的基本语法是什么？√

        select * from a,b where a.id = b.id;

 

###38. 说说数据库触发器的好处？√

        比如上网发日志，事先会自动通知好友；其实就是在增加发日志时做了一个后触发，先告知好友，再向通知表中写入信息；效率高。

 

###39. 说一些关于数据库优化方面的经验？√

        有外键约束会影响（DML）插入和删除性能，如果程序能够保证数据的完整性，

        那么就在创建数据库时去掉外键约束。

        扩展：实际开发有一个种叫分区优化技术。

 

###40. 处理数据库大数据量下的分页解决方法？√

        最好的办法是利用sql语句进行分页，这样每次查询出的结果集中就只包含某页数据内容，再sql语句无法实现分页的情况下，

        可以考虑对大的结果集通过游标定位方式来获取某页的数据。

        总结：简单就是用sql分页语句进行分页；再大的数据量可以考虑对大的结果集

        通过游标定位方式来获取某页的数据。

        扩展：(说说你对数据库大数据量怎么处理)？

    可以用分区功能：
        
        范围分区：范围分区就是对数据表中的某个值的范围进行分区，根据某个值的范围，决定将该数据存储在哪个分区上。如根据序号分区，根据时间等来进行分区。  
        
        Hash分区(散列分区)：散列分区为通过指定分区编号来均匀分布数据的一种分区类型，因为通过在I/O设备上进行散列分区，使得这些分区大小一致。
        
        也就是只命名分区名称，这样均匀进行数据分布。
        
        复合分区：有时候我们需要根据范围分区后，每个分区内的数据再散列地分布在几个表空间中，这样我们就要使用复合分区。复合分区是先使用范围分区， 然后在每个分区内再使用散列分区的一种分区方法。

 

###41. 运行异常与一般异常有何异同？√

        异常表示程序运行过程中可能出现的非正常状态，运行时异常表示虚拟机

        的通常操作中可能遇到异常，是一种常见运行错误，java编译器要求方法
    
        必须声明抛出可能发生的非运行时异常，但是并不要去必须声明抛出未被
    
        捕获的运行时异常。

 

###42. JDBC中的perparedStatement比Statement的好处？ √
        一个sql命令发给服务器区执行的步骤是：语法检查，语言分析，

        编译成内部指令，缓存指令，执行指令等过程；所以perparedStatement比Statement可以防止sql注入。

 

###43. Servlet的生命周期？√

        1：实例化：容器收到请求时，会创建一个serlvet实例。

    　　2：初始化：容器在创建好servlet对象之后，会接着调用servlet对象的init()方法。注意：该方法只会执行一次。作用是，获取资源。
    
    　　3：就绪：调用servlet对象的service()方法
    
    　　4：销毁：容器会依据自身的算法，删除servlet对象。在删除之前，会先调用destroy()方法。

 

###44. 说说XML的理解？说明web应用中的web.xml文件的作用？√

        XML即可扩展标记语言，它与HTML一样，都是SGML标准通用标记语言；

        XML是Internet环境中跨平台的，依赖于内容的技术，是当前处理结构化文档信息的有力工具。扩展标记语言XML是一种简单的数据存储语言，使用

        一系列简单的标记描述数据，而这些标记可以用方便的方式建立，虽然XML占用的空间比二进制数据要占用更多的空间，但XML极其简单易于掌握和使用。

        Web.xml的作用是配置欢迎页，servlet，filter，listener等的。

 

###45.Http协议的一些技术特点是什么？√

        无连接：无连接的含义是限制每次连接只处理一个请求。

        服务器处理完客户的请求，并收到客户的应答后，即断开连接。采用这种方式 可以节省传输时间。

        无状态：HTTP协议是无状态协议。无状态是指协议对于事务处理没有记忆能力。缺少状态意味着如果后续处理需要前面的信息，则它必须重传，

        这样可能导致每次连接传送的数据量增大。另一方面，在服务器不需要先前信息时它的应答就较快。

 

###46. 什么是web容器？√

        容器就是一种服务程序，在服务器一个端口就有一个提供相应服务的程序，而这个程序就是处理从客户端发出的请求，

        如JAVA 仲的Tomcat容器，ASP的IIS 或 PWS 都是這样的容器。

 

###47. Tomcat服务器的默认端口是多少？怎样修改tomcat的端口？√

        默认端口为8080，可以通过service.xml的connector元素的port属性来修改端口。

 

###48. 基于<bean>（xml配置）的Spring MVC控制流程：√

        客户端发送请求经过DispatcherServlet控制器处理之后，通过HandlerMapping组件找到相应的Controller控制器，Controller会调用业务层Model处理请求并且返回ModelAndView，然后DispatcherServlet会通过ViewResolver返回相应的jsp视图，在客户端进行页面呈现；

 

###49. 接收请求参数值的3种方式：√

        使用HttpServletRequest获取（getParameter()方法）
        *优点：直接获取数据，获取到的数据比较完整（表单，ip，url，cookies等）；
        
        缺点：需要自己处理数据类型转换；
        
        -Spring会自动将表单name属性参数注入到方法参数中（参数名一致）
        使用@RequestParam注解映射参数名不一致的属性
        
        *优点：数据类型自动转换；
        
        缺点：有可能出现数据类型转换异常；
        
         -使用自动机制封装成Bean属性
        定义FromBean实体类，属性名与表单组件的name名一致
        
        *优点：表单属性量大，解耦，简化代码量；

 

###50.说说Tomcat有几种部署方式？√

        （1）利用Tomcat自动部署
    
        （2）利用控制台进行部署
        
        （3）增加自定义的Web部署文件(%Tomcat_Home%\conf\Catalina\localhost\AppName.xml)
            
        （4）手动修改%Tomcat_Home%\conf\server.xml文件来部署web应用

 

###51.Tomcat的优化经验？√

        去掉对web.xml的监视，把jsp提前编辑成Servlet。
        
        有富余物理内存的情况，加大tomcat使用的jvm的内存。

 

###52.说说您对Ajax的理解，还有为什么要用Ajax？有什么好处？√

        Ajax就是异步的JavaScript跟xml同时访问数据库。

 

###53.Hibernate是什么及优缺点？√

        hibernate是基于ORM对象关系映射（完成对象数据到关系数据映射的机制）实现的，做数据持久化的工具。

        Hibernate的缺点:性能比较差，尤其是批处理方面，如果在大数据量开发的时候，最好使用JDBC。

 

###54.Hibernate的核心接口有哪些？√

        Session、SessionFactory、Transaction、Query、Criteria、Configuration

 

###55.Hibernate 中，不看数据库，不看XML文件，不看查询语句，怎么样能知道表结构？√

        可以看与XML文件对应的域模型。

 

###56.Struts是什么？√

        struts1是基于JSP和servlet的一个开源的Web应用框架，使用的是MVC的设计模式 struts2是基于webwork技术的框架，

        是sun和webwork公司联手开发的一个功能非常齐全的框架，struts2和struts1没有关系，是一个全新的框架。

 

###57. 说说 你对Struts的理解？√

        struts是一个按MVC模式设计的Web层框架，其实它就是一个大大的servlet，
        
        这个Servlet名为ActionServlet，或是ActionServlet的子类。我们可以在web.xml文件中 将符合某种特征的所有请求交给这个Servlet处理，
        
        这个Servlet再参照一个配置文件（通常为/WEB-INF/struts-config.xml）将各个请求分别分配给不同的action去处理。
        
        总结：struts其实是以MVC设计模式的web层框架，也就是一个大大的servlet，
        
        而这个servlet我们称之为ActionServlet，我们可以在web.xml配置文件中 将符合某种特征的请求交给对应的Servlet类处理，再通过struts.xml配置文件对应的action处理。

 

###58.Spring是什么？√

        spring是一个集成了许多第三方框架的大杂烩，其核心技术是IOC（控制反转，也称依赖注入）和AOP（面向切面编程）。

 

###59.什么是AOP？什么IOC 及好处什么？√

        AOP简称为：面向方面编程或面向切面编程。
        
        AOP关注点是共同处理，可以通过配置将其作用到某一个或多个目标对象上。
        
        好处：是实现组件复利用，改善程序的结构，提高灵活性。将共通组件与目标对象解耦。

 

###60.什么是IOC？√

        IOC主要是解决两个组件对象调用的问题，可以以低耦合方式建立使用的关系。

 

###61.依赖注入指的是什么？√

        依赖注入指的是在运行期间，由外部容器(BeanFactory)动态体将依赖对象(DAO)注入到组件(Action)中。

 

###62.Bean注入方式与注入数据类型？√

        注入方式分为
        
         Setter注入法    默认 <bean>  <property>
        
         构造方法注入法       <bean>  <constructor-arg>
        
            注入数据类型分为
        
         引用型注入   ref
        
         基本数据类型注入  value
        
         集合类型注入   <list><set><map><props>

 

###63.在项目中用过Spring的哪些方面？及用过哪些Ajax框架？√

        在项目使用过SpringIOC,AOP,DAO,ORM，还有上下文环境。
        
        在项目使用过Ext（应用于界面层开发），JQuery等Ajax框架。

 

###64. 从控制器向页面传值的4种方式（将业务处理结果在界面显示）：√

        -使用HttpServletRequest，session，application的setAttribute()方法
        
        -使用ModelAndView对象
        Controller处理完业务之后通过散列表HashMap接收处理结果 ，之后将结果数据绑定到
        
        ModelAndView对象中，通过绑定名向jsp页面传递数据；
        
        Map<String,Object> map=
        
        new HashMap<String,Object>();
        
        map.put("绑定名",业务处理结果);
        
        -使用ModelMap参数对象
        在Controller处理业务的方法中追加一个ModelMap类型的参数，ModelMap会利用
        
        HttpServletRequest的Attribute将数据传递到jsp页面；
        
        model.addAttribute("绑定名",业务处理结果);
        
        -使用@ModelAttribute注解
        在Controller处理业务方法的参数部分或者Bean属性方法上使用@ModelAttribute注解
        
        @ModelAttribute会利用HttpServletRequest的Attribute将数据传递到jsp页面；

 

###65. 转发与重定向的区别：√

        -转发  ：一次请求，地址不变，不能访问外部资源，效率较高
        
        -重定向：二次请求，地址会变，能访问外部资源，效率较低
     

`余路那么长，还是得带着虔诚上路...`
