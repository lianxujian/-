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
