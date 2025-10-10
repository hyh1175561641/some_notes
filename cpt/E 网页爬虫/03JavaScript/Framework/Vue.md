


https://vuejs.org/

https://nuxt.com/ Nuxt.js

https://jestjs.io/ Jest
https://www.graphql.org/ GraphQL

https://vitest.dev/ Vitest
https://vite.dev/ Vite

https://vueuse.org/ VueUse
https://formkit.com/ FormKit
https://astro.build/ Astro


# 开源代码


https://pure-admin.github.io/vue-pure-admin/
https://github.com/pure-admin/vue-pure-admin


https://vue3.youlai.tech/#/dashboard
https://gitee.com/youlaiorg/vue3-element-admin
https://gitee.com/youlaiorg/youlai-boot

https://doc.iocoder.cn/
https://gitee.com/zhijiantianya/ruoyi-vue-pro





HalseySpicy/Geeker-Admin
snapshot-labs/snapshot
Chanzhaoyu/chatgpt-web
gcpaas/DataRoom
Akryum/vue-virtual-scroller
requarks/wiki

yangjian102621/geekai
un-pany/v3-admin-vite
imsyy/home
radix-vue/shadcn-vue
bastienwirtz/homer



# Vue

https://vuejs.org/
https://router.vuejs.org/
https://pinia.vuejs.org/
https://nuxt.com/




https://blog.csdn.net/weixin_42413684/article/details/81609468 Vue.js介绍以及优缺点
https://www.bilibili.com/video/BV15741177Eh

《Vue.js实战》 梁灏 清华大学出版社 ISBN 978-7-302-48492-9随书源代码 
https://github.com/icarusion/vue-book

vuejs是渐进式框架,简单应用引入一个js文件,复杂应用引入多个js文件

coderwhy：这个是视频中的讲师,网上能搜到这个人的文章 这个人用的postman软件干啥的



```js

// 安装及配置
开发环境：https://vuejs.org/js/vue.js
生产环境：https://vuejs.org/js/vue.min.js
//min.js 简化变量名,撤掉换行符,删掉了警告和打印的内容
CDN:<script src="https://unpkg.com/vue/dist/vue.min.js"></script>

npm安装：后面通过webpack和CLI的使用,脚手架

```





# VUE基础

vue特色
1使用声明式编程范式,可以使代码和数据进行分离。
2响应式：数据改变后,界面会自动跟着改变

在VUE生命周期当中,过程中会调用很多回调函数,进行改变数据和布局
https://cn.vuejs.org/v2/guide/instance.html最下面有图

```html


<!-- mustache语法,插值表达式 -->
<div id="app">
    <p>数值 {{ 123 }}</p>
    <p>运算 {{ 25 + 34 + num }}</p>
    <p>字符串 {{ 'string' }}</p>

    <p>属性 Hello {{ str }}</p>
    <p>数组 {{ arr[0] }}</p>
    <p>对象 {{ obj.name }}</p>

    <p>字符串拼接 {{ "Hello " + str }}</p>
    <p>双目运算符 {{ isTrue ? 'Yes' : 'NO' }}</p>
    <p>调用方法 {{ printInfo() }}</p>
    <p>布尔类型 {{ typeof isTrue }}</p>
</div>
<script>
    let app = new Vue({
        el: '#app',
        data: {
            isTrue: true,
            num: 3,
            str: 'VueJS',
            arr: ['星际穿越', '大话西游'],
            obj: {name: "aaa"},
        },
        methods: {printInfo() {return "Info"}}
    })
</script>



<!-- 控制台可以改变值 -->
app.data.name='Hello'


```

# v-指令

https://cn.vuejs.org/v2/api/#v-text
v-bind(缩写:动态的属性绑定)(设置类的布尔值,能够决定选择什么类)(数组决定)
v-model(双向绑定)
v-once(一次性显示,无法跟着变量值改变)
v-html="varName"(把值解析成html,link是变量名)
v-text(显示文本)
v-pre(显示原本的代码,不进行解析)
v-cloak(斗篷之意,先将模块隐藏,加载好之后显示)


v-text
v-html
v-show
v-bind
v-model
v-slot
v-pre
v-cloak
v-once



