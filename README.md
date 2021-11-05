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

- computed计算属性
  - computed是vm实例对象的属性，里面是一个函数，函数返回HTML里复杂逻辑的动态解析数据，this参数开头，直接可以通过this(指向vm)控制data属性(相对于vm而言)里的属性和对象
  - 当动态解析的数据逻辑很复杂时，比如data对象里内嵌的数据嵌套了对象和属性等复杂逻辑数据，那么在HTML中动态解析这些数据就会变得很复杂，这个时候我们就需要计算属性computed了
  - Vue实例里新加的computed属性，里面是一个函数(getter)，函数返回值就是待解析的复杂逻辑值，函数名就是HTML代码里解析的文本
  - computed计算属性里的函数变成了一个DOM节点，可以通过Vue实例对象进行访问
  - computed好像并没有提供像el和data通过$el和$data在HTML进行绑定的方法
  - computed不是一个DOM节点，通过vm实例对象是访问不到的，反而是computed里面的函数作为了vm实例的属性，进而可以作为DOM节点进行访问
  - get函数和set函数不懂

## 05-绑定class和style

- v-bind绑定class的时候，class后不仅仅可以跟data对象(相对于data而言)里的属性，还可以是一个键值对的对象或者数组，而且v-bind绑定和HTML原生的class是可以共存的
- class对象里的自定义属性对应的data动态解析数据是不是都是做一个true和false的逻辑判断，判断为真就将其属性渲染为class的属性值，判断为假，class后面就什么都没有
- 那这样是不是这种class绑定只用在data对象里设置两个属性，属性值分别为true和false
