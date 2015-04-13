# HTML5 地理定位

HTML5 Geolocation API 允许我们对喜欢的网站共享我们的位置。JavaScript 可以捕获到纬度和经度，还可以发送给后端服务器，然后做一些位置感知的事情，比如查找本地企业或者在地图上显示我们的位置。

当前大多数浏览器和移动设备都支持 Geolocation API。地理定位 APIs 是作为全局 navigator 对象的一个新属性工作的。可以按照如下方式创建地理定位对象：

```javascript
var geolocation = navigator.geolocation;
```

地理对象是一个允许组件检索设备地理位置相关信息的服务对象。

## Geolocation 方法

地理定位对象提供了下列方法：

<table>
	<tbody>
		<tr>
			<th>
				方法
			</th>
			<th>
				描述
			</th>
		</tr>
		<tr>
			<td>
				<a href="http://www.tutorialspoint.com/html5/geolocation_getcurrentposition.htm" title="getCurrentPosition">
					getCurrentPosition()
				</a>
			</td>
			<td>
				<p>
					这个方法用于检索用户的当前地理位置。
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<a href="http://www.tutorialspoint.com/html5/geolocation_watchposition.htm" title="watchPosition">
					watchPosition()
				</a>
			</td>
			<td>
				<p>
					这个方法用于检索设备当前地理位置定期更新信息。
				</p>
			</td>
		</tr>
		<tr>
			<td>
				<a href="http://www.tutorialspoint.com/html5/geolocation_clearwatch.htm" title="clearWatch">
					clearWatch()
				</a>
			</td>
			<td>
				<p>
					这个方法用于取消 watchPosition 方法调用。
				</p>
			</td>
		</tr>
	</tbody>
</table>

### 示例

下面是一个使用上述方法的示例代码：

```javascript
function getLocation() {
   var geolocation = navigator.geolocation;
   geolocation.getCurrentPosition(showLocation, errorHandler);
}
```

这里的 showLocation 和 errorHandler 分别是用来下一节会讲述的获取实际位置和处理错误的回调方法。

## Location 属性

地理定位方法 getCurrentPosition() 和 getPositionUsingMethodName() 指定了检索位置信息的回调方法。这些方法使用一个存储完整位置信息的 __Position__ 对象异步调用。

这个 __Position__ 对象指定了设备的当前地理位置。这个位置以一组带有方向和速度信息的地理坐标表示。

下面的表格描述了 Position 对象的属性。对于可选属性，如果系统没有提供值，则该属性值为 null。

<table>
	<tbody>
		<tr>
			<th>
				属性
			</th>
			<th>
				类型
			</th>
			<th>
				描述
			</th>
		</tr>
		<tr>
			<td>
				coords
			</td>
			<td>
				objects
			</td>
			<td>
				<p>
					表示设备的地理位置。位置以一组带有方向和速度信息的地理坐标表示。
				</p>
			</td>
		</tr>
		<tr>
			<td>
				coords.latitude
			</td>
			<td>
				Number
			</td>
			<td>
				<p>
					十进制的纬度估值。值范围为 [-90.00, +90.00]。
				</p>
			</td>
		</tr>
		<tr>
			<td>
				coords.longitude
			</td>
			<td>
				Number
			</td>
			<td>
				<p>
					十进制的经度固执。值范围为 [-180.00, +180.00]。
				</p>
			</td>
		</tr>
		<tr>
			<td>
				coords.altitude
			</td>
			<td>
				Number
			</td>
			<td>
				<p>
					<b>【可选】</b>
					WGS-84 球面以上的海拔高度固执，以米为单位计算。
				</p>
			</td>
		</tr>
		<tr>
			<td>
				coords.accuracy
			</td>
			<td>
				Number
			</td>
			<td>
				<p>
					<b>【可选】</b>
					以米为单位的纬度和经度精确估值。
				</p>
			</td>
		</tr>
		<tr>
			<td>
				coords.altitudeAccuracy
			</td>
			<td>
				Number
			</td>
			<td>
				<p>
					<b>【可选】</b>
					以米为单位的海拔高度精确估值。
				</p>
			</td>
		</tr>
		<tr>
			<td>
				coords.heading
			</td>
			<td>
				Number
			</td>
			<td>
				<p>
					<b>【可选】</b>
					相对正北方向设备以顺时针方向运动计算的当前方向。
				</p>
			</td>
		</tr>
		<tr>
			<td>
				coords.speed
			</td>
			<td>
				Number
			</td>
			<td>
				<p>
					<b>【可选】</b>
					以米/每秒为单位的设备当前地面速度。
				</p>
			</td>
		</tr>
		<tr>
			<td>
				timestamp
			</td>
			<td>
				date
			</td>
			<td>
				<p>
					检索位置信息和创建 Position 对象的日期时间。
				</p>
			</td>
		</tr>
	</tbody>
