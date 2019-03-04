# Dom-Event
通过 HTML DOM，可访问 JavaScript HTML 文档的所有元素。

## 什么是-DOM
`HTML DOM` (文档对象模型)，当页面在加载的时候，浏览器会创建页面的 `文档对象模型` ，`文档对象模型` 被构造为对象的树。

`Javascript` 可以改变页面中任何 `html` 元素<br>
`Javascript` 可以改变页面中任何 `html` 属性<br>
`Javascript` 可以改变页面中任何 `css` 样式<br>
`Javascript` 可以改变页面中任何所有时间做出反应。

`文档对象` 是网页中所有对象的所有者，或者说是根。

>所以要访问页面中的对象的话，始终要访问 `document` 对象。

实例：
```copy
document.body.innerHTML = 'hello world';
```

>由于 `body` 是 `dom` 节点，所以我们可以访问 `document` 来修改 `body` 的属性 `innerHTML`

## 选择元素

通过 `id` 找元素：
```copy
document.getElementById(id);
```

通过 `class` 找元素：
```copy
document.getElementByClassName(name);
```

通过 `tag` 找元素：
```copy
<script>
document.getElementByTagName(tag);
</script>
```

实例：
```copy
<script>
document.getElementById('demo');
document.getElementsByClass('demo');
document.getElementsByTagName('div');
</script>
```

## 改变属性
!>回顾一下，只有对象才有方法和属性。

通过选择元素后，我们可以改变该元素的属性。

改变 `img` 的 `src` 属性实例：
```copy
<img src="https://vuejs.org/images/logo.png" />;

<script>
var dom = document.getElementsByTagName('img');
dom.src = 'https://developer.mozilla.org/static/img/web-docs-sprite.22a6a085cf14.svg';
</script>
```

改变 `a` 链接的 `href` 属性实例：
```copy
<a href="https://www.baidu.com/"></a>

<script>
var dom = document.getElementsByTagName('a');
dom.src = 'https://www.taobao.com/'；
</script>
```

改变 `div` 链接的 `style` 属性实例：
```copy
var dom = document.getElementsByTagName('div');
dom.style.backgroundColor = '#000';
```

!>你不能在属性中使用 `-` 符号，需要以大驼峰的写法（复合词的字母需要大写），比如说 `backgroundColor`。

## 添加-移除-替换元素

#### 添加元素
`dom.cloneNode()`：克隆元素并返回结果节点。<Br>
`document.createElement(element)`：创建一个新的元素。<Br>
`document.createTextNode(text)`：创建一个新的文本节点。<Br>

```copy
<script>
document.createElement('div');
document.createTextNod('hello world');
</script>
```

!>是不是很奇怪我们并没有在文档中找到以上方法创建的元素。<br>
当你用 `document.createTextNode(text)` 的时候，它不会出现在文档中，你必须添加来放到文档中。

```copy
<script>
var dom = document.getElementsByTagName('div')[0];
var domClone = dom.cloneNode();
document.body.append(domClone);
</script>
```

!>`cloneNode()` 和 `cloneNode(true)` 是不一样的。<br>
`cloneNode()` 并不是 `深度` 复制，它只是复制这个对应的节点，而不会复制子节点。<br>
`cloneNode(true)` 是 `深度` 复制，它复制的是对应的节点已经该节点下面的所有子节点。

```copy
<script>
var dom = document.createTextNode('hello wold');
document.body.append(dom);      //直接放入到 `body` 中
document.getElementsById('content').appendChild(dom)      //直接放入到 `content` id中的最末尾
document.getElementsById('content').insertBefore(dom,node)      //直接放入到 `content` id中,并且放在 `node` 节点前面。
</script>
```

#### 移除元素
`dom.removeChild(node)`：父级节点移除子级节点

要删除元素，你必须先找到该元素的父级元素，再通过父级元素使用 `removeChild(node)` 的方法来删除该元素。

>我们可以使用 `node.parentNode` 属性来找到该元素的父级元素。

删除 `p` 元素实例：
```copy
<script>
var dom = document.getElementsTagName('p')[0];
dom.parentNode.removeChild(dom);
</script>
```

#### 替换元素
`dom.replaceChild(newNode,oldNode)`：父级元素替换新的子级元素。

把 `p` 节点替换成 `div` 节点实例：
```copy
var oldNode = document.getElementsByTagName('p')[0];
var newNode = document.getElementsByTagName('div')[0];
var dom = oldNode.parentNode;
dom.replaceChild(newNode,oldNode);
```

