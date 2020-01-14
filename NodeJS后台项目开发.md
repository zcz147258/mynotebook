## NodeJS后台项目开发

### 1.后台常用的UI框架ElementUI、LayUI

### 2.任务

1）创建数据库及对应的数据表

2）登录验证

3）后台操作cookie

4）操作数据库实现相关信息的增删改查

5）分页处理

### 3.项目实施

#### 3.1 搭建项目环境

```
a.安装node.js
	去网站下载并安装(http://nodejs.cn)
	用node -v测试是否安装成功及版本号。
b.安装express(后台框架，依赖于node.js)（建议自学koa.js框架，它也是依赖于node.js的一个后台框架）
	用express --version测试是否安装成功及版本号。如果没有安装，请用下面的命令安装：
	如果没有安装yarn，请安装：npm i yarn -g
	yarn add express -g
	或：
	cnpm install express --global
c.安装express-generator(生成器，用它来生成项目环境)
	yarn add express-generator -g
	或：
	cnpm i express-generator -g
d.生成项目（搭建后台项目环境）
	express -e 项目名(项目名中不能汉字、空格和其他符号，最好也不要用大写字母)
	说明：-e表示在后台项目中可以使用ejs模板引擎；如果不加，则默认的模板引擎是jade。
e.安装依赖包
    cd 项目名
    yarn/npm i/cnpm i
f.修改端口
    app.js中倒数第二行添加：
    	app.listen(80,() => {
            console.log('服务器已启动！');
        })
g.启动项目
	node app
```

#### 3.2 整理项目文件夹

​		1）删除public目录中原有的内容。

​		2）将admin前端项目文件复制到项目的public目录下，重启项目。

​		3）浏览器显示结果如下：

![](1.png)

#### 3.3 修改首面默认跳转

​		修改admin中的index.html首页文件的跳转。

![2](2.png)

#### 3.4 登录实现

##### 3.4.1 前端实现

![3](3.png)

​		注意：上面代码中的$('form').serialize()是将所有表单组件中含有name属性的内容发向服务器端。

##### 3.4.2 后台实现

![4](4.png)

​		注意：前端代码修改不需要重启服务，而后台代码必须重启服务！

##### 3.4.3 验证登录

cookie用法：

添加cookie  							res.cookie(变量名，值)

删除（清空）cookie  			 res.clearCookie(变量名)

修改cookie							   res.cookie(变量名，新的值)

获取cookie							   req.cookies.变量名

```
cookie与本地存储的区别：
    1. cookie在浏览器和服务器间来回传递。而sessionStorage和localStorage不会自动把数据发给服务器，仅在本地保存。
    2. cookie数据还有路径（path）的概念，可以限制cookie只属于某个路径下。存储大小限制也不同，cookie数据不能超过4k，同时因为每次http请求都会携带cookie，所以cookie只适合保存很小的数据，如会话标识。sessionStorage和localStorage 虽然也有存储大小的限制，但比cookie大得多，可以达到5M或更大。
    3. 数据有效期不同，sessionStorage：仅在当前浏览器窗口关闭前有效，自然也就不可能持久保持；localStorage：始终有效，窗口或浏览器关闭也一直保存，因此用作持久数据；cookie只在设置的cookie过期时间之前一直有效，即使窗口或浏览器关闭。
    4. 作用域不同，sessionStorage不在不同的浏览器窗口中共享，即使是同一个页面；localStorage 在所有同源窗口中都是共享的；cookie也是在所有同源窗口中都是共享的。Web Storage 支持事件通知机制，可以将数据更新的通知发送给监听者。Web Storage 的 api 接口使用更方便。
```

​		提示：谷歌清除cookie的快捷键是Ctrl+Shift+Del。

后台代码：

![5](5.png)

前端代码：

![6](6.png)

#### 3.5 导航栏代码抽离，形成JS文件

1）抽离userlist中的代码

![](19.png)

