# HTML5 微数据

微数据是一种在网页中提供附加语义的标准化方式。

微数据允许我们定义自定义元素以及在网页中嵌入自定义属性。从较高的角度而言，微数组由一组名-值对组成。

这个分组被称作__条目__，每个名-值对就是一个__属性__。条目和属性使用普通元素表示。

## 示例

- 用 __itemscope__ 属性创建一个条目。
- 给条目添加一个属性，__itemprop__ 属性用于条目的后代。

这里有两个条目，其中每个条目都有一个 "name" 属性：

```html
<div itemscope>
 <p>My name is <span itemprop="name">Zara</span>.</p>
</div>

<div itemscope>
 <p>My name is <span itemprop="name">Nuha</span>.</p>
</div>
```

属性值通常是字符串，但是它可以是下列数据类型。

## 全局属性

微数据引入了五个全局属性，这些属性适用于在任意元素以及为数据提供上下文机制。

<table>
	<tbody>
		<tr>
			<th>
				属性
			</th>
			<th>
				描述
			</th>
		</tr>
		<tr>
			<td>
				itemscope
			</td>
			<td>
				用于创建一个条目。itemscope 属性是一个布尔值属性，说明页面上有微数据以及它从哪里开始。
			</td>
		</tr>
		<tr>
			<td>
				itemtype
			</td>
			<td>
				这个属性是一个有效的 URL，用于定义条目以及为属性提供上下文。
			</td>
		</tr>
		<tr>
			<td>
				itemid
			</td>
			<td>
				这个属性是条目的全局标识符。
			</td>
		</tr>
		<tr>
			<td>
				itemprop
			</td>
			<td>
				这个属性为条目定义属性。
			</td>
		</tr>
		<tr>
			<td>
				itemref
			</td>
			<td>
				这个属性提供了一个附加元素列表来抓取条目的名-值对。
			</td>
		</tr>
	</tbody>
</table>

## 属性数据类型

属性通常有一个正如上面的例子中提到的字符串值，但是它们的值也可以是 URLs。下面的例子中有一个 "image" 属性，它的值是一个 URL：

```html
<div itemscope>
	<img itemprop="image" src="tp-logo.gif" alt="TutorialsPoint">
</div>
```

属性的值也可以是日期，时间或者日期和时间。下面是一个使用 __time__ 元素和 __datetime__ 属性的实现。

```html
<div itemscope>
My birthday is:
<time itemprop="birthday" datetime="1971-05-08">
   Aug 5th 1971
</time>
</div>
```

属性本身也可以是一组名-值对，通过在元素上放置 itemscope 属性来声明属性。

## 微数据 API 支持

如果浏览器支持 HTML5 微数据 API，那么全局 document 对象上就会有一个 getItems() 函数。如果浏览器不支持微数据，getItems() 函数就会是 undefined。

```javascript
function supports_microdata_api() {
  return !!document.getItems;
}
```

Modernizr 还不支持微数据 API 检测，因此我们需要使用像上面一样列出的函数来检测。

HTML5 微数据标准包含 HTML 标记（主要用于搜索引擎）和一系列 DOM 函数（主要用于浏览器）。

我们可以在网页中引入微数据标记，不理解微数据属性的搜索引擎将会忽略它们。但是，如果需要通过 DOM 访问或者操作微数据，我们还需要检查浏览器是否支持微数据 DOM API。

## 定义微数据词汇表

要定义一个微数据词汇表我们需要一个只想有效网页的命名空间 URL。例如 http://data-vocabulary.org/Person 可以用作带下列命名属性的个人微数据词汇表的命名空间。

- __name__ - 人名，简单的字符串值。
- __Photo__ - 指向人物照片的 URL。
- __URL__ - 属于个人的网站。

下面是一个使用个人微数据相关属性的例子：

```html
<section itemscope itemtype="http://data-vocabulary.org/Person">
<h1 itemprop="name">Andy Runie</h1>
<p>
<img itemprop="photo" src="http://www.example.com/photo.jpg">
</p>
<a itemprop="url" href="http://www.example.com/blog">My Blog</a>
</section>
```

Google 支持将微数据作为他们 Rich Snippets 程序的一部分。当 Google 的网页爬虫解析我们的页面并发现符合 http://data-vocabulary.org/Person 词汇表的微数据属性时，它会解析出这些属性并把他们存储到其他页面数据的旁边。

你可以利用 [Rich Snippets 测试工具](http://www.google.com/webmasters/tools/richsnippets) 使用 http://www.tutorialspoint.com/html5/microdata.htm 测试上面的例子。

对于微数据的进一步发展可以参考 [HTML5 Microdata](http://www.w3.org/TR/html5/microdata.html)。