```html

<!-- vue指令 -->
<!-- 语法糖是某些语法的简写 -->

v-if v-else 当属性是true时渲染该元素,没有该标签
v-show false时,display为none


<!-- v-bind 动态绑定属性值 超链接 图片地址 -->
<!-- 冒号是v-bind:src="/img"的简写 -->
<div id="app">
    <img title="鼠标悬停文本" v-bind:src="imgUrl" alt="i.img">
    <img title="语法糖简写" :src="imgUrl" alt="i.img">
    <img title="绑定方法" :src="getUrl()" alt="i.img">
    <!-- 类的动态绑定 -->
    <!-- 可以放入methods或一个computed中 -->
    <div class="color size">Text</div>
    <div :class="classes">动态绑定</div>
    <div class="color" :class="size">如果空值则不显示</div>
    <!-- 类的数组动态绑定 -->
    <div :class="['color','size']">数组</div>
    <div :class="[color, size]">数组绑定</div>
    <div :class="classesArr">会自动合并</div>
    <div :class="[{'color':true},{'size':true}]">布尔值</div>
    <div :class="[(isColor?'color':''),'size']">双目判断</div>
    <!-- 类的对象动态绑定 -->
    <div :class="{'color':true,'size':false}">对象布尔值绑定</div>
    <div :class="{'color':isColor,'size':!isColor}">类取反操作</div>
    <!-- style属性对象动态绑定 -->
    <div :style="{'font-size':'30px'}">对象绑定</div>
    <div :style="{fontSize:'30px'}">支持驼峰命名绑定</div>
    <div :style="{fontSize:fontSizePx}">动态绑定大小值</div>
    <div :style="{fontSize:+fontSize+'px'}">拼接样式属性</div>
    <div :style="[baseStyle1,baseStyle2]">数组样式</div>
    <button type="button" @click="isColor=!isColor">颜色取反</button>
</div>
<script>
    let app = new Vue({
        el: '#app',
        data: {
            imgUrl: 'i.img',
            color: 'color',
            size: 'size', // 可以赋值空字符串
            classes: 'color size',
            classesArr: ['color', 'size'],
            isColor: true,
            fontSizePx: '30px',
            fontSize: 30,
            baseStyle1: {'background-color': 'red'},
            baseStyle2: {'font-size': '30px'},},
        methods: {
            getUrl: function () {return this.imgUrl;}}
    })
</script>
<style>.color {color: red;}
.size {font-size: 30px;}</style>



<!-- v-model 实现双向绑定 表单 输入框 文本域 下拉菜单 -->
<div id="app">
    <input type="text" v-model="message">
    <!-- v-model等同于v-bind绑定value属性,v-on绑定当前元素的input事件-->
    <!-- v-bind指令只能实现输入框响应js,修改输入框的值js不受影响,需要与绑定输入事件结合 -->
    <input type="text" :value="message" @input="message = $event.target.value">
    <textarea v-model="message"></textarea>
    <input type="text" v-model.lazy="message" value="lazy修饰符,当用户失去焦点或回车才会更新值">
    <input type="number" v-model.number="num" value="number修饰符,输入的值是数字类型,v-model默认是字符串类型">{{ num + '-' + typeof num }}
    <input type="text" v-model.trim="message" value="去除输入框内头和尾的空格,js里面的空格也去除了">
    <p>{{ message }}</p>
    <!-- 单选框radio -->
    <input type="radio" v-model="gender" name="sex" value="male" id="male"><label for="male">男</label>
    <input type="radio" v-model="gender" name="sex" value="female" id="female"><label for="female">女</label>
    <p v-if="gender=='male'">男</p>
    <p v-else-if="gender=='female'">女</p>
    <!-- 复选框checkbox -->
    <input type="checkbox" v-model="isLicense" id="license"><label for="license">同意协议</label>
    <p>复选框: {{ isLicense }}</p>
    <input type="checkbox" v-model="hobbies" value="篮球" id="b"><label for="b">篮球</label>
    <input type="checkbox" v-model="hobbies" value="游泳" id="s"><label for="s">游泳</label>
    <input type="checkbox" v-model="hobbies" value="骑车" id="r"><label for="r">骑车</label>
    <p>爱好: {{ hobbies }}</p>
    <!-- select -->
    <select v-model="fruit">
        <option value="apple">苹果</option>
        <option value="banana">香蕉</option>
        <option value="orange">橘子</option>
    </select>
    <select v-model="fruits" multiple>
        <option value="apple">苹果</option>
        <option value="banana">香蕉</option>
        <option value="orange">橘子</option>
    </select>
    <p>单选 {{ fruit }} 多选 {{ fruits }}</p>
    <!-- 值绑定 -->
    <label v-for="hobby in originHobbies" :for="hobby">
        <input type="checkbox" v-model="hobbies" :value="hobby" :id="hobby">{{ hobby }}
    </label>
</div>
<script>
    const app = new Vue({
        el: '#app',
        data: {
            message: '你好啊',
            num: 32,
            gender: 'male', // 单选框
            isLicense: false, // 复选框
            hobbies: [], // 多选框
            fruit: 'apple', //下拉选项
            fruits: [], //下拉选项
            originHobbies: ['篮球', '游泳', '骑车',],
        },
    })
</script>

<!-- v-if,v-else-if,v-else指令 -->
<!-- v-if后面的条件为false,元素不会渲染 -->
<div id="app">
    <p v-if="true">显示</p>
    <p v-if="false">不显示</p>
    <p v-if="isShow">Show Data</p>
    <p v-if="!isShow">Not Show Data</p>
    <!-- v-else不需要条件 -->
    <p v-if="score>=90">优秀</p>
    <p v-else-if="score>=80">良好</p>
    <p v-else-if="score>=60">及格</p>
    <p v-else>不及格</p>
    <!-- 使用计算属性来替代上面的多重if判断 -->
    <p>{{ result }}</p>
</div>
<script>
    let app = new Vue({
        el: '#app',
        data: {
            isShow: false,
            score: 66,},
        computed: {
            result() {
                let result = '';
                if (this.score >= 90) {result = '优秀';
                } else if (this.score >= 80) {result = '良好';
                } else if (this.score >= 60) {result = '及格';
                } else {result = '不及格';}
                return result;}}
    })
</script>


<!-- v-for指令,v-for指令支持嵌套 表单 列表 表格 -->
<div id="app">
    <!--遍历数组-->
    <li v-for="item in arr">{{ item }}</li>
    <li v-for="(item,index) in arr">{{ '遍历数组' + item + index }}</li>
    <!-- 遍历对象的值 -->
    <li v-for="value in obj">{{ 'value = ' + value }}</li>
    <li v-for="(value,key,index) in obj">{{ '遍历对象' + key + value + index }}</li>
    <!-- 在遍历当中,v-for最好是绑定一个key,key是不可变化的唯一的 -->
    <!-- 为了高效的更新虚拟DOM,插入更更方便,更好的复用 -->
    <!-- 不加:key指令会重新渲染整个元素,加上则使用diff算法插入新增元素-->
    <li v-for="(item,index) in arr" :key="index">{{ item + index }}</li>
    <li v-for="(value,key,index) in obj" :key="value">{{ key + value + index }}</li>
</div>
<script>
    let app = new Vue({
        el: '#app',
        data: {
            arr: ['星际穿越', '大话西游', '少年派', '盗梦空间'],
            obj: {name: 'zhangsan', age: '23'}
        }
    })
</script>




<!-- v-on绑定事件指令 链接 按钮 键盘事件 拖拽 -->
<div id="app">
    <p>点击次数: {{ counter }}</p>
    <button v-on:click="counter++">点击我+1</button>
    <button v-on:click="btnClick()">使用方法</button>
    <button @click="btnClick">语法糖简写</button>
    <button @dblclick="btnClick">双击事件</button>
    <!-- 事件冒泡子元素和父元素同时绑定同一事件,触发子元素父元素会跟着触发,修饰符可以阻止事件的触发,.stop写在子元素上,.self写在父元素上,阻止默认事件的冒泡.prevent写在子元素上 -->
    <!---->
    <!---->
    <button @click.self="fun1">点击我</button>
    <button @click.stop="fun1">点击我</button>

</div>
<script>
    let app = new Vue({
        el: '#app',
        data: {
            counter: 0
        },
        methods: {
            btnClick() {
                this.counter++ } }
    })
</script>
```








