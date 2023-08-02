<template>
    <div class="content">
        <button @click="buttonClick">点击触发事件</button>
    </div>
</template>

<script>
// let有块作用域 {} 。 作用域还有 全局 函数 eval(es5严格模式)
// let不存在变量提升，而var会提升 并且赋值undefined。
// 不影响作用域链的变量查找规则。
// const 必须给初始值。一般用大写变量名。 不能修改。 有块级作用域。 对对象和数组做修改不会报错
// 解构赋值，从对象和数组中提取数据队变量进行赋值。let [a,b,c,d] = ['1','2','3','4',] console.log(a) 对象同理。let {a,b,c,d} = obj
// 对象的会常用 如果找不到就会按顺序取。
// 模板字符串
// 对象的简化写法  name:name  等于name
// 箭头函数 let fn = function(a) {}    相当于let fn  = (a) => {}  重要，this是静态的，始终指向函数声明时所在作用域下的this的值。 call apply bind  都没用，改不了。
// 箭头函数不能作为构造函数实例化对象 没有构造器。 也没有arguments 变量。
// 还可以简写 形参只有一个 a => { return a++}     语句只有一个时可以省略{}，此时return也必须省略，此时函数的执行结果就是返回值。 let fn= n => n++;
// 定时器的this是指向window的，因为是在window下定义的。但是可以用保存变量的方法改变this，也可以把定时器的回调函数写成箭头函数，箭头函数的this指向定义定时器函数作用域下的this。
// 箭头函数适合与this无关的回调，比如 定时器，数组方法的回调。 
// 箭头函数不适合与this有关的回调， 比如事件源的直接回调，对象的方法。  
// es6允许给函数赋值初始值， (a,b,c=10) => {a+b+c}   一般赋值初始值的形参放在最后。  赋值初始值还可以与结构赋值结合用 function fn({a=10,b,c}) {a+b+c}   fn(obj)  如果obj里没有a，则给初始值
// rest(数组) 代替arguments(对象)    这个形参必须写...   function fn (...arg) {console.log(arg)}        rest参数在形参里必须放到最后
// 扩展运算符  ...  可以把数组转换成逗号分隔的参数序列, 一般传值用  fn(...arr)     ...arr一般做实参传， ...arg 一般做形参接收全部的实参。 
// 数组合并  arrc = arra.concat(arrb) arrc = [...arra, ...arrb]
// 数组的克隆 arra = [a,b,c]  arrb = [...arra]  如果里面是引用类型的数据那么是浅拷贝，否则就是深拷贝。
// 可以把伪数组(对象)转成数组， arra = [...伪数组]
// symbol 独一无二的值， 第七种数据类型 用来解决命名冲突，限制很多， 不能参与运算，symbol定义的对象不能for in循环遍历 但可以用Reflect.ownKeys来货物对象的所有键名。
// let s = Symbol()   let s = Symbol('尚硅谷')   同名不同人    let s = Symbol.for('尚硅谷') 看成对象函数   同名同人
// undefined string symbol object null number boolean
// symbol 使用场景 给对象添加属性和方法    不确定对象里面会不会被覆盖   具体用法在es6的第16小节
// symbol的属性    是来扩展对象的属性功能的
// 迭代器 是一种接口
// 只要部署了迭代器就可以用for of来遍历它。for(let e of arr) {e 是值}  for(let e in arr) {e是键名}  原生自带迭代器的有array arguments Set String TypedArray Nodelist。
// 这里的接口可以看成是一种属性。
// 迭代器的原理是有个指针指向起始，同时有个next方法指向第一个位置元素。
// 给对象加上一个属性 Symbol.iterator  可以用for of 遍历对象了。 具体写法看es6第19小节
// 迭代器可以自定义遍历数据。
// 生成器是一种异步的解决方案。是一种特殊的函数。主要靠next 解决异步的，不调next就不走。 function * fn () {}  let f = fn() f是迭代器对象   f.next()  这样调才能执行里面的代码。{}里面可以写yield 函数代码的分隔符  f既然是个迭代器 就可以遍历他  输出的是yield后面的语句值。
// promise是第二种新的异步解决方案。是一个构造函数。
// 实例化一个promise  const p = new Promise(function(resolve,reject) {setTimeOut(function() { a++; resolve(a)}, 1000)})。  p.then(function(value) {},function(reseon) {})   如果p的状态是成功则then方法掉第一个，而状态是在实例化p时resoleve或者reject时改变的。关键逻辑写在实例化p时里面。
// sqw 地址 get https://api.apiopen.top/get
// promise 封装常用异步函数具体写法 见es6 第26小节。
// then方法可以取到实例化对象的值，而值是resolve返回的。而resolve是在实例化p时自己判断写的。
// catch 类似于语法糖，不需要then写两个参数了。
// 新的数据结构集合Set  值是唯一的，类似于数组，也实现了迭代器，所有可以使用...和for of遍历。    let s = new Set(['a','b'])  s.size  s.add('c') s.delete('a')  s.has('c')  s.clear()
// 去重 let arr = [...new Set(arra)] 交集filter has 并集set ... 差集 交集取反 let arr = [...new Set(arra)]
// 新的数据结构Map 类似于对象，键名不限于字符串，也实现了迭代器，所有可以使用...和for of遍历。let m = new Map()  m.set('name', '尚硅谷')    m.size m.delete('name')  m.get(name)  m.clear() 
// class  类  就是个语法糖 es5全可以实现。
// 以前是 function Phone(a,b) {this.sss= a, this.ddd= b}
class Phone {
    static a = '3'; // 类专属 实例化对象访问不到。
    static run () {
        console.log('pao')
    }  // 类专属 实例化对象访问不到。
    constructor(a,b) {
        this.sss= a
        this.ddd= b
    }   
    say() {
        console.log('ssss')
    }
    get eat() {
        console.log('干饭')     // 加了get以后 只要实例化对象用.的方式就会读取执行这个方法属性的代码，返回值就是对象.属性的值。  get 一般封装动态的值
    }
    set eat(biff) {
        console.log('吃牛肉')     // 加了set以后 只要实例化对象.属性被赋值就会读取执行这个方法属性的代码，       set一般封装一些控制
    }
}
class Smartphone extends Phone {
    // Phone.call(this, a,b) // es5 借用方法和改子类原型指向 构造指向  实现组合继承
    constructor(a,b) {
         super(a,b)    // es6  组合继承  也继承了父原型，也实现了call的借用。super 只能写在构造里。
    }
    say() {
        console.log('ssssdddd')  // 重写
    }

}
// 数值扩展 Number.EPSILON 最小精度，如果两个数的差值比他小，则这两个数是相等的。 Math.abs(a-b) < Number.EPSILON  则a b 相等。 
// 二进制 0b2 八进制 0o3 十六进制 0x3 
// Number.isFinite 检测一个数是否是有限数
// Number.isNaN 检测一个数是否为NaN
// Number.isInteger 判断一个数是否为整数  
// Number.parseInt Number.parseFloat  将字符转整数
// Math.trunc 将数字的小数部分抹去
// Math.sign 判断一个数是正数 负数 0
// 对象方法扩展 
// Object.is()  判断两个值是否完全相等
// Object.assign()  对象的合并 重名后面覆盖前面的
// Object.setPrototypeOf 设置原型对象   不建议这么做  在create时就做最好
// 模块化 防止命名冲突 代码复用 高维护性
// es6 模块化语法 export {a, say}   export default {             这里面是：的写法              }
// 通用import * as m1 from './src/m1.js'   解构赋值 import { userIonfo } from ''  import { userIonfo as  userIonfo1} from ''    import { default as  userIonfo1} from ''  import m3 from '' 针对默认暴露不用写花括号。
 // 引入NPM包
// babel 是es6 转es5
// 
// async await
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
// 
export default {
    name: "css01",
    components: {
        // HelloWorld
    },
    data() {
        return {};
    },
    mounted() {},
    computed: {},
    watch: {},
    methods: {
        buttonClick() {
            alert('不要点我啦')
            console.log('你好JS')
        }
    },
};
</script>

<style lang="less" scoped>

</style>
