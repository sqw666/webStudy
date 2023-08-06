<template>
    <div class="content">
        <button @click="buttonClick">点击触发事件</button>
    </div>
</template>

<script>
// let a: number;    let c:boolean = false; 相当于let c = false; 
// function(a: number,b: number): number 指定返回值的类型 { return a + b}
// let a: male | female;  let b: string | boolean;  let c: any;  字面量，一般不用。 |是或的意思
// let d; 默认any
// let s: string; s= d; s会变成any；  let d: unknow;   d 可以被赋值任意类型，当 s = d； 此时d不会改变s的类型，会报错。除非做了类型判断，才能赋值。typeof。  或者用断言 s = d as string d就是字符串。断言也可以这样，s = <string>d;</string>    建议用unknow
// 类型一共 string number boolean 字面量 any unkonw void never object array tuple enum
// let obj: {name: string, age?: number}  let obj: {name: string, [propName: string]: any}
// let d: (a: number, b: number) =>number   定义一个函数d 希望它的参数和返回值都是number.   d= function(n1: number, n2: number) {return n1 + n2}
// let e: string[]   字符串数组  let e: Array<number>;  数值型数组。  两种写法。
// tuple 元祖  固定长度的数组。 let h: [string, string]  h= ['hh', '33']
// enum 枚举  Enum Gender{male=0,famale = 1}     let i: {name: string, gender: Gender; i ={name: '孙悟空', gender: Gender.male}； 
// let j: {name: string} & {age: number}; & 且。  用法 let j:  {name : '孙悟空'. age: 18}  都要满足
// 类型的别名 type mytype = string;  let k: mytype;    type type1 = 1|2|3   let m: type1;
// ts的类型 都是用： 去定义类型， 用= 赋值。
// 类的简介 实例
// class Person {
//     name: string = '孙悟空';
//     age: number;
//     readonly gerder: number = '1';  对象的只读属性 不能赋值
//    static yy: string = '假猴子' // 静态属性，用类才能访问；
//     constructor(name: string, age: number) {
//         this.name = name;
//         this.age = age;
//     }
//     sayHello() {

//     } 
// }
//  const per = new Person('小黑'， '2')  // 实参传在constructor里面了，constructor里面的属性必须在constructor外面定义一下。
// 构造函数 和 this
// 构造函数 会在实例化对象时调用，  this就表示当前的实例。
// 继承
// class Student extends Person{}   此时Person为父类， Student为子类。子类将有父类中所有的属性和方法。
// 子类中可以添加父类中没有的属性和方法。如果父类中有的属性和方法，此时子类再写的话，就是方法重写，优先调用子类的。
// super关键字  超级的意思   父类也叫超类，所以super就代表父类。
// 在子类中用super.sayhello()   就是调用父类的sayhelle() 方法。
// 在子类加新属性后，肯定要写constructor初始化这个属性，但是一旦写了constructor，就会覆盖父类的constructor，歇逼，所以在子类的constructor中要调一下父类的constructor，写法是super(name)
// 抽象类 
// 我们不想别人用父类来实例化对象，只用来继承， 类名前面要加上abstract，变成抽象类，只是不能用来创建对象，只能继承。
// 抽象类中才可以添加抽象方法， 抽象方法就是让子类来重写的。在方法前加abstract，可以没有函数语句，但子类必须要重写这个方法。
// 接口 interface
// interface myinterface {name: string}  很像那个类型别名 type mytype = {name: string} ，但是接口可以重复声明 interface myinterface {gender: string}
// 接口可以在定义类的时候来限制类的结构，interface myinterface {gender: string；sayhello(): void)}  接口中不能写实际数据。
// class myclass implements myinterface {}   myclass类中必须要满足这个接口myinterface的结构。
// 接口就是规范出一种固定结构属性和方式的类。一种规范。
// 属性的封装 
// 我不想实例化对象的属性可以被任意修改，年龄没有负的吧。
// TS 可以在属性的前面 加public 可以修改           private 私有属性 只能在类内部进行修改，可以在类中加方法间接让实例化对象来改和访问，getter()  setter() 属性的存取器，                            
// TS中 get name { return this.name } 实例化对象访问name时就会触发这个方法。  实例化对象赋值它的属性时会触发set name (name) {this.name = name }
// get set 方法 用来提高安全性。
// 在父类中属性前面加 protected 此属性则只能在父类和子类中访问。
// 语法糖定义类 class Person {constructor(public name: string) { this.name = name }}
// 泛型
// 在定义函数和类时不明确类型时，用泛型。  function fn<T>(a: T): T {return a}  定义一种类型时T， 参数要是T，返回值也要是T。
// fn(a: 10)  fn<string>(a: 'hello')  手动指定类型T。 建议手动指定一下。
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
