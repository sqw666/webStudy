<template>
    <div class="content">
        <button @click="buttonClick">点击触发事件</button>
    </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
// \' 表示单引号   n表示换行
// typeof 检查变量类型
// NaN  算了，算出来不是一个数字。
// JS整数的运算基本正确，小数会不精确，因为计算机不能精确表示小数。可以放在服务器里运算。
// null表示一个空对象，typeof null 是object。typeof undefined  返回是undefined。
// undefined 声明但未赋值
// 强制类型转换，a.toSring()方法 不会影响原数据。Sring(a) 函数。区别是对null和undefined转的不同，前面报错，后面是直接转加‘’。
// 强制类型转换， Number(), 纯数字字符串则直接转城数字，但是非数字内容，则转成NAN。空串会转成0。true转成1，false转成0. null转成0，undefined转成NaN.
// 强制类型转换 parseInt（）从字符串中有效的整数取出来从左往右转成整型，遇到非数字就直接G。parseFloat（）能取有效的小数。不是字符串的会先转字符串再转数字。
// 0x10 16进制的数字10，但是输的时候会转换成10进制输出。0开头是8进制，0b开头是2进制数字。parseInt(a,10) 当成10进制转换。
// 强制类型转换 Boolean（） ，对于数字，除了NAN和0是false。对于字符串 除了空串是false。 null转的是false，undefined也是false。
// 算数运算符，数字 + '' 可以利用这一个特点把数字转成字符串。除了+运算符会隐形转字符串计算拼接，其余的- * / 都会隐形转数字再计算。
// 算数运算符 % 取模运算。9%3 余0.
// 一元运算符 + 正号 - 负号。+ - 会先把其他数据类型转换成number再加负号。
// 自增自减 -- ++a 代表先算完再赋值， a-- a++ 是直接复制再自增自减。
// 逻辑运算符 && || ！   返回第一个或者第二个看该运算符还管不管第二个值了， 其他代码用该值来判断truefalse） 后面再复习。
//  ture && 会执行这个。 false && 不会执行这个了。  这个运算符可以简化代码。sqw
// \u1C00 Unicode编码 在js中 \u 加前缀        在网页中&#9760  后面要跟10进制 
// isNaN() 判断是不是NaN
// 三元运算符也叫条件运算符  a？b：c   a是true执行b
// let a， b = 1， c 逗号可以声明多个变量
// 括号可以提升优先级，一人一下，万人之上。
// switch case 方法参数的值会跟case后面的值比较。值可以是表达式，两者的值全等就行。
// while 循环 有break就停止   for循环 for （let i =1； i< 100 ; i++）{}
// break 只对离他最近的for生效。 可以给外层循环起名字 xxx：   break后面跟着 xxx；
// continue可以直接跳过当次循环。 也是对离他最近的循环生效。也可以给外for起名字。
// 对象

