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

22.table内规定只允许tr td th等表格元素，所以在table内直接使用组件是无效的，可以使用is来挂载组件

23.vue不允许在已经实例化的组件上添加新的动态根级响应属性（既直接挂载再data下的属性）但是可以使用Vue.set(object, key, value)方法添加响应式属性

24.vue对Dom的更新是异步的。在需要人为操作DOM的场景下，ssss为了在vue响应数据变化之后再更新Dom，可以手动调用Vue.nextTick(callback),并将DOM操作逻辑纺织在callback回调函数中，从而确保响应式更新完成之后再进行DOM操作

25. _.debounce是lodash当中限制操作频率的函数

26.通过jQuery对DOM进行的操作可以放置在Mounted属性上进行，即当Vue组件已经完成在DOM上挂载的时候。

27.如果你有一个巨大的数组或object，并且数据不会更改，可以使用Object.freeze()提升 性能

28.track-by是vue为循环提供的优化方法，可以复用多次v-for中id相同的dom。如果你的数据没有一个唯一的id，也可以选择使用track-by="$index"，但必须注意一些副作用。

29.有时候需要直接在父组件中访问子组件实例，或者直接操作DOM元素，此时需要使用ref。ref被用来给元素或子元素注册引用信息。引用信息会根据父组件的$refs对象进行注册。如果在普通的DOM元素上使用，引用信息就是元素，如果用在子组件上，引用信息就是组件实例。

<!-- let vm = new Vue();
vm = {
  // Vue实例属性的代理
  $data: "被watch的data对象",
  $props: "当前组件收到的props",
  $el: "Vue实例使用的根DOM元素",
  $options: "当前Vue实例的初始化选项",
  $parent: "父组件Vue对象的实例",
  $root: "根组件Vue对象的实例",
  $children: "当前实例的直接子组件",
  $slots: "访问被slot分发的内容",
  $scopedSlots: "访问scoped slots",
  $refs: "包含所有拥有ref注册的子组件",
  $isServer: "判断Vue实例是否运行于服务器",
  $attrs: "包含父作用域中非props的属性绑定",
  $listeners: "包含了父作用域中的v-on事件监听器",
  // 数据
  $watch: "观察Vue实例变化的表达式、计算属性函数",
  $set: "全局Vue.set的别名",
  $delete: "全局Vue.delete的别名",
  // 事件
  $on: "监听当前实例上的自定义事件，事件可以由vm.$emit触发",
  $once: "监听一个自定义事件，触发一次之后就移除监听器",
  $off: "移除自定义事件监听器",
  $emit: "触发当前实例上的事件",
  // 生命周期
  $mount: "手动地挂载一个没有挂载的Vue实例",
  $forceUpdate: "强制Vue实例重新渲染，仅影响实例本身和插入插槽内容的子组件",
  $nextTick: "将回调延迟到下次DOM更新循环之后执行",
  $destroy: "完全销毁一个实例",
}
 -->
<!-- <html
  v-text = "更新元素的textContent"
  v-html = "更新元素的innerHTML"
  v-show = "根据表达式的true/false，切换HTML元素的display属性"
  v-for = "遍历内部的HTML元素"
  v-pre = "跳过表达式渲染过程，可以显示原始的Mustache标签"
  v-cloak = "保持在HTML元素上直到关联实例结束编译，可以隐藏未编译的Mustache"
  v-once = "只渲染元素和组件一次"
></html>
<!-- 根据表达式的true和false来决定是否渲染元素 -->
<!-- <div v-if="type === "A"">A</div>
<div v-else-if="type === "B"">B</div>
<div v-else-if="type === "C"">C</div>
<div v-else>Not A/B/C</div> -->
<!-- 动态地绑定属性或prop到表达式 -->
<!-- <p v-bind:attrOrProp
  .prop = "被用于绑定DOM属性"
  .camel = "将kebab-case特性名转换为camelCase"
  .sync = "语法糖，会扩展成一个更新父组件绑定值的v-on监听器"
></p> -->
<!-- 绑定事件监听器 -->
<!-- <button
  v-on:eventName
  .stop = "调用event.stopPropagation()"
  .prevent = "调用event.preventDefault()"
  .capture = "添加事件监听器时使用capture模式"
  .self = "当事件是从监听器绑定的元素本身触发时才触发回调" 
  .native = "监听组件根元素的原生事件"-
  .once = "只触发一次回调"
  .left = "点击鼠标左键触发"
  .right = "点击鼠标右键触发"
  .middle = "点击鼠标中键触发"
  .passive = "以{passive: true}模式添加监听器"
  .{keyCode | keyAlias} = "触发特定键触事件"
>
</button> -->
<!-- 表单控件的响应式绑定 -->
<!-- <input 
  v-model
  .lazy = "取代input监听change事件"
  .number = "输入字符串转为数字"
  .trim = "过滤输入的首尾空格" />  -->

