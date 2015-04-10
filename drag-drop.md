# HTML5 拖放

拖放（DnD）是一个强大的用户界面相关的概念，借助鼠标点击的帮助，它让复制，重新排序以及删除条目变得很容易。这就允许用户在某个元素上点击并按住鼠标按键，把它拖到另外一个位置，然后释放鼠标按键把与元素放到该位置。

要使用传统的 HTML4 实现拖放的功能，开发者要么使用复杂的 JavaScript 变成，要么使用 JavaScript 框架，比如 jQuery 等等。

现在 HTML5 提出了拖放（DnD）API，为浏览器带来了原生拖放支持，让编码变得更容易。

所有的主流浏览器比如 Chrome，FireFox 3.5 以及 Safari 4 等等都支持 HTML5 拖放。

## Drag 和 Drop 事件

下面列出了一些在执行拖放操作各个阶段会触发的事件：

<table>
	<tbody>
		<tr>
			<th>
				事件
			</th>
			<th>
				描述
			</th>
		</tr>
		<tr>
			<td>
				dragstart
			</td>
			<td>
				用户开始拖动对象时触发。
			</td>
		</tr>
		<tr>
			<td>
				dragenter
			</td>
			<td>
				鼠标初次移到目标元素并且正在进行拖动时触发。这个事件的监听器应该之指出这个位置是否允许放置元素。如果没有监听器或者监听器不执行任何操作，默认情况下不允许放置。
			</td>
		</tr>
		<tr>
			<td>
				dragover
			</td>
			<td>
				拖动时鼠标移到某个元素上的时候触发。大多数时候，监听器触发的操作与 dragenter 事件相同。
			</td>
		</tr>
		<tr>
			<td>
				dragleave
			</td>
			<td>
				拖动时鼠标离开某个元素的时候触发。监听器应该移除用于放置反馈的高粱或插入标记。
			</td>
		</tr>
		<tr>
			<td>
				drag
			</td>
			<td>
				对象被拖拽时每次鼠标移动都会触发。
			</td>
		</tr>
		<tr>
			<td>
				drop
			</td>
			<td>
				拖动操作结束，放置元素时触发。监听器负责检索被拖动的数据以及在放置位置插入它。
			</td>
		</tr>
		<tr>
			<td>
				dragend
			</td>
			<td>
				拖动对象时用户释放鼠标按键的时候触发。
			</td>
		</tr>
	</tbody>
</table>

__注意__：只会触发拖动事件；拖动操作期间鼠标事件，比如 _mousemove_ 并不会触发。

## DataTransfer 对象

所有 drag 和 drop 事件的事件监听器都接收一个 __Event__ 对象作为参数，它有一个叫做 __dataTransfer__ 的只读属性。__event.dataTransfer__ 返回与事件相关的 __DataTransfer__ 对象，如下所示：

```javascript
function EnterHandler(event) {
    DataTransfer dt = event.dataTransfer;
    .............
}
```

_DataTransfer_ 对象持有 drag 和 drop 操作相关的数据。可以检索这些数据以及设置 DataTransfer 对象相关联的各种属性，正如下面所阐述的：

<table>
	<tbody>
		<tr>
			<th>
				S.N.
			</th>
			<th>
				DataTransfer 属性及其描述
			</th>
		</tr>
		<tr>
			<td>
				1
			</td>
			<td>
				<b>
					dataTransfer.dropEffect [ = value ]
				</b>
				<br>
				<ul>
					<li>
						<p>
							返回当前选中的操作类型。
						</p>
					</li>
					<li>
						<p>
							这个属性也可以设置改变当前选中的操作。
						</p>
					</li>
					<li>
						<p>
							可选值为<b>none，copy，link</b>和<b>move</b>。
						</p>
					</li>
				</ul>
			</td>
		</tr>
		<tr>
			<td>
				2
			</td>
			<td>
				<b>
					dataTransfer.effectAllowed [ = value ]
				</b>
				<br>
				<ul>
					<li>
						<p>
							返回允许的操作类型。
						</p>
					</li>
					<li>
						<p>
							这个属性也可以设置改变允许的操作。
						</p>
					</li>
					<li>
						<p>
							可选值为<b>none，copy，copyLink，copyMove，link，linkMove，move，all</b>和<b>uninitialized</b>。
						</p>
					</li>
				</ul>
			</td>
		</tr>
		<tr>
			<td>
				3
			</td>
			<td>
				<b>
					dataTransfer.types
				</b>
				<br>
				<p>
					返回列出设置给 dragstart 事件格式的 DOMStringList。此外，如果任意文件被拖拽，那么其中一个类型将会是字符串“Files"。
				</p>
			</td>
		</tr>
		<tr>
			<td>
				4
			</td>
			<td>
				<b>
					dataTransfer.clearData( [ format ] )
				</b>
				<br>
				<p>
					移除指定格式的数据。如果省略参数则移除所有数据。
				</p>
			</td>
		</tr>
		<tr>
			<td>
				5
			</td>
			<td>
				<b>
					dataTransfer.setData(format, data)
				</b>
				<br>
				<p>
					添加给定的数据。
				</p>
			</td>
		</tr>
		<tr>
			<td>
				6
			</td>
			<td>
				<b>
					data = dataTransfer.getData(format)
				</b>
				<br>
				<p>
					返回指定的数据。如果没有该数据则返回空字符串。
				</p>
			</td>
		</tr>
		<tr>
			<td>
				7
			</td>
			<td>
				<b>
					dataTransfer.files
				</b>
				<br>
				<p>
					如果有，返回表示被拖拽文件的 FileList。
				</p>
			</td>
		</tr>
		<tr>
			<td>
				8
			</td>
			<td>
				<b>
					dataTransfer.setDragImage(element, x, y)
				</b>
				<br>
				<p>
					使用给定的元素更新拖拽反馈信息，替换先前指定的反馈信息。
				</p>
			</td>
		</tr>
		<tr>
			<td>
				9
			</td>
			<td>
				<b>
					dataTransfer.addElement(element)
				</b>
				<br>
				<p>
					把给定的元素添加到用来渲染拖拽反馈的元素列表。
				</p>
			</td>
		</tr>
	</tbody>