// 内建对象 宿主对象 自定义对象
// delete 对象.属性
// 对象采用特殊的属性名 要用obj['123'] = 789  取的时候也要用obj['123']  推荐这种 因为可以传变量   n= ‘123’  obj[n]   但是中括号最后还要是字符串才行
// in 运算符检测对象是否有该属性 ‘test’ in obj  返回布尔值 原型中的也算。
// 字面量对象的属性名 可以不加引号，但是如果使用特殊的名字，必须加引号。
// var fn = New function  构造函数创建一个函数对象
// function fn（） {} 声明试函数
// var fn = function（）{} 表达式函数
//  上面三个都是存起来 没调用
// fn（）调用执行函数
// 声明形参就相当于在函数内部声明了变量，只声明未赋值。
// 调用函数时，解析器不会检查实参的类型和实参，多余的实参不会赋值。
// return 返回函数执行的结果， 可以结束函数的运行，不写等于return； 返回undefined
// 函数也可以作为一个实参传给一个形参a，此时a就是这个函数。 如果是把fn（）作为实参传，相当于把fn的返回值传过去，只写fn是把函数对象传过去，没调用。
//  加了（）是传的返回值，形参是这个函数的返回值。不加（）是把函数传过去，形参等于这个函数
// break跳过for循环，continue跳过当次循环，return跳过整个函数。 
// 函数内部再定义一个函数，内部再写b（）可以调用内部的这个函数。 
// fn（）（） 相当是fn函数的返回值是个函数，它在调用。
// 立即执行函数，声明后用括号包起来，后面加个（）。
// 函数作为一个属性存在对象的属性里，则称之为方法，本质上和函数一样，就是名字不同。
// 表达式1 && 表达式2 || 表达式3  如果1是真则执行2,2为假则不执行3,2为真则执行假。 && 比 || 优先级高一点。
// 枚举对象中的属性，for （let a in obj）{obj[n]}  【】里面可以写变量 .的方式是认死理
// 作用域一共两种，全局和函数。 全局的在页面打开时创建，关闭时销毁。
// 全局的变量都作为window的属性保存。
// 只有用var会产生变量声明提前 用var定义的声明函数的会声明提前所有 会直接提到解析器最高级且啥都过去了。 用表达式赋值的函数不会提函数体，只会定义一个变量未赋值。
// 函数作用域 在调用函数时创建作用域，函数执行完毕后作用域销毁。在函数作用域可以访问到全局变量，它会从里往外一层一层找直到全局作用域都没找到就会报错。
// 在函数作用域中使用var 也会提前到函数执行时最前面但不会被赋值。
// 在函数作用域中不使用var声明的变量都会成为全局的变量。
// 函数在调用时，解析器每次会传递一个隐含的参数叫this。 this指向的是函数执行的上下文对象。根据调用的方式不同。跟创建无关。
// 一函数调用时是指向window，用方法调用时是指向那个方法对象。
// 工厂函数创建对象 没有this代替对象，因为对象写在死在函数里面了，都是New的Objecet。
// 构造函数规范是首字母大写，构造函数调用时要加New，不加就是普通函数。                     有this代替对象了，返回的对象就是外面等待赋值的对象。
// 构造函数的执行流程，只要出现New立刻会创建一个新对象，作为返回值返回。1 立即创建一个对象，把新的对象设置为this，执行函数中的代码，把对象返回。
// per instance Person 检查一个对象是不是一个构造函数的实例。 per instance Object per是对象，则永远是true。
// this的问题是构造函数调一次就会创一个对象，功能重复，浪费内存。原型就出来了
// 原型对象出现的目的， 虽然把功能函数提到全局，在构造函数中把功能函数赋值解决了功能函数被创建多次，但是会污染全局作用域，且在全局中也不安全（会被覆盖）。
// 只要是函数，解析器都会向函数添加一个prototype对象。普通函数的原型没有任何作用，一构造函数创建的对象中都会有一个隐含的属性_proto_会指向构造函数的原型对象。
// 原型对象相当于一个公共区域，同一个类的实例都可以访问，所有可以把对象的公共功能添加到原型对象中。Person.prototype.a = '666';
// 当访问一个对象的属性或者方法时，会先在自身找，找不到会去原型对象中找。
// obj.hasOwnproPerty('name') 该方法可以只检测自身对象中有没有name。in关键字是包括了原型。
// 原型对象也有_proto_指向他的原型对象。
// 找某个属性或者方法的顺序，自身 自身的原型对象，直到自身的原型对象的原型（Object），Object没有原型对象了指向null。
// 打印某个变量 是打印他的toString（）方法返回值。可以改它自身的toSring（）。
// 垃圾回收，不用就置为null。
// 数组 也是内建对象 New Array（）。  arr[0] = 10; 读取不存在的索引不会报错会返回undefined。
// 数组的长度是它最大索引+1，无论里面连不连续。
// 数组方法 push（）添加一个或多个数据并返回新的长度。
// pop（）删除数组最后的一个数据。调用一次删一个，返回被删除的元素。
// unshift（） 和push相反 往前面加 返回新长度。
// shift和pop相反，删除前面的，调用一次删一个，返回被删除的元素
// 循环数组， for（let i=0； i< arr.length； i++）{arr[i]}
// forEach（）由我们声明 但不由我们调，浏览器调的，称为回调函数。
// slice(开始，结束) 截取数组指定元素，不包括结束索引。不会改变原数组，把截取的放在一个新数组返回。只写一个参数 会截取到最后。
// splice（开始，结束） 删除原数组数据，把删除的元素作为返回值返回。第一个参数表示开始位置，第二个参数表示删除几个。第三个参数及以后可以传入新的元素，自动插入删除的位置。 （3,0，新元素）等于把新元素插入在索引为3的位置
// 数组去重 双重循环，不如forEach+ include
// arr1.concat(arr2) 合并成数组返回，不会影响原数组。arr1.concat(arr2， arr3，'333)
// arr.join（连接符默认，） 把数组转成字符串，返回结果，不会影响原数组。可以传空串转成字符串啊。
// arr.reverse() 反转数组，会影响原数组。
// arr.sort() 数组排序，会影响原数组。默认按照Unicode编码排序。不准确，需要传回调函数。回调函数返回大于0的数，就会交换位置。
// 函数的方法，因为函数也是一个对象啊。fn.call() fn.apply() fn()都会执行函数。
// fn.call() fn.apply() 会将一个对象成为这个函数的this。fn.call(obj) 
// call(this对象，实参1，实参2...) call的实参直接写在指定this对象之后。
// apply（this对象，[实参1，实参2...]) applly要把实参写数组里。
// 函数在调用时，解析器除了每次会传递一个隐含的参数this，还有一个类数组对象arguments，所有的实参都在这里，不用写形参接收。arguments.length 实参的数量。arguments[0]对应实参1。
// arr instance Array 检测数组。type只能检测出对象。还有一个Array.isArray(arr)，也可以检测数组。
// arguments中还有一个自带属性callee，对应当前执行的函数对象。
// Date对象 它是一个构造函数，使用时需要New，New出来的对象有很多方法。
// Math对象，它是一个工具类对象，不需要New，直接传参用它的方法即可。 随机数。
// 包装类 String() Number() Boolean() 可以把基本数据类型转成对应的对象 let a = New Number（3）。可以当对象使用。一般开发中不用，它自己会偷偷用。
// 当基本数据去调属性和方法时，解析器会临时把它包装成一个对象。
// 字符串方法 字符串底层是以字符数组的形式保存的。str.length str[1]
// charAt() 返回指定位置的字符 str.charAt(0) 索引第0个字符。 String.fromCharCode(222)
// str.concat('11')  连接字符串，参数可以写多个用逗号，返回新字符串，不会影响原数据。
// indexOf() str.indexOf('h') 查找指定字符串，找到就返回第一次出现的索引，找不到则返回-1。 str.indexOf('h',5) 从第五个位置开始查找。
// lastIndexOf() 从后往前找。
// slice(0,6) 截取字符串 返回新，不影响原数据。
// substring（）与slice类似。第二个参数不能是负数。
// split（，）  str.spilt(,) 根据字符串中的，拆成一个数组。如果根据其中的字符拆，则会把这个字符吃掉。传一个空串则会把每个字符都拆分成一个数组。
// toUperCase() 转成大写
// 字符串方法都不会影响原数据，都会返回新数据。
// 正则 是用来制定规则的，或者把复活规则的东西提取出来。
// let reg = New RegExp(正则表达式，匹配模式) 创建正则对象。   reg.test(str) 检查找str里面符不符合规则，返回布尔值。
// 第二个参数 i 忽略是大小写，g全局匹配。
// 字面量创建正则规则对象 reg = /正则表达式/匹配模式/        简单但没有构造函数灵活。
// reg= /a|b/i/                   a|b 查找a或者b，忽略大小写。            
// [ab] 也是或者的关系
// [a-z] [A-Z] [A-z] 任意小写 大写 大小写
// /abc|aec|afc/ 相当于 a[bef]c
// [^ef] 除了ab以外的。 ^在[] 里是除了， 在外面是以什么开头。
// [0-9] 任意数字
// 正则与字符串结合使用。
// let newstrArr = str.split(/[A-z]/) 根据任意字母拆分成一个数组。  这个方法即使不加g 也会全局匹配。
// str.search('a') 除了跟indexOF一样，还可以用正则，str.search(/a[sh]f/) 返回索引或者-1，只会查找第一个，即使加了g也没用。
// str.match(/[A-z]/) 只提取出一个字母，str.match(/[A-z]/g)  加g可以全部一个一个找出来。  返回在新数组。
// str.replace(/a/gi, '888') 把所有的a替换成888 第二个参数用空串，等于删a。
// 量词 /a{3}/  等于3个a，量词只对前面的字符生效，全体需要加（）包起来。[]是对前面全体，不用加().
// /ab{1,3}/ b出现1到3次都行。/ab{2,}/ 2次以上才行。
// /ab+c/ 至少一个b  /ab*c/ 0个或多个b都行。  /ab？c/  相等于1个或者0个。
//  /^a/ 以a开头才行          /a$/ 必须以a结尾。   /^a$/ a既开始有结尾   /^a|a$/ 以啊开头或者以a结尾。
// 手机号 let reg = /^1[3-9][3-9{9}$/  reg.test('13128889829')  返回true
// .表示任意字符。 检测.用转义字符   /\./
// let reg = New RegExp('\\.'，匹配模式)  找.
// 只去除前后空格 str.replace(/^\s*|\s*$/g, '') 以空格开头 多个空格
// 邮件正则 
// 百度搜 常用正则表达式
// dom 宿主对象，用js来操作网页。文档网页对象模型
// 节点死忠 文档节点document 元素节点标签名 属性节点属性名 文本节点（里面内容）text
// document.getElementById('btn') btn.innerHtml = 'hjhadjasdhj' btn.onclick = function() {}
// scipt标签写在dom元素之前会拿不到dom元素，所以一般写dom下面。或者写上面时加个事件window.onload = function() {代码放这里}
// document.getElementsByTagName('span') 一组 类数组对象 通过标签名
// document.getElementsByName('disabled')[3].male   通过name属性名   一般获取表单属性  class不给用 用className.
// innerHtml 元素内部的HTML代码 对于自结束标签 这个属性没用。
// 案例 上一张下一张切换图片sqw
// 获取元素的自己的子节点元素 document.getElementsById('city') city.getElementsByTagName('li') city里面的一组li
// city.childNodes 所有子节点   标签与标签之间的空格会被当成空白节点。
// city.children 所有子元素  不包括空白节点了 只是元素。 元素不包括空格空白 节点包括。
// city.fisrtChild 第一个子节点 包括空白节点
// city.fisrtElementChild 第一个子元素 不包括空白节点
// 获取父亲 兄弟节点
// city.parentNode  父亲节点
// innerText 元素内部的文本内容  没有标签包着了。
// city.previousSibling 前一个兄弟节点 节点会包含空白节点。
//  city.previousElememntSibling 前一个兄弟元素 元素不会包含空白节点。
// 表单.value  
// 节点的属性 nodeValue就是文本节点的本文内容
// 案例 全选练习 sqw
// body 可以用document.getElementsByTagName  也可以直接document.body。 document.documentElement 是根标签html。  document.all是页面所有元素相当于document.getElementsByTagName('*')
// 根据class获取 document.getElementsByclassName('box1')  一组
// 根据css选择器  document.querySelect('.box div')  获取后代  
// document.querySelect 只会返回第一个
// document.querySelectAll 返回类数组对象
// 增删改 节点 插入子节点appendChild() 删除子节点city.removeChild('bj') ===bj.parentNode.removeChild('bj')     在指定子节点前面差个子节点insertBefore(新，旧) createElement() creatTextNode() 替换子节点replaceChild(新， 旧)
//  let li = document.createEmlement('li') let text = document.creatTextNode('广州')   li.appendChild(text)
// city.innerHtml += '<li>广州</li>' 也可以这样加子节点，但是动静大。
// 可以结合用先获取li    li.innerHtml = '广州'    city.appendChild(li)   推荐。
// 案例 增删改练习。
// for循环先执行，响应函数后执行。
// 通过dom改样式   box1.style.width= '300px' (可能会用到驼峰写法)  权重干不过important   读取的时候也是只能读取的写的内敛样式
// 获取元素当前正在显示的样式 元素.currentStyle.样式名  box1.currentStyle.width
// 上面的currentStyle只能用于IE。
// getComputedStyle() 是window的方法，通用。需要两个参数（元素对象，伪元素）。一般不获取伪元素。let obj = getComputedStyle(box1, null)  obj.width
// 对象.属性，用点的方式取是是写死属性名。[] 这里才可以写变量的属性名。
// 通过getComputedStyle() 和currentStyle 得到的都是只读的，不能这样改，要通过box1.style.width= '300px'   这样改。
// 变量没找到会报错，而属性只会返回undefined。
// 其他样式相关的属性 box1.clientHight  返回值不带px单位，可以直接计算。且包括（内边距padding）。（之前的获取的都是带单位。）  clientHight获取的也是只读的，不能被赋值。
// offsetWithd 返回元素的宽度  包括padding和边框。也没有px。
// offsetParent 获取当前元素的最近的定位祖先元素。如果都没有则返回body。
// offsetLeft 当前元素相对于其定位祖先元素的水平偏移量。offsetTop.........垂直。
// scrollHight 返回实际的滚动元素真正的高度。width 同理
// scrollLeft 返回水平滚动条滚动的距离。top  同里
// scrollHight - scrollTop 等于被滚动完的高度即clientHight可见高度也就是滚到底了。sqw  如果有水平滚动条在下面挡住一部分可见的，也要算的。
// onscroll 当滚动条滚动时触发。 （滚动的元素）box.onscroll = function() {}
// 事件对象
// 鼠标 onmousemove 自带一个实参浏览器传的（ie8不传）   box1.onmousemove = function(event) {鼠标坐标 键盘按键  滚动方向}
// clientX 获取当前可见窗口鼠标水平坐标 clientY  event.clientY。   但是box1.style.left是相对于整个页面的. 所以用 event.pageY  和它配合。
// box1跟随鼠标移动 在document 里绑定才对document.onmousemove = 。  但是用clientX 不准确，可以用pageX，也可以滚动时，把盒子往下移动滚动距离 body的f父亲的html，谁滚动就是谁的 document.body.scrollTop
// 事件冒泡 子的同名事件触发后会往上冒泡（祖先也会触发）。触发父级的同名事件。 点html没用，只会往上冒泡。 可以取消，事件event.cancelBuble = true
// 事件委派 是为了解决后来加的子节点绑定事件，因为后来的没绑定上。 给祖先绑定事件。子元素冒上来，且用target可以获取是哪个子元素。event.target.className === 'link'，有隐患 可以用正则匹配。
// 使用对象.事件 同名事件会覆盖。 但可以用这个 addEventListener('click'，function() {alert(1)},是否在捕获阶段触发一般给false)  不支持ie8 ie8用btn1.attachEvent('onclick'，function() {alert(1)})  执行顺序相反。
// 天才 bind函数。 形参回调函数callback还是在小括号里，没问题，只是外面套了个匿名函数，执行匿名函数时会调用形参callback.call(obj).为什么写匿名函数时因为要求接收的是个函数，不能是函数执行完的返回值啊，例如callback()==== 从浏览器手里抢手动权利  sqw
// 事件的传播 从里往外是冒泡 最开始是捕获阶段从外往里 默认不触发事件 可以传true addEventListener。
// 拖拽功能 1当鼠标按下时onmousedown  2当鼠标移动时onmousemove  3当鼠标松开时，元素固定onmouseup。  嵌套这写。 document.onmousemove  = null 取消事件
// btn1.setCapture() 捕获鼠标事件，抢事件。   取消捕获 btn1.realeaseCapture() 释放 。。。。。 只ie支持
// 封装函数的本质是往上再扩一级，把变得东西当成形参穿进去。
// 滚轮的事件  box1.onmousewheel = function() {}   event.wheelDelta 滚轮方向
// 键盘事件 onkeydown某个按键被按下 按住不松手会连续触发    onkeyup某个按键被松开   document.onkeydown = function(event) {event.keyCode}
// input1.onkeydown = function() { return false会禁止输入}
// BOM 浏览器对象模型 通过操作js来操作浏览器 window窗口 navigation信息识别不同浏览器 location地址栏信息 history历史记录前后页 screen显示器屏幕信息
// navigation.userAgent
// history.back() history.forward() history.go(-2)
// location地址栏信息  修改它 可以跳转。location.assign() 也可以跳转。 location.reload() 刷新  replace  不能回退
// 定时器
// let timer = setInterval(function(if() {clearInterval(timer)}) {}, 1000)   clearInterval(timer)  
// 自动切换功能，如果数组到最后了，直接用模运算处理，就不需要if了、
// 在开启新的定时之前 把上一个关了
// 延时调用 let timeOut = setTimeout(function() {},3000) 不马上执行，隔3秒以后再执行，而且只会执行一次。 clearTimeout(timeOut)   和定时调用是可以互相代替的，一般常用定时调用。
//  去px  parseInt(39px)
// 盒子移动案例 sqw
// 轮播图 案例 sqw  要保持向左转 在塞进去一张(第一张)放在后面，当转到这的时候，改索引，这时候他会往右回来，但是这样不好，所以当他到最后一张时，不仅改索引为0还要把偏移量left置为0；如果不加第一张到后面就会出现切换的过程不好隐藏。
// 开发中不建议大量用box1.style.width 这种改样式，1 多了麻烦 2 和css耦合 3 性能差 没改一次就渲染一次。
// 建议修改class名字 box.className += ' b2'  b2是样式class
// 用正则检查有没有b2 y以防多个b2加上去
// 用repace替换 来删除一个class obJ.className.replace('b1', '')
// 切换样式，有就删除，没有就添加。
// 案例二级菜单 展开隐藏 sqw
// 加过渡 
// JSON.parce(json1字符串)  返回一个对象  JSON，stringify(obj) 转换成json字符串  JSON是js自带的工具类对象
// eval() 可以执行一段字符串形式的JS代码 但是如果有{} 则需要两边加()   性能差 有安全隐患
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