2）在webstorm中新建一个JS文件，将上面的代码复制过来，结果如下：

```
var nav = '<div class="navbar-default sidebar" role="navigation">\n' +
  '\t\t\t\t\t<div class="sidebar-nav navbar-collapse">\n' +
  '\t\t\t\t\t\t<ul class="nav" id="side-menu">\n' +
  '\t\t\t\t\t\t\t<li>\n' +
  '\t\t\t\t\t\t\t\t<a href="#"><i class="fa fa-bar-chart-o fa-fw"></i> 库存管理<span class="fa arrow"></span></a>\n' +
  '\t\t\t\t\t\t\t\t<ul class="nav nav-second-level">\n' +
  '\t\t\t\t\t\t\t\t\t<li>\n' +
  '\t\t\t\t\t\t\t\t\t\t<a href="receiptplanlist.html">进货计划</a>\n' +
  '\t\t\t\t\t\t\t\t\t</li>\n' +
  '\t\t\t\t\t\t\t\t\t<li>\n' +
  '\t\t\t\t\t\t\t\t\t\t<a href="signlist.html">进货签收</a>\n' +
  '\t\t\t\t\t\t\t\t\t</li>\n' +
  '\t\t\t\t\t\t\t\t\t<li>\n' +
  '\t\t\t\t\t\t\t\t\t\t<a href="boundin.html">入库管理</a>\n' +
  '\t\t\t\t\t\t\t\t\t</li>\n' +
  '\t\t\t\t\t\t\t\t\t<li>\n' +
  '\t\t\t\t\t\t\t\t\t\t<a href="boundout.html">出库管理</a>\n' +
  '\t\t\t\t\t\t\t\t\t</li>\n' +
  '\t\t\t\t\t\t\t\t\t<li>\n' +
  '\t\t\t\t\t\t\t\t\t\t<a href="inventory.html">盘点管理</a>\n' +
  '\t\t\t\t\t\t\t\t\t</li>\n' +
  '\t\t\t\t\t\t\t\t</ul>\n' +
  '\t\t\t\t\t\t\t</li>\n' +
  '\t\t\t\t\t\t\t<li>\n' +
  '\t\t\t\t\t\t\t\t<a href="#"><i class="fa fa-bar-chart-o fa-fw"></i> 供货管理<span class="fa arrow"></span></a>\n' +
  '\t\t\t\t\t\t\t\t<ul class="nav nav-second-level">\n' +
  '\t\t\t\t\t\t\t\t\t<li>\n' +
  '\t\t\t\t\t\t\t\t\t\t<a href="ghsend.html">送货单管理</a>\n' +
  '\t\t\t\t\t\t\t\t\t</li>\n' +
  '\t\t\t\t\t\t\t\t\t<li>\n' +
  '\t\t\t\t\t\t\t\t\t\t<a href="ghreceive.html">收款单管理</a>\n' +
  '\t\t\t\t\t\t\t\t\t</li>\n' +
  '\t\t\t\t\t\t\t\t</ul>\n' +
  '\t\t\t\t\t\t\t</li>\n' +
  '\t\t\t\t\t\t\t<li>\n' +
  '\t\t\t\t\t\t\t\t<a href="#"><i class="fa fa-wrench fa-fw"></i> 财务管理<span class="fa arrow"></span></a>\n' +
  '\t\t\t\t\t\t\t\t<ul class="nav nav-second-level">\n' +
  '\t\t\t\t\t\t\t\t\t<li>\n' +
  '\t\t\t\t\t\t\t\t\t\t<a href="cwreceive.html">收款管理</a>\n' +
  '\t\t\t\t\t\t\t\t\t</li>\n' +
  '\t\t\t\t\t\t\t\t\t<li>\n' +
  '\t\t\t\t\t\t\t\t\t\t<a href="cwpay.html">付款管理</a>\n' +
  '\t\t\t\t\t\t\t\t\t</li>\n' +
  '\t\t\t\t\t\t\t\t</ul>\n' +
  '\t\t\t\t\t\t\t</li>\n' +
  '\t\t\t\t\t\t\t<li>\n' +
  '\t\t\t\t\t\t\t\t<a href="#"><i class="fa fa-wrench fa-fw"></i> 统计分析<span class="fa arrow"></span></a>\n' +
  '\t\t\t\t\t\t\t\t<ul class="nav nav-second-level">\n' +
  '\t\t\t\t\t\t\t\t\t<li>\n' +
  '\t\t\t\t\t\t\t\t\t\t<a href="tjin.html">进货单查询</a>\n' +
  '\t\t\t\t\t\t\t\t\t</li>\n' +
  '\t\t\t\t\t\t\t\t\t<li>\n' +
  '\t\t\t\t\t\t\t\t\t\t<a href="tjout.html">出库汇总表</a>\n' +
  '\t\t\t\t\t\t\t\t\t</li>\n' +
  '\t\t\t\t\t\t\t\t\t<li>\n' +
  '\t\t\t\t\t\t\t\t\t\t<a href="tjinsum.html">入库汇总表</a>\n' +
  '\t\t\t\t\t\t\t\t\t</li>\n' +
  '\t\t\t\t\t\t\t\t\t<li>\n' +
  '\t\t\t\t\t\t\t\t\t\t<a href="tjhasdetail.html">存货明细账</a>\n' +
  '\t\t\t\t\t\t\t\t\t</li>\n' +
  '\t\t\t\t\t\t\t\t\t<li>\n' +
  '\t\t\t\t\t\t\t\t\t\t<a href="tjshouldpay.html"> 应付货款报告</a>\n' +
  '\t\t\t\t\t\t\t\t\t</li>\n' +
  '\t\t\t\t\t\t\t\t\t<li>\n' +
  '\t\t\t\t\t\t\t\t\t\t<a href="tjsource.html">食材来源统计</a>\n' +
  '\t\t\t\t\t\t\t\t\t</li>\n' +
  '\t\t\t\t\t\t\t\t</ul>\n' +
  '\t\t\t\t\t\t\t</li>\n' +
  '\t\t\t\t\t\t\t<li>\n' +
  '\t\t\t\t\t\t\t\t<a href="#"><i class="fa fa-sitemap fa-fw"></i>基础数据<span class="fa arrow"></span></a>\n' +
  '\t\t\t\t\t\t\t\t<ul class="nav nav-second-level">\n' +
  '\t\t\t\t\t\t\t\t\t<li>\n' +
  '\t\t\t\t\t\t\t\t\t\t<a href="unitlist.html">单位管理</a>\n' +
  '\t\t\t\t\t\t\t\t\t</li>\n' +
  '\t\t\t\t\t\t\t\t\t<li>\n' +
  '\t\t\t\t\t\t\t\t\t\t<a href="supplierlist.html">供应商管理</a>\n' +
  '\t\t\t\t\t\t\t\t\t</li>\n' +
  '\t\t\t\t\t\t\t\t\t<li>\n' +
  '\t\t\t\t\t\t\t\t\t\t<a href="foodclasslist.html">菜品类别</a>\n' +
  '\t\t\t\t\t\t\t\t\t</li>\n' +
  '\t\t\t\t\t\t\t\t\t<li>\n' +
  '\t\t\t\t\t\t\t\t\t\t<a href="foodlist.html">菜品管理</a>\n' +
  '\t\t\t\t\t\t\t\t\t</li>\n' +
  '\t\t\t\t\t\t\t\t</ul>\n' +
  '\t\t\t\t\t\t\t</li>\n' +
  '\t\t\t\t\t\t\t<li>\n' +
  '\t\t\t\t\t\t\t\t<a href="#"><i class="fa fa-files-o fa-fw"></i> 系统管理<span class="fa arrow"></span></a>\n' +
  '\t\t\t\t\t\t\t\t<ul class="nav nav-second-level">\n' +
  '\t\t\t\t\t\t\t\t\t<li>\n' +
  '\t\t\t\t\t\t\t\t\t\t<a href="userlist.html">用户管理</a>\n' +
  '\t\t\t\t\t\t\t\t\t</li>\n' +
  '\t\t\t\t\t\t\t\t\t<li>\n' +
  '\t\t\t\t\t\t\t\t\t\t<a href="editpassword.html">修改密码</a>\n' +
  '\t\t\t\t\t\t\t\t\t</li>\n' +
  '\t\t\t\t\t\t\t\t\t<li>\n' +
  '\t\t\t\t\t\t\t\t\t\t<a href="log.html">日志管理</a>\n' +
  '\t\t\t\t\t\t\t\t\t</li>\n' +
  '\t\t\t\t\t\t\t\t\t<li>\n' +
  '\t\t\t\t\t\t\t\t\t\t<a href="login.html">退出系统</a>\n' +
  '\t\t\t\t\t\t\t\t\t</li>\n' +
  '\t\t\t\t\t\t\t\t</ul>\n' +
  '\t\t\t\t\t\t\t</li>\n' +
  '\t\t\t\t\t\t</ul>\n' +
  '\t\t\t\t\t</div>\n' +
  '\t\t\t\t</div>';
document.write(nav)
```

