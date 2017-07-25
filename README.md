# 前端JS命名规范 
 
本篇主要介绍JS的命名规范、注释规范以及框架开发的一些问题。<br/>
目录<br/>
1. 命名规范：介绍变量、函数、常量、构造函数、类的成员等等的命名规范<br/>
2. 注释规范：介绍单行注释、多行注释以及函数注释<br/>
3. 框架开发：介绍全局变量冲突、单全局变量以及命名空间<br/>
 
1. 命名规范<br/>
驼峰式命名法介绍：<br/>
驼峰式命名法由小(大)写字母开始，后续每个单词首字母都大写。<br/>
按照第一个字母是否大写，分为：<br/>
① Pascal Case 大驼峰式命名法：首字母大写。eg：StudentInfo、UserInfo、ProductInfo <br/>
② Camel Case 小驼峰式命名法：首字母小写。eg：studentInfo、userInfo、productInfo  <br/>
1.1 变量  <br/>
命名方法：小驼峰式命名法。<br/>
命名规范：前缀应当是名词。(函数的名字前缀为动词，以此区分变量和函数)<br/>
命名建议：尽量在变量名字中体现所属类型，如:length、count等表示数字类型；而包含name、title表示为字符串类型。<br/>
示例：<br/>
1	// 好的命名方式<br/>
2	var maxCount = 10;<br/>
3	var tableTitle = 'LoginTable';<br/>
4	 
5	// 不好的命名方式<br/>
6	var setCount = 10;<br/>
7	var getTitle = 'LoginTable';<br/>


1.2 函数<br/>
命名方法：小驼峰式命名法。<br/>
命名规范：前缀应当为动词。<br/>
命名建议：可使用常见动词约定<br/>
<table>
  <thead>
    <tr><td>动词</td><td>含义</td><td>返回值</td></tr>
  </thead>
  <tbody>
    <tr><td>can</td><td>判断是否可执行某个动作(权限)</td><td>函数返回一个布尔值。true：可执行；false：不可执行</td></tr>
    <tr><td>has</td><td>判断是否含有某个值</td><td>函数返回一个布尔值。true：含有此值；false：不含有此值</td></tr>
    <tr><td>is</td><td>判断是否为某个值</td><td>数返回一个布尔值。true：为某个值；false：不为某个值</td></tr>
    <tr><td>get</td><td>获取某个值</td><td>函数返回一个非布尔值</td></tr>
    <tr><td>set</td><td>设置某个值</td><td>无返回值、返回是否设置成功或者返回链式对象</td></tr>
    <tr><td>load</td><td>加载某些数据</td><td>无返回值或者返回是否加载完成的结果</td></tr>
  </tbody>
</table><br>
<br>
示例：<br>
1	// 是否可阅读<br>
2	function canRead() {<br>
3	    return true;<br>
4	}<br>
5	 <br>
6	// 获取名称<br>
7	function getName() {<br>
8	    return this.name;<br>
9	}<br>
 <br>
1.3 常量<br>
命名方法：名称全部大写。<br>
命名规范：使用大写字母和下划线来组合命名，下划线用以分割单词。<br>
命名建议：无。<br>
示例：<br>
1	var MAX_COUNT = 10;<br>
2	var URL = 'http://www.baidu.com';<br>
 <br>
1.4 构造函数<br>
介绍：在JS中，构造函数也属于函数的一种，只不过采用new 运算符创建对象。<br>
命名方法：大驼峰式命名法，首字母大写。<br>
命名规范：前缀为名称。<br>
命名建议：无。<br>
示例：<br>
1	function Student(name) {<br>
2	    this.name = name;<br>
3	}<br>
4	 <br>
5	var st = new Student('tom');<br>
 <br>
1.5 类的成员<br>
类的成员包含：<br>
① 公共属性和方法：跟变量和函数的命名一样。<br>
② 私有属性和方法：前缀为_(下划线)，后面跟公共属性和方法一样的命名方式。<br>
示例：<br>
1	function Student(name) {<br>
2	    var _name = name; // 私有成员<br>
3	 <br>
4	    // 公共方法<br>
5	    this.getName = function () {<br>
6	        return _name;<br>
7	    }<br>
8	 <br>
9	    // 公共方式<br>
10	    this.setName = function (value) {<br>
11	        _name = value;<br>
12	    }<br>
13	}<br>
14	var st = new Student('tom');<br>
15	st.setName('jack');<br>
16	console.log(st.getName()); // => jack：输出_name私有变量的值<br>
 
2. 注释规范<br>
JS支持两种不同类型的注释：单行注释和多行注释。<br>
2.1 单行注释<br>
说明：单行注释以两个斜线开始，以行尾结束。<br>
语法：// 这是单行注释<br>
使用方式：<br>
① 单独一行：//(双斜线)与注释文字之间保留一个空格。<br>
② 在代码后面添加注释：//(双斜线)与代码之间保留一个空格，并且//(双斜线)与注释文字之间保留一个空格。<br>
③ 注释代码：//(双斜线)与代码之间保留一个空格。<br>
示例：<br>
1	// 调用了一个函数；1)单独在一行<br>
2	setTitle();<br>
3	 <br>
4	var maxCount = 10; // 设置最大量；2)在代码后面注释<br>
5	 <br>
6	// setName(); // 3)注释代码<br>
 