# js内容


```js

// option选项,可以使用很多属性
// https://cn.vuejs.org/v2/api 中的option选项中有很多东西
// 钩子函数,计算属性,侦听器
let vm = new Vue({
	el: "#app",
    data:{},//组件当中data必须是一个函数
    //有时候我们需要对数据进行一些转化后再进行显示
    //或者需要将多个数据结合起来进行显示
    //计算属性起名字别加动词名称,计算属性本质是属性
    //计算属性和方法的区别：方法调用一次会执行一次
    //计算属性有缓存,只有当依赖属性变化时才重新计算,否则不变
    //<h2>{{fullName}}</h2>计算属性不加括号
    computed:{
        fullName: function(){
            return this.firstName + ' ' + this.lastName
        };
        //计算属性是只读的,每个计算属性都有getter方法
        //如果需要,可以给计算属性添加setter方法
        //默认情况下使用getter方法
    },
    methods:{},
    watch:{},
    
    // 钩子函数
    beforeCreate(){创建前},
    created(){创建后},
    beforeMount(){载入前},
    mounted(){载入后},
    beforeUpdate(){更新前},
    updated(){更新后},
    beforeDestroy(){销毁前},
    destroyed(){销毁后}
})


```


```js
export default {
  name: 'App',
  data() {
    return {
      msg: "aaa",
      msg2: "aaa2",
      msg3: "aaa3"
    }
  }
}

```