3）再将该JS文件复制到项目的pages->js目录下。

4）在需要引入该导航的地方引入该文件。

#### 3.6 新增用户

##### 3.6.1 思路

```
1）修改前端代码
2）获取表单组件对应的数据
3）将获取到的数据用ajax发向后台
4）获取前端传过来的数据
5）在后台将数据写入到数据表中
6）后台向前端返回结果
```

##### 3.6.2 修改前端代码

![7](7.png)

##### 3.6.3 将前端的数据发向后台

![8](8.png)

##### 3.6.4 修改account表结构

![9](9.png)

##### 3.6.5 后台功能实现

![10](10.png)

##### 3.6.6 将所有用户数据动态渲染到前端

1）前端向后台发ajax请求，获取所有用户数据

![11](11.png)

2）后台接口实现

![12](12.png)

3）引入template.js文件

![](14.png)

4）创建模板文件

![](15.png)

5）修改前端代码

![](16.png)

6）将模板的内容渲染到前端

![](17.png)7）渲染结果如下：

![](18.png)

#### 3.7 分页显示

1）前端分页

思路：将所有数据发向前端，前端遍历数据，将数据拆为二维数组，从而达到分页效果。

2）后端实现分页（分页尽量在后台实现，从而达到优化性能的效果。）

解决问题：

