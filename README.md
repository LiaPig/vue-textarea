# vue-textarea

> A Vue Demo that can change the height of the textarea according to the content.

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).

如图所示，当`textarea`里的内容超过一行后，会出现滚动条并隐藏前一行的内容，特别是在移动端使用到textarea多行文本输入的话，这样显示其实是很不友好的。所以要做一个可根据内容改变高度的textarea的组件。

![](https://upload-images.jianshu.io/upload_images/7016617-d411168fc0306f32.gif?imageMogr2/auto-orient/strip)


### 踩坑尝试

利用`rows`属性来改变高度：

![W3C HTML <textarea> 标签](https://upload-images.jianshu.io/upload_images/7016617-4d7fe23427edee5e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

踩坑时的思路：

+ 给`textarea`加上`rows`属性，并双向绑定在`data`的`rows`上。(`<textarea ref="textarea" :rows="rows" v-model="value" class="textarea" ></textarea>`)；
+ 获取初始页面时候`textarea`的高度，这就是一行的高度`oneHeight`；
+ 通过`vue`的`watch`数据监听，当`textarea`的内容发生变化时触发，获取`textarea`的`scrollHeight`，再除以`oneHeight`求整数然后加一就是`rows`的数量。


踩坑感想：

这样做是可以实现当内容变多，行数跟着变多的情况的，但是，当内容变少，`scrollHeight`是不会减少的！所以`rows`也不会变，一旦被撑大，就再也缩不回去。。。。显然，这不是我想要的效果。


### 正确姿势

猛然回想起ElementUI上就有可根据内容调整高度的组件[ElementUI input](https://element.eleme.cn/#/zh-CN/component/input)！

然后就去扒源码看看是怎么实现的，结果都已经封装好了，太棒了，直接下载来引用就行了！

饿了么组件的源码github地址：

[https://github.com/ElemeFE/element/blob/dev/packages/input/src/calcTextareaHeight.js](https://github.com/ElemeFE/element/blob/dev/packages/input/src/calcTextareaHeight.js)


![无论是单个输入或删减，还是一段输入或删减，都能立刻自适应改变高度](https://upload-images.jianshu.io/upload_images/7016617-a2441f7af6e7abd8.gif?imageMogr2/auto-orient/strip)


