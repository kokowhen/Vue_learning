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