​		a.下标从哪开始

```
(page - 1) * pageSize
```

​		b.每页多条

```
pageSize
```

​		c.实现分页

```
命令格式：limit 起始下标,每页显示的条数

limit (page - 1) * pageSize,pageSize
```

​		d.将所有数据所占用的页码数发向前端

分页后的后台代码：

```
// 获取用户数据接口并实现后台分页
router.get('/getusers',(req,res) => {
	let page = req.query.page ? req.query.page : 1;
	let pageSize = 5;
	let start = (page - 1) * pageSize;

	conn.query('select * from users',(error,results) => {
		// res.send('' + results.length) // 后台不能直接向前端发数值型数据，如果发数值型数据，前端会视为该数字为状态码。
		let len = results.length;
		  // 如果传的有页码，则后台接的就是传过来的页码；如果没传，则默认为1
		
		// let str = 'select id,account,username,role,deparment,flag,sort from users order by sort limit ' + start +',' + pageSize;
		// let str = `select id,account,username,role,deparment,flag,sort from users order by sort limit "${start}","${pageSize}"`;
		let str = 'select id,account,username,role,deparment,flag,sort from users order by sort limit ?,?'
		// conn.query(str,(err,data) => {
		conn.query(str,[start,pageSize],(err,data) => {
			if(err){
				res.json({
					errorCode: 1
				})
			}else{
				res.json({
					errorCode: 0,
					data,// 发向前端分页后的数据
					len // 该表的总条数
				})
			}
		})
	})
	
})
```