2.2 多行注释<br>
说明：以/*开头，*/结尾<br>
语法：/* 注释说明 */<br>
使用方法：<br>
① 若开始(/*)和结束(*/)都在一行，推荐采用单行注释。<br>
② 若至少三行注释时，第一行为/*，最后行为*/，其他行以*开始，并且注释文字与*保留一个空格。<br>
示例：<br>
1	/*<br>
2	* 代码执行到这里后会调用setTitle()函数<br>
3	* setTitle()：设置title的值<br>
4	*/<br>
5	setTitle();<br>
 
2.3 函数(方法)注释<br>
说明：函数(方法)注释也是多行注释的一种，但是包含了特殊的注释要求，参照 javadoc(百度百科)。<br>
语法：<br>
/** <br>
* 函数说明 <br>
* @关键字 <br>
*/<br>
常用注释关键字：(只列出一部分，并不是全部)<br>

<table>
  <thead>
    <tr><td>注释名</td><td>语法</td><td>含义</td><td>示例</td></tr>
  </thead>
  <tbody>
    <tr><td>@param</td><td>@param 参数名 {参数类型}</td><td>描述参数的信息</td><td>@param name {String} 传入名称</td></tr>
    <tr><td>@return</td><td>@return {返回类型} 描述信息</td><td>描述返回值的信息</td><td>@return {Boolean} true:可执行;false:不可执行</td></tr>
    <tr><td>@author</td><td>@author 作者信息 [附属信息：如邮箱、日期]</td><td>描述此函数作者的信息</td><td>@author 张三 2015/07/21 （备注：插件、组件 以及类信息必填</td></tr>
    <tr><td>@version</td><td>@version XX.XX.XX</td><td>描述此函数的版本号</td><td>@version 1.0.3    （备注：插件、组件 必填）</td></tr>
    <tr><td>@example</td><td>@example 示例代码</td><td>演示函数的使用</td><td>@example setTitle('测试')    （备注：插件、组件 和调用复杂的方法必填）</td></tr>
  </tbody>
</table>
<br>
示例：<br>
1	/**<br>
2	* 合并Grid的行<br>
3	* @param grid {Ext.Grid.Panel} 需要合并的Grid<br>
4	* @param cols {Array} 需要合并列的Index(序号)数组；从0开始计数，序号也包含。<br>
5	* @param isAllSome {Boolean} ：是否2个tr的cols必须完成一样才能进行合并。true：完成一样；false(默认)：不完全一样<br>
6	* @return void<br>
7	* @author polk6 2015/07/21 <br>
8	* @example<br>
9	* _________________                              _________________<br>
10	* |  年龄 |  姓名 |                             |  年龄 |  姓名 |<br>
11	* -----------------      mergeCells(grid,[0])   -----------------<br>
12	* |  18   |  张三 |              =>             |       |  张三 |<br>
13	* -----------------                             -  18   ---------<br>
14	* |  18   |  王五 |                             |       |  王五 |<br>
15	* -----------------                             -----------------<br>
16	*/<br>
17	function mergeCells(grid, cols, isAllSome) {<br>
18	    // Do Something<br>
19	}<br>
 <br>
3. 框架开发<br>
3.1 全局变量冲突<br>
在团队开发或者引入第三方JS文件时，有时会造成全局对象的名称冲突，比如a.js有个全局函数sendMsg()，b.js也又有个全局函数sendMsg()，引入a.js和b.js文件时，会造成sendMsg()函数冲突。<br>
示例：<br>
a.js  代码如下：<br>
function sendMsg(){<br>
  console.log("a.js")<br>
}<br>
b.js  代码如下：<br>
function sendMsg(){<br>
  console.log("b.js")<br>
}<br>
页面中引入两个js文件<br>
<script src='a.js'></script><br>
<script src='b.js'></script><br>
<script><br>
  sendMsg();  =>  弹出“b.js”,b.js 会覆盖a.js<br>
</script><br>
 
3.2 单全局变量<br>
所创建的全局对象名称是独一无二的，并将所有的功能代码添加到这个全局对象上。调用自己所写的代码时，以这个全局对象为入口点。<br>
如：<br>
* JQuery的全局对象：$和JQuery<br>
示例：<br>
a.js  代码如下：<br>
var A =A||{};
A.sendMsg = function(){<br>
  console.log("a.js")<br>
}<br>
b.js  代码如下：<br>
var B =B||{}; <br>
B.sendMsg = function(){ <br>
  console.log("b.js") <br>
} <br>
页面中引入两个js文件<br>
<script src='a.js'></script>  <br>
<script src='b.js'></script>  <br>
<script><br>
  A.sendMsg();  =>  弹出“a.js”  <br>
  B.sendMsg();  =>  弹出“b.js”  <br>
</script> <br>
 
 
3.3 命名空间<br>
在项目规模日益壮大时，可采用命名空间方式对JS代码进行规范：即将代码按照功能进行分组，以组的形式附加到单全局对象上。<br>
以Ext的chart模块为例：<br>
<br>
Ext.chart.axis.Axis   <br>
Ext.chart.axis.Category   <br>
......   <br>
Ext.chart.series.Area   <br>
Ext.chart.series.Bar  <br>








