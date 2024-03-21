# **(面试题一)在浏览器地址栏输入地址，按下回车键后，发生了哪些事情？**
* 1. 浏览器自动补全协议与端口
* 2. 浏览器自动完成url编码
* 3. 浏览器根据url地址查找本地缓存，根据缓存规则查看是否命中缓存，若命中缓存则直接使用缓存，不再发出请求。（一般页面不会去查找缓存）
* 4. 通过DNS解析找到服务器的IP地址
* 5. 浏览器向服务器发出建立TCP连接的申请，完成三次握手后，连接通道建立
* 6. 若使用了HTTPS协议，则还会进行SSL握手，建立加密信道。使用SSL握手时，会确定是否用HTTP2
* 7. 浏览器决定要附带哪些cookie到请求头中去
* 8. 浏览器自动设置好请求头，协议版本，cookie，发出GET请求
* 9. 服务器处理请求，进入后端处理流程。完成处理后，服务器响应一个HTTP报文给浏览器。
* 10. 浏览器根据使用的协议版本，以及Connection字段的约定，决定是否要保留TCP连接。
* 11. 浏览器根据响应状态码决定如何处理这一次响应
* 12. 浏览器根据响应头中的content-type字段识别响应类型，如果是text/html，则对响应体中的内容进行HTML解析，否则做其它处理
* 13. 浏览器根据响应头的其它内容完成缓存，cookie的设置
* 14. 浏览器开始从上到下解析HTML，若遇到外部资源链接，则进一步请求资源
* 15. 解析过程中生成DOM树，CSSOM树，一边生成，一边把二者合并为渲染树。然后对渲染树中的每个节点进行计算位置和大小，最后把每个节点用GPU绘制到屏幕
* 16. 解析过程中还会触发一系列的事件，当DOM树完成后会触发DOMContentLoaded事件，当所有资源加载完毕后会出发load事件。