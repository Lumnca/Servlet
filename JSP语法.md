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

`<%@ directive attribute="value" %>`

指令可以有很多个属性，它们以键值对的形式存在，并用逗号隔开。

JSP中的三种指令标签：


|指令|	描述|
|:---|:----|
|`<%@ page ... %>`|	定义网页依赖属性，比如脚本语言、error页面、缓存需求等等|
|`<%@ include ... %>`	|包含其他文件|
|`<%@ taglib ... %>`|	引入标签库的定义|

**Page指令**

Page指令为容器提供当前页面的使用说明。一个JSP页面可以包含多个page指令。

Page指令的语法格式：

`<%@ page attribute="value" %>`

等价的XML格式：

`<jsp:directive.page attribute="value" /`

|属性	|描述|
|:---|:----|
|buffer|	指定out对象使用缓冲区的大小|
|autoFlush|	控制out对象的 缓存区|
|contentType|	指定当前JSP页面的MIME类型和字符编码|
|errorPage|	指定当JSP页面发生异常时需要转向的错误处理页面|
|isErrorPage|	指定当前页面是否可以作为另一个JSP页面的错误处理页面|
|extends	|指定servlet从哪一个类继承|
|import	|导入要使用的Java类|
|info	|定义JSP页面的描述信息|
|isThreadSafe|	指定对JSP页面的访问是否为线程安全|
|language|	定义JSP页面所用的脚本语言，默认是Java|
|session|	指定JSP页面是否使用session|
|isELIgnored|	指定是否执行EL表达式|
|isScriptingEnabled|	确定脚本元素能否被使用|

**Include指令**

JSP可以通过include指令来包含其他文件。被包含的文件可以是JSP文件、HTML文件或文本文件。包含的文件就好像是该JSP文件的一部分，会被同时编译执行。

Include指令的语法格式如下：

`<%@ include file="文件相对 url 地址" %>`

include 指令中的文件名实际上是一个相对的 URL 地址。

如果您没有给文件关联一个路径，JSP编译器默认在当前路径下寻找。

等价的XML语法：

`<jsp:directive.include file="文件相对 url 地址" />`

**Taglib指令**

JSP API允许用户自定义标签，一个自定义标签库就是自定义标签的集合。

Taglib指令引入一个自定义标签集合的定义，包括库路径、自定义标签。

Taglib指令的语法：

`<%@ taglib uri="uri" prefix="prefixOfTag" %>`

uri属性确定标签库的位置，prefix属性指定标签库的前缀。

等价的XML语法：

`<jsp:directive.taglib uri="uri" prefix="prefixOfTag" />`



