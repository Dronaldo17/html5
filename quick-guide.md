# HTML5 快速指南

HTML5 是 HTML 标准的下一个重要版本，用于接替 HTML 4.01，XHTML 1.0 和 XHTML 1.1。HTML5 也是一种在万维网上构建和呈现内容的标准。

最新版的 Apple Safari，Google Chrome，Mozilla FireFox 和 Opera 支持大部分 HTML 5 特性，IE 9.0 也支持一些 HTML5 功能。

## 新特性

HTML5 引入了许多新元素和属性帮助我们构建现代化的网站。下面是 HTML5 引入的主要特性：

- __新的语义化元素：__ 比如 &lt;header&gt;，&lt;footer&gt; 和 &lt;section&gt;。

- [表单 2.0](forms.md)：改进了 HTML Web 表单，给 &lt;input&gt; 标签引入了一些新的属性。

- [持久化本地存储](storage.md)：为了不使用第三方插件实现、

- [WebSocket](websocket.md)：用于 Web 应用程序的下一代双向通信技术。

- [服务器推送事件](sse.md)：HTML5 引入了从 Web 服务器到 Web 浏览器的事件，也被称作服务器推送事件（SSE）。

- [Canvas](canvas.md)：支持用 JavaScript 以编程的方式进行二维绘图。

- [音频和视频](audio-video.md)：在网页中嵌入音频或视频而无需借助第三方插件。

- [地理定位](geolocation.md)：用户可以选择与我们的网页共享他们的地理位置。

- [Microdata](microdata.md)：允许我们创建 HTML5 之外的自定义词汇表，以及使用自定义语义扩展网页。

- [拖放](drag-drop.md)：把同一网页上的条目从一个位置拖放到另一个位置。

## HTML5 语法

HTML5 有“自己的” HTML 语法，它与已经发布在网络上的 HTML 4 以及 XHTML1 文档兼容，但是不兼 HTML 4 中更复杂的 SGML 特性。

HTML5 并没有 XHTML 中需要小写标签名，属性要带引号，属性必须有一个值以及必须闭合所有空元素的语法规则。

但是 HTML5 更具灵活性，支持下列形式：

- 标签名大写。
- 属性的双引号可选。
- 属性值可选。
- 闭合空元素可选。

## DOCTYPE

在老版本的 HTML 中，DOCTYPE 很长，因为 HTML 语言是基于 SGML 的，需要引用一个 DTD。

HTML5 作者可以使用简单的语法来指定如下形式的 DOCTYPE：

```html
<!DOCTYPE html>
```

上述语法不区分大小写。

## 字符编码

HTML5 作者可以使用如下所示的简单语法指定字符编码：

```html
<meta charset="UTF-8">
```

上述语法不区分大小写。

## HTML5 元素

HTML5 元素使用起始标签和结束标签标记。标签使用尖括号之间的标签名限定。

起始标签和结束标签的区别在于后者标签名前面包含一个斜杠。

下面是一个 HTML5 元素示例：

```html
<p>...</p>
```

HTML5 标签名不区分大小写，可以全部大写或者混合使用，虽然最常见的约定是始终使用小写。

大多数元素都包含一些内容，比如 &lt;p&gt;...&lt;/p&gt; 包含一个段落。但是，有些元素不能包含任意内容，它们被称作空白元素。比如，br，hr，link 和 meta 等等。

这里有一个完整的 [HTML5 元素](tags-reference.md)列表。

## HTML5 属性

元素可以包含属性（attributes），用来给一个元素设置各种属性（properties）。

有些属性被定义为全局的，可以用在任何元素上，而其他的被定义为元素特有的。所有的属性都有一个名称和一个值，看起来如下面的示例所示。

下面是一个使用 HTML5 属性的例子，演示了如何用名为 class 的属性和值 “example” 标记一个 div 元素：

```html
<div class="example">...</div>
```

属性只能在起始标签中指定，绝对不能用在结束标签中。

HTML5 属性不区分大小写，可以全部大写或者混合使用，尽管最常见的约定是始终使用小写。

这里有一个完整的 [HTML5 属性](attributes.md)列表。

## HTML5 事件

当用户访问我们的网站时，他们会点击文本，图片，链接，将鼠标悬停在某些东西上面等等。这些都是 JavaScript 调用事件的例子。

我们可以在 JavaScript 或者 vbscript 中编写事件处理程序，然后把这些事件处理程序指定为事件标签属性的值。下面列出了 HTML5 规范定义的各种事件属性。

当任意事件发生在 HTML5 元素上时，下列属性可以用来触发任何作为值提供的 __JavaScript__ 和 __vbscript__ 代码。

这里有一个完整的 [HTML5 事件](events.md)列表。

## HTML5 文档

为了得到更好的结构，引入了下面的标签：

- __section：__ 这个标签表示一个通用的文档或者应用程序节。它可以和 h1-h6 一起使用来表示文档结构。

- __article：__ 这个标签表示文档内容的一个独立块，比如博客条目或者报纸上的文章。

- __aside：__ 这个标签表示与页面其他部分略微相关的内容块。

- __header：__ 这个标签表示一个节的头部。

- __footer：__ 这个标签表示一个节的脚注，可以包含作者，版权等信息。

- __nav：__ 这个标签表示用于导航文档的节。

- __dialog：__ 这个标签可以用于标记会话。

- __figure：__ 这个标签可以用于关联标题和某些嵌入内容，比如图表和视频。

一个 HTML5 文档的标记看起来就像下面这样：

```html
<!DOCTYPE html>
<html>
<head>
   <meta charset="utf-8">
   <title>...</title>
</head>
<body>
  <header>...</header>
  <nav>...</nav>
  <article>
    <section>
      ...
    </section>
  </article>
  <aside>...</aside>
  <footer>...</footer>
</body>
```

便于学习这一概念 - 可以进行[在线练习](http://www.tutorialspoint.com/cgi-bin/practice.cgi?file=html5_document_syntax)。

我知道你不会满足于这个快速指南，因此我建议你探索完整的 HTML5 教程，因为它在 HTML4 版本的基础上有巨大的变化，这并不能在简短的随笔中覆盖。