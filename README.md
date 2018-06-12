# vue-learn

学习vue, 记录笔记

代码放在：[vue-learn](https://github.com/solate/vue-learn)


## Hello World

1. 创建vue 实例
2. el 表示 vue 管理的区域
3. data 表示管理区域内的数据
4. {{内容}} 进行绑定


## TODOList

### v-for

循环遍历 data中 list 的数据

### v-on

绑定事件, 放在methods 内

todoList 中在按钮中绑定提交事件

```
简写: v-on:click => @click
```


### v-model

数据的双向绑定

输入框数据发生变化, 则data中数据也发送变化. data 中定义变量发送变化则页面数据也跟着变

### v-bind

向组件传入绑定值，

props 组件接受那些值

```
简写: v-bind:index => :index
```

### v-if

条件判断语句

### v-else

判断语句, 必须紧跟 v-if, 中间不能插入其他元素

### v-else-if

判断语句, 必须紧跟 v-if, 中间不能插入其他元素


### v-text

将值输出成文本

### v-html

将值输出成html

### v-show

输出元素，不会移除dom， 经常控制界面元素显示和影藏

v-show 会渲染到页面，只是display: none;

## MVVM 模式

### 传统MVP 设计模式

主要面向DOM进行操作

View <=> Presenter <=> Model

View : 视图
Presenter : 控制器, 大量的DOM操作

### MVVM

View <=> ViewModel <=> Model

ViewModel : DOM Listeners , Data Bindings.  Vue 内置的, 我们并不需要关注

主要面向数据进行操作


## 前端组件化

可以将页面进行切分, 组件就是界面中的一小块。

父组件使用v-bind 向子组件传值，子组件使用 this.$emit 向父组件触发事件，父组件监听这个时间, 并接受事件的参数


## Vue 实例

全局变量： app.$data.xx

以$开头的都是这个实例的**实例属性**和**实例方法**

app.$destroy() //将这个实例销毁，销毁后再修改值,页面不会发送变化

### 生命周期钩子

生命周期函数就是vue实例在某个时间点自动执行的函数

1. init : 初始化事件和生命周期相关部分
2. beforeCreate()
3. init : 处理外部注入和 双向绑定等
4. created() //初始化完成
5. has el : 是否有元素绑定，没有执行 vm.$mount(el)
6. has template : 是否有模版, 有模版就执行模版，没有就把el的内容当成模版
7. beforeMount() //模版和数据即将挂载的一瞬间, 未渲染页面
8. vm.$el replace el 模版和数据进行挂载
9. mounted() //已渲染页面
10. mount 挂载
11. 当 data 中数据有变化 (app.$data.seen = false)
12. beforeUpdate() //渲染之前
13. DOM 重新开始渲染
14. updated()  //渲染之后
15. 当 vm.$destroy() 被调用,下面开始执行 (app.$destroy())
16. beforeDestroy() //销毁之前
17. 销毁
18. destroyed() //销毁之后

### 模版语法

这3个内容之中都可以写js 表达式

1. 插值表达式 : {{data}}
2. v-text
3. v-html

## 计算属性， 方法， 侦听器

* computed
* methods
* watch



## 样式绑定

### class

1. 绑定obj
2. 绑定数组

### style

1. 绑定obj
2. 绑定数组

### 条件渲染

给元素加 key="xx" vue就会认为是页面中唯一的元素，如果key不同就不会复用

```会复用
    <div v-if="show">
        用户名： <input>
    </div>
    <div v-else>
        邮箱名： <input>
    </div>
```

加key 不会复用


```不会复用
    <div v-if="show">
        用户名： <input key="username" />
    </div>
    <div v-else>
        邮箱名： <input key="mail" />
    </div>
```

### 列表渲染

```
    <div v-for="(item, index) of list"
         :key="item.id">
    {{item}} -- {{index}}
    </div>
```

性能高： key值唯一，不是用index

我们操作数组的时候，不能使用下标的方式，

1. 使用vue提供的方法。

* push 增加
* pop 删除最后一条
* shift 删除第一项
* unshift 第一项加内容
* splice 切割
* sort 排序
* reverse 取反

2. 改变数组引用，

app.list = [{新数据}]

3. set 方法

```
Vue.set(app.list, 1, 5)

app.$set(app.list, 1, 5)
```


####  template

模版占位符, 包裹一些元素，并不会被渲染

```
    <template v-for="(item, index) of list"
         :key="item.id">
        <div>{{item}} -- {{index}}</div>
        <span>xxx</span>
    </template>
```



#### 对象循环

```
    <div  v-for="(item, key, index) of userInfo">
        <div>{{item}} -- {{key}} -- {{index}} </div>
    </div>


```

1. 改变引用来进行渲染的改变
2. set 方法进行改变

```
//全局方法
Vue.set(app.userInfo, "address", "beijin")

//实例方法
app.$set(app.userInfo, "address", "beijin")

```


### is

使用is 解决h5中 标签规范 的bug, 包含后页面展现错误

```


<select>
    <option is="row"></option>
</select>


Vue.component("row", {
    template : "<tr><td>this is a row</td></tr>",
})


```

### 注意点

子组件定义data, 必须是一个函数，而不能是一个对象,

```
Vue.component("row", {
    data : function () {
      return {
          content : "this is a row"
      }
    },
    template : "<tr><td>{{content}}</td></tr>",
})
```










## 参考