# HTML5 字符编码

字符编码就是将字节转换为字符的一种方法。要验证或者显示一个 HTML 文档，程序必须选择一个字符编码。HTML5 作者有三种方式设置字符编码：

## HTTP Content-Type 头：

如果你在编写 cgi 程序或者类似的程序，那么可以使用 HTTP _Content-Type_ 头设置任意字符编码：

下面是一个简单的例子：

```
print "Content-Type: text/html; charset=utf-8\r\n";
```

## &lt;meta&gt; 元素：

可以使用带有 charset 属性的 &lt;meta&gt; 元素指定 HTML5 文档前 512 个字节的编码：

下面是简化的例子：

```html
<meta charset="UTF-8">
```

尽管这种语法是被允许的，但上述语法需要使用 &lt;meta http-equiv="Content-Type" content="text/html; charset=UTF-8"&gt; 替换。

## Unicode 字节顺序标记（BOM）

一个字节顺序标记（BOM）由数据流开头的 U+FEFF 字符码组成，它可以用作定义字节顺序和编码形式的签名，主要是未标记的明文文件。

许多 Windows 程序（包括 Windows 记事本）都会在保存为 UTF-8 的任意文档开头添加 0xEF, 0xBB, 0xBF。这就是 Unicode 字节顺序标记（BOM）的 UTF-8 编码，通常被称为 UTF-8 BOM，尽管它和字节顺序没有关系。

对于 HTML5 文档，我们可以在文件的开头使用 Unicode 字节顺序标记（BOM）字符。这个字符为使用的编码提供了签名。