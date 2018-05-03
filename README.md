个人vue学习笔记

1.常用的生命周期：created:实例创建完成后调用，此阶段完成了数据的观测，但尚未挂载
mounted: el挂载到实例后调用  beforeDestory: 实例销毁之前调用，主要解绑一些使用监听的事件和定时器

2.想显示{{}}标签，而不进行替换，使用v-pre

3.还可以使用javascript表达式进行简单的运算、三元表达式

4.{{ data | formatDate}}  filters过滤器里的方法

5.v-bind:href 简写 :href 用于绑定数据

6.v-on:click 简写 @click 用于绑定方法 

7.计算属性computed 包含一个get 和 set

8.使用计算属性还是methods取决于你是否需要缓存，当遍历大数组和做大量计算时，应当使用计算属性，除非你不希望得到缓存

9.v-clock 主要与display：none 配合使用

10.v-once只渲染一次，不再随数据的变化重新渲染

11.v-if、v-else-if、v-else的条件根据表达式渲染或销魂元素

12.v-show不能在<tempalte>上使用

13.v-if更适合条件不经常改变的场景，因为他切换开销比较大，而v-show适用于频繁切换条件

14.v-for用来循环列表或者对象

15.修饰符 .stop阻止时间冒泡 .prevent阻止默认事件 .once只触发一次  @keyup.13 只有在keycode是13时调用

16.v-model表单双向绑定数据

17.修饰符 .lazy 会转变change事件中同步= 失焦或者按回车时更新 .number可以将输入转换成Number类型 trim可以自动过滤输入的首尾空格

18.父组件向子组件通信，通过props传递数据就可以了

19.子组件向父组件通信，子组件用$emit()触发事件，父组件用$on来监听子组件的事件

20.非父子组件通信可以通过 1.扩展bus实例 2.父链 3.子组件索引

21.$nextTick就是用来知道什么时候DOM更新完成的

