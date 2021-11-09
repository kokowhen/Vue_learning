# Vue_learning
记录自己学习Vue的仓库

## 01-第一个Vue程序

创建的Vue是一个对象，el属性用来和HTML的id作绑定，data可以看作是存放动态解析数据的容器对象，里面存放的可以是属性：属性值的键值对，也可以是另一个对象。👌

data里面的数据就是需要被动态解析的数据

- {{}}是用来输出动态解析的数据的，它的作用不是绑定
- 使用v-bind来绑定一个动态的值是很常用的
- 渲染动态解析的文本的方法：{{属性}}、v-text绑定

## 02-组件基础及组件注册

data必须是一个函数，组件data函数体里可以只写一个返回的空语句

prop里传递的值变成了组件实例的属性，例如，我创建了一个todo-list的组件，向prop里传递了两个值title和about，那么这两个值就可以在组件中作为属性使用

```javascript
// prop里的值
prop:{
    title:[],
    about:[]
}
// 对应HTML里的属性
<todo-list title="" about=""></todo-list>
```

- prop里传递的值和根实例data对象里的值不用有联系
- v-bind属性绑定：本质就是把Vue里data对象的数据绑定给HTML的属性，作为其动态的属性值，v-bind不是页面渲染显示的指令，它只是把Vue里data对象的数据值绑定给HTML的属性，让HTML的属性能够被动态的影响
- 创建的组件也可以访问到根实例data对象里的数据，但是要绑定
- template模板的内容是HTML里的
- template模板里只能有一个语句吗？不是的，需要将多条语句包裹在一个大的div里，div的类名称是组件名

## 03-模板语法

- v-bind可以这样理解，它是一个指令，这个指令将Vue实例data对象里的数据绑定给HTML元素的属性，而且这个数据值是动态解析的，能在DOM里被找到的，这样HTML元素的属性也就跟着这个动态的属性值动态起来了
- v-bind：后面要跟上HTML属性，如果是组件还可以是自定义的属性，如果是HTML原生的，就跟上HTML元素原生的属性
- v-bind可以响应式的更新HTML的属性值

- 如果Vue实例data对象里的属性值为HTML的原生代码，使用{{}}的形式是不能在页面上渲染出效果的，只会显示原生的HTML代码，v-html指令就会解决这个问题，渲染出HTML的效果而不是显示原生HTML代码
- 动态参数不太理解

## 04-计算属性

> 通过已有的属性(Vue管理下的属性)计算得来
>
> 所谓的计算属性就是拿着data里的属性再去进行加工和计算的属性
>
> 计算好的值直接作为vm的新属性，不要再进行自调用(fullName.first是不对的)，可以访问到，但是它不在data里面
>
> 配置在data里的属性在计算属性里不能直接访问到，要用this参数指向vm
>
> 相比于methods，computed会将调用的函数缓存起来，只会在初次读取的时候调用里面的函数，而methods是读取一次就要调用一次，效率不高
>
> data和methods里面写什么就是什么，例如写对象就会变为vm里面的嵌套对象，写属性就是vm的属性，在computed里面是这样操作的，**computed里的函数名和函数返回值会被vm找到然后分别作为vm的属性和属性值**
>
> get函数一般设置返回值，当初次读取fullName时被调用，或者所依赖的数据发生改变时也会被调用，get函数是默认存在的；set函数当fullName被修改时被调用
>
> 如果确定实现的功能是只读不写，那么直接写函数就行了，注意在读取的时候不要写为函数调用的形式，永远记住计算属性是vm的一个属性，直接调用即可

- computed计算属性
  - computed是vm实例对象的属性，里面是一个对象，对象里可以设置get函数和set函数
  - 当动态解析的数据逻辑很复杂时，比如data对象里内嵌的数据嵌套了对象和属性等复杂逻辑数据，那么在HTML中动态解析这些数据就会变得很复杂，这个时候我们就需要计算属性computed了
  - Vue实例里新加的computed属性，里面是一个函数(getter)，函数返回值就是待解析的复杂逻辑值，函数名就是HTML代码里解析的文本
  - computed计算属性里的函数变成了一个DOM节点，可以通过Vue实例对象进行访问
  - computed好像并没有提供像el和data通过$el和$data在HTML进行绑定的方法
  - computed不是一个DOM节点，通过vm实例对象是访问不到的，反而是computed里面的函数作为了vm实例的属性，进而可以作为DOM节点进行访问
  - get函数和set函数不懂

