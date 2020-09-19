# Cookie 和 Session 对象

`Cookie` 是最常用的Http会话跟踪机制，且所有`Servlet容器`都应该支持。当客户端不接受`Cookie`时，服务端可使用`URL重写`的方式作为会话跟踪方式。会话`ID`必须被编码为URL字符串中的一个路径参数，参数的名字必须是 `jsessionid`。

浏览器和服务端创建会话(`Session`)后，服务端将生成一个唯一的会话ID(`sessionid`)用于标识用户身份，然后会将这个会话ID通过`Cookie`的形式返回给浏览器，浏览器接受到`Cookie`后会在每次请求后端服务的时候带上服务端设置`Cookie`值，服务端通过读取浏览器的`Cookie`信息就可以获取到用于标识用户身份的会话ID，从而实现会话跟踪和用户身份识别。

因为`Cookie`中存储了用户身份信息，并且还存储于浏览器端，攻击者可以使用`XSS`漏洞获取到`Cookie`信息并盗取用户身份就行一些恶意的操作。
