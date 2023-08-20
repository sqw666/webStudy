<template>
    <div class="content">
        <button @click="buttonClick">点击触发事件</button>
    </div>
</template>

<script>
// vue.config 是vue的全局配置对象， vue.config.productionTip = false   禁掉生产一直提示。
// 页签图标 是浏览器打开网站默认请求的，本机放在根目录就行。
// new Vue({el: '#root', data: {name: '尚硅谷'}})  和容器建立联系， 把容器中变化的东西交给这个实例vm保管，再取出来。
// 差值语法可以取到data中保存的数据 {{name}}
// 实例只对一个接管的容器负责。容器里的html代码被称为Vue模板
// 容器只能被一个实例接管。 二者是一对一的关系。
// 差值语法里可以写js表达式， 
// 传统的js是 获取dom  处理数据  给dom赋值，  而vue是改变数据就行，vue帮你赋值了。
// 模板语法 v-bind:  用来绑定标签里属性，加了之后，会把引号里包着的东西当成表达式执行。  v-bind: 可以简写成：
// v-bind 一般用来管理标签的属性，差值语法用来写标签体内容。
// 单向数据绑定 v-bind   data数据变化后会改变页面数据，但是改变页面数据不会改变data数据
// 双向数据绑定 v-model  页面数据变化也会改变data数据
// v-model 只能用在表单类元素(输入类元素)
// v-model:value 可以简写为v-model 因为v-model默认手机的就是value值。例如 v-model:value='name'
// 容器和vue实例的关系
// const vm = new Vue(。。。。) vm身上带$的方法是给程序员用的。vm.$mount('#root')   就不用写el了，这是第二种写法了。
// data的两种写法，第一种是对象，第二种是函数，第二种必须是返回一个对象， data() { return{name: '尚硅谷'}}
// MVVM模型  M 模型 data V 视图 模板 VM 视图模型 Vue实例对象
// data中所有的数据都可以在vm中看见， VM上所有的属性包括原型对象上的属性都可以用在模板上。
// 数据代理 方法在Object身上，叫defineProperty，定义属性。 Object.defineProperty(person,'age',{value: 18}) 写完之后，age是不参与遍历的。例如Object.Keys(person)，在配置项上写enumerable：true，就可以被遍历。age是不能被修改的，加完writable:true, 才可以被修改。 也不让删除，加完configurable：true，可以被删除。
// 除了上面四个基本的配置项，还有很多高级的配置项。
// numer = 18；person =  {age：number} 此时改name，person中的name不会跟着变，因为已经执行完了。 但是Object.defineProperty可以 
// 高级配置项，get() {rreturn number} 当有人读取person的age属性时，get函数就会被调用，且返回值就是age的值。这样每一次访问age 都会触发get函数的调用。
// set(value){number = value} 整体也叫setter  当有人修改person的age属性时，set函数就会被调用，且会收到修改的具体值。
// 什么是数据代理？用Object.defineProperty的get set通过一个对象代理对另一个对象中属性的操作 读和写。
// vue中是如何数据代理的？
// data属性在vm身上时会有三个点... 表示是用Object.defineProperty加上去的，当读取data中name时，getter把别的地方的name拿过来，当改的时候，setter改别的地方name。
// 验证两条线，getter  和 setter。 其实就是把data中数据到处用，VM上本来没有的，我data给你，你想改，就改我data中的。 读的时候好解释，改的时候麻烦点，改会触发setter，改的是data中的数据(VM._data = data)， _data中再把数据代理劫持一下，再改到页面上。
// _data在vm上，data是代码中data，二者一个源头，只是VM把data拿了一份出来。让我们读写数据的时候就是读写的data中改的数据。
// 模板上的变量name读的是vm._data中的数据，_data是VM从data中拿的，_data在vm上，data是代码中data，二者一个源头。name在解析的时候走_data代理，返回的是_data中的数据
// vue中是如何数据代理的？  
// 通过vm对象来代理data对象中属性的操作，更加方便的操作data中的数据，通过Object.defineProperty() 把data对象中所有属性添加到vm上，为每一个添加到vM上的属性，都指定一个getter/setter，在getter/setter内部去操作读写data只能怪对应的数据，后面实现的数据劫持改页面要把_data中的数据再代理一下。
// 总结 给VM身上的name属性做数据代理访问的是data，vm身上的_data和data指向同一个对象，_data中的数据代理做的事数据劫持，改变页面数据的。
// 事件处理 v-on:click='showInfo(66,$event)'; 不传参 默认接收event 简写是@click 
// 事件修饰符  阻止默认行为，接收的event，event.preventDefault(). 也可以在模板@click.prevent
// 一共6个，prevent 阻止默认事件 stop 阻止冒泡 once 事件值触发一次 capture 使用事件的捕获模式 self 只有event.target是当前操作的元素才触发事件 passive 事件的默认行为立即执行，无需等待事件回调执行完。
// @scroll='demo'滚动条行为  @wheel.passive='demo1' 滚轮行为  不用等wheel执行完，滚动条直接滚。
// 键盘事件@keyup='showInfo'  e.target.value  e.keycode e.key  @keyup.enter='showInfo'   vue常用的键盘别名   tab比较特殊，必须配合keydown 
// Vue.config.keyCodes.huiche = 13;  自定义 不太推荐了
// 修饰符可以连着写。@click.prevent.stop  @keyup.ctrl.y
// 计算属性 {{ 里面一万个逻辑}}，太臃肿， {{funllname()}} 差值语法里也可以写函数，取得返回值，但是数据一变会导致vue重新解析语法，因为vue不知道差值语法里的函数返回值还是不是不变。
// vue 数据一发生变化，模板会重新解析。
// 计算属性 就是拿有的属性计算出一个新的属性，computed: {fullname: {get() {return}, set(value) {}}} 底层也用的defineProperty
// 在模板读取到计算属性时，会缓存，读到重复使用时就重用，get什么时候调用？ 1 初次读取fullname时 2.所依赖的数据发生变化时。  set什么时候调用？ 当fullname被修改时，set会收到修改的值，在set中不要改fullname  而是去改依赖的数据。
// 简写 fullname:function() {return}  当get用
// 在模板cllck后面可以写点简单的js代码，不要写太多，而且模板上的方法它只会去实例找，但是在配置项中的方法会通过作用域找到window
// 监视 watch: {isHot: {immediate: true  handlet(new,old) {}}} immediate: true 初始化时让handler调用一次。  old默认是undefined。
// vm.$watch('ishot',{immediate: true.......})  第二种   位置在最后 跟vm同一层
// 'numbers.a': {handle....}
// 深度监视 监视对象所有属性 numbers: {deep:true, handler。。。。。。。}
// 监视的简写 watch: {ishot(new,old){}}   vm.$watch('ishot',function(new,old) {})
// 计算属性和监视的区别 计算属性不用重复写，监视要监视所有依赖的数据。但是监视可以写定时器等函数啊，计算属性需要返回值，监视自己写需求。
// 定时器写成普通函数时，有自己的this，因为定时器是交给js引擎调的，也就是window，所以，this会指向window，但是如果定时器写成箭头函数，箭头函数没有自己的this会出去找上下文的this，找到vm。
// 计算属性能完成的监视也可以，监视还可以写异步。
// 定时器的回调和ajax的回调和promise的回调最好写成箭头函数。
// 所有被vue管理的函数写成最好普通函数，不被vue管理的函数最好写成箭头函数，这样this就会都指向vm实例。箭头函数跳两层函数？？？
// 绑定class样式 字符串写法 :class='a'  data中有a   style中有a的值的样式  适用于类名不确定，会动态改变。
// 数组写法 :class='arr' arr中存的是类名，类名的具体样式要写在style里     适用于样式个数不确定， 名字也不确定。
// 对象写法 :class='obj' obj:{box:false}   适用于个数确定，样式也确定， 要动态决定用不用。
// 绑定style样式 :style='{fontSize: fsize+'px';}'
// 对象写法  :style='obj'   obj:{fontSize: '40px'}
// 数组写法 :style='arr'   arrL里面是obj
// 条件渲染 v-if v-show 
// v-show 是display none
// v-if  结构都干没了 display none 都没了
// v-else-if v-else  v-if 与 v-else-if 之间不允许被打断
// <template v-if=''> </template> 用template不会破坏结构，不用外面包div。但是要注意template不能和v-show配合使用。
// 列表渲染 <div v-for= '(obj,i) in arr':key='i'> arr数组里面放对象  of 和in 都可以
// v-for 遍历对象也行 (item,value) item是属性名 value是值
// v-for 遍历字符串也行(item,index)
// v-for 指定次数 v-for='(number,index) of 5'
// key的原理  给节点做标识
// diff对比渲染会依赖之前的节点key值，如果在循环数组前面插入数据，索引就变了 同key，diff节点把之前的节点复用了，可能只是改了一点点小内容的替换。新旧同key节点后面结构一样的也复用了.
// 最好选择数据项里面数据的唯一标识.如果仅仅用来展示,也不会逆序添加.逆序删除,使用index也是没问题的.
// 计算属性时会一上来就会调一次，watch要加属性为true才会上来就调一次。
//  数组sort方法 可以排序，且会改变原数组，不用接收，它的return不是返回数组，而是排序数组。最后啊哟用这个数字返回或者做其他操作的。
//  vue怎么知道data数据变了要去重新渲染模板？ vue默认的监视就会监视data数据，一旦变了就会重新渲染模板数据。
// 有一种情况 数据改了 页面不改。如果页面上遍历的是对象数组数据，你在data里整个改这个对象数组的某条对象，vue不认为模板上的对象数据发生了变换。
// 监测数据变化的原理 先说对象再说数组。
// vue上属性是从_data中拿的且做代理访问的是data，而_data是从data中拿的，拿的时候还加工了data，_data和data指向的是同一个对象。
// 数据代理 不要读自己和改自己，会死循环。 下面是加工的步骤。
// const obs = new Observer(data)   观察者会收集data的所有属性key值，循环这个key值，给this做代理，这里的this不是data 而是给构造函数观察者的实例对象上添加k属性，get里写的是data里的值，是给实例对象里的key值做代理，get返回的data的key属性也不会触发代理自己的。相当于读实例对象返回data的，再把实例对象赋值给data和_data，这样obs的代理也给了data和_data
// 就是用新对象代理返回旧对象的值，再把新对象赋值给旧对象。data虽然被obs改变了也做了代理，为什么不死循环，是因为它临死前把具体对象给了形参obj，内存中还保存着一份data呢。get返回的也是obj
// 把data给另外一个形参接收一下，新实例添加的属性代理返回的都是形参的，data后面被赋值也没事。应该是有闭包赋值的。用obj返回值的obj在内存没有消失，
// 实例obs 构造函数Observer 想被代理的对象data 构造函数形参obj 给实例做代理get返回的是obj值，产生闭包obj。闭包还避免了循环结束后一直返回最后的值。不然没有闭包，则obj消失，返回谁？后面实例通过赋值把data改了，但是obj没变还是指向data曾经指向的对象。
// 渲染模板是改闭包obj触发的set中渲染模板。其实set中改的也是obj的.........,后面再读obj正好..........
// 实例化构造函数时，数据做代理响应式，对象里后加的属性没走构造函数，所以不是代理响应式的，没有set。
// vue.set(目标对象，键值，值) 再次开启新加属性的代理和响应式(set触发时做的)
// vm.$set(目标对象，键值，值) 同上
// vue的双向绑定原理就是数据劫持和set响应式。至于页面改了怎么影响data的？
// set方法的第一个参数不能直接是data和vm。 可以是data中的某个属性。
// vue对数组的监视，对数组里面字符串数据不做监视，直接取到的索引给它改，直接改索引上的值vue是不认的，改索引上的对象属性vue是认识的，还有调用数组的api方法(被VUE包装了，先做原始api操作，会再渲染模板)，vue是认识的，filter不行哦，因为filter不改变原数组。
// vm.$set(目标数组，索引，值) 也可以触发响应式。
// 给对象或者数组加新属性，vue是不知道的，但是给已有属性赋值，vue是知道的，数组的索引也没有get 所以直接改数组索引的值，没用，要有vue封装过的数组方法。
// Vue.set(this.student,'sex','男')  this.$set(this.student,'sex','男')
// 做响应式是因为set里可以检测到改变并更新页面
// 收集表单数据 v-model 收集的是value的值。！！！v-model.number= 'ss'  v-model.lazy= 'ss'失去焦点生效  v-model.trim
// 过滤器 {{ time | timeFormater}} fillters: {timeFormater(value, str) { return '111'}}     全局 过滤器 Vue.filter('myfilter', function(value) {return '33'})
// 过滤器只支持差值写法和v-bind写法。
// 第三方库 bootCDN 搜索day
// v-text 不如差值  v-html 可以解析标签 但是可以干坏事 document.cookie   如果不是http的话 用 document.cookie会获得空就可以避免泄露。服务器返回的勾不勾上。
// cookie 登录成功 跳转成功且返回cookie给浏览器  第二次访问时就会携带这个cookie，服务收到后有可能再给cookie，不给的话就是一开始都给了。
// v-cloak  在vue工作之前加这个  要配合 style display none
// v-once 初次动态渲染后就转为静态内容了，可以用于优化性能。
// v-pre 让vue跳过解析这个节点。原样输出。一般用在不要动态渲染的节点上。
// 自定义指令 给dom绑定事件，改属性改内容等..........
// <h1 v-big='n'>n 让数值放大十倍.
// directives: {big(element,binging) {element.innerHtml = binging.value * 10}}  big调用时机，1.指令与元素成功绑定时（c此时并未放入页面呢）。2.指令所在的模板被重新编译时。
// v-fbind:value='n' 上来默认获取焦点  fbind(element,binging) {element.value = binging.value; element.focus()}指令与元素成功绑定时（c此时并未放入页面呢）函数式不满足了 要写成对象式。
// fbind: {bind(){指令与元素成功绑定时},inserted(所在元素被插入页面时),update(){指令所在的模板被重新编译时}}  对象比函数式多了一个插入页面后的回调时机。 指令回调里的this都是window.
// 多字母分隔符写法 'big-number': function(......) 模板上 v-big-number
// 全局指令 Vue.directive('big', {bind(){},inset。。。。。。})
// 定时器写成普通函数，普通函数有自己的this，定时器是浏览器调的，里面的this就指向window，如果写成箭头函数，箭头函数没有this，window找不到this不会给this赋值，最后箭头函数的自己写的this它会出去找vm。
// 生命周期 
// beforeCreate 只是开始初始化vue，无法访问data，methods。beforeCreate走完之后开始完成数据监测没数据代理
// create  可以访问到data，methods。create走完 之后生成虚拟dom
// beforeMount 解析模板完了 还没放到页面。 此时对dom的操作造成的模板都会被之后的放页面流程替换掉。
// motuned vue把编译过的初始的dom元素放在页面。可以改dom了，但是尽量避免这样操作。
// beforeUpdate 页面是旧的，数据是新的。数据和页面不同步。
// updated 页面和数据都是新的了，保持同步了。
// beforeDestroy 可以被this.$destroy()手动调起来，也可以卸载关闭一个组件时自动触发。它表示在销毁前，东西都还在，一般在此阶段做一些丢弃操作。但是这个阶段数据的修改不会再重新编译模板了。
// destroy 已经结束了，没什么用。
// 一般用motuned beforeDestroy就够了
// 8 + 3？
// 组件相关细节 ？？？
// app组件在vm下面  管着很多组件，一人之下 万人之上 
// 定义一个组件const school = Vue.extend({template:'',data() {return}})  组件的本质就是个函数，是构造函数vueComponent，是Vue.extend返回的构造函数，组件不同每次返回的是不同的vueComponent。在模板上写组件名时，其实是vue帮我们创建的school(Vue.extend返回的构造函数)的实例对象。   
// vueComponent构造函数 。 之所以能用this访问到data是因为data放在了vueComponent的实例对象上。而this就是vueComponent的实例对象。称之为VC对象。
// vm管理着一堆vc。
// vm是new Vue产生的。  vc是new vueComponent产生的只不过外面包着一层Vue.extend。   区别是 vm中的data可以写成对象，vm可以写el容器。
// vueComponent.prototype.__proto__ === vue.prototype         把vueComponent.prototype.__proto__ 指向改了，本来指向object的原型对象，被改成了指向vue的原型对象。当然了顺着vue的原型对象也可以找到object的原型对象。多了一层中转，有用。让vc也可以访问vue原型对象的属性和方法。
// computed
//  vm是new vue产生的 组件是 new vueComponent 产生的，一个项目只有一个vm，所有组件都交给app组件来管理，vm只需要管理app组件就行。 
// 第61节  改npm地址镜像  安装脚手架卡了就按enter 看着点
// 分析脚手架配置
// bable.config.js es6 转es5
// packge.json 一些依赖 webpack？
// packge-lock.json 包配置，锁住某个版本的
// npm run serve 运行之后就是执行的main.js
// ctrl点击vue 跳转到nodemoudules 会默认读取它的packge.json的module
// reder函数是创建元素的  是vue帮我们调的。后面要来再深入。 这里的render代替的是teplata的地位。
// 修改脚手架的配置文件 默认被隐藏了 看是output.js  改vue.config.js 可以改main.js位置 关闭eslint 等  要重启
// ref 就是document.byelementId的替代品 this.$ref.     ref是dom和组件的实例
// props 父传子 写属性上 子接收一下。  加冒号是把引号里面的作为表达式
// props: {name: {type: String,required: true, default:''}}  default 不传下来就会给默认值啦  优先级比data高 实在想改就把data中定义一个赋值给它。
// mixin 混合 就是复用配置，相当于把混合里面的内容复制到组件中，多个组件都会重复调用的。如果数据重了，data以组件的为主，混合里面的钩子函数不以任何人为主，来着不拒，会先调混合的再调你自己的。  全局混合 写到main.js里面
// 插件 要vue.use(plugin) plugin里面写install方法，形参就是vue，install是vue帮你调的。这样的插件里面 vue可以写全局过滤器 全局指令 混入 定义vue原型方法。总之vue.use(插件)  插件啊就是增强vue使用的。
// scoped样式 引入很多组件后面的组件样式会覆盖前面组件的样式。加上scoped就会限制住。原理就是给你标签上加个随机属性，后面会作为标签属性选择器选择到它。但是app组件不能用，因为你都在app用样式了，肯定是全局都要用了。
// less在vue里面用要安装less loader  版本要注意和webpack安装版本兼容性。
// 组件化思想，如果拆的过程中 拆的东西还可以写很多逻辑 则建议也写成组件。vue鼓励是MySchool 这样的组件名 标签也可以这样用。
// 样式写的时候可以写点注释表示一块区域都是哪部分的。
// 组件案例 
// 唯一id 随机数 时间戳 uuid==> nanoid 
// 用props实现子传父 在父组件提前定义一个方法 把这个方法用props传过去，子接收后，公用这个函数，子在方法逻辑里掉一下就行，父组件就会触发这个函数。
// 数组方法 reduce  es6 专门做条件统计的
// 数据放在父组件上 最好。
// 浏览器的本地存储 local storage 保存搜索历史的， locationStorage.setItem get delete clear 。json.strafy可以转对象成字符串
// 它还有个弟弟 sessionStorage.setItem............   浏览器一关就没了。
// 自定义事件是子传父   给组件使用的， 就是给组件实例对象VC上加个函数。在子组件里面this.$emit('atguigu', this.name)  在父组件的子组件标签上加上atguigu相当于在父组件中用this.$refs.studenmgt.$on('atguigu',this.getname). 解绑事件 this.$off([])     $on 是绑定一个事件， emit是触发
// 自定义事件就是在子组件里发射emit携带方法和数据，在父组件的子组件实例对象上@自定义事件，或者在钩子函数上加this.$refs.studenmgt.$on('atguigu',this.getname)也是一样的加上去了。或者把逻辑函数直接写在ref里，但是要注意this指向的是子组件，写箭头函数就行。
// 给组件加点击事件要加.native
// 全局事件总线  把一个vc给到Vue.prototype上面的一个变量保存，因为vc是可以访问到Vue.prototype上的$on $off $emit 所以那个保存vc的变量就可以直接在任何组件上用了。或者直接vm放上去，但是vm又没new好，在newvm的过程中写beforecreate钩子，把this赋值给变量。这个变量叫做$bus 被称之为安装全局事件总线。 this.$bus.on('',method()) this.$bus.$emit('',data) 
// 消息订阅与发布 发布消息，需要数据的人就订阅它。     引入pubsub.js 
//  this.$nextTick 下一轮的意思 里面的回调会在下次模板更新后执行。  因为普 通函数没执行完，Vue不会给你更新模板的，难道给你更新100次？ 在函数中改数据后想获取焦点 是拿不到的，因为它是整个数据更改加获取焦点，然后再更新模板，前面获取的焦点没有用了。
// 当改变数据后，要基于更新后的新dom进行某些操作时，要在this.$nextTick所指定的回调函数中执行。
// vue动画效果 .come {animation: atguigu 1s}; @keyframes atguigu { from{ transform : translateX(-100%)}} 
// vue新加标签 transition appear = true 一出现就有效果  可以加name = 'hello'  配合 .hello/v-enter-active{} 和 v-show 一起做的 
// 过渡来实现动画效果 是vue给你加上的类名，你要自己复写。  sqw 案例 重要
// .hello-enter {transform : transla teX(-100%) 进入起点的样式}  .hello-enter-to {进入终点的样式}  .come {transition: 1s liner}
// 第三方库 实现动画 引入An imate.css  sqw  香啊
// fetch 包了两层promise 兼容性垃圾    推荐axios
// axios 引入封装 axios.get('地址').then(res => {res.data},error => {})
// nodejs 没有xhr的 xhr是浏览器的。
// cors 和 Access   让后端用cors配置给特殊响应头，任何浏览器都能给到，有隐患。 jsonp 用script src属性引入外部资源时不受同源策略限制的特点。只能解决get，有点鸡肋。3  推荐代理服务器的方式。
// 跨域要求协议名 主机名 端口号同  借助脚手架
// 代理服务器 不是代理浏览器，代理服务器与目标服务器之间的通信可没有浏览器，就没有同源策略。
// 用vue-cli 实现代理服务器 vue.config.js  deServer: {proxy: 'http://local:5000 '}  5000数据服务器 ，代理服务器已经跟你本浏览器保持一致地址了。  组件发请求时不能直接向数据服务器要数据了，向代理服务器要，跟本机地址是一样的，
// 第一个问题public文件夹是vue默认的放服务器数据的文件夹地址 ，如果在public里面有的数据，就不往5000服务器拿数据了，直接从public里面拿了。
// 第二个细节问题，就是不能配置多个目标服务器代理。
// 解决以上两个问题的方案，deServer: {proxy: {'atguigu': {target: 'http:目标地址'}}} 只要你的请求前缀是atguigu骂我就给你王目标地址发。可以配多个前缀对象了。组件里写代理服务器地址atguigu是紧挨着端口号的，其余的不变不要动。这样代理服务器就会知道你带了atguigu，我就给你往目标地址发。但是代理服务器会把前缀atguigu也带着发过去了，会报404。pathRewrite: {'^/atguigu': ''}proxy配置项里加这个重写地址就可以解决了。
// ws：true 用于支持websocket      changeOrigin: true      代理服务器说谎 说和目标地址一样，写false就说实话。 用于控制请求头中host的值。
// 解决跨域的原理就是浏览器发给同源代理服务器，代理服务器与目标服务器之间是服务器通信，不受同源限制。
// 如果引入的第三方库里面它有引入的东西，你没有，但是你用import方式引入这个第三方库，那么vue就会严格校验并报错，解决办法就是link方式引入第三方库，vue不校验，在public的index.html里面引。
// 请求加载前的处理  请求后的展示 welcome loading users error  四种时机 
// xhr jquery axios fetch vue-resource  都是发ajax的
// vue-resource 也是对xhr的封装  在main.js里面引入这个插件库，再用 vue.use(vr)  ,vc上面就会有$http
// 插槽 
// 重复使用某个组件的问题，给它传不同类型数据的值，展示的风格可能也有变化。就是重用组件，但是展示不同的东西。？
// 如果用十几次同一个组件，就要写二十几个v-show，太乱
// 在组件上写img标签，把组件名当成一个标签。在组件里面写<slot>默认值 </slot> 这样就把img弄过去了。   样式写哪都可以。
// 具名插槽 可以传两个插槽，要传两个带名字的插槽内容，在组件里面定义插槽名字配合接收。 <slot name='s'>默认值 </slot>. 这个用来传  <img slot = 's'></slot>
// 可能会无缘无辜包一个div合一起传，用templata包。 一旦用templata就有第二种写法了。<templata v-slot:footer> </templata>  因为你想传两个平级div，所以要包在一起。所有才有前半句话。
// 作用域插槽 数据再组件里，结构在父组件上，在组件里slot写:games='games'  在父组件上写templata scope= ‘scope' atguigu.games就是games，传回来了。   就是说 数据你来定，结构给我父组件，且结构我来定。 可能有些语法被废弃了，要去官网看看最新的案例。
// v-model.number=
// vuex 是个插件，Vue.use(Vuex)，new Vue时传store进去。 就有$store了。 vc和vm都能看到了。 
// 把数据给vuex， 
// 要看vuex原理图
// Actions 是动作  组件vc调用dispatch触发Actions。Actions里面一定有你发过来的动作函数。
// Mutation 是加工  Actions里面调用commit提交触发Mutation。Mutation里面一定有那个动作函数，且形参是state，和传过来的值。给state里面的数据赋值
// State    是数据
// Actions好像多余的，但是存在这样一个场景，vc只告诉Actions动作，但没有值，这时候就要在Actions里面发ajax获取值，最后在Actions里面commit告诉Mutation。
// 如果实在不用查数据，不需要Actions获取处理，那vue也允许你直接越过Actions操作Mutation，直接在vc里面调用commit。
// 总结 vc想改state数据，要发commit告诉Mutation，Mutation来改，但是如过告诉它的值不确定，那么vc就不能越过Actions，先告诉Actions，让Actions处理后得到的数据，在Actions里面调用commit告诉Mutation改数据啦。
// Actions不止可以调ajax才用到，它还可以处理一些业务逻辑再交给Mutation。
// vc可以发commit告诉Mutation，Actions也是用commit告诉Mutation的。
// vc用dispatch告诉Actions。
// store文件夹下建立index.js 该文件用于vuex中最核心的store  
// const actions = {}
// const mutations = {}
// const state = {}
// const sore = new Vuex.Store({actions:actions,mutations:mutations,state:state})
// 在main.js里面引入这个index.js
// 脚手架会把所有import先执行。所以要把引入vuex和vue.use(vuex)的位置放在store的index.js里面。
// 形参a,b 
// actions里面的a是小store也被称之为上下文context(因为要用到store身上的commit)，b是接收的数据。
// mutations中的a是state，b是接收的数据。
// vuex调试工具的使用。
// context里面的dispatch可以再给另一个服务员处理。里面的state可能要读取，所以 会给你挂在上面。
// 不是必须得配置项
// getters 用于给state数据重新加工  可以多组件复用   this.$store.getters.bignums
// const getters = {bignum(state) {return state.sum * 10}}
// mapState 帮助我们把state中的数据影射为计算属性  this.$store.state 一遍一遍的写太麻烦， 引入mapState 从vuex。在computed里面写 ...mapState({'he':'sum','xueke':'school'})  第二种写法 ...mapState(['sum','subject']) 这种数组简写要求生成计算属性是sum且VUeX里面state数据必须也叫sum
// mapGtters 帮助我们把getter中的数据影射为计算属性 与上面类似
// mapMutations  ...mapMutations({increment:'JIA',..}) 代替this.$store.commit  参数问题是鼠标事件  要在模板里面把value加上， 借用mapMutations生成的对应的方法，方法中会调用commit去联系mutations
// 简写 ...mapMutations(['JIA','JIAN']) 名字要对应成vuex里面的mutation函数。参数也是要在模板上写好
// mapActions    ...mapActions({oddjia: 'ODDJIA'})   参数也是要在模板上写好
// 数组简写 ...mapActios(['OODJIA'])        参数也是要在模板上写好
// 总结 第114小节 大全
// mapState 帮我们映射state中的数据未计算属性
// mapGetters 帮助我们映射getters中的数据未计算属性
// mapActions 帮助我们生成与actions对话的方法，即 包含$store.dispatch(xxx)的函数
// mapMutations 帮助我们生成与mutations对话的方法，即 包含$store.commit(xxx)的函数
// vuex模块化写法  和开启命名空间
// 订单的方法  人员的方法  商品的方法 都网mutation里放，会很臃肿。
// 把Actions Mutation State Getters 里面东西分类   
// const  shangpintOptions = {namespaced: true,mactions : {},state: {},mutation。。。。。}
// const  renyuantOptions = {actions : {},state: {},mutation。。。。。}
// 暴露的时候写法  modules: {shangpintOptions, renyuantOptions}
// vc里面...mapState({shangpintOptions}) 写法要改成这样，取数据的时候要套一层shangpintOptions。  第二种 ...mapState({shangpintOptions,['JIA',;JIAN]})                 
// mapGetters mapActions mapMutations 同上
// this.$store.state.shangpintOptions.personname   this.$store.commit('shangpintOptions/JIA',personname)
// this.$store.shangpintOptions.getters['shangpintOptions/firstname'].personname   this.$store.diapatch('shangpintOptions/JIA',personname)
// 总结 vuex模块化写法  和开启命名空间   可以解决变量命名冲突 和好维护
// 路由
// 路由就是一组key value的对应关系
// 路由器是管理着很多路由的东西.
// 单页应用是怎么实现跳转的   页面更新的时候，是不刷新页签的，只更新地址(假地址，自己配的)和显示区。
// 点击显示区按钮跳转页面的过程：  地址发生变化，被路由器发现了，路由器就会按程序员配置的规则的地址匹配组件。 地址就是key  value就是组件。
// 引入 vue-router  vue.use(vr )
// nodejs 开启服务器写法 案例 sqw 第117节  第
// router写在 new Vue里面 
// router文件夹  index.js 里面写 引入需要路由管理的组件，配置 path 和component 
// router-link 标签 包着元素，元素属性to写配置的path
// 路由组件显示的区域用router-view 作为出口
// 切走的路由组件其实是被销毁了。 
// 切换进入某个路由组件时会走组件的生命周期钩子。
// 路由组件身上会有 $route(不一样)  $router(一样)
// 路由组件放pages  一般组件放component
// 嵌套路由  体现在地址上。 在父路由组件上写router to  和 router-view。 
// 路由传参 上一级路由传给下一级路由    父路由to里面写?id=666&  在子组件里的写$route.query.id
// 传参to的字符串写法可以配合模板字符串方法写   to的对象写法{path： ， query: {id}}推荐对象写法。  
// 上面传参方式一点也不打扰$router
// 命名路由  配置路由js时候，可以起名字name ，那么在to对象写法里面 path就不用写了，写name：''
// 路由传参第二种 params    this.$route.params.
// to里面直接写/666/你好啊    如果想这样写 就要在路由js里面配置path的时候在路径后面写:id/:title  占位符
// to的对象写法如果写了params写法，那么就不能再to对象写法里写path而只能写name  to={name: '', params: {id}}
// 如果传的参数很多，就会在模板上重复写很多次$route.query。。。。。
// 解决以上问题   在配置js里面 在(children)里面写props: {a:1.b:'hello'} 该props对象中所有的key-vbalue都会以props的形式传给当前配置path的组件。去那个组件用props接收就行了，但是是死数据，不常用。
// 第二中写法， 在配置js里面props:true    若布尔值为真，就会把该路由组件收到的params参数，以props的形式传给当前配置的组件。再去接收就行了。   
// 还有更香的  上面那个只能接收params。n拿不到query
// props的第三种写法，写成函数    props($route) {return {id: $route.query.id}}   这样在对应组件也用props接收一下。    
// 结构的连续赋值  形参里query:{id,title}   id就可以拿出来用    query其实是$route 中的属性，此时被结构了一层在形参里。
// 路由器的后退前进  历史记录    
// push模式   用router-link的  
// replace模式  替换之前的 回不去了   router-link 上属性写 replace = true
// 默认是push模式
// 编程式路由  防止把button包着router-link时会解析成a标签，破坏了dom结构。
// 编程式路由  不破坏dom标签，还能定时跳转。前一种要点击啊。
// 编程式路由 this.$router.push({name: query:}) 和  to差不多写法。
// this.$router.replacef工作模式来跳转组件。此时还是需要router-view的，但是不需要router-link标签了，to也不要啦。
// 前进 和 后退按钮   this.$router.back()  this.$router.forward() this.$router.go(-1)
// 编程式路由  脱离了router-link.
// 缓存路由组件 因为要保持前一个组件的input框内容，不想被切走时销毁组件。 keep-alive    include='[News]' 包裹着router-view  News是组件名。
// 两个新的生命周期钩子  保持缓存又想销毁里面的定时器。 
// actived() {}  deactved() {} 路由组件才有的生命周期钩子。激活  失活。
// 8个基础钩子  加nextTick  加 actived() {}  deactved() {}
// 路由守卫  很重要  权限
// new出来的路由器不能直接暴露出去了，要变量router接收一下， 每次路由器切换之前会触发router.beforEach((to,from,next)=> {})) 
// to 要去的路由组件 from 从哪个路由组件来   next() 放行
// localStorage.getItem('school')    to.path ===          
// 如果有几十个要检验的页面  就很臃肿 
// 给需要检验的每个路由加个属性 表示哪个路由需要校验  mata 路由元信息
// mata: {isAuth:ture} 
// to.mata.isAuth === ture
// 后置守卫  router.afterEach((to,from) = > {})
// 用的不多  一般这样用  改页签标题   document.title =  to.mata.title  || 'ss'
// 独享路由守卫
// 写在自己route配置里  beforeEach：(to,from,next) => {}   就不是beforeEach了。
// 独享路由守卫 没有后置守卫
// 组件路由守卫  写在组件里的
// beforRouteEnter (to,from,next) {通过路由规则，进入该组件时被调用}   beforRouteLeave (to,from,next) {通过路由规则，离开该组件时被调用}  
// 组件路由守卫  不是前置 后置守卫，是那种进入  和离开的时机调的。会隔一段时间的，而前置后置守卫是紧连着调的。
// 这个组件显示时如果不是通过路由规则进来的  不会触发组件路由守卫 
// hash模式 #号后面的都是hash值 ，hash值都不是发送给服务器的。前端自己在玩。
// history模式   在new 路由器时  mode: 'history'
// 兼容性区别 
// history 会在网页刷新时 把地址全发服务器 就报错了
// 第133节  nodejs 搭建微型服务器
// app.use(express.static(_dirname +'/static'))
// 就想用history   让后端配合   中间件 connect-history-api-fallback   app.use(history)
// 组件库  vant cubeui mint ui nutui  element ui   iview ui  
// 是个插件  要vue.use() 用vue.use()是全局引入
// 也可以按需引入  样式不用自己引入了。有坑   第135节
// vue3  更新快  占用内存少  响应式原理 proxy 组合式api 内置组件 生命周期 data ts
// main.js 引入的是名为createApp的工厂函数  不用new  直接调。 创建的是app  不是vm  更轻量 
// setup 组合式api   数据 方法 计算属性 生命周期  都放到setup里面。
// setup() {let name = '张三'，function sayhello() {name},   return {name, sayhello}} 如果setup返回的是对象，则返回的数据和方法可以直接在模板上面用。常用   return () => {return h('h1','尚硅谷')}  如果返回一个渲染函数。 不常用。
// 也可以写data  methods 配置项   但不推荐  因为data methods可以访问到setup里的。但setup不能访问到data methods的。
// 不要混用v2 v3的配置项。  setup 优先级高     
// setup 前面不能加async  被promise包裹了。
// ref函数 包数据包装成一个对象了    引用的实现  就叫它引用对象  let name = ref('张三')   用的时候要用name.value 但是模板上可以直接写name     原理也是defineproperty
// 如果用ref包的是个对象类型的数据，那么 底层走的响应式是proxy
// const student = reactive({name: age:})        返回一个proxy对象。
// 定义一个基本数据类型时不要用reactive，ref如果包的是对象，内部也是求助的reactive。
// 用ref包的数据 取得时候要加value 有点恶心  reactive好像不需要。
// proxy干掉了$set  $delete 数组可以直接操作索引啦 赋值
// proxy的响应式原理   
// const p = new Proxy(person,{get(target就是person,读的属性propName) { return target[propName]    就算你要八百个属性要代理也不用在遍历重写，直接就传进来的}, set(target,propName,value改的值) {有人修改了，我要去更新页面了},deleteProperty(target,propNmae) {删除时触发的,有人删了，我要去更新数据 }})  
// 里面的配置项get set deleteproperty 可以不写，也能实现代理式，重写是因为在触发的时候，我们要更新页面实现响应式。
// set不止在修改的时候调用，新增属性的时候也会触发，
// vue3里面没这么low   用的window.Reflect.get(obj,'a')  Reflect.set(obj,'a') Reflect.deleproperty(obj,'a')       Reflect里也有defineProperty   Reflect在执行defineProperty失败时不会挂掉，它会给返回布尔值，程序员根据这个布尔值来做判断。
// try {} catch(e) {} 是抛出错误后，程序可以一直走，不会在执行逻辑是挂掉。
// vue3 的proxy的 get里面 return的是rerurn Reflect.get(target,propNmae) set也是同理reflect
// 为什么要用反射对象？ return 用反射读取和改的 删除的，新增的，队源数据的操作。
// ref最好用来定义基本数据类型，reactive用来定义对象类型的，也可以用reactive全部塞进一个对象data里，return出来，梦回vue2。
// setup是在beforeCreate之前调用一次，this是understand
// setup的参数问题  props(就是props) context(attrs 相当于this.$attrs,slots 相当于this.$slots,emit 相当于 this.$emit)
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
