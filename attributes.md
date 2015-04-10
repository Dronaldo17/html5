# HTML5 属性

正如 HTML5 语法中所阐述的，元素可以包含属性（attributes）给一个元素设置各种属性（properties）。

有些属性被定义为全局的，可以用在任何元素上，而其他的被定义为元素特有的。所有的属性都有一个名称和一个值，看起来如下面的示例所示。

下面是一个使用 HTML5 属性的例子，演示了如何用名为 class 的属性和值 “example” 标记一个 div 元素：

```html
<div class="example">...</div>
```

属性只能在起始标签中指定，绝对不能用在结束标签中。

HTML5 属性不区分大小写，可以全部大写或者混合使用，尽管最常见的约定是始终使用小写。

## 标准属性

下面列出的属性几乎所有的 HTML5 标签都支持。

<table>
	<tbody>
		<tr>
			<td>
				<b>
					属性
				</b>
			</td>
			<td>
				<b>
					选项
				</b>
			</td>
			<td>
				<b>
					功能
				</b>
			</td>
		</tr>
		<tr>
			<td>
				accesskey
			</td>
			<td>
				用户自定义
			</td>
			<td>
				定义访问元素的键盘快捷键。
			</td>
		</tr>
		<tr>
			<td>
				align
			</td>
			<td>
				right, left, center
			</td>
			<td>
				水平对齐标签。
			</td>
		</tr>
		<tr>
			<td>
				background
			</td>
			<td>
				URL
			</td>
			<td>
				在元素后面设置一个背景图像。
			</td>
		</tr>
		<tr>
			<td>
				bgcolor
			</td>
			<td>
				数值，十六进制值，RGB值
			</td>
			<td>
				在元素后面设置一个背景颜色。
			</td>
		</tr>
		<tr>
			<td>
				class
			</td>
			<td>
				用户定义。
			</td>
			<td>
				分类一个元素，便于使用级联样式表。
			</td>
		</tr>
		<tr>
			<td>
				contenteditable
			</td>
			<td>
				true, false
			</td>
			<td>
				定义用户是否可以编辑元素的内容。
			</td>
		</tr>
		<tr>
			<td>
				contextmenu
			</td>
			<td>
				Menu id
			</td>
			<td>
				为元素定义上下文菜单。
			</td>
		</tr>
		<tr>
			<td>
				data-XXXX
			</td>
			<td>
				用户定义。
			</td>
			<td>
				自定义属性。 HTML 文档的作者可以定义自己的属性。
				自定义属性必须以 "data-" 开头。
			</td>
		</tr>
		<tr>
			<td>
				draggable
			</td>
			<td>
				true,false, auto
			</td>
			<td>
				定义用户是否可以拖动元素。
			</td>
		</tr>
		<tr>
			<td>
				height
			</td>
			<td>
				数字值
			</td>
			<td>
				定义表格，图像或表格单元的高度。
			</td>
		</tr>
		<tr>
			<td>
				hidden
			</td>
			<td>
				hidden
			</td>
			<td>
				定义元素是否应该可见。
			</td>
		</tr>
		<tr>
			<td>
				id
			</td>
			<td>
				用户定义。
			</td>
			<td>
				命名元素，便于使用级联样式表。
			</td>
		</tr>
		<tr>
			<td>
				item
			</td>
			<td>
				元素列表。
			</td>
			<td>
				用于组合元素。
			</td>
		</tr>
		<tr>
			<td>
				itemprop
			</td>
			<td>
				条目列表。
			</td>
			<td>
				用于组合条目。
			</td>
		</tr>
		<tr>
			<td>
				spellcheck
			</td>
			<td>
				true, false
			</td>
			<td>
				定义元素是否必须有拼写或错误检查。
			</td>
		</tr>
		<tr>
			<td>
				style
			</td>
			<td>
				CSS 样式表。
			</td>
			<td>
				给元素定义内联样式。
			</td>
		</tr>
		<tr>
			<td>
				subject
			</td>
			<td>
				用户定义 id。
			</td>
			<td>
				定义元素关联的条目。
			</td>
		</tr>
		<tr>
			<td>
				tabindex
			</td>
			<td>
				Tab number
			</td>
			<td>
				定于元素的 tab 键顺序。
			</td>
		</tr>
		<tr>
			<td>
				title
			</td>
			<td>
				用户定义。
			</td>
			<td>
				元素的“弹出”标题。
			</td>
		</tr>
		<tr>
			<td>
				valign
			</td>
			<td>
				top, middle, bottom
			</td>
			<td>
				HTML 元素内标签的垂直对齐方式。
			</td>
		</tr>
		<tr>
			<td>
				width
			</td>
			<td>
				数字值。
			</td>
			<td>
				定义表格，图像和表格单元的宽度。
			</td>
		</tr>
	</tbody>
</table>

完整的 HTML5 标签列表以及相关的属性请参考 [HTML5 标签](tags-reference.md)。 

## 自定义属性

HTML5 还引入了一个新特性，就是可以添加自定义的数据属性。

自定义数据属性以 __data-__ 开头，基于我们的需求命名。下面是一个简单的例子：

```html
<div class="example" data-subject="physics" data-level="complex">
...
</div>
```

上面的例子中两个叫做 _data-subject_ 和 _data-level_ 的自定义属性在 HTML5 中是完全有效的。我们还可以使用 JavaScript API 或者在 CSS 中以获取标准属性类似的方式获取它们的值。