## 05-绑定class和style

> 绑定class样式的写法：字符串写法-适用于class样式名称不确定的情况；数组写法-适用于class样式名和样式的个数都不确定的情况；对象写法-适用于绑定的样式的数量和名称都确定，需要动态切换样式是否应用的情况
>
> 绑定style样式：注意styleObject里的key不能随便写

- v-bind绑定class的时候，class后不仅仅可以跟data对象(相对于data而言)里的属性，还可以是一个键值对的对象或者数组，而且v-bind绑定和HTML原生的class是可以共存的

## 06-列表渲染列表

- v-for指令渲染列表，后面的in语句第一个参数解析的结果就是数组里的对象
- v-for指令对应的属性值可以有多个参数

## 07-表单输入绑定

>  v-model表单绑定指令的学习

### 文本输入绑定(简单)

### 复选框绑定

- 单个复选框绑定到布尔值：data里的属性值是两个布尔值，绑定给复选框
- 多个复选框绑定到同一个数组：data里是一个数组，绑定为复选框
- 数组渲染的值是value属性里的值

### 单选按钮绑定

- data里是一个属性，属性值是''

### 选择框

#### 单选时

- 不要写value属性，不然渲染无效
- data里和单选按钮一样，属性值为''

#### 多选时

- select元素里要添加multiple属性才是多选框
- data里是一个数组

## 08-事件处理

> 怎样监听事件
>
> 指令后面跟着methods里的函数，事件触发时执行
>
> 三个重要的事件修饰符，阻止触发默认事件、阻止冒泡、设置事件只被触发一次

### 监听事件

- 使用v-on：xx或者@xx绑定事件，其中xx是事件名
- 事件的回调需要配置在methods对象中，最终会在vm实例对象中
- methods中配置的函数不要使用箭头函数！否则this就不是指向vm而是指向window了
- 传参的问题，@click="demo"和@click="demo($event)"效果一样，但是后者可以传参，前者也传入了event参数，但是没告诉你，后者是直接告诉你我直接传入了event参数了，更灵活

### 事件修饰符

- .prevent修饰符阻止默认事件的触发

- 事件的冒泡：子元素的事件触发会自动带动父元素事件的触发
- .stop修饰符阻止事件的冒泡
- .once修饰符事件只被触发一次
- @click.prevent.stop这种写法的意思是先阻止默认事件的触发，再阻止冒泡

### 键盘事件

![image-20211107132744035](http://my-picture.qiniu.notyourjeffery.top/image-20211107132744035.png)

那如果我想要用其他的按键去触发事件呢？键盘上的按键都有自己的名称和编码，可以使用if和else逻辑去设置只有当按下某个按钮时才符合条件，事件才会被触发

### 事件的总结

- 每次事件被触发都会往函数里传入DOM原生的event对象
- event对象的一些常用用法：event.target.tagName
- 函数传参：想传就加括号，不想传就不用加，可以用简单的参数代替event
- 三个重要常用的修饰符
- 触发键盘事件的修饰符

## 09-监视属性

> 当被监测的属性发生变化时，回调函数handler自动调用
>
> 监视属性必须存在才能进行调用
>
> 监视的两种写法
>
> 什么情况下用简写，什么时候需要配置immediate和deep的完整写法

- 作用：监视某一个属性的变化
- 天气案例中天气的情况是变化着的，我们可以使用watch属性去监视
- 配置那个变化的对象：handler函数、newValue、oldValue参数
- immediate：true可以让data里的属性未改变之前handler函数就被执行
- 深度监视：deep：true开启
- 监视属性的简写

```html
watch:{
	isHot:{
		handler(newValue,oldValue){
			console.log(newValue,oldValue)
		}
	}
}
```

```html
vm.$watch('isHot',{
		handler(newValue,oldValue){
			console.log(newValue,oldValue)
		}
	}
}
```

- note：Vue管理的函数：methods里函数、computed里的getter和setter、watch属性里的handler函数都不要写成箭头函数的形式，不然this参数指向的对象会变为window

- watch和computed的区别：
  - computed能实现的功能watch基本也都能实现；watch能实现的功能computed不一定能实现
  - 计算属性是不能开启异步任务去维护和操作数据的，例如，我想要计算属性函数的返回值等1秒再返回，这是做不到的；而watch是可以的，因为watch不是靠返回值的
