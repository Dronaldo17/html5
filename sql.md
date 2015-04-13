# HTML5 Web SQL 数据库

Web SQL 数据库 API 并不是 HTML5 规范的一部分，但是它是一个独立的规范，引入了一组使用 SQL 操作客户端数据库的 APIs。

假定你是一个优秀的 Web 开发人员，如果是这样的话，毫无疑问你会很清楚 SQL 和 RDBMS 的概念。如果你仍然需要一个 SQL 的议题，可以学习我们的 [SQL 教程](http://www.tutorialspoint.com/sql/index.htm)。

我们可以在最新版的 Safari，Chrome 和 Opera 中使用 Web SQL 数据库。

## 核心方法

下面是规范中定义的三个核心方法。也会涵盖在本教程中：

1. __openDatabase__：这个方法使用现有的数据库或者新建的数据库创建一个数据库对象。
2. __transaction__：这个方法让我们能够控制一个事务，以及基于这种情况执行提交或者回滚。
3. __executeSql__：这个方法用于执行实际的 SQL 查询。

## 开启数据库

如果数据库已经存在，_openDatabase__ 方法负责开启数据库，如果不存在，这个方法会创建它。

使用下面的代码可以创建并开启一个数据库：

```javascript
var db = openDatabase('mydb', '1.0', 'Test DB', 2 * 1024 * 1024);
```

上面的方法接受下列五个参数：

1. 数据库名称
2. 版本号
3. 描述文本
4. 数据库大小
5. 创建回调

最后也是第五个参数，创建回调会在创建数据库后被调用。然而，即使没有这个特性(功能)，运行时仍然会创建数据库以及正确的版本。

## 执行查询

执行查询需要使用 database.transaction() 函数。这个函数需要一个参数，它是一个负责实际执行查询的函数，如下所示：

```javascript
var db = openDatabase('mydb', '1.0', 'Test DB', 2 * 1024 * 1024);
db.transaction(function (tx) {  
   tx.executeSql('CREATE TABLE IF NOT EXISTS LOGS (id unique, log)');
});
```

上面的查询语句会在 'mydb' 数据库中创建一个叫做的 LOGS 的表。

## 插入操作

为了在表中创建条目，我们在上面的例子中加入简单的 SQL 查询，如下所示：

```javascript
var db = openDatabase('mydb', '1.0', 'Test DB', 2 * 1024 * 1024);
db.transaction(function (tx) {
   tx.executeSql('CREATE TABLE IF NOT EXISTS LOGS (id unique, log)');
   tx.executeSql('INSERT INTO LOGS (id, log) VALUES (1, "foobar")');
   tx.executeSql('INSERT INTO LOGS (id, log) VALUES (2, "logmsg")');
});
```

创建条目时还可以传递如下所示的动态值：

```javascript
var db = openDatabase('mydb', '1.0', 'Test DB', 2 * 1024 * 1024);
db.transaction(function (tx) {  
  tx.executeSql('CREATE TABLE IF NOT EXISTS LOGS (id unique, log)');
  tx.executeSql('INSERT INTO LOGS 
                        (id,log) VALUES (?, ?'), [e_id, e_log];
});
```

这里的 e_id 和 e_log 是外部变量，executeSql 会映射数组参数中的每个条目给 "?"。

## 读取操作

要读取已经存在的记录，我们可以使用回调来捕获结果，如下所示：

```javascript
var db = openDatabase('mydb', '1.0', 'Test DB', 2 * 1024 * 1024);
db.transaction(function (tx) {
   tx.executeSql('CREATE TABLE IF NOT EXISTS LOGS (id unique, log)');
   tx.executeSql('INSERT INTO LOGS (id, log) VALUES (1, "foobar")');
   tx.executeSql('INSERT INTO LOGS (id, log) VALUES (2, "logmsg")');
});
db.transaction(function (tx) {
   tx.executeSql('SELECT * FROM LOGS', [], function (tx, results) {
   var len = results.rows.length, i;
   msg = "<p>Found rows: " + len + "</p>";
   document.querySelector('#status').innerHTML +=  msg;
   for (i = 0; i < len; i++){
      alert(results.rows.item(i).log );
   }
 }, null);
});
```

## 最终示例

最后，然我们把这个例子放到如下所示的完整 HTML5 文档中，然后尝试在 Safari 浏览器中运行它：

```html
<!DOCTYPE HTML>
<html>
<head>
<script type="text/javascript">
var db = openDatabase('mydb', '1.0', 'Test DB', 2 * 1024 * 1024);
var msg;
db.transaction(function (tx) {
  tx.executeSql('CREATE TABLE IF NOT EXISTS LOGS (id unique, log)');
  tx.executeSql('INSERT INTO LOGS (id, log) VALUES (1, "foobar")');
  tx.executeSql('INSERT INTO LOGS (id, log) VALUES (2, "logmsg")');
  msg = '<p>Log message created and row inserted.</p>';
  document.querySelector('#status').innerHTML =  msg;
});

db.transaction(function (tx) {
  tx.executeSql('SELECT * FROM LOGS', [], function (tx, results) {
   var len = results.rows.length, i;
   msg = "<p>Found rows: " + len + "</p>";
   document.querySelector('#status').innerHTML +=  msg;
   for (i = 0; i < len; i++){
     msg = "<p><b>" + results.rows.item(i).log + "</b></p>";
     document.querySelector('#status').innerHTML +=  msg;
   }
 }, null);
});
</script>
</head>
<body>
<div id="status" name="status">Status Message</div>
</body>
</html>
```

在最新版的 Safari 或者 Opera 浏览器中这会生成如下所示结果：

```
Log message created and row inserted.

Found rows: 2

foobar

logmsg
```

便于学习这一概念 - 请使用最新版的 Safari 或者 Opera 进行[在线练习](http://www.tutorialspoint.com/cgi-bin/practice.cgi?file=html5-26.htm)。