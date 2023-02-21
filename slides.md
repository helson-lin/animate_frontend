---
theme: seriph
background: https://pic.kblue.site/%2FiTab-acETWH6lHtU.jpg
class: text-center
highlighter: shiki
lineNumbers: true
info: |
  ## Slidev Starter Template
  FrontEnd Animation

  Learn more at [Sli.dev](https://sli.dev)
drawings:
  persist: false
css: unocss
title: 前端动画
---

# 前端动画
<div  v-motion-roll-visible-once-left
  :initial="{ x: -12000, y: 100, rotateZ: -90}"
  :enter="{ x: 0, y:0, rotateZ: 0 ,transition: {
      delay: 1000,
    } }">FrontEnd Animation (JS/CSS)</div>

<!--
admin
123123123
-->

---

# 动画类型

常见的动画类型：普通的交互动画; 纯动画

- 按钮动效（点击按钮之后执行一些动画效果，转变按钮的状态）
- 数据加载动效（懒加载loading效果）
- 组件切换动效（轮播切换）
- 文字动效（文字渐显）
- 纯动画（404页面动画）
<br>
<br>

<!-- Read more about [Why Slidev?](https://sli.dev/guide/why) -->

<!--
You can have `style` tag in markdown to override the style for the current page.
Learn more: https://sli.dev/guide/syntax#embedded-styles
-->
<style>
.slidev-layout {
  background-image: "#fff"
}
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

# 实现动画的方式

|     |     |
| --- | --- |
| <kbd>canvas</kbd> | 可以实现2D和3D动画 |
| <kbd>css</kbd> | 使用css的animation属性来实现动画(可以实现简单的对真实性要求不高的3d动画) |
| <kbd>js</kbd> | 使用js操作DOM的样式 （2D/3D）本质和css是一样的 |
| <kbd>WEBGL</kbd> | threeJS/thingJs |

<!-- https://sli.dev/guide/animations.html#click-animations -->

---
layout: image-right
image: https://pic.kblue.site/%2FiTab-gaOltmMTDHM.jpg
---

# 常用的动画库

- [Animate.css](https://animate.style/)
- [Magic.css](https://www.minimamente.com/project/magic/): 提供了一些高频动效
- [Anime.js](https://www.animejs.cn/): 一个轻量的JavaScript 动画库， 拥有简单而强大的API。可对 CSS 属性、 SVG、 DOM 和JavaScript 对象进行动画
- [Mo.js](https://mojs.github.io/): 一个"简洁、高效"图形动画库, 可以实现复杂的动画效果 (SVG动画)
- [lottie](http://airbnb.io/lottie/#/README) 库平台支持的动画库，AE导出`json`, 前端直接加载`json`即可

---


# 3D BOX

如何使用css实现一个3D盒子

<img style="width: 400px; height: 200px;margin-top:40px;" src="/imgs/动画.gif"/>
---

# 3维坐标轴

<div grid="~ cols-2 gap-4">
<img style="width: 300px;margin-top:40px;" src="/imgs/Snipaste_2022-08-08_16-43-36.png"/>
<div>

在了解透视之前，首先要先了解坐标轴。3D变形与2D变形最大的不同就在于其参考的坐标轴不同。2D变形的坐标轴是平面的，只存在x轴和y轴，而3D变形的坐标轴则是x、y、z三条轴组成的立体空间，x轴正向、y轴正向、z轴正向分别朝向<strong style="color:#fa7d35"><i>右、下和屏幕外</i></strong>
</div>
</div>

<div
  v-motion
  :initial="{ x:35, y: 40, opacity: 0}"
  :enter="{ y: 0, opacity: 1, transition: { delay: 3500 } }">

[Learn More](https://www.cnblogs.com/xiaohuochai/p/5351477.html)

</div>

---


# translate rotate

3D转换常用的属性: translate rotate

<br>

<Perspective/>

<br>

[Learn more](https://sli.dev/guide/syntax#latex)

---

# transform-style 和  preserve

<div grid="~ cols-2 gap-4">
<div>

[`transform-style`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/transform-style)属性: 设置元素的子元素是位于 3D 空间中(preserve-3d)还是平面中(flat); 默认值: `flat`

由于这个属性不会被继承，因此必须为元素的所有非叶子子元素设置它

`perspective`属性：指定观察者距离 z=0 平面的距离，为元素及其内容应用透视变换。当值为 0 或负值时，无透视变换。（属性不会被继承）

</div>
<div>

<!-- ./components/Demo.vue -->
<Demo :zPx="-1800" :threeD="true" />
</div>
</div>
---

# 3D BOX

animation配置keyframes可以实现基本动画效果，结合transform-style: preserve-3d;可以实现3D效果动画

3D盒子代码实现：
<iframe height="300" style="width: 100%;" scrolling="no" title="Untitled" src="https://codepen.io/helson-lin/embed/dyJrRbo?default-tab=css%2Cresult&editable=true" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/helson-lin/pen/dyJrRbo">
  Untitled</a> by helson-lin (<a href="https://codepen.io/helson-lin">@helson-lin</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

<arrow v-click="3" x1="440" y1="460" x2="320" y2="370" color="#fa9739" width="3" arrowSize="1" />

<style>
.footnotes-sep {
  @apply mt-20 opacity-10;
}
.footnotes {
  @apply text-sm opacity-75;
}
.footnote-backref {
  display: none;
}
</style>

---


# Anime

anime.js 可以和CSS3 属性，SVG，DOM 元素和JS 对象一起工作，制作出各种高性能，平滑过渡的动画效果。
animejs 实现交互动效
<div grid="~ cols-2 gap-4">
<div>
```js
anime({
		targets: "#lop",
		fill: ["#eee", "#ffa214"],
		translateY: ["0", "-90px", "0"],
		scale: [1, 0.8, 1],
		duration: 800,
		easing: "easeInOutQuad",
	});
	anime({
		targets: ".home",
		scale: [1, 0.8, 1],
		fill: ["#ffa214", "#eee"],
		duration: 800,
		easing: "easeInOutQuad",
	});
  //`#lop`为中间的小方块; `#home`为整个大房子
```
</div>
<div>
<Anime/>
<Walk/>
</div>
</div>

[Learn More](https://www.animejs.cn/documentation/#propertyKeyframes)

---
---

# CSS3D

<Hourse/>


---
---
# 参考文章和工具

- [AnimeJs官网](https://www.animejs.cn/)
- [MoJs官网](https://mojs.github.io/tutorials/shape-swirl/#use-cases)
- [lottie](http://airbnb.io/lottie/#/web?id=troubleshooting)
- [Magic Effects](https://www.minimamente.com/project/magic/)
- [深入理解Css变形Tranform(3d)](https://www.cnblogs.com/xiaohuochai/p/5351477.html)
- [Intro to CSS 3D transforms](https://3dtransforms.desandro.com/perspective)
- [CodePen](https://codepen.io/your-work)
- [Slidev](https://cn.sli.dev/)