</table>

## Drag 和 Drop 过程

下面是实现拖拽操作的步骤：

### 步骤1：创建一个可拖拽对象

下面是要采用的步骤：

- 如果想要拖动某个元素，需要设置元素的 __draggable__ 属性为 __true__。
- 给 __dragstart__ 设置一个事件监听器存储拖拽数据。
- 事件监听器 __dragstart__ 会设置允许的效果（copy，move，link或者是组合形式的）。

下面是一个让对象可拖拽的示例：

```html
<!DOCTYPE HTML>
<html>
<head>
<style type="text/css">
#boxA, #boxB {
   float:left;padding:10px;margin:10px; -moz-user-select:none;
}
#boxA { background-color: #6633FF; width:75px; height:75px;  }
#boxB { background-color: #FF6699; width:150px; height:150px; }
</style>
<script type="text/javascript">
function dragStart(ev) {
   ev.dataTransfer.effectAllowed='move';
   ev.dataTransfer.setData("Text", ev.target.getAttribute('id'));
   ev.dataTransfer.setDragImage(ev.target,0,0);
   return true;
}
</script>
</head>
<body>
<center>
<h2>Drag and drop HTML5 demo</h2>
<div>Try to drag the purple box around.</div>

<div id="boxA" draggable="true" 
        ondragstart="return dragStart(event)">
   <p>Drag Me</p>
</div>
<div id="boxB">Dustbin</div>
</center>
</body>
</html>
```

便于学习上述概念 - 请使用最新版的 FireFox，Safari 或 Chrome 进行[在线练习](http://www.tutorialspoint.com/cgi-bin/practice.cgi?file=html5-58.htm)。

### 步骤2：放置对象

为了接受放置，放置目标至少要监听三个事件。

- __dragenter__ 事件，用来确定放置目标是否接受放置。如果放置被接受，那么这个事件必须取消。
- __dragover__ 事件，用来确定给用户显示怎样的反馈信息。如果这个事件被取消，反馈信息（通常就是光标）就会基于 dropEffect 属性的值更新。
- 最后是 __drop__ 事件，允许执行真是的放置。

下面是把一个对象放入另一个对象的示例：

```html
<!DOCTYPE HTML>
<html>
<head>
<style type="text/css">
#boxA, #boxB {
   float:left;padding:10px;margin:10px;-moz-user-select:none;
}
#boxA { background-color: #6633FF; width:75px; height:75px;  }
#boxB { background-color: #FF6699; width:150px; height:150px; }
</style>
<script type="text/javascript">
function dragStart(ev) {
   ev.dataTransfer.effectAllowed='move';
   ev.dataTransfer.setData("Text", ev.target.getAttribute('id'));
   ev.dataTransfer.setDragImage(ev.target,0,0);
   return true;
}
function dragEnter(ev) {
   event.preventDefault();
   return true;
}
function dragOver(ev) {
    return false;
}
function dragDrop(ev) {
   var src = ev.dataTransfer.getData("Text");
   ev.target.appendChild(document.getElementById(src));
   ev.stopPropagation();
   return false;
}
</script>
</head>
<body>
<center>
<h2>Drag and drop HTML5 demo</h2>
<div>Try to move the purple box into the pink box.</div>

<div id="boxA" draggable="true" 
     ondragstart="return dragStart(event)">
   <p>Drag Me</p>
</div>
<div id="boxB" ondragenter="return dragEnter(event)" 
     ondrop="return dragDrop(event)" 
     ondragover="return dragOver(event)">Dustbin</div>
</center>
</body>
</html>
```

便于学习上述概念 - 请使用最新版的 FireFox，Safari 或 Chrome 进行[在线练习](http://www.tutorialspoint.com/cgi-bin/practice.cgi?file=html5-59.htm)。