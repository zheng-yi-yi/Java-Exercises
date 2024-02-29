<div align="center">

<h1>Web开发 (Web Development)</h1>

</div>


---

【多选题】在 `J2EE` 中，使用 `Servlet` 过滤器，需要在`web.xml`中配置（）元素

A. `<filter>`

B. `<filter-mapping>`

C. `<servlet-filter>`

D. `<filter-config>`

<details>
<summary> 查看答案</summary>

**正确答案：AB**

`Servlet`过滤器的配置包括两部分：

- 第一部分是过滤器在 `Web` 应用中的定义，由 `<filter>` 元素表示，包括 `<filter-name>` 和 `<filter-class>` 两个必需的子元素
- 第二部分是过滤器映射的定义，由 `<filter-mapping>` 元素表示，可以将一个过滤器映射到一个或者多个 `Servlet` 或 `JSP` 文件，也可以采用 `url-pattern` 将过滤器映射到任意特征的`URL`。



</details>

---

【单选题】下面哪个不属于 `HttpServletResponse` 接口完成的功能？

A. 设置HTTP头标

B. 设置cookie

C. 读取路径信息

D. 输出返回数据

<details>
<summary> 查看答案</summary>

**正确答案：C**

选项C "读取路径信息" 不属于 `HttpServletResponse` 接口完成的功能。

`HttpServletResponse`接口主要用于向客户端发送响应信息，包括设置`HTTP头标`（选项A）、设置`cookie`（选项B）和输出返回数据（选项D）。

读取路径信息通常是`HttpServletRequest`的职责，它用于处理来自客户端的请求信息。

```java
// 举例：
// 设置HTTP头标   
response.setHeader("Refresh","3"); //三秒刷新页面一次

// 设置cookie 
Cookie c1 = new Cookie("username","only");
response.addCookie(c1);

// 读取路径信息,request读取路径信息
request.getRealPath("url"); // 虚拟目录映射为实际目录
request.getRealPath("./");    // 网页所在的目录
request.getRealPath("../"); // 网页所在目录的上一层目录
request.getContextPath();    // 应用的web目录的名称

// 输出返回数据
HttpServleteResponse.getOutputStream().write();
```
</details>

---

<!-- <details>
<summary> 查看答案</summary>

**正确答案：**

知识点：



</details> -->