# 脚手架

https://vite.dev/



```js





# 配置vue大型项目
npm install -g vue-cli --registry=https://registry.npm.taobao.org
npm install -g webpack
npm install -g @vue/cli-init
vue init webpack my-vue
cd my-vue

npm install --save vuex@3.6.2
npm install element-ui -S
npm install mint-ui
npm install axios





```

```js
//目录结构
build
config
node_modules //依赖包
src // 网页源码
  api // 函数接口
  assets
  components//组件在这里
  pages // 页面
  router
    index.js//路由配置
  store
  styles
  types
  utils
  App.vue // 网站首页
  main.js // 首页
static // 静态文件如图片音乐


```


# 组件

组件化插件:将页面拆分成一个个小小的功能块,每个功能块完成属于自己的独立功能。Vue内部会抽象成一颗组件树
调用Vue.extend()方法创建组件构造器,调用Vue.component()方法注册组件,在Vue实例的作用范围内使用组件



```html




```





# 跨域

```js
//跨域问题解决
//vue.config.js
module.exports = {
    devServer: {
        proxy: {  // 导出devserver的代理配置,可以解决跨域问题
            '/api' : {  // /api 表示拦截以/api开头的请求路径
                target: 'http://i.im', // 跨域的域名(不需要写路径)
                // ws: true, // 是否代理websocked
                secure: false, //如果是https需要配置这个参数
                changeOrigin: true, //是否开启跨域
                pathReweite: { // 重写路径
                    '^/api': '' // 把 /api变成空字符
                }
            },
        }}}
//调用后端时,用api替换域
axios.get('/api).then(response => {
    condole.log(response)
})

```


# Vuex

是一个专为Vue.js应用程序开发的状态管理模式+库。它采用集中式存储管理应用的所有组件状态,并以相应的规则保证状态以一种可预测的方式发生变化。Vuex由五个部分组成,分别是State,Mutation,Action,Module,Getter
Vuex的状态存储是响应式的,Vuex的状态不能直接修改

```bash
# 安装
cd myProject
npm install --save vuex@3.6.2

```

```
# 配置Vuex
import Vuex from 'vuex'
Vue.use(Vuex)
const store = new Vuex.Store({ state:{num:0} })
```

```js
# vuex由几部分组成
export default{
    state:{},//定义共享的状态变量
    actions:{},//执行本地或者远端的某一操作
    getters:{},//获取变量的值,可以做一些简单修改
    mutations:{}//修改器,可以修改state变量的值
}
```

```

# 组件中获取state的数据
<div>vuex state:{{$store.state.num}}</div>//插值表达式
data(){return {students: this.$store.state.students}}//函数获取

```

```js
# vue添加favicon图标
先在index.html添加标签,把icon图标放在根目录下
# build/webpack.dev.conf.js下
new HtmlWebpackPlugin({
    //code,
    favicon: path.resolve('favicon.ico')
})
```

# Element UI

Element-vue2官网https://element.eleme.io/#/en-US
Element-Vue3官网https://element-plus.org/en-US/


# Mint UI

https://mint-ui.github.io/#!/zh-cn
饿了么团队开源的一款基于vue.js的移动端UI框架

```bash

// 安装
# Vue 1.x
npm install mint-ui@1 -S
# Vue 2.0
npm install mint-ui -S

```




实战篇 掌握Vue. js 框架主要API 的使用方法、自定义指令、组件开发、单文件组件、Render 函数、使用
webpack 开发可复用的单页面富应用等

```js
//浏览器属性内容
/*  //vue.js是否掺杂了普通开发者不知道的语言和参数,它实现的这些功能是普通开发者用原生js就能做到的吗？
    //为什么data和 methods内的对象被提到前面
    vm//输出vue对象
    vm.$el//doller符号是干啥的
    vm._data//数据对象被提到了前面
    vm.方法在哪里

    如果我想学这一套,在哪里能找到这样的手册（浏览器原理？）
    生命周期函数在哪能找到：vue5-index3
    > vm.create()
        VM109:1 Uncaught TypeError: vm.create is not a function
        at <anonymous>:1:4
*/
```

