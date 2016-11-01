# 第一个polymer

### 什么是polymer

Ploymer 是 web component native化的规范的项目代码

它的核心类库存放在webcomponentsjs

> google自家的chrome就以原生支持web component规范

> 其它浏览器却不能work,一定要引入Polyfills(webcomponents-lite.js)


### 生命周期

`polymer`  6大生命周期

1. created
        当组件被 new 时调用，最早被触发，此时还不能访问组件的属性
2. ready
        当组件内部依赖的子组件或者原生dom组件加载成功，会调用ready
3. factoryImpl
        只有使用new ElementClass()方式创建组件时会被调用，发生在ready后
4. attached
        组件被添加到父组件中（显示在舞台）时触发，只会触发一次
5. attributedChanged
        组件被父组件设置属性时触发，只有使用setAttribute()方式设置属性才会触发，切记！（elementInstance.attr = xxx, <my-element att="xxx"></my-element>都不会触发它）
6. detached
        当被父组件removeChild时候触发

### 消息机制

1. 父子通讯
        父 -> 子   设置子的公共属性
        子 -> 父    子触发时间，父监听事件，父捕获倒子发出的事件后再做后续处理

2. 兄弟通讯
        兄 -> 父    跟父子通讯一样，先通过事件把需求提交给父
        父 -> 弟    父拿到兄的需求后， 统一调度，通过设属性的方式来访问弟

3. 爷孙通讯
        参照父子通讯， 一层层向上传递事件，再一层层向下设置属性，世纪开发时尽量将组件的接口都设计合理避免跨n级通讯的尴尬场面

4. 远亲通讯
        使用前端消息总线（如单例的消息总线类）


### style

在`<dom-module>`标签中使用`<style>`标签定义组件内部样式

动态设置自定义css属性就需要`updateStyles()`

[参考](https://segmentfault.com/a/1190000003834899)