</table>

### 示例

下面是一个使用 Position 对象的示例代码。其中 showLocation 方法是一个回调方法：

```javascript
function showLocation( position ) {
  var latitude = position.coords.latitude;
  var longitude = position.coords.longitude;
  ...
}
```

## 处理错误

地理定位是复杂的。非常需要我们捕获任意错误并优雅的处理它。

地理定位方法 getCurrentPosition() 和 watchPosition() 可以使用一个提供 __PositionError__ 对象的错误处理回调方法。这个对象有下列两属性。

<table>
	<tbody>
		<tr>
			<th>
				属性
			</th>
			<th>
				类型
			</th>
			<th>
				描述
			</th>
		</tr>
		<tr>
			<td>
				code
			</td>
			<td>
				Number
			</td>
			<td>
				<p>
					错误码。
				</p>
			</td>
		</tr>
		<tr>
			<td>
				message
			</td>
			<td>
				String
			</td>
			<td>
				<p>
					错误描述信息。
				</p>
			</td>
		</tr>
	</tbody>
</table>

下面这个表格描述了 PositionError 对象可能返回的错误码。

<table>
	<tbody>
		<tr>
			<th>
				错误码
			</th>
			<th>
				常量
			</th>
			<th>
				描述
			</th>
		</tr>
		<tr>
			<td>
				0
			</td>
			<td>
				UNKNOWN_ERROR
			</td>
			<td>
				<p>
					由于未知错误，检索设备位置信息失败。
				</p>
			</td>
		</tr>
		<tr>
			<td>
				1
			</td>
			<td>
				PERMISSION_DENIED
			</td>
			<td>
				<p>
					由于应用程序没有权限使用位置服务，检索设备位置信息失败。
				</p>
			</td>
		</tr>
		<tr>
			<td>
				2
			</td>
			<td>
				POSITION_UNAVAILABLE
			</td>
			<td>
				<p>
					设备位置信息无法确定。
				</p>
			</td>
		</tr>
		<tr>
			<td>
				3
			</td>
			<td>
				TIMEOUT
			</td>
			<td>
				<p>
					不能在给定的最大超时区间内检索位置信息。
				</p>
			</td>
		</tr>
	</tbody>
</table>

### 示例

下面是一个使用 PositionError 对象的示例代码。其中 errorHandler 方法是一个回调方法:

```javascript
function errorHandler( err ) {
  if (err.code == 1) {
    // access is denied
  }
  ...
}
```

## Position 选项

下面是 getCurrentPosition() 方法的实际语法：

```javascript
getCurrentPosition(callback, ErrorCallback, options)
```

其中第三个参数是指定一组检索设备地理位置选项的 __PositionOptions__ 对象。

下列选项可以指定为第三个参数：

<table>
	<tbody>
		<tr>
			<th>
				属性
			</th>
			<th>
				类型
			</th>
			<th>
				描述
			</th>
		</tr>
		<tr>
			<td>
				enableHighAccuracy
			</td>
			<td>
				Boolean
			</td>
			<td>
				<p>
					是否想要检索最精准的位置估值。默认值为 false。
				</p>
			</td>
		</tr>
		<tr>
			<td>
				timeout
			</td>
			<td>
				Number
			</td>
			<td>
				<p>
					timeout 属性就是 Web 应用程序要等待定位的毫秒数。
				</p>
			</td>
		</tr>
		<tr>
			<td>
				maximumAge
			</td>
			<td>
				Number
			</td>
			<td>
				<p>
					用于缓存位置信息的过期时间毫秒数。
				</p>
			</td>
		</tr>
	</tbody>
</table>

### 示例

下面这个示例代码展示了如何使用上面提到的方法：

```javascript
function getLocation() {
   var geolocation = navigator.geolocation;
   geolocation.getCurrentPosition(showLocation, errorHandler, {maximumAge: 75000});
}
```