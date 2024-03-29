# **(面试题一)HTTP常见的请求方法有哪些？**
* 答：
    * GET:表示向服务器获取资源。业务数据在请求行中，无需请求体。
    * POST:表示向服务器提交信息，通常用于产生新的数据，比如注册。业务数据在请求体中。
    * PUT:表示希望修改服务器的数据，通常用于修改。业务数据在请求体中。
    * DELETE:表示希望删除服务器数据。业务数据在请求行中，无需请求体。
    * OPTIONS:发生在跨域的预检请求中，表示客户端向服务器申请跨域提交。
    * TRACE：主要用于测试和诊断。
    * CONNECT:用于建立连接管道，通常在代理场景中使用。
# **(面试题二)简要说明GET与POST的区别？**
* 答：由于浏览器和服务器间约定俗成的规则，造成了GET和POST请求在web中的区别：
    1. 浏览器在发送GET请求时，不会附带请求体。而发送POST请求时，会附带请求体。
    2. GET在请求行中传递的信息量有限(浏览器规定请求行和请求头长度有限)，适合传递少量数据；POST请求在请求体中传递信息量是没有限制的，适合传输大量数据。
    3. GET请求只能传递ASCII数据(浏览器规定请求行中只能传递ASCII数据，但如果传递了非ASCII码，浏览器会自动帮助进行编码)，遇到非ASCII数据需要进行编码；POST请求没有限制。
    4. 大部分GET请求传递的数据都附在path参数中，能通过分享地址完整的重现页面，同时暴露了所有请求用到的数据。若碰到敏感数据，不应该使用GET方式请求，至少不应该放到path中。
    5. 刷新页面时，若当前的页面是通过POST请求得到的，则浏览器会提示用户是否重新提交。若是GET请求得到的页面则没有提示。

# 请求方法的本质（了解）
* 答： http请求协议中并没有指定请求方法，只给出请求方法的建议，具体请求方法需要根据服务器和浏览器间的约定来确定。
    * ![alt text](image-3.png)

# 请描述下http请求消息的结构(面试题1)
* 请求行(Request Line)
    * 由三部分构成请求行，之间用空格分隔：
        1. HTTP请求方法
        2. 请求的URL
        3. HTTP协议
* 请求头部(Headers)
    * 请求头由多个键值对组成，每个键值对表示一个头部字段和它的值，每个头独占一行。常见的请求头部字段：
        * Host：请求的主机名 or IP地址
        * User-Agent:发送请求的用户代理信息
        * Content-Type:请求体类型
        * Content-Length:请求体长度
        * Cookie:客户端发送给服务器的Cookie信息。
* 空行(Empty Line)
    * 空行用于分隔请求头部和请求体。
* 请求体(Body)
    * 请求体包含发送给服务器的数据，例如POST请求中包含的表单数据、JSON数据等。
* 注意：不是所有的HTTP请求都包含请求体，比如GET请求通常不包含请求体，而POST请求通常包含请求体。