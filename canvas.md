# HTML5 画布

HTML5 &lt;canvas&gt; 元素为我们使用 JavaScript 绘制图形提供了一种简单而又强大的方式。它可以用来绘制图表，制作摄影作品或者做一些简单（以及复杂）的动画。

这里有一个简单的 &lt;canvas&gt; 元素，除了所有核心的 HTML5 属性，比如 id，name 和 class 等等之外，它只有两个特定的属性 __width__ 和 __height__。

```html
<canvas id="mycanvas" width="100" height="100"></canvas>
```

使用 _getElementById()__ 方法很容易找到这个 &lt;canvas&gt; 元素，如下所示：

```javascript
var canvas  = document.getElementById("mycanvas");
```

我们来看一个在 HTML5 文档中使用 &lt;canvas&gt; 元素的简单示例。

```html
<!DOCTYPE HTML>
<html>
<head>
<style>
#mycanvas{
   border:1px solid red;
}
</style>
</head>
<body>
   <canvas id="mycanvas" width="100" height="100"></canvas>
</body>
</html>
```

便于学习上述概念 - 请使用最新版的 Safari 或者 Opera 进行[在线练习](http://www.tutorialspoint.com/cgi-bin/practice.cgi?file=html5-27.htm)。

## 渲染上下文

&lt;canvas&gt; 初始为空，要显示某物，脚本首先需要访问渲染上下文，然后再上面绘图。

canvas 元素有一个叫做 __getContext__ 的 DOM 方法，用于获得渲染上下文和它的绘图功能。这个函数接受一个参数，__2d__ 上下文类型。

下面的代码就是访问需要的上下文以及检测浏览器是否支持 &lt;canvas&gt; 元素：

```javascript
var canvas  = document.getElementById("mycanvas");
if (canvas.getContext){   
   var ctx = canvas.getContext('2d');   
   // drawing code here   
} else {   
   // canvas-unsupported code here 
}  
```

## 浏览器支持

最新版的 FireFox，Safari，Chrome 和 Opera 都支持 HTML5 Canvas，但是 IE8 不支持原生 Canvas。

我们可以使用 [ExplorerCanvas](http://code.google.com/p/explorercanvas/) 让 IE 浏览器支持 Canvas。只需按照如下方式引入这个脚本即可：

```html
<!--[if IE]><script src="excanvas.js"></script><![endif]-->
```

## HTML5 Canvas 示例

本教程涵盖下列 HTML5 &lt;canvas&gt; 元素相关的示例。

<table>
	<tbody>
		<tr>
			<th width="30%">
				示例
			</th>
			<th>
				描述
			</th>
		</tr>
		<tr>
			<td>
				<a href="http://www.tutorialspoint.com/html5/canvas_drawing_rectangles.htm" title="Drawing Rectangles">
					绘制矩形
				</a>
			</td>
			<td>
				<p>
					学习如何使用 HTML5 &lt;canvas&gt; 元素绘制矩形。
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<a href="http://www.tutorialspoint.com/html5/canvas_drawing_paths.htm" title="Drawing Paths">
					绘制路径
				</a>
			</td>
			<td>
				<p>
					学习如何在 HTML5 &lt;canvas&gt; 元素中使用路径创建形状。
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<a href="http://www.tutorialspoint.com/html5/canvas_drawing_lines.htm" title="Drawing Lines">
					绘制线条
				</a>
			</td>
			<td>
				<p>
					学习如何使用 HTML5 &lt;canvas&gt; 元素绘制线条。
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<a href="http://www.tutorialspoint.com/html5/canvas_drawing_bezier.htm" title="Drawing Bezier">
					绘制贝塞尔曲线
				</a>
			</td>
			<td>
				<p>
					学习如何使用 HTML5 &lt;canvas&gt; 元素绘制贝塞尔曲线。、
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<a href="http://www.tutorialspoint.com/html5/canvas_drawing_quadratic.htm" title="Drawing Quadratic">
					绘制二次曲线
				</a>
			</td>
			<td>
				<p>
					学习如何使用 HTML5 &lt;canvas&gt; 元素绘制二次曲线。
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<a href="http://www.tutorialspoint.com/html5/canvas_using_images.htm" title="Using images">
					使用图像
				</a>
			</td>
			<td>
				<p>
					学习如何在 HTML5 &lt;canvas&gt; 元素中使用图像。
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<a href="http://www.tutorialspoint.com/html5/canvas_create_gradients.htm" title="Create Gradients">
					创建渐变
				</a>
			</td>
			<td>
				<p>
					学习如何使用 HTML5 &lt;canvas&gt; 元素创建渐变。
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<a href="http://www.tutorialspoint.com/html5/canvas_styles_and_colors.htm" title="Styles and Colors">
					样式和颜色
				</a>
			</td>
			<td>
				<p>
					学习如何使用 HTML5 &lt;canvas&gt; 元素应用样式和颜色。
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<a href="http://www.tutorialspoint.com/html5/canvas_text_fonts.htm" title="Text and Fonts">
					文本和字体
				</a>
			</td>
			<td>
				<p>
					学习如何使用不同的字体和尺寸绘制神奇的文字。
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<a href="http://www.tutorialspoint.com/html5/canvas_pattern_shadow.htm" title="Pattern and Shadow">
					图案和投影
				</a>
			</td>
			<td>
				<p>
					学习如何绘制不同的图案和阴影。
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<a href="http://www.tutorialspoint.com/html5/canvas_states.htm" title="Canvas States">
					画布状态
				</a>
			</td>
			<td>
				<p>
					学习如何在画布上做复杂绘图时保存和恢复画布状态。
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<a href="http://www.tutorialspoint.com/html5/canvas_translation.htm" title="Canvas Translation">
					画布平移
				</a>
			</td>
			<td>
				<p>
					这个方法用于移动画布和它原点到网格上的不同点。
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<a href="http://www.tutorialspoint.com/html5/canvas_rotation.htm" title="Canvas Rotation">
					画布旋转
				</a>
			</td>
			<td>
				<p>
					这个方法用于围绕当前原点旋转画布。
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<a href="http://www.tutorialspoint.com/html5/canvas_scaling.htm" title="Canvas Scaling">
					画布缩放
				</a>
			</td>
			<td>
				<p>
					这个方法用于增大或者减小画布网格中的单位。
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<a href="http://www.tutorialspoint.com/html5/canvas_transform.htm" title="Canvas Transform">
					画布变换
				</a>
			</td>
			<td>
				<p>
					这个方法允许我们直接修改变换矩阵。
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<a href="http://www.tutorialspoint.com/html5/canvas_composition.htm" title="Canvas Composition">
					画布合成
				</a>
			</td>
			<td>
				<p>
					这个方法用于从画布上屏蔽某些区域或者清除某一部分。
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<a href="http://www.tutorialspoint.com/html5/canvas_animation.htm" title="Canvas Animation">
					Canvas 动画
				</a>
			</td>
			<td>
				<p>
					学习如何使用 HTML5 画布和 JavaScript 创建基本的动画。
				</p>
			</td>
		</tr>
	</tbody>
</table>