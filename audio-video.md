# HTML5 音频和视频

HTML5 特性，包括原生音频和视频支持而无需 Flash。

HTML5 &lt;audio&gt; 和 &lt;video&gt; 标签让我们给站点添加媒体变得简单。我们只需要设置 __src__ 属性来识别媒体资源，包含 controls 属性让用户可以播放和暂停媒体。

## 嵌入视频

下面是在 Web 页面中嵌入视频文件最简单的形式：

```html
<video src="foo.mp4"  width="300" height="200" controls>
    Your browser does not support the <video> element.   
</video>
```

目前的 HTML5 规范草案还没有指定浏览器应该在 video 标签中支持哪种视频格式。但是最常用的视频格式是：

1. __Ogg__：带有 Thedora 视频编码器和 Vorbis 音频编码器的 Ogg 文件。
2. __mpeg4__：带有 H.264 视频编码器和 AAC 音频编码器的 MPEG4 文件。

我们可以使用带有媒体类型和其他属性的 &lt;source&gt; 标签指定媒体文件。video 元素允许使用多个 source 元素，浏览器会使用第一个认可的格式：

```html
<!DOCTYPE HTML>
<html>
<body>
   <video  width="300" height="200" controls autoplay>
       <source src="/html5/foo.ogg" type="video/ogg" />
       <source src="/html5/foo.mp4" type="video/mp4" />
       Your browser does not support the <video> element.
   </video>
</body>
</html>
```

