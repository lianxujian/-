1、Vue set方法
    Object Array
    data(){
        return {
            obj: {
                a:1
            },
            arr: [1]
        }
    },mounted(){
        this.obj.a = 2;//可以更新视图
        this.arr[0] = 2;//不可以更新视图
        //解决方法
        1、this.$set
        2、数组可以用splice方法可以改变原数组;
    }
    原理：https://blog.csdn.net/XuM222222/article/details/99942522
    数组用splice改变原数组
    对象手动触发更新
    defineReactive(ob.value, key, val)
    ob.dep.notify()

2、HTTPS和HTTP的主要区别
    1、https协议需要到CA申请证书，一般免费证书较少，因而需要一定费用。
    2、http是超文本传输协议，信息是明文传输，https则是具有安全性的ssl/tls加密传输协议。
    3、http和https使用的是完全不同的连接方式，用的端口也不一样，前者是80，后者是443。
    4、http的连接很简单，是无状态的；HTTPS协议是由SSL/TLS+HTTP协议构建的可进行加密传输、身份认证的网络协议，比http协议安全。

3、Vue3.x的双向数据绑定原理
    Proxy的优势
    相比于vue2.x，使用proxy的优势如下
    1 defineProperty只能监听某个属性，不能对全对象监听
    2 可以省去for in、闭包等内容来提升效率（直接绑定整个对象即可）
    3 可以监听数组，不用再去单独的对数组做特异性操作

4、箭头函数
    箭头函数的this永远指向其上下文的this，任何方法都改变不了其指向，如 call(),bind(),apply() 
    普通函数的this指向调用它的那个对象

哗啦啦
1、模块化amd cmd; import require、Module.export、export的区别
    commonJs (nodeJs)
    1、require('xx')是“运行时加载”，而es6的import ... form ...是编译时加载(按需引入（动态加载）);
    CommonJs的exports.xx=xx,依靠exports变量自身来暴露的,export命令不需要=，只要后面跟一个变量即可,不能是值;
    AMD/CMD比较

    2、Module.export、export的区别:
        exports只是module.exports的全局引用，意思是：在模块被导出之前exports被赋值为module.exports，切记千万不能给exports赋值;exports===module.exports;模块导出相当于 return module.exports;

    3、(requireJs)AMD推崇依赖前置，在定义的时候就要声明其依赖的模块,
       (seaJs)CMD推崇就近依赖，只有在用到这个module的时候才去require;
       AMD异步CMD同步;
       执行顺序：
            amd:依赖前置，AMD加载module完成后就会执行该module，所有module都加载执行完成后会进入require的回调函数，执行主逻辑。  依赖的执行顺序和书写的顺序不一定一致，谁先下载完谁先执行，但是主逻辑 一定在所有的依赖加载完成后才执行(有点类似Promise.all)
            cmd:CMD加载完某个依赖后并不执行，只是下载而已。在所有的module加载完成后进入主逻辑，遇到require语句的时候才会执行对应的module。module的执行顺序和书写的顺序是完全一致的

2、settimeout、promise
    
3、for in，for of区别
    for in遍历的是数组的索引（即键名），而for of遍历的是数组元素值。
    for of遍历的只是数组内的元素，而不包括数组的原型属性method和索引name
4、symbol
    创建symbol let s1 = Symbol(description) description可以是任何可以被转型成字符串的值，如：字符串、数字、对象、数组等;
    Symbol类型的key是不能通过Object.keys()或者for...in来枚举的;JSON.stringify()时，Symbol属性也会被排除在输出内容之外;
    访问的话：
        // 使用Object的API
        Object.getOwnPropertySymbols(obj) // [Symbol(name)]
        // 使用新增的反射API
        Reflect.ownKeys(obj) // [Symbol(name), 'age', 'title']
    使用Symbol可以定义类的私有属性/方法(只允许内部使用);
    注册和获取全局Symbol
        let gs1 = Symbol.for('global_symbol_1')  //注册一个全局Symbol
        let gs2 = Symbol.for('global_symbol_1')  //获取全局Symbol
        gs1 === gs2  // true

5、generator
    ./水滴筹/generator.html
6、闭包：闭包解决了什么问题
    函数外部读取函数内部的变量
7、函数式
    函数式编程是种编程方式，它将电脑运算视为函数的计算
8、递归有什么问题，怎么解决的
    栈的大小是固定的，这也就意味着不能无限的递归
    null、undefined、Number、string、Boolean存在于栈内存（自动分配自动释放）；
    object存在于堆内存，指针存于栈内存（不会自动释放）
9、虚拟dom：diff算法
    virtual DOM是将真实的 DOM 的数据抽取出来，以对象的形式模拟树形结构，diff算法比较的也是virtual DOM
    Diff算法的作用是用来计算出 Virtual DOM 中被改变的部分，然后针对该部分进行原生DOM操作，而不用重新渲染整个页面
10、express中间件
    Express 是一个路由和中间件 Web 框架(基于Node.js平台的web应用开发框架)，能够访问请求对象 (req)、响应对象 (res) 以及应用程序的请求/响应循环中的下一个中间件函数next();
    var app = express();
    应用层中间件
        app.use(function(req, res, next))、app.get()、app.post()
    路由器层中间件
        var router = express.Router();
        router.use()
    错误处理中间件
        app.use(function())四个参数而不是三个
    内置中间件
        app.use(express.static('public'));
    第三方中间件   
        var cookieParser = require('cookie-parser');
        app.use(cookieParser());
11、Service worker、webworker
    Service Worker 脚本最常用的功能是截获请求和缓存资源文件, 这些行为可以绑定在下面这些事件上:
    install 事件中, 抓取资源进行缓存
    activated 事件中, 遍历缓存, 清除过期的资源
    fetch 事件中, 拦截请求, 查询缓存或者网络, 返回请求的资源
    特点：
        无法操作DOM、只能使用HTTPS以及localhost、可以拦截全站请求从而控制你的应用、与主线程独立不会被阻塞（不要再应用加载时注册sw）、完全异步，无法使用XHR和localStorage、一旦被 install，就永远存在，除非被 uninstall或者dev模式手动删除、独立上下文、响应推送、后台同步
12、webpack

13、vue-router的路由模式及区别
    路由跳转 hash 与 history(go、forward、back)
    https://www.cnblogs.com/karthuslorin/p/9450068.html
    history使用pushState的第一个参数进行传值，使用History的state属性进行取值
    pushState(params,新页面title,新页面路由url)
    popstate 事件监听
    replaceState 该方法基本和pushState一致，但是不同的是，该方法会直接替换当前的历史记录
14、v-if、v-show的区别

15、keep-alive

16、react hook

17、react state

18、网站优化措施