3）前端分页实现

```
function showUsers(page){
            page = page?page : 1;
            $.ajax({
                url:'/getusers?page='+ page
            }).then(function(res){
                console.log(res);
                /*

                    <li class="paginate_button previous disabled" aria-controls="dataTables-example" tabindex="0" id="dataTables-example_previous"><a href="#">上页</a></li>
                                        
                                        <li class="paginate_button next disabled" aria-controls="dataTables-example" tabindex="0" id="dataTables-example_next"><a href="#">下页</a></li>
                */
                let html = '';
                let txt = template('users',res);
                $('tbody').html(txt)
                
                // 根据数据条数显示所有页码
                let pageSize = 5; // 每页显示的条数，该数目由项目需求决定
                let pages = Math.ceil(res.len / pageSize);// 分多少页  3
                // console.log(pages)
                for(var i=1;i<=pages;i++){  // 1,2,3
                    if(page === i){
                         html += '<li class="paginate_button active" aria-controls="dataTables-example" tabindex="0"><a href="javascript:showUsers('+i+')">'+i+'</a></li>';
                    }else{
                         html += '<li class="paginate_button" aria-controls="dataTables-example" tabindex="0"><a href="javascript:showUsers('+i+')">'+i+'</a></li>';
                     }                   
                }
                
                $('.pagination').html(html)
            })
        }
        showUsers();
```

Tip:

​	js多行字符串连接

```
https://www.jb51.net/article/49480.htm
```

工作中会大量用到百度和github（代码托管仓库）。

4）上一页

```
if(page === 1){
                    html += '\
                        <li class="paginate_button previous disabled" aria-controls="dataTables-example" tabindex="0" \
                        id="dataTables-example_previous"><a href="#">上页</a></li>'
                }else{
                    html += '\
                        <li class="paginate_button previous" aria-controls="dataTables-example" tabindex="0" \
                        id="dataTables-example_previous"><a href="javascript:showUsers('+(page-1)+')">上页</a></li>'
                }
```

5）下一页

```
if(page === pages){
                    html += '\
                        <li class="paginate_button next disabled" aria-controls="dataTables-example" tabindex="0" id="dataTables-example_next"><a \
                        href="#">下页</a></li>'
                }else{
                    html += '\
                        <li class="paginate_button next" aria-controls="dataTables-example" tabindex="0" id="dataTables-example_next"><a \
                        href="javascript:showUsers('+(page+1)+')">下页</a></li>'
                }
```

6）每页条目提示

```
let start = (page*pageSize) - (pageSize - 1);
    let end = 0;
    if(page * pageSize<=res.len){
    end = page * pageSize; 
    }else{
    end = res.len; 
}  

$('.show').html('<div class="dataTables_info" id="dataTables-example_info" role="status" aria-live="polite">显示第 '+start+' 至 '+end+' 项记录，共 '+pageSize+' 项</div>')
```

#### 3.8 项目上线步骤

1）登录阿里云；

2）在阿里云安装node.js（如已安装请略过）；

3）在阿里云安装phpStudy（如已安装请略过），并启动mysql服务；

4）在阿里云安装Navicat（如已安装请略过），并破解；

5）在Navicat上创建连接和空的数据库；

6）将自己的数据库导入到第五步创建的数据库中；

7）将项目代码复制到阿里云服务器的C盘下（注意不要复制node_modules，因为复制它太慢）；

8）进入第七步的项目目录中，安装依赖包；

```
npm i
```

9）启动项目（注意端口必须是80）；

```
node app
```

10）前端测试项目。

如：

```
http://www.zczsylm.top/admin/
```