便于学习上述概念 - 请使用最新版的 Safari 或 Opera 进行[在线练习](http://www.tutorialspoint.com/cgi-bin/practice.cgi?file=html5-49.htm)。

## Video 属性规范

HTML5 video 标签可以使用多个属性控制外观和感觉以及各种控制功能：

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
				autoplay
			</td>
			<td>
				如果指定这个布尔值属性，只要没有停止加载数据，视频就会立刻开始自动播放。
			</td>
		</tr>
		<tr>
			<td>
				autobuffer
			</td>
			<td>
				如果指定这个布尔值属性，即使没有设置自动播放，视频也会自动开始缓冲。
			</td>
		</tr>
		<tr>
			<td>
				controls
			</td>
			<td>
				如果指定这个属性，就允许用户控制视频播放，包括音量控制，快进，暂停或者恢复播放。
			</td>
		</tr>
		<tr>
			<td>
				height
			</td>
			<td>
				这个属性以 CSS 像素的形式指定视频显示区域的高度。
			</td>
		</tr>
		<tr>
			<td>
				loop
			</td>
			<td>
				如果指定这个布尔值属性，表示允许播放结束后自动回放。
			</td>
		</tr>
		<tr>
			<td>
				preload
			</td>
			<td>
				指定这个属性，视频会在载入页面时加载并准备就绪。如果指定自动播放则忽略。
			</td>
		</tr>
		<tr>
			<td>
				poster
			</td>
			<td>
				这是一个图像 URL，显示到用户播放或快进。
			</td>
		</tr>
		<tr>
			<td>
				src
			</td>
			<td>
				要嵌入的视频 URL。可选，可以在 video 块中使用 &lt;source&gt; 元素替代来指定要嵌入的视频。
			</td>
		</tr>
		<tr>
			<td>
				width
			</td>
			<td>
				这个属性以 CSS 像素的形式指定视频显示区域的宽度。
			</td>
		</tr>
	</tbody>
</table>

## 嵌入音频

HTML5 支持的 &lt;audio&gt; 标签用于在如下所示的 HTML 或 XHTML 文档中嵌入语音内容。

```html
<audio src="foo.wav" controls autoplay>
    Your browser does not support the <audio> element.   
</audio>
```

当前的 HTML 草案规范还没有指定浏览器应该在 audio 标签中支持哪种音频格式。但是最常用的音频格式是 __ogg__，__mp3__ 和 __wav__。

我们可以使用带媒体类型以及其他属性的的 &lt;source&gt; 标签指定媒体。Audio 元素允许使用多个 source 元素，并且浏览器会使用第一个认可的格式：

```html
<!DOCTYPE HTML>
<html>
<body>
   <audio controls autoplay>
       <source src="/html5/audio.ogg" type="audio/ogg" />
       <source src="/html5/audio.wav" type="audio/wav" />
       Your browser does not support the <audio> element.
   </audio>
</body>
</html>
```

便于学习上述概念 - 请使用最新版的 Safari 或 Opera 进行[在线练习](http://www.tutorialspoint.com/cgi-bin/practice.cgi?file=html5-50.htm)。

### Audio 属性规范

HTML5 audio 标签可以使用多个属性来控制外观，感受以及各种控制功能：

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
				autoplay
			</td>
			<td>
				如果指定这个布尔值属性，只要没停止加载数据，音频就会立刻自动开始播放。
			</td>
		</tr>
		<tr>
			<td>
				autobuffer
			</td>
			<td>
				如果指定这个布尔值属性，即使没有设置自动播放，音频也会自动开始缓冲。
			</td>
		</tr>
		<tr>
			<td>
				controls
			</td>
			<td>
				如果指定这个属性，表示允许用户控制音频播放，包括音量控制，快进以及暂停/恢复播放。
			</td>
		</tr>
		<tr>
			<td>
				loop
			</td>
			<td>
				如果指定这个布尔值属性，表示允许音频播放结束后自动回放。
			</td>
		</tr>
		<tr>
			<td>
				preload
			</td>
			<td>
				这个属性指定加载页面时加载音频并准备就绪。如果指定自动播放则忽略。
			</td>
		</tr>
		<tr>
			<td>
				src
			</td>
			<td>
				要嵌入的音频 URL。可选，可以在音频块里面使用 &lt;source&gt; 元素指定要嵌入的音频来替代。
			</td>
		</tr>
	</tbody>
</table>

## 处理媒体事件

HTML5 audio 和 video 标签可以用多个属性利用 JavaScript 控制各种控制功能：

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
				abort
			</td>
			<td>
				播放中止时生成这个事件。
			</td>
		</tr>
		<tr>
			<td>
				canplay
			</td>
			<td>
				足够的数据可用并且媒体可以播放时生成这个事件。
			</td>
		</tr>
		<tr>
			<td>
				ended
			</td>
			<td>
				播放完成时生成这个事件。
			</td>
		</tr>
		<tr>
			<td>
				error
			</td>
			<td>
				发生错误时生成这个事件。
			</td>
		</tr>
		<tr>
			<td>
				loadeddata
			</td>
			<td>
				媒体第一帧载入完成时生成这个事件。
			</td>
		</tr>
		<tr>
			<td>
				loadstart
			</td>
			<td>
				开始加载媒体时生成这个事件。
			</td>
		</tr>
		<tr>
			<td>
				pause
			</td>
			<td>
				播放暂停时生成这个事件。
			</td>
		</tr>
		<tr>
			<td>
				play
			</td>
			<td>
				播放开始或者恢复时生成这个事件。
			</td>
		</tr>
		<tr>
			<td>
				progress
			</td>
			<td>
				定期通知媒体下载进度时生成这个事件。
			</td>
		</tr>
		<tr>
			<td>
				ratechange
			</td>
			<td>
				播放速度改变时生成这个事件。
			</td>
		</tr>
		<tr>
			<td>
				seeked
			</td>
			<td>
				快进操作完成时生成这个事件。
			</td>
		</tr>
		<tr>
			<td>
				seeking
			</td>
			<td>
				快进操作开始时生成这个事件。
			</td>
		</tr>
		<tr>
			<td>
				suspend
			</td>
			<td>
				媒体加载被暂停时生成这个事件。
			</td>
		</tr>
		<tr>
			<td>
				volumechange
			</td>
			<td>
				音频音量变化时生成这个事件。
			</td>
		</tr>
		<tr>
			<td>
				waiting
			</td>
			<td>
				请求操作（比如播放）被延迟，等待另一个操作完成（比如快进）时生成这个事件。
			</td>
		</tr>
	</tbody>
</table>

下面是一个允许播放给定视频的示例：

```html
<!DOCTYPE HTML>
<head>
<script type="text/javascript">
function PlayVideo(){
   var v = document.getElementsByTagName("video")[0];  
   v.play(); 
}
</script>
</head>
<html>
<body>
   <form>
   <video  width="300" height="200" src="/html5/foo.mp4">
       Your browser does not support the <video> element.
   </video>
   <input type="button" onclick="PlayVideo();"  value="Play"/>
   </form>
</body>
</html>
```

便于学习上述概念 - 请使用最新版的 Safari 或 Opera 进行[在线练习](http://www.tutorialspoint.com/cgi-bin/practice.cgi?file=html5-51.htm)。

## 配置服务器媒体类型

大多数服务器默认都没使用正确的 MIME 类型提供 Ogg 或 mp4 媒体，因此我们可能需要添加适当的配置。

```shell
AddType audio/ogg .oga
AddType audio/wav .wav
AddType video/ogg .ogv .ogg
AddType video/mp4 .mp4
```