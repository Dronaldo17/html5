# HTML5 表单 2.0

Web 表单 2.0 就是 HTML4 表单特性的一个扩展。HTML5 中的表单元素和属性相比 HTML4 提供了更大程度的语义标记，移除了大量 HTML4 中需要的繁琐脚本和样式。

## HTML4 中的 &lt;input&gt; 元素

HTML4 输入框元素使用 __type__ 属性指定数据类型。HTML4 提供了下列类型：

<table>
	<tbody>
		<tr>
			<th>
				类型
			</th>
			<th>
				描述
			</th>
		</tr>
		<tr>
			<td>
				text
			</td>
			<td>
				自由形式的文本字段，名义上没有换行符。
			</td>
		</tr>
		<tr>
			<td>
				password
			</td>
			<td>
				用于敏感信息的自由形式的文本字段，名义上没有换行符。
			</td>
		</tr>
		<tr>
			<td>
				checkbox
			</td>
			<td>
				预定义列表中的一组零个或多个值。
			</td>
		</tr>
		<tr>
			<td>
				radio
			</td>
			<td>
				一个枚举值。
			</td>
		</tr>
		<tr>
			<td>
				submit
			</td>
			<td>
				一个自由形式的启动表单的按钮。
			</td>
		</tr>
		<tr>
			<td>
				file
			</td>
			<td>
				带有 MIME 类型的任意文件以及可选的文件名。
			</td>
		</tr>
		<tr>
			<td>
				image
			</td>
			<td>
				一个坐标，相对于特定图片的尺寸，额外的语义是它必须是最后选中的值，同时启动表单提交。
			</td>
		</tr>
		<tr>
			<td>
				hidden
			</td>
			<td>
				默认不显示给用户的任意字符串。
			</td>
		</tr>
		<tr>
			<td>
				select
			</td>
			<td>
				枚举值，类似 radio 类型。
			</td>
		</tr>
		<tr>
			<td>
				textarea
			</td>
			<td>
				自由形式的文本字段，名义上没有换行的限制。
			</td>
		</tr>
		<tr>
			<td>
				button
			</td>
			<td>
				自由形式的按钮，可以启动按钮相关的任何事件。
			</td>
		</tr>
	</tbody>
</table>

下面是一个使用标注标签，单选按钮以及提交按钮的简单示例：

```html
...
<form action="http://example.com/cgiscript.pl" method="post">
    <p>
    <label for="firstname">first name: </label>
              <input type="text" id="firstname"><br />
    <label for="lastname">last name: </label>
              <input type="text" id="lastname"><br />
    <label for="email">email: </label>
              <input type="text" id="email"><br>
    <input type="radio" name="sex" value="male"> Male<br>
    <input type="radio" name="sex" value="female"> Female<br>
    <input type="submit" value="send"> <input type="reset">
    </p>
 </form>
 ...
 ```

## HTML5 中的 &lt;input&gt; 元素

 除了上面提到的属性，HTML5 给输入框元素的 __type__ 属性引入了几个新值。如下表所列。

 __注意：__ 请使用最新版的 __Opera__ 浏览器运行下面所有例子。

