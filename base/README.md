# Threejs
`three.js`是 JavaScript 编写的 `WebGL` 第三方库。
* 使用 `Three.js` 不需要了解太多图形学知识，可以降低学习成本。
* 使用ThreeJS可以用更少的代码实现更多的内容，它屏蔽很多处理细节，提供更多组件，提高开发效率。
* ThreeJS有很高的易用性，但同时也不失灵活性。

`three.js` 最终它会以 `canvas` 的节点呈现在 `html` 上。

#### GibHub 地址

`Github` 里面有很多案例，大家可以去看一下。

[![](../img/threejs.svg)](https://github.com/josdirksen/learning-threejs)

!>学习这门语言，最好要有一点 `Javascript` 功底，对浏览器控制台有一定的认识，这样学起来才会更加容易上手，不那么吃力。<br>
必须要把底层的东西弄懂，弄明白，后面的进度才会比较顺。


## 起步
引入 `three.js`

```copy
<script type="text/javascript" src="js/three.js"></script>
```

## 基础的三大元素
在 `Three.js` 中必须要有三样东西，才可以将物体渲染到页面当中去。

* `scene 场景`：场景是一个容器，我们所要看到的，展示的东西都会存放在这个场景中。<br>
* `camera 相机`：相机让我们能够在渲染好的场景中看到内容。<br>
* `renderer 渲染器`：渲染器负责计算制定的相机角度下，场景呈现的效果。

#### scene 场景
`new THREE.Scene()` 这个函数对象本身没有太多的选项和方法。

#### camera 相机
`new THREE.PerspectiveCamera(fov, aspect, near, far)` 这个函数里面有4个参数。

* fov：可视角度；`可视角度越小看到的物体越大`
* aspect：`canvas` 的长宽比；
* near：近距离的值；`小于 near 的值的物体不会被渲染`
* far：远距离的值；`大于 far 的值的物体不会被渲染`

>`PerspectiveCamera` 是透视相机，`Three.js` 里还有其他的相机，后面我们会说到。这个相机一般参数设置是 `new THREE.PerspectiveCamera(75,window.innerWidth/window.innerHeight,.1,1000)` 

#### renderer 渲染器
`new THREE.WebGLRenderer()` 像素级的渲染。

一般渲染器的背景是黑色的，我们可以通过以下的方式改变渲染器的背景颜色。
```copy
renderer.setClearColor(0xffffff,1.0);       
renderer.setClearColor('rgb(255,255,255)',1.0);
renderer.setClearColor('rgba(255,255,255,1)',1.0);
renderer.setClearColor('#fff',1.0);
```
!>`0xffffff` 16进制的色值没有引号

## 立体几何图形
`Three.js` 里面的立体几何图形有：<br>
`BoxGeometry`：立方体<br>
`CylinderGeometry`：圆柱体<br>
`SphereGeometry`：球体<br>
`TorusGeometry`：圆环<br>