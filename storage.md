# HTML5 Web 存储

HTML5 引入了两种机制，类似于 HTTP 的会话 cookies，用于在客户端存储结构化数据以及克服以下缺点。

- 每个 HTTP 请求中都包含 Cookies，从而导致传输相同的数据减缓我们的 Web 应用程序。

- 每个 HTTP 请求中都包含 Cookies，从而导致发送未加密的数据到互联网上。

- Cookies 只能存储有限的 4KB 数据，不足以存储所需的数据。

这两种存储方式是 __session storage__ 和 __local storage__，它们将用于处理不同的情况。

几乎所有最新版的浏览器都支持 HTML5 存储，包括 IE 浏览器。

## 会话存储

_会话存储_被设计用于用户执行单一事务的场景，但是同时可以在不同的窗口中执行多个事务。

### 示例

_比如，如果用户在同一网站的两个不同的窗口中购买机票。如果该网站使用 cookie 跟踪用户购买的机票，当用户在窗口中点击页面时，从一个窗口到另一个时当前已经购买的机票会“泄漏”，这可能导致用户购买同一航班的两张机票而没有注意到。_

HTML5 引入了 _sessionStorage_ 属性，这个网站可以用来把数据添加到会话存储中，用户仍然可以在打开的持有该会话的窗口中访问同一站点的任意页面，当关闭窗口时，会话也会丢失。

下面的代码将会设置一个会话变量，然后访问该变量：

```html
<!DOCTYPE HTML>
<html>
<body>

  <script type="text/javascript">
    if( sessionStorage.hits ){
       sessionStorage.hits = Number(sessionStorage.hits) +1;
    }else{
       sessionStorage.hits = 1;
    }
    document.write("Total Hits :" + sessionStorage.hits );
  </script>
  <p>Refresh the page to increase number of hits.</p>
  <p>Close the window and open it again and check the result.</p>

</body>
</html>
```

便于学习上面的概念 - 请进行[在线练习](http://www.tutorialspoint.com/cgi-bin/practice.cgi?file=html5-23.htm)。

## 本地存储

_本地存储_被设计用于跨多个窗口进行存储，并持续处在当前会话上。尤其是，出于性能的原因 Web 应用程序可能希望在客户端存储百万字节的用户数据，比如用户撰写的整个文档或者是用户的邮箱。

Cookies 并不能很好的处理这种情况，因为每个请求都会传输。

### 示例

HTML5 引入了 _localStorage_ 属性，可以用于访问页面的本地存储区域而没有时间限制，无论何时我们使用这个页面的时候本地存储都是可用的。

下面的代码设置了一个本地存储变量，每次访问这个页面时都可以访问该变量，甚至是下次打开窗口时：

```html
<!DOCTYPE HTML>
<html>
<body>

  <script type="text/javascript">
    if( localStorage.hits ){
       localStorage.hits = Number(localStorage.hits) +1;
    }else{
       localStorage.hits = 1;
    }
    document.write("Total Hits :" + localStorage.hits );
  </script>
  <p>Refresh the page to increase number of hits.</p>
  <p>Close the window and open it again and check the result.</p>

</body>
</html>
```

便于学习上述概念 - 请进行[在线练习](http://www.tutorialspoint.com/cgi-bin/practice.cgi?file=html5-24.htm)。

## 删除 Web 存储

在本地机器上存储敏感数据可能是危险的，可能会留下安全隐患。

_会话存储数据_在会话终止之后将由浏览器立即删除。

要清除本地存储设置需要调用 __localStorage.remove('key')__；这个 'key' 就是我们想要移除的值对应的键。如果想要清除所有设置，需要调用 __localStorage.clear()__ 方法。

下面的代码会完全清除本地存储：

```html
<!DOCTYPE HTML>
<html>
<body>

  <script type="text/javascript">
    localStorage.clear();

    // Reset number of hits.
    if( localStorage.hits ){
       localStorage.hits = Number(localStorage.hits) +1;
    }else{
       localStorage.hits = 1;
    }
    document.write("Total Hits :" + localStorage.hits );
  </script>
  <p>Refreshing the page would not to increase hit counter.</p>
  <p>Close the window and open it again and check the result.</p>

</body>
</html>
```

便于学习上述概念 - 请进行[在线练习](http://www.tutorialspoint.com/cgi-bin/practice.cgi?file=html5-25.htm)。