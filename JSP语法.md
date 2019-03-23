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

### :notebook:JSP 动作元素 ###

与JSP指令元素不同的是，JSP动作元素在请求处理阶段起作用。JSP动作元素是用XML语法写成的。

利用JSP动作可以动态地插入文件、重用JavaBean组件、把用户重定向到另外的页面、为Java插件生成HTML代码。

动作元素只有一种语法，它符合XML标准：

`<jsp:action_name attribute="value" />`

动作元素基本上都是预定义的函数，JSP规范定义了一系列的标准动作，它用JSP作为前缀，可用的标准动作元素如下：

|语法|	描述|
|:---|:---|
|jsp:include|	在页面被请求的时候引入一个文件。|
|jsp:useBean|	寻找或者实例化一个JavaBean。|
|jsp:setProperty|	设置JavaBean的属性。|
|jsp:getProperty|	输出某个JavaBean的属性。|
|jsp:forward|	把请求转到一个新的页面。|
|jsp:plugin	|根据浏览器类型为Java插件生成OBJECT或EMBED标记。|
|jsp:element	|定义动态XML元素|
|jsp:attribute	|设置动态定义的XML元素属性。
|jsp:body	|设置动态定义的XML元素内容。|
|jsp:text|	在JSP页面和文档中使用写入文本的模板|

***

**常见的属性**

所有的动作要素都有两个属性：id属性和scope属性。

  **id属性：**

  >id属性是动作元素的唯一标识，可以在JSP页面中引用。动作元素创建的id值可以通过PageContext来调用。

  **scope属性：**

>该属性用于识别动作元素的生命周期。 id属性和scope属性有直接关系，scope属性定义了相关联id对象的寿命。 scope属性有四个可能的值： page(当前页面), request(请求), session(会话), 和 application (应用程序)。

***

**<jsp:include>动作元素**

`<jsp:include>动作元素用来包含静态和动态的文件。该动作把指定文件插入正在生成的页面。语法格式如下：`

`<jsp:include page="相对 URL 地址" flush="true" />`

　前面已经介绍过include指令，它是在JSP文件被转换成Servlet的时候引入文件，而这里的jsp:include动作不同，插入文件的时间是在页面被请求的时候。

以下是include动作相关的属性列表。

page :	包含在页面中的相对URL地址。
flush :	布尔属性，定义在包含资源前是否刷新缓存区。

***

**实例**

以下我们定义了两个文件 date.jsp 和 main.jsp，代码如下所示：

date.jsp文件代码：

```java
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<p>
   今天的日期是: <%= (new java.util.Date()).toLocaleString()%>
</p>
```

main.jsp文件代码：

```java
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<body>

<h2>include 动作实例</h2>
<jsp:include page="date.jsp" flush="true" />

</body>
</html>
```

现在将以上两个文件放在服务器的根目录下，访问main.jsp文件即可。

***

**<jsp:useBean>动作元素**

jsp:useBean 动作用来加载一个将在JSP页面中使用的JavaBean。即类对象引入与访问

这个功能非常有用，因为它使得我们可以发挥 Java 组件复用的优势。

jsp:useBean动作最简单的语法为：

`<jsp:useBean id="name" class="package.class" />`

name是类实例化的名称，class是类/包引入的url。

在JSP中如果要应用JSP提供的Javabean的标签来操作简单类的话，则此类必须满足如下的开发要求：

 * (1)所有的类必须放在一个包中，在WEB中没有包的是不存在的；

 * (2)所有的类必须声明为public class，这样才能够被外部所访问；

 * (3)类中所有的属性都必须封装，即：使用private声明；

 * (4)封装的属性如果需要被外部所操作，则必须编写对应的setter、getter方法；

 * (5)一个JavaBean中至少存在一个无参构造方法，此为JSP中的标签所使用。  
 
在类载入后，我们既可以通过 `jsp:setProperty` 和 `jsp:getProperty `动作来修改和检索bean的属性。

***

如下是Student类的代码：

```java
package Deal;

public class Student {
    private int ID;
    private String Name;
    public  Student(){
        
    }
    public  Student(int i,String n){
        ID = i;
        Name = n;
    }
    public String getName(){
        return  Name;
    }
    public  int getID(){
        return  ID;
    }
    public  void setID(int id){
        ID =id;
    }
    public  void setName(String name){
        Name = name;
    }
}
```

下面就可以在jsp中使用这个：

```java
  <body>
        <jsp:useBean id="stu" class="Deal.Student"  ></jsp:useBean>

        <%
            stu.setID(26);           //赋值
            stu.setName("lumnca");
        %>

         <h2> ID:<%=stu.getID() %> </h2>      //获取
         <h2> Name:<%=stu.getName() %> </h2>
  </body>
```

当然也可以使用`jsp:setProperty` 和 `jsp:getProperty `动作来修改和检索bean的属性。

```java
  <body>
        <jsp:useBean id="stu" class="Deal.Student"  ></jsp:useBean>

        <jsp:setProperty name="stu" property="ID" value="206" ></jsp:setProperty>
        <jsp:setProperty name="stu" property="name" value="Lumnca"></jsp:setProperty>


         <h2> ID: <jsp:getProperty name="stu" property="ID"></jsp:getProperty> </h2>
         <h2> Name:<%=stu.getName() %> </h2>
  </body>
```

从上面可以看出`jsp:setProperty` 和 `jsp:getProperty `动作主要参数为name，property。对于`jsp:setProperty`含有value参数用于修改值。

***

**<jsp:forward> 动作元素**

　jsp:forward动作把请求转到另外的页面。jsp:forward标记只有一个属性page。语法格式如下所示：

`<jsp:forward page="相对 URL 地址" />`

有关其他动作不做解释。

