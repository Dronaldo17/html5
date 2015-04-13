# HTML5 Modernizr 教程

Modernizr 是一个很小的用来检测下一代 Web 技术原生实现可用性的 __JavaScript 库__。

HTML5 和 CSS3 都引入了各自的新特性，但是同时也有很多浏览器不支持这些新特性。

Modernizr 提供了一种简单的方式检测任意新特性，从而让我们可以采取相应的操作。比如，浏览器还不支持视频特性，那么我们可以显示一个简单的页面。

我们还可以基于某个特性的可用性来创建 CSS 规则，如果浏览器不支持某个新特性，那么这些规则将会自动应用到网页上。

可以从 [Modernizr 官网](http://www.modernizr.com/) 下载最新版的程序。

## 语法

开始使用 Modernizr 之前，需要在 HTML 页面的头部引入这个 JavaScript 库，如下所示：

```html
<script src="modernizr.min.js" type="text/javascript"></script>
```

正如上面提到的，我们可以基于特性的可用性来创建 CSS 规则，如果浏览器不支持这个新特性，那么这些规则就会自动应用到网页上。

下面是处理支持和不支持特性的一个简单语法：

```html
/* In your CSS: */
.no-audio #music {
   display: none; /* Don't show Audio options */
}
.audio #music button {
   /* Style the Play and Pause buttons nicely */
}

<!-- In your HTML: -->
<div id="music">
   <audio>
      <source src="audio.ogg" />
      <source src="audio.mp3" />
   </audio>
   <button id="play">Play</button>
   <button id="pause">Pause</button>
</div>
```

这里要注意的是，我们需要为想要处理的浏览器还不支持的特性或者属性使用 “no-” 前缀。

下面是通过 JavaScript 检测特定属性的语法：

```javascript
if (Modernizr.audio) {
     /* properties for browsers that
     support audio */
}else{
     /* properties for browsers that
     does not support audio */
}
```

便于学习上述概念 - 请使用不同的浏览器进行[在线练习](http://www.tutorialspoint.com/cgi-bin/practice.cgi?file=html5-55.htm)。

## Modernizr 提供的特性检测

下面是可以通过 Modernizr 进行检测的特性列表：

<table>
	<tbody>
		<tr>
			<th>
				特性
			</th>
			<th>
				CSS 属性
			</th>
			<th>
				JavaScript 检测
			</th>
		</tr>
		<tr>
			<td>
				@font-face
			</td>
			<td>
				.fontface
			</td>
			<td>
				Modernizr.fontface
			</td>
		</tr>
		<tr>
			<td>
				Canvas
			</td>
			<td>
				.canvas
			</td>
			<td>
				Modernizr.canvas
			</td>
		</tr>
		<tr>
			<td>
				Canvas Text
			</td>
			<td>
				.canvastext
			</td>
			<td>
				Modernizr.canvastext
			</td>
		</tr>
		<tr>
			<td>
				HTML5 Audio
			</td>
			<td>
				.audio
			</td>
			<td>
				Modernizr.audio
			</td>
		</tr>
		<tr>
			<td>
				HTML5 Audio formats
			</td>
			<td>
				NA
			</td>
			<td>
				Modernizr.audio[format]
			</td>
		</tr>
		<tr>
			<td>
				HTML5 Video
			</td>
			<td>
				.video
			</td>
			<td>
				Modernizr.video
			</td>
		</tr>
		<tr>
			<td>
				HTML5 Video Formats
			</td>
			<td>
				NA
			</td>
			<td>
				Modernizr.video[format]
			</td>
		</tr>
		<tr>
			<td>
				rgba()
			</td>
			<td>
				.rgba
			</td>
			<td>
				Modernizr.rgba
			</td>
		</tr>
		<tr>
			<td>
				hsla()
			</td>
			<td>
				.hsla
			</td>
			<td>
				Modernizr.hsla
			</td>
		</tr>
		<tr>
			<td>
				border-image
			</td>
			<td>
				.borderimage
			</td>
			<td>
				Modernizr.borderimage
			</td>
		</tr>
		<tr>
			<td>
				border-radius
			</td>
			<td>
				.borderradius
			</td>
			<td>
				Modernizr.borderradius
			</td>
		</tr>
		<tr>
			<td>
				box-shadow
			</td>
			<td>
				.boxshadow
			</td>
			<td>
				Modernizr.boxshadow
			</td>
		</tr>
		<tr>
			<td>
				Multiple backgrounds
			</td>
			<td>
				.multiplebgs
			</td>
			<td>
				Modernizr.multiplebgs
			</td>
		</tr>
		<tr>
			<td>
				opacity
			</td>
			<td>
				.opacity
			</td>
			<td>
				Modernizr.opacity
			</td>
		</tr>
		<tr>
			<td>
				CSS Animations
			</td>
			<td>
				.cssanimations
			</td>
			<td>
				Modernizr.cssanimations
			</td>
		</tr>
		<tr>
			<td>
				CSS Columns
			</td>
			<td>
				.csscolumns
			</td>
			<td>
				Modernizr.csscolumns
			</td>
		</tr>
		<tr>
			<td>
				CSS Gradients
			</td>
			<td>
				.cssgradients
			</td>
			<td>
				Modernizr.cssgradients
			</td>
		</tr>
		<tr>
			<td>
				CSS Reflections
			</td>
			<td>
				.cssreflections
			</td>
			<td>
				Modernizr.cssreflections
			</td>
		</tr>
		<tr>
			<td>
				CSS 2D Transforms
			</td>
			<td>
				.csstransforms
			</td>
			<td>
				Modernizr.csstransforms
			</td>
		</tr>
		<tr>
			<td>
				CSS 3D Transforms
			</td>
			<td>
				.csstransforms3d
			</td>
			<td>
				Modernizr.csstransforms3d
			</td>
		</tr>
		<tr>
			<td>
				CSS Transitions
			</td>
			<td>
				.csstransitions
			</td>
			<td>
				Modernizr.csstransitions
			</td>
		</tr>
		<tr>
			<td>
				Geolocation API
			</td>
			<td>
				.geolocation
			</td>
			<td>
				Modernizr.geolocation
			</td>
		</tr>
		<tr>
			<td>
				Input Types
			</td>
			<td>
				NA
			</td>
			<td>
				Modernizr.inputtypes[type]
			</td>
		</tr>
		<tr>
			<td>
				Input Attributes
			</td>
			<td>
				NA
			</td>
			<td>
				Modernizr.input[attribute]
			</td>
		</tr>
		<tr>
			<td>
				localStorage
			</td>
			<td>
				.localstorage
			</td>
			<td>
				Modernizr.localstorage
			</td>
		</tr>
		<tr>
			<td>
				sessionStorage
			</td>
			<td>
				.sessionstorage
			</td>
			<td>
				Modernizr.sessionstorage
			</td>
		</tr>
		<tr>
			<td>
				Web Workers
			</td>
			<td>
				.webworkers
			</td>
			<td>
				Modernizr.webworkers
			</td>
		</tr>
		<tr>
			<td>
				applicationCache
			</td>
			<td>
				.applicationcache
			</td>
			<td>
				Modernizr.applicationcache
			</td>
		</tr>
		<tr>
			<td>
				SVG
			</td>
			<td>
				.svg
			</td>
			<td>
				Modernizr.svg
			</td>
		</tr>
		<tr>
			<td>
				SVG Clip Paths
			</td>
			<td>
				.svgclippaths
			</td>
			<td>
				Modernizr.svgclippaths
			</td>
		</tr>
		<tr>
			<td>
				SMIL
			</td>
			<td>
				.smil
			</td>
			<td>
				Modernizr.smil
			</td>
		</tr>
		<tr>
			<td>
				Web SQL Database
			</td>
			<td>
				.websqldatabase
			</td>
			<td>
				Modernizr.websqldatabase
			</td>
		</tr>
		<tr>
			<td>
				IndexedDB
			</td>
			<td>
				.indexeddb
			</td>
			<td>
				Modernizr.indexeddb
			</td>
		</tr>
		<tr>
			<td>
				Web Sockets
			</td>
			<td>
				.websockets
			</td>
			<td>
				Modernizr.websockets
			</td>
		</tr>
		<tr>
			<td>
				Hashchange Event
			</td>
			<td>
				.hashchange
			</td>
			<td>
				Modernizr.hashchange
			</td>
		</tr>
		<tr>
			<td>
				History Management
			</td>
			<td>
				.historymanagement
			</td>
			<td>
				Modernizr.historymanagement
			</td>
		</tr>
		<tr>
			<td>
				Drag and Drop
			</td>
			<td>
				.draganddrop
			</td>
			<td>
				Modernizr.draganddrop
			</td>
		</tr>
		<tr>
			<td>
				Cross-window Messaging
			</td>
			<td>
				.crosswindowmessaging
			</td>
			<td>
				Modernizr.crosswindowmessaging
			</td>
		</tr>
		<tr>
			<td>
				addTest() Plugin API
			</td>
			<td>
				NA
			</td>
			<td>
				Modernizr.addTest(str,fn)
			</td>
		</tr>
	</tbody>
</table>