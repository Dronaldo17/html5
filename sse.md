# HTML5 服务器推送事件

传统的 Web 应用程序生成发送到 Web 服务器端的事件。比如，点击一个链接会从服务器请求一个新页面。

这种从 Web 浏览器到 Web 服务器的时间类型可以称作客服端事件。

随着 HTML5 的出现，[WHATWG](http://www.whatwg.org/) Web Applications 1.0 引入了一个从 Web 服务器到 Web 浏览器的事件流，被称作服务器推送事件（SSE）。使用 SSE 可以不停的将 DOM 事件推送到用户的浏览器中。

这个事件流方法会打开一个到服务器的持久连接，新消息可用时发送数据到客户端，从而不再需要持续的轮询。

## SSE Web 应用程序

要在 Web 应用程序中使用服务器推送事件，我们需要给文档添加一个 &lt;eventsource&gt;元素。

&lt;eventsource&gt; 元素的 __src__ 属性应该指向一个 URL，这个 URL 应该提供一个 HTTP 持久连接用于发送包含事件的数据流。

这个 URL 将会指向一个持续发送事件数据的 PHP，PERL 或者任意 Python 脚本。下面是一个简单的期望获得服务器时间的 Web 应用程序示例。

```html
<!DOCTYPE HTML>
<html>
<head>
<script type="text/javascript">
/* Define event handling logic here */
</script>
</head>
<body>
<div id="sse">
   <eventsource src="/cgi-bin/ticker.cgi" />
</div>
<div id="ticker">
   <TIME>
</div>
</body>
</html>
```

## SSE 服务器端脚本

服务器端脚本应该发送 __Content-type__ 头指定类型为 _text/event-stream_，如下所示：

```perl
print "Content-Type: text/event-stream\n\n";
```

设置 Content-type 之后，服务器端脚本将发送一个后面紧跟事件名称的 __Event:__ 标签。下面的示例将会发送一个以换行符结束的 Server-Time 作为事件名称。

```perl
print "Event: server-time\n";
```

最后一步是使用 __Data:__ 标签发送事件数据，紧随其后的是以换行符结束的整数字符串值，如下所示：

```perl
$time = localtime();
print "Data: $time\n";
```

下面是用 perl 编写的完整 ticker.cgi：

```perl
#!/usr/bin/perl

print "Content-Type: text/event-stream\n\n";
while(true){
   print "Event: server-time\n";
   $time = localtime();
   print "Data: $time\n";
   sleep(5);
}
```

## 处理服务器推送事件

让我们修改一下我们的 Web 应用程序来处理服务器推送时间。下面是最终示例：

```html
<!DOCTYPE HTML>
<html>
<head>
<script type="text/javascript">
   document.getElementsByTagName("eventsource")[0].
            addEventListener("server-time", eventHandler, false);
   function eventHandler(event)
   {
       // Alert time sent by the server
       document.querySelector('#ticker').innerHTML = event.data;

   }
</script>
</head>
<body>
<div id="sse">
   <eventsource src="/cgi-bin/ticker.cgi" />
</div>
<div id="ticker" name="ticker">
   [TIME]
</div>
</body>
</html>
```

在测试服务器推送事件之前，建议你确保你的 Web 浏览器支持这一概念。