## XXX旅游APP(Vue.js+ES6+Node.js+Stylus)项目开发

### 01、[准备]项目分析

项目参考网址：

```
http://touch.piao.qunar.com
```

```
1）功能
	这是一个展示型APP。
2）数据
	。。。（mock数据）
3）技术选型
	Vue.js+ES6+Axios+Vuex+stylus+node.js
4）开发方式
	组件化、模块化和自动化。
```

### 02、[准备]开发环境

```
Win7/win10/Mac OS+webstorm2017+ 或(sublime3/vs code/atom/hbuilder)
```

### 03、[准备]项目操作内容

```
1）代码托管（码云）
	码云(http://gitee.com):是 OSCHINA.NET 推出的代码托管平台,支持 Git 和 SVN,提供免费的私有仓库托管。
2）搭建项目环境
3）插件
	轮播图
	解决移动端点击延时300ms问题
	滚动
	地图定位
	补充：可视化图表
4）真机测试
5）项目打包
6）生成安装包
```

### 04、安装git

下载并安装。

### 05、[准备]码云代码托管

```
码云：
	http://gitee.com

1）注册登录
2）在码云上新建项目
3）安装git
4）克隆到本地
	git clone 仓库地址
5）搭建项目环境
6）将代码上传到gitee.com的仓库中
	git add .
	git commit -m '备注文本'
	//git push -u origin master -f   强制上传
	git push （需要输入您的帐号（邮箱号）和密码）
	
老师的码云仓库地址：https://gitee.com/houyi_studio_admin/yungu_travel.git	
```

### 06、git常用命令

```
git init    初始化
git status  查看仓库当前的状态
git diff <file>  查看具体修改了什么内容
git diff HEAD --<file> 命令可以查看工作区和版本库里面最新版本的区别
git add <file> 添加到暂存
git add -f <file>  假如文件被忽略这样可以强制添加
git commit -m "balabalabala" 提交暂存区的文件到本地仓库
git log --graph --pretty=oneline 查看日志
git reset --hard HEAD^   (git reset --hard 版本编号)  版本回退 
git reset HEAD <file> 添加到了暂存区时，想丢弃修改 
git checkout --<file>  当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时
git rm <file> 从版本库中删除该文件(然后commit)
git remote   查看远程库信息
git remote -v  更加详细的查看
git remote add origin 地址  本地关联远程库
git clone  地址   克隆远程库
git branch  查看当前分支 
git branch <name>   创建分支
git checkout <name>   切换分支
git checkout -b <name>  我们创建分支，然后切换到分支
git merge <name>  合并分支到当前分支
git merge --no-ff -m "xxxxx" <name>   合并分支时，加上--no-ff参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而fast forward合并就看不出来曾经做过合并
git branch -d <name>   删除分支
git branch -D <name>   强行删除
git pull origin <name>   拉取
git push origin <name>  推送
git stash    把当前工作现场“储藏”起来，等以后恢复现场后继续工作
git stash list   查看贮藏区
git stash apply  恢复后，stash内容并不删除
git stash drop    删除贮藏区的内容
git stash pop     恢复的同时把stash内容也删了
你可以多次stash，恢复的时候，先用git stash list查看，然后恢复指定的stash，用命令 git stash apply stash@{0}
git rebase  变基(线路变得好看)
git tag <tagname>   打标签
git tag -a <tagname> -m "balabalbal..."   可以指定标签信息
git tag   查看所有标签
git show <tagname>   查看该标签版本信息
git tag -d <tagname>  删除标签
git push origin <tagname>  推送标签到远程
git push origin --tags   一次性推送全部尚未推送到远程的本地标签
git push origin :refs/tags/<tagname>  可以删除一个远程标签
在Git工作区的根目录下创建一个特殊的.gitignore文件，然后把要忽略的文件名填进去，Git就会自动忽略这些文件。
git reflog用来记录你的每一次命令
```

### 07、[准备]搭建项目环境

```
1）安装node.js（下载）（忽略）
2）选择安装cnpm（国内淘宝镜像）或Yarn或Bower或nrm...（忽略）
	cnpm:npm install -g cnpm --registry=https://registry.npm.taobao.org
	yarn:npm i yarn -g
3）安装webpack（忽略）
	yarn add webpack -g
4）安装vue-cli（忽略）
	yarn add i vue-cli -g
5）生成项目
	vue init webpack 项目名

	Project name my-project  回车
    Project description A Vue.js project 回车
    Author uplyw <xxx@xxx.com>  回车
    Vue build standalone  回车
    Install vue-router?    输入y
    Use ESLint to lint your code? 输入y
    Set up unit tests 输入n
    Setup e2e tests with Nightwatch? 输入n
    。。。安装依赖包
6）切换目录
	cd qinsi_tourism
7）启动项目
	npm run dev
8）在浏览器的地址栏中输入localhost:8080，查看是否启动成功！	
```

### 08、将项目文件上传到gitee.com

```
1）设置公钥（用来打通线上和线下通道）
2）在git bash here中进入到项目目录中，输入：
	git add .
	git commit -m '说明文字'
	git push (git push --force)
```

### 09、[准备]项目文件

```
build:打包配置文件
config:项目配置文件
node_modules:依赖包（项目中所有的外部模块文件下载处，如果需要某个模块，只需要使用require引入即可）
src:工作目录
	assets:放资源文件处（一般放css/js/styl/img等）
	components:所有的组件放在该文件夹下，除了App.vue（顶层组件）
	router:配置路由处
	App.vue:项目的入口文件，也是router出口处
	main.js:全局配置
static:所有的静态资源存放处，项目打包时，该文件夹中的文件不参与打包（一般放css/js/styl/img/json/xml等）
.babelrc:编译ES6
.editorconfig:编辑器配置
.gittgnore:github配置文件
.postcssrc.js:在写CSS时，可以不考虑兼容，postcss会自动识别浏览器和浏览器版本，会自动加上厂商前缀
package.json:包管理器
	(1.3.2-28434 主版本号.次版本号.修订版本号-补丁)
	^:匹配次版本的最高版本
	~：匹配修订版本的最高版本
	*:匹配任意版本
README.md：项目说明书
```

### 10、package.json及项目文件详解

现代的前端项目中通常都会有package.json文件。在package.json里，会介绍项目名称、版本、描述、作者、脚本、依赖包，对环境的要求，以及对浏览器要求。

```
 1 {
 2   "name": "uccn",
 3   "version": "1.0.0",
 4   "description": "uccn3.0",
 5   "author": "v_yangtianjiao <v_yangtianjiao@baidu.com>",
 6   "private": true,
　　　// 这里的脚本是分析项目的主要入口
 7   "scripts": {
 8     "dev": "node build/dev-server.js",
 9     "start": "node build/dev-server.js",
10     "build": "node build/build.js",
11     "jsonp": "node build/jsonp-server.js"
12   },
　　　// 项目依赖
13   "dependencies": {
14     "fetch-jsonp": "^1.1.3",
15     "less": "^2.7.2",
16     "less-loader": "^4.0.4",
17     "stylus": "^0.54.5",
18     "stylus-loader": "^3.0.1",
19     "vue": "^2.4.2"
20   },
21   "devDependencies": {
22     "autoprefixer": "^7.1.2",
23     "babel-core": "^6.22.1",
24     "babel-loader": "^7.1.1",
25     "babel-plugin-component": "^0.10.1",
26     "babel-plugin-transform-runtime": "^6.22.0",
27     "babel-preset-env": "^1.3.2",
28     "babel-preset-es2015": "^6.24.1",
29     "babel-preset-stage-2": "^6.22.0",
30     "babel-register": "^6.22.0",
31     "chalk": "^2.0.1",
32     "connect-history-api-fallback": "^1.3.0",
33     "copy-webpack-plugin": "^4.0.1",
34     "css-loader": "^0.28.0",
35     "cssnano": "^3.10.0",
36     "eventsource-polyfill": "^0.9.6",
37     "express": "^4.14.1",
38     "extract-text-webpack-plugin": "^2.0.0",
39     "file-loader": "^0.11.1",
40     "friendly-errors-webpack-plugin": "^1.1.3",
41     "html-webpack-plugin": "^2.28.0",
42     "http-proxy-middleware": "^0.17.3",
43     "opn": "^5.1.0",
44     "optimize-css-assets-webpack-plugin": "^2.0.0",
45     "ora": "^1.2.0",
46     "rimraf": "^2.6.0",
47     "semver": "^5.3.0",
48     "shelljs": "^0.7.6",
49     "url-loader": "^0.5.8",
50     "vue-loader": "^13.0.4",
51     "vue-style-loader": "^3.0.1",
52     "vue-template-compiler": "^2.4.2",
53     "webpack": "^2.6.1",
54     "webpack-bundle-analyzer": "^2.2.1",
55     "webpack-dev-middleware": "^1.10.0",
56     "webpack-hot-middleware": "^2.18.0",
57     "webpack-merge": "^4.1.0"
58   },
     // 对node版本的以及npm版本的要求
59   "engines": {
60     "node": ">= 4.0.0",
61     "npm": ">= 3.0.0"
62   },
　　　// 浏览器要求，vue项目不支持ie8，因为ie8是es3，尚没有Object.defineProperty属性
63   "browserslist": [
64     "> 1%",
65     "last 2 versions",
66     "not ie <= 8"
67   ]
68 }
```