<table>
	<tbody>
		<tr>
			<th>
				类型
			</th>
			<th>
				描述
			</th>
		</tr>
		<tr>
			<td>
				<a href="http://www.tutorialspoint.com/cgi-bin/practice.cgi?file=html5-1.htm" target="_blank">
					datetime
				</a>
			</td>
			<td>
				按照 ISO 8601 编码，时区设置为 UTC 的日期和时间（包括年，月，日，时，分，秒，分秒）。
			</td>
		</tr>
		<tr>
			<td>
				<a href="http://www.tutorialspoint.com/cgi-bin/practice.cgi?file=html5-2.htm" target="_blank">
					datetime-local
				</a>
			</td>
			<td>
				按照 ISO 8601 编码的日期和时间（包括年，月，日，时，分，秒，分秒），不带时区信息。
			</td>
		</tr>
		<tr>
			<td>
				<a href="http://www.tutorialspoint.com/cgi-bin/practice.cgi?file=html5-3.htm" target="_blank">
					date
				</a>
			</td>
			<td>
				按照 ISO 8601 编码的日期（包括年，月，日）。
			</td>
		</tr>
		<tr>
			<td>
				<a href="http://www.tutorialspoint.com/cgi-bin/practice.cgi?file=html5-4.htm" target="_blank">
					month
				</a>
			</td>
			<td>
				由 ISO 8601 编码的年和月组成的日期。
			</td>
		</tr>
		<tr>
			<td>
				<a href="http://www.tutorialspoint.com/cgi-bin/practice.cgi?file=html5-5.htm" target="_blank">
					week
				</a>
			</td>
			<td>
				由 ISO 8601 编码的年和星期数组成的日期。
			</td>
		</tr>
		<tr>
			<td>
				<a href="http://www.tutorialspoint.com/cgi-bin/practice.cgi?file=html5-6.htm" target="_blank">
					time
				</a>
			</td>
			<td>
				按照 ISO 8601 编码时间（包括时，分，秒，和分秒）。
			</td>
		</tr>
		<tr>
			<td>
				<a href="http://www.tutorialspoint.com/cgi-bin/practice.cgi?file=html5-7.htm" target="_blank">
					number
				</a>
			</td>
			<td>
				只接受数值。step 属性可以指定精度，默认为1。
			</td>
		</tr>
		<tr>
			<td>
				<a href="http://www.tutorialspoint.com/cgi-bin/practice.cgi?file=html5-8.htm" target="_blank">
					range
				</a>
			</td>
			<td>
				range 类型适用于应该包含某个范围内数值的输入字段。
			</td>
		</tr>
		<tr>
			<td>
				<a href="http://www.tutorialspoint.com/cgi-bin/practice.cgi?file=html5-9.htm" target="_blank">
					email
				</a>
			</td>
			<td>
				只接受邮箱值。这个类型适用于应该包含一个邮箱地址的输入字段。如果尝试提交一个简单的文本，它会强制要求输入 email@example.com 格式的邮箱地址。
			</td>
		</tr>
		<tr>
			<td>
				<a href="http://www.tutorialspoint.com/cgi-bin/practice.cgi?file=html5-10.htm" target="_blank">
					url
				</a>
			</td>
			<td>
				只接受 URL 值。这个类型适用于应该包含一个 URL 地址的输入字段。如果尝试提交一个简单的文本，它会强制要求输入 http://www.example.com 或者 http://example.com 格式的 URL 地址。
			</td>
		</tr>
	</tbody>
</table>

## &lt;output&gt; 元素

HTML5 还引入了一个新元素 &lt;output&gt;，用来表示不同类型的输出结果，比如输出由脚本所写。

还可以用 __for__ 属性指定输出元素和文档中影响计算的其他元素之间的关系（比如，作为输入源或者参数）。for 属性的值是一个由空格分隔的其他元素的 IDs 列表。

便于学习这一概念 - 请进行[在线练习](http://www.tutorialspoint.com/cgi-bin/practice.cgi?file=html5-11.htm)。

## placeholder 属性

HTML5 引入了一个叫做 __palceholder__ 的新属性。这个属性在 &lt;input&gt; 和 &lt;textarea&gt; 元素上为用户提供了在这个字段可以输入什么的提示。占位符字符不能包含回车符或者换行符。

下面是 placeholder 属性的简单语法：

```html
<input type="text" name="search" placeholder="search the web"/>
```

这个属性只有最新版的 Mozilla，Safari 以及 Chrome 浏览器支持。

便于学习这一概念 - 请进行[在线练习](http://www.tutorialspoint.com/cgi-bin/practice.cgi?file=html5-56.htm)。

## required 属性

现在，我们不需要使用 JavaScript 处理诸如空文本框永远不能被提交的这类客户端验证了，因为 HTML5 引入了一个叫做 __required__ 的新属性，可以按照如下方式使用，它会保证输入框有值：

```html
<input type="text" name="search" required/>
```

这个属性只有最新版的 Mozilla，Safari 以及 Chrome 浏览器支持。

便于学习这一概念 - 请进行[在线练习](http://www.tutorialspoint.com/cgi-bin/practice.cgi?file=html5-57.htm)。