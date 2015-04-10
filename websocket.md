# HTML5 WebSockets 教程

Web Sockets 是用于 Web 应用程序的新一代双向通信技术，运行在单一套接字之上，它通过 JavaScript 接口暴漏在 HTML5 兼容的浏览器中。

一旦取得 Web 服务器上的 Web Socket 连接之后，就可以通过调用 __send()__ 方法从浏览器发送数据到服务器上，通过 __onmessage__ 事件处理程序从服务器接收数据到浏览器中。

下面是创建一个新的 WebSocket 对象的 API。

```javascript
var Socket = new WebSocket(url, [protocal] );
```

第一个参数 url 用于指定要连接的 URL。第二个属性 - 端口是可选的，如果提供，就会指定一个服务器必须支持连接成功的子协议。

## WebSocket 属性

下面是 WebSocket 对象的属性。假定我们已经创建了上述的 Socket 对象：

<table>
	<tbody>
		<tr>
			<th width="30%">
				属性
			</th>
			<th>
				描述
			</th>
		</tr>
		<tr>
			<td>
				Socket.readyState
			</td>
			<td>
				<p>
					只读属性<b>readyState</b>表示连接的状态。有以下取值：
				</p>
				<ol>
					<li>
						<p>
							0 表示连接尚未建立。
						</p>
					</li>
					<li>
						<p>
							1 表示连接已建立，可以进行通信。
						</p>
					</li>
					<li>
						<p>
							2 表示连接正在进行关闭握手。
						</p>
					</li>
					<li>
						<p>
							3 表示连接已经关闭或者连接不能打开。
						</p>
					</li>
				</ol>
			</td>
		</tr>
		<tr>
			<td>
				Socket.bufferedAmount
			</td>
			<td>
				<p>
					只读属性<b>bufferedAmount</b>表示已经使用 send() 方法排队的 URF-8 文本字节数。
				</p>
			</td>
		</tr>
	</tbody>
</table>

## WebSocket 事件

下面是 WebSocket 对象相关的事件。假定我们已经创建了上述的 Socket 对象：

<table>
	<tbody>
		<tr>
			<th width="10%">
				事件
			</th>
			<th width="25%">
				事件处理程序
			</th>
			<th>
				描述
			</th>
		</tr>
		<tr>
			<td>
				open
			</td>
			<td>
				Socket.onopen
			</td>
			<td>
				建立 socket 连接时触发这个事件。
			</td>
		</tr>
		<tr>
			<td>
				message
			</td>
			<td>
				Socket.onmessage
			</td>
			<td>
				客户端从服务器接收数据时触发。
			</td>
		</tr>
		<tr>
			<td>
				error
			</td>
			<td>
				Socket.onerror
			</td>
			<td>
				连接发生错误时触发。
			</td>
		</tr>
		<tr>
			<td>
				close
			</td>
			<td>
				Socket.onclose
			</td>
			<td>
				连接被关闭时触发。
			</td>
		</tr>
	</tbody>
</table>

## WebSocket 方法

下面是 WebSocket 对象相关的方法。假定我们已经创建了上述的 Socket 对象：

<table>
	<tbody>
		<tr>
			<th width="30%">
				方法
			</th>
			<th>
				描述
			</th>
		</tr>
		<tr>
			<td>
				Socket.send()
			</td>
			<td>
				<p>
					send(data) 方法使用连接传输数据。
				</p>
			</td>
		</tr>
		<tr>
			<td>
				Socket.close()
			</td>
			<td>
				<p>
					close() 方法用于终止任何现有连接。
				</p>
			</td>
		</tr>
	</tbody>
</table>

## WebSocket 示例

一个 WebSocket 就是客户端和服务端之间的标准双向 TCP 套接字。套接字以 HTTP 连接开始，在 HTTP 握手之后“升级”为 TCP 套接字。握手之后，任意一端都可以发送数据。

### 客户端 HTML 和 JavaScript 代码

编写这篇教程时，只有少数几个浏览器支持 WebSocket() 接口。你可以使用最新版的 Chrome，Mozilla，Opera 和 Safari 尝试下面这个例子。

```html
<!DOCTYPE HTML>
<html>
<head>
<script type="text/javascript">
function WebSocketTest()
{
  if ("WebSocket" in window)
  {
     alert("WebSocket is supported by your Browser!");
     // Let us open a web socket
     var ws = new WebSocket("ws://localhost:9998/echo");
     ws.onopen = function()
     {
        // Web Socket is connected, send data using send()
        ws.send("Message to send");
        alert("Message is sent...");
     };
     ws.onmessage = function (evt) 
     { 
        var received_msg = evt.data;
        alert("Message is received...");
     };
     ws.onclose = function()
     { 
        // websocket is closed.
        alert("Connection is closed..."); 
     };
  }
  else
  {
     // The browser doesn't support WebSocket
     alert("WebSocket NOT supported by your Browser!");
  }
}
</script>
</head>
<body>
<div id="sse">
   <a href="javascript:WebSocketTest()">Run WebSocket</a>
</div>
</body>
</html>
```

### 安装 pywebsocket

在测试上面的客户端程序之前，需要一个支持 WebSocket 的服务器。可以从 [pywebsocket](http://code.google.com/p/pywebsocket/) 下载 mod_pywebsocket-x.x.x.tar.gz，它只在为 Apache HTTP 服务器提供 WebSocket 扩展，然后按照如下步骤安装。

1. 解压缩和解压下载的文件
2. 进入 __pywebsocket-x.x.x/src/__ 目录。
3. 执行 $python setup.py build
4. 执行 $sudo python setup.py install
5. 然后通过 $pydoc mod_pywebsocket 读取文档

这将会把他安装到我们的 python 环境中。

### 启动服务器

进入 __pywebsocket-x.x.x/src/mod_pywebsocket__ 文件夹并运行如下命令：

```shell
$sudo python standalone.py -p 9998 -w ../example/
```

这会启动监听 9998 端口的服务器，然后使用通过 -w 选项指定的处理程序目录，也就是 echo_wsh.py 所在目录。

现在使用 Chrome 浏览器打开起初创建的 html 文件。如果浏览器支持 WebSocket()，那么会得到一个指示浏览器支持 WebSocket 的消息框，当我们点击 “Run WebSocket” 时会得到服务器脚本发出的 Goodbye 信息。