上面的package.json是从实际vue项目中摘出来的，大家从package.json中就会对项目有一个大概的了解，最主要的是脚本部分。通过npm的自动化任务，可以很方便的执行配置文件中的脚本。通过配置  "jsonp": "node build/jsonp-server.js"，可以方便的使用npm run jsonp命令，代替node build/jsonp-server.js或者更复杂的一系列命令。详细的npm自动化命令可以移步[npm 自动化](https://segmentfault.com/a/1190000000344102)。

![img](https://images2017.cnblogs.com/blog/908144/201710/908144-20171011165137980-405265441.png)

 

 现在的项目目录结构如上，我们从刚才的脚本入手。首先是启服务的脚本npm run dev，实际上是执行node build/dev-server.js，我们在build文件夹中找到dev-server.js,一步步分析。

```
/* eslint-disable */

// 首先检查node和npm的版本
require('./check-versions')()

// 获取配置文件中默认的配置
var config = require('../config')
// 如果node无法判断当前是开发环境还是生产环境，则使用config.dev.env.NODE_ENV作为当前的环境
if (!process.env.NODE_ENV) {
  process.env.NODE_ENV = JSON.parse(config.dev.env.NODE_ENV)
}

var opn = require('opn')// 用来在起来服务之后，打开浏览器并跳转指定URL
var path = require('path')// node自带文件路径工具
var express = require('express')// node框架express（本地开发的核心，起服务）
var webpack = require('webpack')// webpack,压缩打包
var proxyMiddleware = require('http-proxy-middleware')// 中间件
var webpackConfig = require('./webpack.dev.conf')// 开发环境的webpack配置
var mockMiddleware = require('../config/dev.mock')// 开发环境本地mock数据中间件

var port = process.env.PORT || config.dev.port
var autoOpenBrowser = !!config.dev.autoOpenBrowser
var proxyTable = config.dev.proxyTable

var app = express()// 起服务
var compiler = webpack(webpackConfig)// webpack进行编译

// webpack-dev-middleware将编译的文件放在内存中，后续注入
var devMiddleware = require('webpack-dev-middleware')(compiler, {
  publicPath: webpackConfig.output.publicPath,
  quiet: true
})
// 热加载
var hotMiddleware = require('webpack-hot-middleware')(compiler, {
  log: false,
  heartbeat: 2000
})
compiler.plugin('compilation', function (compilation) {
  compilation.plugin('html-webpack-plugin-after-emit', function (data, cb) {
    hotMiddleware.publish({ action: 'reload' })
    cb()
  })
})

// proxy api requests
// proxyTable中的配置挂载到express中
Object.keys(proxyTable).forEach(function (context) {
  var options = proxyTable[context]
  if (typeof options === 'string') {
    options = { target: options }
  }
  app.use(proxyMiddleware(options.filter || context, options))
})

// 处理后退的时候匹配资源
app.use(require('connect-history-api-fallback')())

// 暂存在内存的webpack编译后的文件挂载到express上
app.use(devMiddleware)

// 将本地mock中间件挂载到express上
app.use(mockMiddleware);

// 热加载挂载到express上
app.use(hotMiddleware)

// 拼static静态资源文件路径
var staticPath = path.posix.join(config.dev.assetsPublicPath, config.dev.assetsSubDirectory)
// express为静态资源提供服务
app.use(staticPath, express.static('./static'))

var uri = 'http://localhost:' + port

var _resolve
var readyPromise = new Promise(resolve => {
  _resolve = resolve
})

console.log('> Starting dev server...')
devMiddleware.waitUntilValid(() => {
  console.log('> Listening at ' + uri + '\n')
  if (autoOpenBrowser && process.env.NODE_ENV !== 'testing') {
    opn(uri)
  }
  _resolve()
})
// 通过配置的端口，自动打开浏览器，并跳转拼好的URL，至此，发开环境已经跑起来了
var server = app.listen(port)

module.exports = {
  ready: readyPromise,
  close: () => {
    server.close()
  }
}
```

在上面的dev-server中，有很多变量来自于./config/index.js和webpack.dev.conf.js，我们一个个看上述配置文件。

首先看./config/index.js,这里是整个项目主要的配置入口，我们在代码中一步步分析：

```
// node自带路径工具.
var path = require('path')
// 分为两种环境，dev和production
module.exports = {
  build: {
    env: require('./prod.env'),// 使用config/prod.env.js中定义的编译环境
    index: path.resolve(__dirname, '../dist/index.html'),// 编译输入的index.html文件。node.js中，在任何模块文件内部，可以使用__filename变量获取当前模块文件的带有完整绝对路径的文件名,
    assetsRoot: path.resolve(__dirname, '../dist'),// 编译输出的静态资源路径
    assetsSubDirectory: 'static',// 编译输出的二级目录
    assetsPublicPath: './', // 编译发布的根目录，可配置为资源服务器或者cdn域名
    productionSourceMap: false,//是否开启cssSourceMap
    productionGzip: false,// 是否开启gzip
    productionGzipExtensions: ['js', 'css'],// 需要用gzip压缩的文件扩展名
    bundleAnalyzerReport: process.env.npm_config_report
  },
  dev: {
    env: require('./dev.env'),
    port: 8989,// 起服务的端口
    autoOpenBrowser: true,
    assetsSubDirectory: 'static',
    assetsPublicPath: '/',
    proxyTable: {},// 需要代理的接口，可以跨域
    cssSourceMap: false
  }
}
```

接着我们分析webpack.dev.conf.js：

```
var utils = require('./utils')// 工具类
var webpack = require('webpack')
var config = require('../config')
var merge = require('webpack-merge')// 使用webpack配置合并插件
var baseWebpackConfig = require('./webpack.base.conf')
var HtmlWebpackPlugin = require('html-webpack-plugin')// 这个插件自动生成HTML，并注入到.html文件中
var FriendlyErrorsPlugin = require('friendly-errors-webpack-plugin')

// 将hot-reload相对路径添加到webpack.base.conf的对应的entry前面
Object.keys(baseWebpackConfig.entry).forEach(function (name) {
  baseWebpackConfig.entry[name] = ['./build/dev-client'].concat(baseWebpackConfig.entry[name])
})

// webpack.dev.conf.js与webpack.base.conf.js中的配置合并
module.exports = merge(baseWebpackConfig, {
  module: {
    rules: utils.styleLoaders({ sourceMap: config.dev.cssSourceMap })
  },
  // webpack-devtool有7种模式，cheap-module-eval-source-map模式是比较快的开发模式
　
  devtool: '#cheap-module-eval-source-map',
  plugins: [
　　// 你可以理解为，通过配置了DefinePlugin，那么这里面的标识就相当于全局变量，你的业务代码可以直接使用配置的标识。
    new webpack.DefinePlugin({
      'process.env': config.dev.env
    }),
    // hotModule插件让页面变动时，只重绘对应的模块，不会重绘整个HTML文件
    new webpack.HotModuleReplacementPlugin(),
　　// 在编译出现错误时，使用 NoEmitOnErrorsPlugin 来跳过输出阶段。这样可以确保输出资源不会包含错误
    new webpack.NoEmitOnErrorsPlugin(),
    // 将生成的HTML代码注入index.html文件
    new HtmlWebpackPlugin({
      filename: 'index.html',
      template: 'index.html',
      inject: true
    }),
　　// friendly-errors-webpack-plugin用于更友好地输出webpack的警告、错误等信息
    new FriendlyErrorsPlugin()
  ]
})
```

 刚才的webpack.dev.conf.js中有引到webpack.base.conf.js,我们就把他们一网打尽，继续看webpack.base.conf.js!

```
/* eslint-disable */
var path = require('path')// node自带的文件路径插件
var utils = require('./utils')// 工具类
var config = require('../config')// 上面说过的config/index
var vueLoaderConfig = require('./vue-loader.conf')// vue-loader.conf配置文件是用来解决各种css文件的，定义了诸如css,less,sass之类的和样式有关的loader
// 此函数是用来返回当前目录的平行目录的路径，
function resolve (dir) {
  return path.join(__dirname, '..', dir)
}

module.exports = {
  entry: {
    uccn: './src/main.js'// 入口
  },
  output: {
　　// 路径是config目录下的index.js中的build配置中的assetsRoot，也就是dist目录
    path: config.build.assetsRoot,
    filename: '[name].js',
　　// 上线地址，也就是真正的文件引用路径，如果是production生产环境，其实这里都是 '/'
    publicPath: process.env.NODE_ENV === 'production'
      ? config.build.assetsPublicPath
      : config.dev.assetsPublicPath
  },
　// resolve是webpack的内置选项，顾名思义，决定要做的事情，也就是说当使用 import "jquery"，该如何去执行这件事情，就是resolve配置项要做的，import jQuery from "./additional/dist/js/jquery" 这样会很麻烦，可以起个别名简化操作
  resolve: {
　　// 省略扩展名，比方说import index form '../js/index', 会默认去找index文件，然后找index.js,.vue,.josn.
    extensions: ['.js', '.vue', '.json'],
    alias: {
      'vue$': 'vue/dist/vue.esm.js',
　　　　// 使用上面的resolve函数，意思是用@代替src的绝对路径
      '@': resolve('src'),
    }
  },
　// 不同的模块使用不同的loader
  module: {
    rules: [
      {
　　　　　// 对vue文件，使用vue-loader解析
        test: /\.vue$/,
        loader: 'vue-loader',
        options: vueLoaderConfig
      },
      {
　　　　　// babel-loader把es6解析成es5
        test: /\.js$/,
        loader: 'babel-loader',
        include: [resolve('src'), resolve('test')]
      },
      {
　　　　　// url-loader将文件大小低于下面option中limit的图片，转化为一个64位的DataURL，这样会省去很多请求，大于limit的，按[name].[hash:7].[ext]的命名方式放到了static/img下面，方便做cache
        test: /\.(png|jpe?g|gif|svg)(\?.*)?$/,
        loader: 'url-loader',
        options: {
          limit: 20000,
          name: utils.assetsPath('img/[name].[hash:7].[ext]')
        }
      },
      {
　　　　　// 音频和视频文件处理，同上
        test: /\.(mp4|webm|ogg|mp3|wav|flac|aac)(\?.*)?$/,
        loader: 'url-loader',
        options: {
          limit: 10000,
          name: utils.assetsPath('media/[name].[hash:7].[ext]')
        }
      },
      {
　　　　　// 字体处理，同上　
        test: /\.(woff2?|eot|ttf|otf)(\?.*)?$/,
        loader: 'url-loader',
        options: {
          limit: 10000,
          name: utils.assetsPath('fonts/[name].[hash:7].[ext]')
        }
      }
    ]
  }
}
```

 至此，npm run dev起本地开发环境相关的配置文件基本说完了，接着说一下上面都用到的util工具类：

```
var path = require('path')
var config = require('../config')
// extract-text-webpack-plugin该插件的主要是为了抽离css样式,防止将样式打包在js中引起页面样式加载错乱的现象
var ExtractTextPlugin = require('extract-text-webpack-plugin')

// 返回资源文件路径，path.posix以posix兼容的方式交互，是跨平台的，如果是path.win32的话，只能在win上
exports.assetsPath = function (_path) {
  var assetsSubDirectory = process.env.NODE_ENV === 'production'
    ? config.build.assetsSubDirectory
    : config.dev.assetsSubDirectory
  return path.posix.join(assetsSubDirectory, _path)
}

// 通过判断是否是生产环境，配置不同的样式语言的loader配置
exports.cssLoaders = function (options) {
  options = options || {}

  var cssLoader = {
    loader: 'css-loader',
    options: {
      minimize: process.env.NODE_ENV === 'production',
      sourceMap: options.sourceMap
    }
  }

  // 生成各种loader配置，通过传入不同的loader和option，将不同样式文件语言的loader拼好，push到loader配置中。
  function generateLoaders (loader, loaderOptions) {
    var loaders = [cssLoader]
    if (loader) {
      loaders.push({
        loader: loader + '-loader',
        options: Object.assign({}, loaderOptions, {
          sourceMap: options.sourceMap
        })
      })
    }

    // extract-text-webpack-plugin有三个参数，use指需要用什么loader去编译文件；fallback指编译后用什么loader去提取文件；还有一个publicfile用来覆盖项目路径
    if (options.extract) {
      return ExtractTextPlugin.extract({
        use: loaders,
        fallback: 'vue-style-loader'
      })
    } else {
      return ['vue-style-loader'].concat(loaders)
    }
  }

  // 对不同的样式语言，返回相应的loader
  return {
    css: generateLoaders(),
    postcss: generateLoaders(),
    less: generateLoaders('less'),
    sass: generateLoaders('sass', { indentedSyntax: true }),
    scss: generateLoaders('sass'),
    stylus: generateLoaders('stylus'),
    styl: generateLoaders('stylus')
  }
}

// 生成处理不同的样式文件处理规则
exports.styleLoaders = function (options) {
  var output = []
  var loaders = exports.cssLoaders(options)
  for (var extension in loaders) {
    var loader = loaders[extension]
    output.push({
      test: new RegExp('\\.' + extension + '$'),
      use: loader
    })
  }
  return output
}
```

npm run build，打包编译系列操作

从package.json 中可以看出，npm run build，其实是执行了 node build/build.js，我们在build文件夹中找到build.js，build主要的工作是：检测node和npm版本，删除dist包，webpack构建打包，在终端输出构建信息并结束，如果报错，则输出报错信息。

```
require('./check-versions')()

process.env.NODE_ENV = 'production'

// 在终端显示的旋转器插件
var ora = require('ora')
// 用于删除文件夹
var rm = require('rimraf')
var path = require('path')
// 终端文字颜色插件
var chalk = require('chalk')
var webpack = require('webpack')
var config = require('../config')
var webpackConfig = require('./webpack.prod.conf')

var spinner = ora('building for production...')
spinner.start()

// 删除dist文件夹，之后webpack打包
rm(path.join(config.build.assetsRoot, config.build.assetsSubDirectory), err => {
  if (err) throw err
  webpack(webpackConfig, function (err, stats) {
    spinner.stop()
    if (err) throw err
    process.stdout.write(stats.toString({
      colors: true,
      modules: false,
      children: false,
      chunks: false,
      chunkModules: false
    }) + '\n\n')

    if (stats.hasErrors()) {
      console.log(chalk.red('  Build failed with errors.\n'))
      process.exit(1)
    }

    console.log(chalk.cyan('  Build complete.\n'))
    console.log(chalk.yellow(
      '  Tip: built files are meant to be served over an HTTP server.\n' +
      '  Opening index.html over file:// won\'t work.\n'
    ))
  })
})
```

build.js用到了webpack.prod.conf.js,他与webpack.base.conf.js merge之后，作为webpack配置文件，我们再看看webpack.prod.conf.js,主要做的工作是：
1）提取webpack生成的bundle中的文本，到特定的文件，使得css，js文件与webpack输出的bundle分离。

2）合并基本的webpack配置

3）配置webpack的输出，包括输出路径，文件名格式。

4）配置webpack插件，包括丑化代码。

5）gzip下引入compression插件进行压缩。

```
/* eslint-disable */
var path = require('path')
var utils = require('./utils')
var webpack = require('webpack')
var config = require('../config')
var merge = require('webpack-merge')
var baseWebpackConfig = require('./webpack.base.conf')
var CopyWebpackPlugin = require('copy-webpack-plugin')
var HtmlWebpackPlugin = require('html-webpack-plugin')
// 用于从webpack生成的bundle中提取文本到特定文件中的插件
// 可以抽取出css，js文件将其与webpack输出的bundle分离
var ExtractTextPlugin = require('extract-text-webpack-plugin')
var OptimizeCSSPlugin = require('optimize-css-assets-webpack-plugin')

var env = config.build.env
// 合并基础的webpack配置
var webpackConfig = merge(baseWebpackConfig, {
  module: {
    rules: utils.styleLoaders({
      sourceMap: config.build.productionSourceMap,
      extract: true
    })
  },
　// 7中sourceMap上面有讲过
  devtool: config.build.productionSourceMap ? '#source-map' : false,
　// 配置webpack输出的目录，及文件命名规则
  output: {
    path: config.build.assetsRoot,
    filename: utils.assetsPath('js/[name].min.js'),
    chunkFilename: utils.assetsPath('js/[id].[chunkhash].js')
  },
　// webpack插件配置
  plugins: [
    // 同webpack.dev.conf.js
    new webpack.DefinePlugin({
      'process.env': env
    }),
　　// 丑化代码
    new webpack.optimize.UglifyJsPlugin({
      compress: {
        warnings: false
      },
      sourceMap: true
    }),
    // 抽离css文件到单独的文件
    new ExtractTextPlugin({
      filename: utils.assetsPath('css/[name].min.css')
    }),
    new OptimizeCSSPlugin({
      cssProcessorOptions: {
        safe: true
      }
    }),
    // 生成并注入index.html
    new HtmlWebpackPlugin({
      filename: config.build.index,
      template: 'index.html',
      inject: true,
      minify: {
        removeComments: true,
        collapseWhitespace: false,
        removeAttributeQuotes: true
      },
      chunksSortMode: 'dependency'
    }),
    // keep module.id stable when vender modules does not change
    new webpack.HashedModuleIdsPlugin(),
    split vendor js into its own file
    new webpack.optimize.CommonsChunkPlugin({
      name: 'vendor',
      minChunks: function (module, count) {
        // any required modules inside node_modules are extracted to vendor
        return (
          module.resource &&
          /\.js$/.test(module.resource) &&
          module.resource.indexOf(
            path.join(__dirname, '../node_modules')
          ) === 0
        )
      }
    }),
    extract webpack runtime and module manifest to its own file in order to
    prevent vendor hash from being updated whenever app bundle is updated
    new webpack.optimize.CommonsChunkPlugin({
      name: 'manifest',
      chunks: ['vendor']
    }),
    copy custom static assets
    new CopyWebpackPlugin([
      {
        from: path.resolve(__dirname, '../static'),
        to: config.build.assetsSubDirectory,
        ignore: ['.*']
      }
    ])
  ]
})
// gzip模式下需要引入compression插件进行压缩
if (config.build.productionGzip) {
  var CompressionWebpackPlugin = require('compression-webpack-plugin')

  webpackConfig.plugins.push(
    new CompressionWebpackPlugin({
      asset: '[path].gz[query]',
      algorithm: 'gzip',
      test: new RegExp(
        '\\.(' +
        config.build.productionGzipExtensions.join('|') +
        ')$'
      ),
      threshold: 10240,
      minRatio: 0.8
    })
  )
}

if (config.build.bundleAnalyzerReport) {
  var BundleAnalyzerPlugin = require('webpack-bundle-analyzer').BundleAnalyzerPlugin
  webpackConfig.plugins.push(new BundleAnalyzerPlugin())
}

module.exports = webpackConfig
```

### 11、[准备]引入重置样式reset.css

```
网址：https://meyerweb.com/eric/tools/css/reset/
```

```
html, body, div, span, applet, object, iframe,
h1, h2, h3, h4, h5, h6, p, blockquote, pre,
a, abbr, acronym, address, big, cite, code,
del, dfn, em, img, ins, kbd, q, s, samp,
small, strike, strong, sub, sup, tt, var,
b, u, i, center,
dl, dt, dd, ol, ul, li,
fieldset, form, label, legend,
table, caption, tbody, tfoot, thead, tr, th, td,
article, aside, canvas, details, embed, 
figure, figcaption, footer, header, hgroup, 
menu, nav, output, ruby, section, summary,
time, mark, audio, video {
	margin: 0;
	padding: 0;
	border: 0;
	font-size: 100%;
	font: inherit;
	vertical-align: baseline;
}
/* HTML5 display-role reset for older browsers */
article, aside, details, figcaption, figure, 
footer, header, hgroup, menu, nav, section {
	display: block;
}
body {
	line-height: 1;
}
ol, ul {
	list-style: none;
}
blockquote, q {
	quotes: none;
}
blockquote:before, blockquote:after,
q:before, q:after {
	content: '';
	content: none;
}
table {
	border-collapse: collapse;
	border-spacing: 0;
}
a{
  text-decoration: none;
  color:#000000;
}
```

把reset.css文件入在assets->css目录下，然后再在main.js中引入：

```
// 引入reset.css
import './assets/css/reset.css'
```

### 12、[准备]引入fastclick.js

移动设备上的浏览器默认会在用户点击屏幕大约延迟300毫秒后才会触发点击事件，这是为了检查用户是否在做双击。为了能够立即响应用户的点击事件，才有了FastClick。

1）参考网址：

```
https://www.jianshu.com/p/67bae6dfca90
```

2）安装：

```
cnpm i fastclick -S
```

3）安装完成后在main.js中引入：

```
import FastClick from 'fastclick'
// 使用
FastClick.attach(document.body);
```

### 13、[准备]引入iconfont.css

### 14、[准备]在Webstorm中创建.vue的代码模板

File->settings->editor->File Code and Templates->新建（name为vue，extension为vue），输入以下内容：

```
<template>

</template>
<script type="text/ecmascript-6">
    export default {
    
        
    }
</script>
<style lang="stylus" rel="text/stylus" scoped>

</style>
```

### 15、[准备]整理项目文件夹

1）删除项目中assets下所有内容
2）删除项目中components下所有内容，同时创建一个home文件夹，再在该文件夹下创建一个Home.vue文件。Home.vue文件内容如下：

```
<template>
  <div class="home">
    home
  </div>
</template>
<script type="text/ecmascript-6">
    export default {}
</script>
<style lang="stylus" rel="text/stylus" scoped>

</style>
```

3）修改routes下的index.js文件内容，如下：

```
import Vue from 'vue'
import Router from 'vue-router'
import Home from '@/components/home/home'
Vue.use(Router)
export default new Router({
routes: [
{
path: '/',
name: 'Home',
component: Home
}
]
})
```

4）修改App.vue文件内容，内容如下：

```
<template>
    <div id="app">
    	<router-view/>
    </div>
</template>
<script>
    export default {
    	
    } 
</script>
<style lang="stylus" rel="text/stylus" scoped>

</style>
```

### 10、[准备]安装stylus

```
cnpm i stylus stylus-loader -S
```

安装完后，重启项目。

```
npm run dev
```

stylus用法：

stylus（预处理）类似于sass语法

```
https://stylus-lang.net/
```

### 

### 14、[准备]项目文件结构

```
home
    pages
        Header.vue
        Swiper.vue
        Icons.vue
        Location.vue
        Hot.vue
        Like.vue
        Gowhere.vue
        Footer.vue
    Home.vue
cities
    pages
        Header.vue
        Hotcity.vue
        Sort.vue
        Citylist.vue
    Cities.vue
details
    pages
        Header.vue
        Banner.vue
        Rating.vue
        Location.vue
        ....
    details.vue
```

### 15、[首页]创建Header.vue组件

```
<template>
  <header>
    <div class="return">
      <span class="iconfont iconzuojiantou"></span>
    </div>
    <div class="search">
      <span class="iconfont iconsearch"></span>
      输入城市/景点/游玩主题
    </div>
    <div class="next">
      西安<span class="iconfont iconyoujiantou"></span>
    </div>
  </header>
</template>
<script type="text/ecmascript-6">
    export default {}
</script>
<style scoped>/*scoped:样式只作用于当前组件*/
  header{
    width: 100%;
    line-height: .88rem;
    background-color: #00afc7;
    font-size: .28rem;
    color:#ffffff;
    display: flex;
  }
  .return{
    width: .6rem;
    text-align: center;
    font-size: .36rem;
  }
  .search{
    flex:1;
    background-color: #fff;
    height: .6rem;
    line-height: .6rem;
    margin-top: .14rem;
    border-radius: .1rem;
    color:#e4e7ea;
    padding: 0 .2rem;
  }
  .next{
    padding: 0 .2rem;
  }
</style>
```

在Home.vue中引入并使用Header组件：

```
<template>
  <div class="home">
   <!-- <HomeHeader></HomeHeader>
    <HomeHeader />
    <home-header></home-header>-->
    <home-header/>
  </div>
</template>
<script type="text/ecmascript-6">
  import HomeHeader from './pages/Header'
  export default {
    components:{
      HomeHeader
    }
  }
</script>
<style scoped>

</style>
```

### 16、[首页]创建swiper.vue组件

1）在home目录下的pages目录下新建swiper.vue

```
<template>
  <div class="swiper">
    aaa
  </div>
</template>
<script type="text/ecmascript-6">
    export default {}
</script>
<style lang="stylus" rel="text/stylus" scoped>

</style>
```

2）在Home.vue中引入swiper.vue组件

```
import HomeSwiper from './pages/Swiper'

export default {
    components:{
      HomeHeader,
      HomeSwiper
    }
}

<home-swiper/>
```

3）参考网站

```
进入http://github.com搜索vue-swiper，进入<https://www.swiper.com.cn/api/autoplay/16.html
```

4）安装swiper模块

```
cnpm install vue-awesome-swiper --save
```

5）在main.js中全局引入

```
// 引入swiper
import VueAwesomeSwiper from 'vue-awesome-swiper'
// require styles
import 'swiper/dist/css/swiper.css'
Vue.use(VueAwesomeSwiper);
```

6）复制swiper结构HTML

```
<swiper :options="swiperOption">
    <swiper-slide>I'm Slide 1</swiper-slide>
    <swiper-slide>I'm Slide 2</swiper-slide>
    <swiper-slide>I'm Slide 3</swiper-slide>
    <swiper-slide>I'm Slide 4</swiper-slide>
    <swiper-slide>I'm Slide 5</swiper-slide>
    <swiper-slide>I'm Slide 6</swiper-slide>
    <swiper-slide>I'm Slide 7</swiper-slide>
    <div class="swiper-pagination" slot="pagination"></div>
</swiper>
```

7）swiper逻辑处理

```
data(){
    return{
        swiperOption:{
            pagination: {
            	el: '.swiper-pagination'
            },
            loop:true,
            autoplay: {
                delay: 3000,
                stopOnLastSlide: false,
                disableOnInteraction: false
            }
        }
    }
}
```

8）样式

```
<style lang="stylus" rel="text/stylus" scoped>
  .swiper
    height: 0
    background-color: #ccc
    padding-bottom: 26.666%
    img
      width: 100%
      height: 100%    
</style>
```

9）样式穿透

```
>>> .swiper-pagination-bullet
    width: 6px
    height: 6px
    background-color: #fff
    opacity: 0.2
>>> .swiper-pagination-bullet-active /* 样式穿透 */
    opacity: 1
    background: #e4e7ea
```

10）数据mock

```
"swiperList":[
    {
        "id":"01",
        "imgUrl":"http://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20195/b0732b5a58a2c613f6202beb35c571d3.jpg_750x200_c6a2ebe2.jpg"
    },
    {
        "id":"02",
        "imgUrl":"http://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20198/fffc0c06ddfe6fa9bad3cd813b591873.jpg_750x200_528c2db7.jpg"
    },
    {
        "id":"03",
        "imgUrl":"http://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20193/c807f8e462d269397489ef90b16f61b7.jpg_750x200_aaf543ba.jpg"
    }
]
```

如果加载的是本地的图片，数据代码要写成：

```
"swiperList":[
    {
        "id":"01",
        "imgUrl":require("@/assets/img/swiper01.jpg")
    },
    {
        "id":"02",
        "imgUrl":require("@/assets/img/swiper02.jpg")
    },
    {
        "id":"03",
        "imgUrl":require("@/assets/img/swiper03.jpg")
    }
]
```

11）HTML改写及数据渲染

```
<template>
  <div class="swiper">
    <swiper :options="swiperOption">
      <swiper-slide v-for="item of swiperList" :key="item.id">
        <img :src="item.imgUrl" alt="banner">
      </swiper-slide>
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>
</template>
```

### 17、[首页]CSS中的滤镜filter

```
https://www.cnblogs.com/zheshiyigemanong/p/6943205.html

filter:
    grayscale灰度 				百分比
    sepia褐色（有种复古的旧照片感觉） 百分比
    saturate饱和度
    hue-rotate色相旋转			   角度 
    invert反色					 百分比
    opacity透明度					小数
    brightness亮度
    contrast对比度
    blur模糊						 像素
    drop-shadow阴影
```

### 18、[首页]配置文件修改后必须重启服务！

### 19、[首页]重命名访问路径

修改build->webpack.base.conf.js

```
 resolve: {
    extensions: ['.js', '.vue', '.json'],
    alias: {
      'vue$': 'vue/dist/vue.esm.js',
      '@': resolve('src'),
      'css': resolve('src/assets/css')
    }
  }
```

使用：

main.js中使用：

```
// 引入reset.css
import 'css/reset.css'

// 引入iconfont.css
import 'css/iconfont.css'
```

style标签中使用：

```
@import "~css/common.styl"
```

### 20、[首页]icons分页逻辑处理

1）HTML代码：

```
<template>
  <ul class="icons">
    <swiper :options="swiperOption">
      <swiper-slide v-for="(item,key) of page" :key="key">
        <li class="icons-item" v-for="icon of item" :key="icon.id">
          <img :src="icon.imgUrl" :alt="icon.title" />
          <p>{{ icon.title }}</p>
        </li>
      </swiper-slide>
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </ul>
</template>
```

2）样式

```
.icons
    width: 100%
    overflow: hidden
    .icons-item
      width: 25%
      text-align: center
      padding-top: .2rem
      font-size: .28rem
      float: left
      img
        width: 1.1rem
        height:1.1rem
    .swiper-container {
      height: 200px;
    }
    >>> .swiper-pagination-bullet
      width: 6px
      height: 6px
      background-color: rgba(144,144,144,0.8)
      opacity: 0.5
    >>> .swiper-pagination-bullet-active /* 样式穿透 */
      opacity: 1
      background: rgba(0,175,190,.8)
```

3）数据mock

```
data(){
        return{
          swiperOption:{
            pagination: {
              el: '.swiper-pagination'
            },
            loop:true
          },
          "iconsList":[
            {
              "id":"01",
              "imgUrl":"http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png",
              "title":"景点门票"
            },{
              "id":"02",
              "imgUrl":"http://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20193/f0f00d6dfe038c044dbc9a437f58b0eb.png",
              "title":"一日行"
            },{
              "id":"03",
              "imgUrl":"http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png",
              "title":"景点门票"
            },{
              "id":"04",
              "imgUrl":"http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png",
              "title":"景点门票"
            },{
              "id":"05",
              "imgUrl":"http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png",
              "title":"景点门票"
            },{
              "id":"06",
              "imgUrl":"http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png",
              "title":"景点门票"
            },{
              "id":"07",
              "imgUrl":"http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png",
              "title":"景点门票"
            },{
              "id":"08",
              "imgUrl":"http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png",
              "title":"景点门票"
            },{
              "id":"09",
              "imgUrl":"http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png",
              "title":"景点门票"
            },{
              "id":"011",
              "imgUrl":"http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png",
              "title":"景点门票"
            },{
              "id":"012",
              "imgUrl":"http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png",
              "title":"景点门票"
            }
          ]
        }
      }
```

4）分页逻辑

```
page(){// 把一维数组变成二维数组
    let pages = [];
    this.iconsList.forEach((item,index)=>{
        let idx = Math.floor(index / 8);
        if(!pages[idx])pages[idx] = [];
        pages[idx].push(item);
    });
    return pages;
}
```

### 21、[首页]为列表项前三添加伪类

1）Stylus样式函数封装

```
$txtOverflow()
  text-overflow: ellipsis
  white-space: nowrap
  overflow: hidden
$imgTop(url)
  content: ''
  position: absolute
  top:-.06rem
  left:0
  color:#fff
  width: .84rem
  height: .4rem
  background-image: url(url)
  background-size: cover
```

2）样式调用

```
<style lang="stylus" rel="text/stylus" scoped>
  @import "~css/common.styl"
  .hot
    margin-top:.2rem
    background-color: #fff
    font-size: .24rem
    .hot-title
      position: relative
      padding:.4rem
      .hot-title-left
        font-size: .32rem
        img
          width: .3rem
          height: .3rem
      .hot-title-right
        color:#616161
        font-size: .24rem
        position: absolute
        top: 0.4rem
        right:.2rem
    .hot-list
      padding:.06rem 0 .2rem .2rem
      white-space:nowrap
      overflow-x:scroll
      overflow-y:hidden
      height: 3rem
      .hot-item
        display: inline-block
        width:2rem
        margin-right:.13rem
        text-align: center
        position: relative
        &:nth-child(1):before
          $imgTop('//img1.qunarzz.com/piao/fusion/1710/ab/159673b63e6ca702.png')
        &:nth-child(2):before
          $imgTop('http://img1.qunarzz.com/piao/fusion/1710/2d/36d0c4adaebbbc02.png')
        &:nth-child(3):before
          $imgTop('http://img1.qunarzz.com/piao/fusion/1710/67/edc47ffef9e96b02.png')
        &:last-child
          margin-right: 0
        img
          width: 2rem
          height: 2rem
        .hot-item-title
          margin: .12rem 0
          line-height: .32rem
          $txtOverflow()
        span
          font-size: .28rem
          color:#ff8300
</style>
```

### 22、在Vue项目要尽量减少或避免DOM操作。

### 23、在Vue项目开发中，如果要使用到JQ的步骤

1）安装

```
cnpm i jquery --save
```

2）引入

```
// 可以在main.js中引入（全局引入），也可以在当前组件中引入（局部引入）
let $ = require('jquery);//common.js
或：
import $ from 'jquery' //ES6语法
```

### 24、Footer组件的布局和逻辑

```
<template>
  <footer>
    <ul class="nav-list">
      <li class="nav-item" v-for="(nav,index) in navList" :key="index">
        <span :style="{'background-position':ps(index)}"></span>{{ nav }}
      </li>
    </ul>
    <div class="toggle" @click="toggle"><span class="iconfont" :class="toggleClass"></span>{{ txt }}</div>
  </footer>
</template>
<script type="text/ecmascript-6">
    export default {
      data(){
        return{
          "navList":["机票","酒店","公寓"],
          flag:0,
          txt:'更多',
          toggleClass:'iconshuangjiantouxia'
        }
      },
      methods:{
        ps(index){
          return -(index<7?index:index-7) * 25 +'px '+ (index>6?-25:0)+'px'
        },
        toggle(){
          if(this.flag == 1){
            this.navList = ["机票","酒店","公寓"];
            this.flag = 0;
            this.txt = '更多';
            this.toggleClass = 'iconshuangjiantouxia'
          }else{
            this.navList = ["机票","酒店","公寓","团购","火车票","景点","接送机","度假","攻略","旅图","车车","当地人"]
            this.flag = 1;
            this.txt = '收起';
            this.toggleClass = 'iconshuangjiantoushang'
          }
        }
      }
    }
</script>
<style lang="stylus" rel="text/stylus" scoped>
  footer
    color:#9e9e9e
    font-size: .24rem
    position: relative
    overflow: hidden
    .nav-list
      width:6.4rem
      margin: 0 auto
      overflow: hidden
      padding:10px 10px 0
      .nav-item
        width: 25%
        float: left
        padding-left:.2rem
        height: .44rem
        line-height: .44rem
        span
          width:.44rem
          height:.44rem
          display: inline-block
          background-image: url(../../../assets/img/footer.png)
          background-repeat: no-repeat
          background-size:3.5rem 1rem

    .toggle
      position: absolute
      bottom:0
      right:0
</style>
```

### 25、数据mock

1）整理JSON文件

```
{
  "data": [
    {
      "city": "西安",
      "swiperList":[
        {
          "id":"01",
          "imgUrl":"/api/img/swiper01.jpg"
        },
        {
          "id":"02",
          "imgUrl":"/api/img/swiper02.jpg"
        },
        {
          "id":"03",
          "imgUrl":"/api/img/swiper03.jpg"
        }
      ],
      "iconsList":[
        {
          "id":"01",
          "imgUrl":"/api/img/icons01.png",
          "title":"景点门票"
        },{
          "id":"02",
          "imgUrl":"/api/img/icons02.png",
          "title":"一日游"
        },{
          "id":"03",
          "imgUrl":"/api/img/icons03.png",
          "title":"识春赏花"
        },{
          "id":"04",
          "imgUrl":"/api/img/icons04.png",
          "title":"精品小团"
        },{
          "id":"05",
          "imgUrl":"/api/img/icons05.png",
          "title":"西安必游"
        },{
          "id":"06",
          "imgUrl":"/api/img/icons06.png",
          "title":"动植物园"
        },{
          "id":"07",
          "imgUrl":"/api/img/icons07.png",
          "title":"华清宫"
        },{
          "id":"08",
          "imgUrl":"/api/img/icons08.png",
          "title":"兵马俑"
        },{
          "id":"09",
          "imgUrl":"/api/img/icons09.png",
          "title":"泡温泉  "
        },{
          "id":"10",
          "imgUrl":"/api/img/icons10.png",
          "title":"陕历博"
        }
      ],
      "hotImgs":[
        {
          "id":"01",
          "imgUrl":"/api/img/hot01.jpg",
          "title":"华清宫",
          "price":108
        },{
          "id":"02",
          "imgUrl":"/api/img/hot02.jpg",
          "title":"秦始皇陵博物院（兵马俑）",
          "price":120
        },{
          "id":"03",
          "imgUrl":"/api/img/hot03.jpg",
          "title":"大唐芙蓉园",
          "price":108
        },{
          "id":"04",
          "imgUrl":"/api/img/hot04.jpg",
          "title":"陕西历史博物馆",
          "price":30
        },{
          "id":"05",
          "imgUrl":"/api/img/hot05.jpg",
          "title":"大明宫国家遗址公园",
          "price":82
        },{
          "id":"06",
          "imgUrl":"/api/img/hot06.jpg",
          "title":"曲江海洋极地公园",
          "price":158
        },{
          "id":"07",
          "imgUrl":"/api/img/hot07.jpg",
          "title":"秦岭野生动物园",
          "price":48
        },
        {
          "id":"08",
          "imgUrl":"/api/img/hot08.jpg",
          "title":"西安城墙",
          "price":60
        }
      ],
      "likeList":[
        {
          "id":"01",
          "imgUrl":"/api/img/hot01.jpg",
          "title":"华清池",
          "message":37018,
          "price":108,
          "map":"临潼区"
        },{
          "id":"02",
          "imgUrl":"/api/img/like02.jpg",
          "title":"汤峪天潭温泉酒店",
          "message":241,
          "price":150,
          "map":"蓝田县"
        },{
          "id":"03",
          "imgUrl":"/api/img/like03.jpg",
          "title":"华清爱琴海温泉",
          "message":777,
          "price":138,
          "map":"临潼区"
        },{
          "id":"04",
          "imgUrl":"/api/img/like04.jpg",
          "title":"华夏文旅海洋公园",
          "message":331,
          "price":218,
          "map":"西安"
        },{
          "id":"05",
          "imgUrl":"/api/img/like05.jpg",
          "title":"曲江海洋极地公园",
          "message":10522,
          "price":158,
          "map":"曲江旅游..."
        },{
          "id":"06",
          "imgUrl":"/api/img/like06.jpg",
          "title":"秦始皇陵博物院（兵马俑）",
          "message":121961,
          "price":120,
          "map":"临潼区"
        },{
          "id":"07",
          "imgUrl":"/api/img/like07.jpg",
          "title":"西安临潼悦椿温泉",
          "message":1066,
          "price":198,
          "map":"临潼区"
        },{
          "id":"08",
          "imgUrl":"/api/img/like08.jpg",
          "title":"长恨歌",
          "message":18586,
          "price":223,
          "map":"华清宫"
        },{
          "id":"09",
          "imgUrl":"/api/img/like09.jpg",
          "title":"西安秦岭欢乐世界",
          "message":2030,
          "price":88,
          "map":"长安区"
        },{
          "id":"10",
          "imgUrl":"/api/img/like10.jpg",
          "title":"白鹿原影视城",
          "message":796,
          "price":59,
          "map":"蓝田县"
        },{
          "id":"11",
          "imgUrl":"/api/img/like11.jpg",
          "title":"秦岭国家植物园",
          "message":47,
          "price":65,
          "map":"周至县"
        },{
          "id":"12",
          "imgUrl":"/api/img/like12.jpg",
          "title":"翠华山",
          "message":3077,
          "price":59,
          "map":"长安区"
        },{
          "id":"13",
          "imgUrl":"/api/img/like13.jpg",
          "title":"太平国家森林公园",
          "message":765,
          "price":9,
          "map":"户县"
        },{
          "id":"14",
          "imgUrl":"/api/img/like14.jpg",
          "title":"西安关中民俗艺术博物院",
          "message":430,
          "price":99.8,
          "map":"长安区"
        },{
          "id":"15",
          "imgUrl":"/api/img/like15.jpg",
          "title":"中国唐苑",
          "message":237,
          "price":45,
          "map":"雁塔区"
        },{
          "id":"16",
          "imgUrl":"/api/img/like16.jpg",
          "title":"西安唐乐宫",
          "message":333,
          "price":218,
          "map":"碑林区"
        },{
          "id":"17",
          "imgUrl":"/api/img/like17.jpg",
          "title":"西安植物园",
          "message":164,
          "price":9,
          "map":"雁塔区"
        },{
          "id":"18",
          "imgUrl":"/api/img/like18.jpg",
          "title":"西安东大南山温泉",
          "message":167,
          "price":128,
          "map":"长安区"
        },{
          "id":"19",
          "imgUrl":"/api/img/like19.jpg",
          "title":"大雁塔北广场",
          "message":157,
          "price":189,
          "map":"曲江旅游..."
        },{
          "id":"20",
          "imgUrl":"/api/img/like20.jpg",
          "title":"陕西自然博物馆",
          "message":566,
          "price":45,
          "map":"雁塔区"
        },{
          "id":"21",
          "imgUrl":"/api/img/like21.jpg",
          "title":"高家大院",
          "message":2743,
          "price":15,
          "map":"莲湖区"
        },{
          "id":"22",
          "imgUrl":"/api/img/like22.jpg",
          "title":"大唐芙蓉园",
          "message":27696,
          "price":108,
          "map":"曲江旅游..."
        },{
          "id":"23",
          "imgUrl":"/api/img/like23.jpg",
          "title":"西安电视塔西部之光",
          "message":328,
          "price":58,
          "map":"雁塔区"
        },{
          "id":"24",
          "imgUrl":"/api/img/like24.jpg",
          "title":"陕西历史博物馆",
          "message":41768,
          "price":30,
          "map":"雁塔区"
        }
      ],
      "vacationList":[
        {
          "id":"01",
          "imgUrl":"/api/img/vacation01.jpg",
          "title":"西安泡汤圣地",
          "text":"解压之地，放松自己，来一段轻松的旅程。"
        },{
          "id":"02",
          "imgUrl":"/api/img/vacation02.jpg",
          "title":"西安必打卡",
          "text":"寻长安梦，开启穿越的圆梦之旅。"
        },{
          "id":"03",
          "imgUrl":"/api/img/vacation03.jpg",
          "title":"探寻文化古都",
          "text":"一场时空穿越的旅行，探寻历史悠久的文化古都！寻觅历史留下的点点足迹，细细品味古人的伟大。"
        },{
          "id":"04",
          "imgUrl":"/api/img/vacation04.jpg",
          "title":"西安花花世界",
          "text":"月落星驰又一春，不负人间看花人。"
        },{
          "id":"05",
          "imgUrl":"/api/img/vacation05.jpg",
          "title":"西安演出在线",
          "text":"这里有绚丽奇幻的神秘梦幻舞剧，歌舞揭开盛唐面纱，体验穿越时空的奇妙，感受大唐之盛世。"
        },{
          "id":"06",
          "imgUrl":"/api/img/vacation06.jpg",
          "title":"西安亲子必玩",
          "text":"西安亲子必去景点，和家人一起度过欢乐亲子时光，带你嗨翻假期！"
        }
      ]
    },
    {
      "city": "咸阳",
      "swiperList":[
        {
          "id":"01",
          "imgUrl":"/api/img/swiper01.jpg"
        },
        {
          "id":"02",
          "imgUrl":"/api/img/swiper02.jpg"
        },
        {
          "id":"03",
          "imgUrl":"/api/img/swiper03.jpg"
        }
      ],
      "iconsList":[
        {
          "id":"01",
          "imgUrl":"/api/img/icons01.png",
          "title":"景点门票"
        },{
          "id":"02",
          "imgUrl":"/api/img/icons02.png",
          "title":"一日游"
        },{
          "id":"03",
          "imgUrl":"/api/img/icons03.png",
          "title":"识春赏花"
        },{
          "id":"04",
          "imgUrl":"/api/img/icons04.png",
          "title":"精品小团"
        },{
          "id":"05",
          "imgUrl":"/api/img/icons05.png",
          "title":"咸阳湖必游"
        },{
          "id":"06",
          "imgUrl":"/api/img/icons06.png",
          "title":"动植物园"
        },{
          "id":"07",
          "imgUrl":"/api/img/icons07.png",
          "title":"袁家村"
        },{
          "id":"08",
          "imgUrl":"/api/img/icons08.png",
          "title":"兵马俑"
        },{
          "id":"09",
          "imgUrl":"/api/img/icons09.png",
          "title":"泡温泉  "
        },{
          "id":"10",
          "imgUrl":"/api/img/icons10.png",
          "title":"陕历博"
        }
      ],
      "hotImgs":[
        {
          "id":"01",
          "imgUrl":"/api/img/hot01.jpg",
          "title":"华清宫",
          "price":108
        },{
          "id":"02",
          "imgUrl":"/api/img/hot02.jpg",
          "title":"秦始皇陵博物院（兵马俑）",
          "price":120
        },{
          "id":"03",
          "imgUrl":"/api/img/hot03.jpg",
          "title":"大唐芙蓉园",
          "price":108
        },{
          "id":"04",
          "imgUrl":"/api/img/hot04.jpg",
          "title":"陕西历史博物馆",
          "price":30
        },{
          "id":"05",
          "imgUrl":"/api/img/hot05.jpg",
          "title":"大明宫国家遗址公园",
          "price":82
        },{
          "id":"06",
          "imgUrl":"/api/img/hot06.jpg",
          "title":"曲江海洋极地公园",
          "price":158
        },{
          "id":"07",
          "imgUrl":"/api/img/hot07.jpg",
          "title":"秦岭野生动物园",
          "price":48
        },
        {
          "id":"08",
          "imgUrl":"/api/img/hot08.jpg",
          "title":"西安城墙",
          "price":60
        }
      ],
      "likeList":[
        {
          "id":"01",
          "imgUrl":"/api/img/hot01.jpg",
          "title":"华清池",
          "message":37018,
          "price":108,
          "map":"临潼区"
        },{
          "id":"02",
          "imgUrl":"/api/img/like02.jpg",
          "title":"汤峪天潭温泉酒店",
          "message":241,
          "price":150,
          "map":"蓝田县"
        },{
          "id":"03",
          "imgUrl":"/api/img/like03.jpg",
          "title":"华清爱琴海温泉",
          "message":777,
          "price":138,
          "map":"临潼区"
        },{
          "id":"04",
          "imgUrl":"/api/img/like03.jpg",
          "title":"华清爱琴海温泉",
          "message":777,
          "price":138,
          "map":"临潼区"
        },{
          "id":"05",
          "imgUrl":"/api/img/like03.jpg",
          "title":"华清爱琴海温泉",
          "message":777,
          "price":138,
          "map":"临潼区"
        },{
          "id":"06",
          "imgUrl":"/api/img/like03.jpg",
          "title":"华清爱琴海温泉",
          "message":777,
          "price":138,
          "map":"临潼区"
        },{
          "id":"07",
          "imgUrl":"/api/img/like03.jpg",
          "title":"华清爱琴海温泉",
          "message":777,
          "price":138,
          "map":"临潼区"
        },{
          "id":"08",
          "imgUrl":"/api/img/like03.jpg",
          "title":"华清爱琴海温泉",
          "message":777,
          "price":138,
          "map":"临潼区"
        },{
          "id":"09",
          "imgUrl":"/api/img/like03.jpg",
          "title":"华清爱琴海温泉",
          "message":777,
          "price":138,
          "map":"临潼区"
        },{
          "id":"10",
          "imgUrl":"/api/img/like03.jpg",
          "title":"华清爱琴海温泉",
          "message":777,
          "price":138,
          "map":"临潼区"
        }
      ],
      "vacationList":[
        {
          "id":"01",
          "imgUrl":"/api/img/vacation01.jpg",
          "title":"西安泡汤圣地",
          "text":"解压之地，放松自己，来一段轻松的旅程。"
        },{
          "id":"02",
          "imgUrl":"/api/img/vacation02.jpg",
          "title":"西安必打卡",
          "text":"寻长安梦，开启穿越的圆梦之旅。"
        },{
          "id":"03",
          "imgUrl":"/api/img/vacation02.jpg",
          "title":"西安必打卡",
          "text":"寻长安梦，开启穿越的圆梦之旅。"
        },{
          "id":"04",
          "imgUrl":"/api/img/vacation02.jpg",
          "title":"西安必打卡",
          "text":"寻长安梦，开启穿越的圆梦之旅。"
        },{
          "id":"05",
          "imgUrl":"/api/img/vacation02.jpg",
          "title":"西安必打卡",
          "text":"寻长安梦，开启穿越的圆梦之旅。"
        },{
          "id":"06",
          "imgUrl":"/api/img/vacation02.jpg",
          "title":"西安必打卡",
          "text":"寻长安梦，开启穿越的圆梦之旅。"
        },{
          "id":"07",
          "imgUrl":"/api/img/vacation02.jpg",
          "title":"西安必打卡",
          "text":"寻长安梦，开启穿越的圆梦之旅。"
        },{
          "id":"08",
          "imgUrl":"/api/img/vacation02.jpg",
          "title":"西安必打卡",
          "text":"寻长安梦，开启穿越的圆梦之旅。"
        }
      ]
    },
    {
      "city": "北京",
      "swiperList":[
        {
          "id":"01",
          "imgUrl":"/api/img/swiper01.jpg"
        },
        {
          "id":"02",
          "imgUrl":"/api/img/swiper02.jpg"
        },
        {
          "id":"03",
          "imgUrl":"/api/img/swiper03.jpg"
        }
      ],
      "iconsList":[
        {
          "id":"01",
          "imgUrl":"/api/img/icons01.png",
          "title":"景点门票"
        },{
          "id":"02",
          "imgUrl":"/api/img/icons02.png",
          "title":"一日游"
        },{
          "id":"03",
          "imgUrl":"/api/img/icons03.png",
          "title":"识春赏花"
        },{
          "id":"04",
          "imgUrl":"/api/img/icons04.png",
          "title":"精品小团"
        },{
          "id":"05",
          "imgUrl":"/api/img/icons05.png",
          "title":"北京必游"
        },{
          "id":"06",
          "imgUrl":"/api/img/icons06.png",
          "title":"动植物园"
        },{
          "id":"07",
          "imgUrl":"/api/img/icons07.png",
          "title":"故宫"
        },{
          "id":"08",
          "imgUrl":"/api/img/icons08.png",
          "title":"鸟巢"
        },{
          "id":"09",
          "imgUrl":"/api/img/icons09.png",
          "title":"泡温泉  "
        },{
          "id":"10",
          "imgUrl":"/api/img/icons10.png",
          "title":"陕历博"
        }
      ],
      "hotImgs":[
        {
          "id":"01",
          "imgUrl":"/api/img/hot01.jpg",
          "title":"华清宫",
          "price":108
        },{
          "id":"02",
          "imgUrl":"/api/img/hot02.jpg",
          "title":"秦始皇陵博物院（兵马俑）",
          "price":120
        },{
          "id":"03",
          "imgUrl":"/api/img/hot03.jpg",
          "title":"大唐芙蓉园",
          "price":108
        },{
          "id":"04",
          "imgUrl":"/api/img/hot04.jpg",
          "title":"陕西历史博物馆",
          "price":30
        },{
          "id":"05",
          "imgUrl":"/api/img/hot05.jpg",
          "title":"大明宫国家遗址公园",
          "price":82
        },{
          "id":"06",
          "imgUrl":"/api/img/hot06.jpg",
          "title":"曲江海洋极地公园",
          "price":158
        },{
          "id":"07",
          "imgUrl":"/api/img/hot07.jpg",
          "title":"秦岭野生动物园",
          "price":48
        },
        {
          "id":"08",
          "imgUrl":"/api/img/hot08.jpg",
          "title":"西安城墙",
          "price":60
        }
      ],
      "likeList":[
        {
          "id":"01",
          "imgUrl":"/api/img/hot01.jpg",
          "title":"华清池",
          "message":37018,
          "price":108,
          "map":"临潼区"
        },{
          "id":"02",
          "imgUrl":"/api/img/like02.jpg",
          "title":"汤峪天潭温泉酒店",
          "message":241,
          "price":150,
          "map":"蓝田县"
        },{
          "id":"03",
          "imgUrl":"/api/img/like03.jpg",
          "title":"华清爱琴海温泉",
          "message":777,
          "price":138,
          "map":"临潼区"
        },{
          "id":"04",
          "imgUrl":"/api/img/like03.jpg",
          "title":"华清爱琴海温泉",
          "message":777,
          "price":138,
          "map":"临潼区"
        },{
          "id":"05",
          "imgUrl":"/api/img/like03.jpg",
          "title":"华清爱琴海温泉",
          "message":777,
          "price":138,
          "map":"临潼区"
        },{
          "id":"06",
          "imgUrl":"/api/img/like03.jpg",
          "title":"华清爱琴海温泉",
          "message":777,
          "price":138,
          "map":"临潼区"
        },{
          "id":"07",
          "imgUrl":"/api/img/like03.jpg",
          "title":"华清爱琴海温泉",
          "message":777,
          "price":138,
          "map":"临潼区"
        },{
          "id":"08",
          "imgUrl":"/api/img/like03.jpg",
          "title":"华清爱琴海温泉",
          "message":777,
          "price":138,
          "map":"临潼区"
        },{
          "id":"09",
          "imgUrl":"/api/img/like03.jpg",
          "title":"华清爱琴海温泉",
          "message":777,
          "price":138,
          "map":"临潼区"
        },{
          "id":"10",
          "imgUrl":"/api/img/like03.jpg",
          "title":"华清爱琴海温泉",
          "message":777,
          "price":138,
          "map":"临潼区"
        }
      ],
      "vacationList":[
        {
          "id":"01",
          "imgUrl":"/api/img/vacation01.jpg",
          "title":"西安泡汤圣地",
          "text":"解压之地，放松自己，来一段轻松的旅程。"
        },{
          "id":"02",
          "imgUrl":"/api/img/vacation02.jpg",
          "title":"西安必打卡",
          "text":"寻长安梦，开启穿越的圆梦之旅。"
        },{
          "id":"03",
          "imgUrl":"/api/img/vacation02.jpg",
          "title":"西安必打卡",
          "text":"寻长安梦，开启穿越的圆梦之旅。"
        },{
          "id":"04",
          "imgUrl":"/api/img/vacation02.jpg",
          "title":"西安必打卡",
          "text":"寻长安梦，开启穿越的圆梦之旅。"
        },{
          "id":"05",
          "imgUrl":"/api/img/vacation02.jpg",
          "title":"西安必打卡",
          "text":"寻长安梦，开启穿越的圆梦之旅。"
        },{
          "id":"06",
          "imgUrl":"/api/img/vacation02.jpg",
          "title":"西安必打卡",
          "text":"寻长安梦，开启穿越的圆梦之旅。"
        },{
          "id":"07",
          "imgUrl":"/api/img/vacation02.jpg",
          "title":"西安必打卡",
          "text":"寻长安梦，开启穿越的圆梦之旅。"
        },{
          "id":"08",
          "imgUrl":"/api/img/vacation02.jpg",
          "title":"西安必打卡",
          "text":"寻长安梦，开启穿越的圆梦之旅。"
        }
      ]
    }
  ]
}
```

2）Axios异步请求

　　　a）安装

```
cnpm i axios -S
或者：
	yarn add axios
	nrm i axios -S
```

　　　b）全局引入

```
// 引入axios
import axios from 'axios'
Vue.prototype.$http = axios;
```

　　　c）在Home.vue中发请求

```
mounted(){
      this.$http({
        url:'http://192.168.0.102:8091/static/mock/data/travel.json'
      }).then(res=>{
        console.log(res.data.data[0])
      }).catch(err=>{//异常处理
        console.log(err)
      })
    }
    
mounted(){
      this.$http({
        url:'http://192.168.0.102:81/api/travel'
      }).then(res=>{
        console.log(res.data.data[0]);
        let data = res.data.data[0];
        
        this.iconsList = data.iconsList;
        this.hotList = data.hotList;
        this.likeList = data.likeList;
        this.swiperList = data.swiperList;
        
      }).catch(err=>{//异常处理
        console.log(err)
      })
    }    
```

### 26、在Vue项目中创建后台接口

在build的webpack.dev.conf.js文件中，添加如下代码：

```
...
const portfinder = require('portfinder')

const express = require('express');
const app = express();
const appData = require('../static/mock/data/travel.json');
const data = appData.data;
const apiRoutes = express.Router();
app.use('/api',apiRoutes);

const HOST = process.env.HOST
....
devServer: {
	// 配置路由
    before(app) {
      app.get('/api/travel',(req, res) => {
        res.json({
          errCode: 0,
          data: data
        })
      });
      app.post('/api/travel',(req, res) => {
        res.json({
          errCode: 0,
          data: data
        })
      });
    },
    
    clientLogLevel: 'warning',
    historyApiFallback: {
    ....
```

### 27、修改端口

1）修改config->index.js文件中的代码

```
......
dev: {
    // Paths
    assetsSubDirectory: 'static',
    assetsPublicPath: '/',
    proxyTable: {},

    // Various Dev Server settings
    host: '192.168.0.102', // can be overwritten by process.env.HOST
    port: 80, // can be overwritten by process.env.PORT, if port is in use, a free one will be determined
    autoOpenBrowser: false,
    errorOverlay: true,
    notifyOnErrors: true,
    poll: false, // https://webpack.js.org/configuration/dev-server/#devserver-watchoptions-
......
```

2）重启服务

### 28、从Home.vue向其子组件派数据

1）绑定数据到子组件

```
<div class="home">
    <HomeHeader />
    <home-header></home-header>-->
    <home-header />
    <home-swiper :swiperList="swiperList" />
    <home-icons :iconsList="iconsList" />
    <home-location />
    <home-hot :hotList="hotList" />
    <home-like :likeList="likeList" />
    <home-footer />
</div>
```

2）子组件接收传值

```
export default {
    props:{
        hotList:{
            type:Array,
            default:[]
        }
	},
...
```

### 29、在阿里云上利用node.js搭建后台数据接口

1）搭建node环境

```
express -e 项目名
```

2）将img和json复制到public目录下

3）routes->index.js文件中创建接口

```
var express = require('express');
var router = express.Router();
const fs = require('fs');

// 解决跨域
router.all("*",function(req,res,next){
    //设置允许跨域的域名，*代表允许任意域名跨域
    res.header("Access-Control-Allow-Origin","*");
    //允许的header类型
    res.header("Access-Control-Allow-Headers","content-type");
    //跨域允许的请求方式 
    res.header("Access-Control-Allow-Methods","DELETE,PUT,POST,GET,OPTIONS");
    if (req.method.toLowerCase() == 'options')
        res.send(200);  //让options尝试请求快速结束
    else
        next();
});

/*秦思旅游项目接口*/
router.get('/travel',(req,res)=>{
    var file = './public/data/travel.json';
    //读取json文件
    fs.readFile(file, 'utf-8', function(err, data) {
        if (err) {
            res.send({error_code:1});
        } else {
            res.send({
                error_code:0,
                data:JSON.parse(data)
            });
        }
    });
})
module.exports = router;
```

### 30、在阿里云上利用PHP搭建后台数据接口

1）启动phpstudy，端口为80，路径为自己项目的目录

2）在项目目录下创建travel.php文件，文件内容如下：

```
<?php
    header("Content-Type: text/html;charset=utf-8");
    header("Access-Control-Allow-Origin:*");
    header('Access-Control-Allow-Methods:POST');
    header('Access-Control-Allow-Headers:x-requested-with, content-type');
    //$callback = isset($_REQUEST['callback']) ? trim($_REQUEST['callback']) : '';
    //jsonp回调参数，必需
    function getKey($key,$default=""){
    	return trim(isset($_REQUEST[$key])?$_REQUEST[$key]:$default);
    } 
    $json_string = file_get_contents("./data/travel.json");// 从文件中读取数据到PHP变量
    $data = json_decode($json_string,true);// 把JSON字符串转成PHP数组
    echo json_encode($data,JSON_UNESCAPED_UNICODE);//将处理后的数据发向前端
```

3）前端实现

```
this.$http({
	url:'http://47.105.51.229/travel.php'
}).then(res=>{
    console.log(res.data.data);
    let data = res.data.data[0];

    this.iconsList = data.iconsList;
    this.hotList = data.hotList;
    this.likeList = data.likeList;
    this.swiperList = data.swiperList;

}).catch(err=>{
	console.log(err)
})
```

### 31、给城市列表页添加滚动条

参考网址：

```
https://github.com/huangjincq/vue-better-scroll
```

1）安装better-scroll插件

```
cnpm i better-scroll -S
```

2）整合页面布局

```
把Hot.vue、Sort.vue和List.vue整合到List.vue中。注意；要优化CSS样式，数据传值。
```

3）引better-scroll

```
import BScroll from 'better-scroll'
```

4）逻辑处理

```
data(){
    return{
    	scroll:''
    }
},
mounted(){
    //console.log(this.$refs['container']);
    const container = this.$refs['container'];
    this.scroll = new BScroll(container);
}
```

5）添加样式

```
.container{
    position: absolute;
    left:0;
    right:0;
    bottom:0;
    top:.88rem;
    overflow: hidden;
}
```

6）解决better-scroll不能滚动问题

　　需要DOM加载完成后才能正确应用. vue中应用在$nextTick中，异步初始化。 　　子元素高度需要超过父元素。而且父元素需要设置高度。这才是better-scroll能够滚动的原理。 　　better-scroll在使用的时候，滚动只作用于第一个子元素，其它的元素都会被忽略。在vue中，获取的ref是seller，那么它的子元素seller-wrapper才是需要滚动的部分。

```
<div class="seller" ref="seller">
    <div class="seller-wrapper">
        ...这里才是内容
    </div>
</div>
```

　　还有一种可能就是隐藏切换显示。这样都会导致插件参数的scrollerHeight:0。此时需要加上click:true，使better-scroll支持点击事件，再调用下refresh(）重新渲染DOM就行了。

```
 this.$nextTick(()=>{
     if (!this.scroll) {
         this.scroll = new BScroll(this.$refs.rongqi, {
         	click: true
         });
     } else {
     	this.scroll.refresh();
     };
 });
```

### 32、单击城市字母跳转到对应位置

1）better-scroll API网址：

```
https://ustbhuangyi.github.io/better-scroll/doc/zh-hans/api.html#scrolltoelementel-time-offsetx-offsety-easing
```

2）HTML

![](E:\秦思IT11&12班\03 项目\02 秦思旅游(Vue+Node.js+Stylus)\项目笔记\better_scroll.png)

3）逻辑实现

![](E:\秦思IT11&12班\03 项目\02 秦思旅游(Vue+Node.js+Stylus)\项目笔记\better_scroll1.png)

### 33、Vuex创建数据仓库（商店）

官方文档：

```
https://vuex.vuejs.org/zh/
```

Vuex:数据仓库/数据商店/响应式存储，它的核心是store。

1）安装

```
cnpm i vuex -S
```

2）创建js文件(src->store->index.js)

```
import Vue from 'vue'
import Vuex from 'vuex'
Vue.use(Vuex)

const state = {
	city:'xxx'
}

export default new Vuex.Store({
	state
})
```

3）全局引入数据仓库并注册(main.js)

```
import store from './store'
new Vue({
    ...
    store,//注册数据仓库
    ...
});
```

4）使用 

 a.在要使用仓库数据的组件中，引入

```
import { mapState } from 'vuex'
```

b.再在该组件中添加计算属性

```
export default {
    computed:{
    	...mapState(['city'])
    }
}
```

c.数据渲染

```
<router-link to="/city">
    <div class="next">
    	{{ cityName }}<span class="iconfont iconsanjiao_xia"></span>
    </div>
</router-link>
```

### 34、修改仓库中的数据

1)定义修改数据的方法

```
const mutations = {//mutation用来修改state中的数据
    changeCity(state,cityName){
    	state.city = cityName
    }
};

export default new Vuex.Store({//抛出
    state,
    mutations
})
```

2）在组件中调用修改数据的方法 	a.引入

```
import { mapMutations } from 'vuex'
```

b.用mutations引入方法

```
...mapMutations(['changeCity'])
```

c.调用方法

```
methods:{
    changeCityName(cityName){
        this.changeCity(cityName);
        this.$router.push('/');
    },
    ...mapMutations(['changeCity'])
}
```

Tips:

```
  state和mutation是vuex的一个语法糖（语法糖（Syntactic sugar），也译为糖衣语法，指计算机语言中添加的某种语法，这种语法对语言的功能并没有影响，但是更方便程序员使用。通常来说使用语法糖能够增加程序的可读性，从而减少程序代码出错的机会）。
  语法糖是指在不影响功能的情况下,添加某种方法实现同样的效果,从而方便程序开发。Vue.js的v-bind和v-on指令都提供了语法糖,也可以说是缩写,比如 v-bind,可以省略v-bind,直接写一个冒号":"。
```

### 35、本地存储

由于vue自身特性的原因，vuex中的数据在页面刷新之后其中的数据会初始化，这就导致组件之间通过vuex传递的数据在用户F5刷新页面之后会丢失。

```
解决方案：结合localStorage或sessionStorage实现页面刷新之后数据不丢失。
```

### 35、keep-alive

作用：用来缓存DOM数据，不重复刷新，从而达到优化请求的目的。

1）用keep-alive包裹

```
<keep-alive>
	<router-view></router-view>
</keep-alive>
```

2）keep-alive会产生一个activated的生命周期

```
activated(){
    if(this.changeCity != this.city){
        this.getHttp();
        this.changeCity = this.city;
    }
}
```

### 36、添加移动端手机定位（百度地图）

```
1）在vue项目中使用H5新特性在IOS手机上打开vue网页会有适应性问题，并且无法获取所在城市，因此使用第三方库百度地图api。
	2）使用步骤
		a.获取百度地图密钥
		(1).注册百度开发者帐户 <http://lbsyun.baidu.com/>
		(2).创建网站为网站申请百度地址访问密钥 AccessKey
		b.实现百度地图定位
		(1).在vue项目中index.html中引入百度地图api
			<script type="text/javascript" src="http://api.map.baidu.com/api?v=2.0&ak=【你的秘钥】"></script>
		(2).在build/webpack.base.conf.js里面配置
            module.exports = {
                context: path.resolve(__dirname, '../'),
                entry: {
                    app: './src/main.js'
                },
                //添加
                externals: {
                    "BMap": "BMap"
                },
            }
		(3).定义方法，并在mounted中进行引用

            <template>
              <header class="header">
                <p>{{ city }}</p>
              </header>
            </template>

            <script>
              //引入BMap
              import BMap from 'BMap'

              export default {
                //定义数据
                data() {
                  return {
                    location: null,
                    city: ''
                  }
                },
                methods: {
                  //定义方法
                  getCity() {
                    let _this = this;
                    var geolocation = new BMap.Geolocation();
                    geolocation.getCurrentPosition(function (r) {
                      /*if (this.getStatus() == BMAP_STATUS_SUCCESS) {
                        if(r.accuracy==null){
                          alert('您已拒绝地理位置授权');
                          //用户决绝地理位置授权
                          return;
                        }else{*/
                      const myGeo = new BMap.Geocoder()
                      myGeo.getLocation(new BMap.Point(r.point.lng, r.point.lat), data => {
                        /*if (data.addressComponents) {
                          const result = data.addressComponents
                          const location = {
                            creditLongitude: r.point.lat, // 经度
                            creditLatitude: r.point.lng, // 纬度
                            creditProvince: result.province || '', // 省
                            creditCity: result.city || '', // 市
                            creditArea: result.district || '', // 区
                            creditStreet: (result.street || '') + (result.streetNumber || '') // 街道
                          };
                          _this.location = location;
                          _this.creditLongitude=location.creditLongitude;
                          _this.creditLatitude=location.creditLatitude;
                          _this.creditCity=location.creditCity;*/
                        _this.city = data.addressComponents.city.replace('市', '')
                        //}
                      })
                      // }
                      // }
                    })
                 }
                },
                //mounted中引用
                mounted() {
                  this.getCity();
                }
              }
            </script>
```

### 37、移动端添加地图(vue-baidu-map)

```
1）安装
		cnpm i --save vue-baidu-map
	2）引入（可以只在当前组件中引入）
    	  import BMap from 'BMap'
          import BaiduMap from 'vue-baidu-map'

          Vue.use(BaiduMap, {
            ak: 'xxxx'
          });
	3）使用

    	<template>
        <header>
          {{ city }}
          <baidu-map class="map" style="display: flex; flex-direction: column" center="陕西">
            <bm-view style="width: 100%; height:100px; flex: 1"></bm-view>
            <bm-scale anchor="BMAP_ANCHOR_TOP_RIGHT"></bm-scale>
            <bm-navigation anchor="BMAP_ANCHOR_TOP_RIGHT"></bm-navigation>
            <bm-geolocation anchor="BMAP_ANCHOR_BOTTOM_RIGHT" :showAddressBar="true" :autoLocation="true"></bm-geolocation>
            <bm-map-type :map-types="['BMAP_NORMAL_MAP', 'BMAP_HYBRID_MAP']" anchor="BMAP_ANCHOR_TOP_LEFT"></bm-map-type>
          </baidu-map>
        </header>
    </template>

    <script>
      //引入BMap
      import BMap from 'BMap'
      import BaiduMap from 'vue-baidu-map'

      Vue.use(BaiduMap, {
        ak: 'vebSflNH1t7anWyMXHZf09hhTtM2bx3R'
      });
      export default {
        props:['title'],
        //定义数据
        data() {
          return {
            location: null,//必须赋初值为null
            city: ''
          }
        },
        methods: {
          //定义方法
          getCity() {
            let _this = this;
            var geolocation = new BMap.Geolocation();
            geolocation.getCurrentPosition(function (r) {
              const myGeo = new BMap.Geocoder()
              myGeo.getLocation(new BMap.Point(r.point.lng, r.point.lat), data => {
                /*if (data.addressComponents) {
                  const result = data.addressComponents
                  const location = {
                    creditLongitude: r.point.lat, // 经度
                    creditLatitude: r.point.lng, // 纬度
                    creditProvince: result.province || '', // 省
                    creditCity: result.city || '', // 市
                    creditArea: result.district || '', // 区
                    creditStreet: (result.street || '') + (result.streetNumber || '') // 街道
                  };
                  _this.location = location;
                  _this.creditLongitude = location.creditLongitude;
                  _this.creditLatitude = location.creditLatitude;
                  _this.creditCity = location.creditCity;
                  console.log(location)
                }*/
                /*console.log(data.addressComponents.city.replace('市', ''))*/
                _this.city = data.addressComponents.city.replace('市', '')
              })
            })
          }
        },
        mounted() {
          this.getCity();
        }
      }
    </script>

    <style scoped>
      .map {
        width: 100%;
        height: 300px;
      }
    </style>
```

### 38、Vue父子组件数据双向绑定，子组件可修改props

　　父组件 => props[parent-data] => 子组件 => watch[parent-data] => children-data = parent-data // 子组件监听父组件的改变；

　　子组件 => $emit[children-data] => 父组件 => parant-data = children-data // 子组件通知父组件自身的改变。

```
// 父组件
<div>
    <Children :parentData="parentData" @getChildrenStatus="getChildrenStatus"></Children>
</div>
// 父组件
data(){
    return {
        parentData: 1
    }
},
methods: {
    getChildrenStatus: function(data){ // 实时更新子组件的变化
        this.parentData = data
    }
}
//子组件
data(){
    return {
        childrenData: 1
    }
},
props: ['parentData'],
watch: {
    parentData: function(){ // 监听父组件的变化
        this.childrenData = this.parentData
    }
}
mounted(){
    this.$emit('getChildrenStatus', this.childrenData) // 将改变通知父组件(保证父子组件数据一致)
}
```

### 39、图表

```
1.安装并在需要用图表的地方引入 例如：hello.js
 	cnpm i -S echarts
    import echarts from 'echarts'
 
2.hello.vue  中写个容器     
    <div id='myChart' style='width：600px;height:600px'></div> 
3.在hello.js     
 export default {
  name: 'hello',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  mounted(){
    this.drawLine();
  },
  methods: {
    drawLine(){
        // 基于准备好的dom，初始化echarts实例
        let myChart = this.$echarts.init(document.getElementById('myChart'))
        // 绘制图表
        myChart.setOption({
            title: { text: '在Vue中使用echarts' },
            tooltip: {},
            xAxis: {
                data: ["衬衫","羊毛衫","雪纺衫","裤子","高跟鞋","袜子"]
            },
            yAxis: {},
            series: [{
                name: '销量',
                type: 'bar',
                data: [5, 20, 36, 10, 10, 20]
            }]
        });
    }
  }
}
```

### 40、 真机测试

```
进入https://cli.im/，可以用网址，如http://192.168.0.114生成二维码预览。
也可以用同一网段的Wifi，直接在手机端打开浏览器，输入网址http://192.168.0.114进入。
```

### 41、项目打包

因为服务器不识别.vue等的文件，需要打包成.html(.css/.js等)。

1）修改config->index.js文件：

```
build: {
    // Template for index.html
    index: path.resolve(__dirname, '../dist/index.html'),

    // Paths
    assetsRoot: path.resolve(__dirname, '../dist'),
    assetsSubDirectory: 'static',
    assetsPublicPath: './',//修改处
    ......
```

2）打包

```
npm run build
```

3）测试

```
直接双击index.html文件。
```

4）测试后发现本地数据拿不到，数据（.json和图片）必须挂到服务器上才能拿到，这里用php解决跨域问题。

```
<?php
    // 制定允许其他域名访问
    header("Access-Control-Allow-Origin:*");
    // 响应类型
    header('Access-Control-Allow-Methods:POST');
    // 响应头设置
    header('Access-Control-Allow-Headers:x-requested-with, content-type');

    //$callback = isset($_REQUEST['callback']) ? trim($_REQUEST['callback']) : ''; //jsonp回调参数，必需
    function getKey($key,$default=""){
        return trim(isset($_REQUEST[$key])?$_REQUEST[$key]:$default);
    }
    $json_string = file_get_contents("./data/home_data.json");// 从文件中读取数据到PHP变量
    $data = json_decode($json_string,true);// 把JSON字符串转成PHP数组
    echo json_encode($data,JSON_UNESCAPED_UNICODE);//将处理后的数据发向前端,传到阿里云时，要把",JSON_UNESCAPED_UNICODE"删除。
```

### 42、项目生成安装包

```
1）在线云打包
	借助于HBuilder实现（HBuilder是一个绿色版前端开发IDE，不需要安装，解压即可）
2）本地打包（cordova）（需要安装node/jdk/cordova）
```

### 43、网站参考

1. 项目参考网站：<http://touch.piao.qunar.com/touch/index_%E8%A5%BF%E5%AE%89.html>
2. base64转换：<http://imgbase64.duoshitong.com/>
3. reset.css:<https://meyerweb.com/eric/tools/css/reset/>
4. FastClick:<https://majing.io/posts/10000007721218> 解决移动端300ms的延时
5. Iconfont:<https://www.iconfont.cn/>
6. better-scroll:（1）<https://github.com/ustbhuangyi/better-scroll>（2）<http://ustbhuangyi.github.io/better-scroll/doc/api.html>
7. vuex:<https://vuex.vuejs.org/zh/guide/state.html>
8. 移动端地图:<https://dafrok.github.io/vue-baidu-map/#/>
9. Vue+echarts图表:<https://www.cnblogs.com/ifannie/p/7992917.html>
10. vue-schart图表：<https://github.com/lin-xin/vue-schart>
11. 草料二维码:<https://cli.im/>