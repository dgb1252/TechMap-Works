# 1.任务1-4

以下序号表示任务的id

1. 前中后序遍历还好，利用递归设置好输出位置就行
2. 实现之初遇到了很多次的栈溢出(递归的死循环)，解决方案:
   - 设置了一个变量(来识别当前是左子节点还是右子节点)
   - 本质上就是：根节点左右输出，再用递归分别让左右子节点再执行

4. 任务3我是最后做的，如果是不改变中序的话(以下以待删除节点为出发点)
   1. 只有左子树，那就直接把左子树拿上来
   2. 没有子树，直接让父节点删除这个节点
   3. 剩下的情况(只要是有右子树)，那就是把右子节点的最左边的节点拿上来(因为中序是先输出最左边的)
   4. 遇到的问题:
      - **和单向链表一样，若要删除就要从父节点开始判断**，但是二叉树相当于一个节点指向俩个方向，所有很多if判断，上面本来就有三种情况再有俩方向还要判断不为空。
      - 导致写起来很窝火，不过思路清晰慢慢来还是能写出来

3. 最初思路，想直接通过每个节点比较来进行输出(后来发现我是实现不了的,因为我当时只会递归，如果用递归来做的话，俩递归放一个递归方法里不就乱套了吗，于是我就学习了非递归遍历)，利用Stack()函数的特性(相当于是倒着的单项链表,压栈出栈嘛)将俩二叉树弄出来O(m+n),因为本身是二叉搜索树，中序遍历出来是有序的，直接合并O(m+n)就行了俩时间复杂度O(2m+2n)==O(m+n)

# 2.任务5

这5个任务我都是有学习笔记的(相对于前两次任务，发现笔记很重要，还是详细的好)，但是笔记中图片较多，就只带上http的笔记

## 1.http

### 1.什么是http

http(超文本传输协议)是一个简单的请求-响应协议，它通常运行在TCP之上.

- 文本:html,字符串...
- 超文本:图片,音乐,视频,定位,地图...
- 默认端口80

https:(security)安全的

- 默认端口443

### 2.两个时代

- http 1.0
  - HTTP/1.0:客户端可以与Web服务器连接后,只能获得一个web资源,断开连接
- http 2.0
  - HTTP/1.1:可以获得多个web资源

### 3.Http请求

- 客户端---发请求(Request)---服务器

百度:

```java
请求 URL: https://www.baidu.com/
请求方法: GET
状态代码: 200 OK
远程地址: 14.215.177.38:443
引用站点策略: no-referrer-when-downgrade
```

```java
Accept: text/html
Accept-Encoding: gzip, deflate, br
Accept-Language: zh-CN,zh;q=0.9,en;q=0.8,en-GB;q=0.7,en-US;q=0.6
Cache-Control: max-age=0
Connection: keep-alive
```

#### 1.请求行

- 请求行中的请求方式:GET
- 请求方式GET/POST/HEAD/DELETE/PUT/TRACT
  - GET:请求能够携带的参数比较少,大小有限制,会在浏览器的URL地址栏显示数据内容,不安全,但是高效
  - post:请求能够携带的参数没有限制,大小没有限制,不会在浏览器的URL地址栏显示数据内容,安全,但是不高效

#### 2.请求头

```java
Accept                  告诉浏览器,它所支持的数据类型
Accept-Encoding         支持哪种编码格式   GBK   UTF-8   GB2312   ISO8859-1
Accept-Language         告诉浏览器,它的语言环境
Cache-Control           缓存控制
Connection              告诉浏览器,请求完成是断开还是保存连接
```

### 4.Http相应

- 服务器--相应---客户端

```java
Cache-Control: private      缓存控制
Connection: keep-alive      说明走的是http1.1
Content-Encoding: gzip
Content-Type: text/html;charset=utf-8
```

#### 1.响应体

```java
Accept                  告诉浏览器,它所支持的数据类型
Accept-Encoding         支持哪种编码格式   GBK   UTF-8   GB2312   ISO8859-1
Accept-Language         告诉浏览器,它的语言环境
Cache-Control           缓存控制
Connection              告诉浏览器,请求完成是断开还是保存连接
Refresh                 告诉客户端多久刷新一次
Location                让网页重新定位
```

#### 2.响应状态码

200:请求响应成功             200

3**:请求重定向

- 重定向:你重新到我给你的新位置去

4**:找不到资源                 404

- 资源不存在

5**:服务器代码错误         500

- 502网关错误

