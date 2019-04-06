# :books:JSTL标签库 #

### :ledger:EL表达式语言 ###

EL表达式语言是用于在JSP页面中进行数据的存取操作。

#### :bookmark:EL与EL隐含对象 ####

所有的EL都以$定界。内容包括在{}中，如下：

```java
${变量}
```

>EL表达式中的常量与变量

EL表达式中的常量直接书写，对于EL来说，变量是一个存储了特定数据内容的符号，EL可以直接访问：

```jsp
  <body>
      <%
          application.setAttribute("b","Lumnca");
      %>
      <h2>${b}</h2>
      <p>${"ID:5523600"}</p>
  </body>
```

如上可以通过设置全局变量进行访问，这种方式可以让jsp读取到servelt的变量内容，也可以作为相互交互的变量。

>EL隐含对象

EL本身内建了11个隐含对象，用户可以通过这些对象，取得特定的网页信息，如下表：

|EL隐含对象分类|隐含对象|说明|
|:--:|:--:|:---------------|
|读取页面上下文|pageContext|取得网页运行环境的相关相信|
|读取JSP作用域|pageScope|取得page范围内特定属性的属性值|
|读取JSP作用域|requestScope|获取request范围内特定的属性值|
|读取JSP作用域|sessionScope|取得session范围内特定的属性值|
|读取JSP作用域|applicationScope|取得application范围内特定的属性值|
|读取客户端表单或查询字符串参数|param|取得request对象的单一参数|
|读取客户端表单或查询字符串参数|paramValues|取得request对象的参数值|
|获取request请求报头|header|取得request对象标头数学|
|获取request请求报头|headerValues|取得request对象标头值|
|读取Cookies|cookie|取得request对象的cookie|
|获取上下文初始化参数|initParam|取得网页运行环境的初始参数值|


如下是使用这几个对象的实例：

```jsp
  <body>
  <form>
    <label>用户</label>
    <input type="text" placeholder="用户" name="user"><br>
    <label>密码</label>
    <input type="password" placeholder="密码" name="pw"><br>
    <input type="submit" value="提交">
  </form>
      <%
          int num = 5;
          application.setAttribute("b","Lumnca");
          request.setAttribute("c","Kaiily");
          session.setAttribute("d","Remiry");
          Cookie cookie = new Cookie("user","lmc");
          cookie.setMaxAge(120);
          response.addCookie(cookie);
      %>

        <ul>
          <li>全局变量: ${applicationScope.get("b")}</li>
          <li>请求 ： ${requestScope.c}</li>
          <li>Session： ${sessionScope.d}</li>
          <li>Cookie ： ${cookie.user.value}</li>
            <li>表单输入1：${param.user}</li>
            <li>表单输入2：${param.pw}</li>
        </ul>

          <ul>
            <li>全局变量:${b}</li>
            <li>请求 ：${c}</li>
            <li>Session：${d}</li>
          </ul>
  </body>
 ```
 
 其中对于请求与相应和全局对象可以直接用变量名直接显示，其余的需要使用实例对象的方法来获取。某些方法还可以使用get来获取。也可以通过request来获取。如果添加类对象的话，也可以使用成员运算符访问。
 
### :ledger:核心标签 ###
 
核心标签提供了一般性的语言功能，例如变量，循环，条件控制及基本输入输出，URL相关操作等，这种标签以字母c为前缀词，如下：

```java
<c:out value="Hello"/>
```
上面可以显示hello，使用核心标签首先需要引入JSTL包，下载地址[JSTL库](http://static.runoob.com/download/jakarta-taglibs-standard-1.1.2.tar.gz)

下载 jakarta-taglibs-standard-1.1.2.zip 包并解压，将 jakarta-taglibs-standard-1.1.2/lib/ 下的两个 jar 文件：standard.jar 和 jstl.jar 文件拷贝到 /WEB-INF/lib/ 下。

将 tld 下的需要引入的 tld 文件复制到 WEB-INF 目录下。

接下来我们在 web.xml 文件中添加以下配置：

```xml
    <jsp-config>
    <taglib>
    <taglib-uri>http://java.sun.com/jsp/jstl/fmt</taglib-uri>
    <taglib-location>/WEB-INF/fmt.tld</taglib-location>
    </taglib>
    <taglib>
    <taglib-uri>http://java.sun.com/jsp/jstl/fmt-rt</taglib-uri>
    <taglib-location>/WEB-INF/fmt-rt.tld</taglib-location>
    </taglib>
    <taglib>
    <taglib-uri>http://java.sun.com/jsp/jstl/core</taglib-uri>
    <taglib-location>/WEB-INF/c.tld</taglib-location>
    </taglib>
    <taglib>
    <taglib-uri>http://java.sun.com/jsp/jstl/core-rt</taglib-uri>
    <taglib-location>/WEB-INF/c-rt.tld</taglib-location>
    </taglib>
    <taglib>
    <taglib-uri>http://java.sun.com/jsp/jstl/sql</taglib-uri>
    <taglib-location>/WEB-INF/sql.tld</taglib-location>
    </taglib>
    <taglib>
    <taglib-uri>http://java.sun.com/jsp/jstl/sql-rt</taglib-uri>
    <taglib-location>/WEB-INF/sql-rt.tld</taglib-location>
    </taglib>
    <taglib>
    <taglib-uri>http://java.sun.com/jsp/jstl/x</taglib-uri>
    <taglib-location>/WEB-INF/x.tld</taglib-location>
    </taglib>
    <taglib>
    <taglib-uri>http://java.sun.com/jsp/jstl/x-rt</taglib-uri>
    <taglib-location>/WEB-INF/x-rt.tld</taglib-location>
    </taglib>
    </jsp-config>
```


 
 
