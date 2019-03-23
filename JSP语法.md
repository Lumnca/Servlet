# :memo:JSP语法 #

### :notebook:脚本代码 ###

在JSP中可以添加java代码向下面所示：

```java
  <body>
        <% out.println("Hello World"); %>

        <jsp:scriptlet>
            out.println("Hello World"); 
        </jsp:scriptlet>
  </body>
```

前者`  <%  代码  %>`是标签形式，具有代码提示。后者是XML形式不具有代码提示，最好使用前者。

### :notebook:JSP声明 ###

一个声明语句可以声明一个或多个变量、方法，供后面的Java代码使用。在JSP文件中，您必须先声明这些变量和方法然后才能使用它们。

JSP声明的语法格式：

```java
  <body>
        <%!
          int a = 5;
          String s ="Hello";
        %>

        <% out.println(a); int c = 7; %>
        <% out.println(s+c); %>
  </body>
```

可以看到`  <%! 代码  %>`与`<%  代码  %>`均可以声明变量。两者并没有太大的差别。

### :notebook:JSP表达式 ###

前面我们可以看到我们的输出显示变量需要使用out.println，下面这种形式可以直接输出变量：

```java
  <body>
        <%!
          int a = 5;
          String s ="Hello";
        %>
        <h2> <%=a %> </h2>
         <i> <%=s %> </i>
  </body>
```

下表是注释以及转义的写法：

|语法|说明|
|:--|:--|
|`<%-- 注释 --%>`|	JSP注释，注释内容不会被发送至浏览器甚至不会被编译|
|`<!-- 注释 -->`|	HTML注释，通过浏览器查看网页源代码时可以看见注释内容|
|`<\%	`|代表静态 `<%`常量|
|`%\>`	|代表静态` %> `常量|
|`\'	`|在属性中使用的单引号|
|`\"`|	在属性中使用的双引号|

### :notebook:指令 ###

JSP指令用来设置整个JSP页面相关的属性，如网页的编码方式和脚本语言。

语法格式如下：

