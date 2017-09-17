流程：
    a . 项目文件夹  全局安装 npm install -g webpack
    b . 检测node是否安装 node -v  --->npm是否安装 npm -v
    c . npm init   初始化 完成后出现一个package.json文件              
    d . npm install --save-dev webpack  会在改项目下下载所需要的依赖包  在node_modules文件夹下

打包：
    对css打包
       1. npm install style-loader css-loader
        2. 将依赖包写在webpack.config.js内  


-----------------
修改打包命令：默认是 webpack
    eg： "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "rui": "webpack" // package.json文件里面的
  }
  执行打包: npm run rui
  

  
  
--------------------配置vue环境
 初始化 npm init
 
 安装webpack
	npm install webpack -g  //全局安装webpack
	npm install webpack --save-dev  //安装到项目文件夹
	
 
 安装各个模块：
	npm install --save-dev less   //less
	npm install --save-dev css-loader style-loader  //css
	npm install --save-dev url-loader  //用来处理图片、字体的模块
	npm install --save-dev html-loader  //html模块
	npm install --save-dev text-loader  //text模块
	npm install --save-dev html-webpack-plugin  //生成html插件
	npm install --save-dev webpack-dev-server  //webpack-server服务器 方便调试\
	npm install --save-dev file-loader
	npm install --save-dev vue  
	npm install --save-dev jquery
	npm install --save extract-text-webpack-plugin   // 单独提取css文件插件
	npm install --save-dev devbabel-core babel-preset-es2015  //es6编译
	npm install --save-dev babel-loader  //babel-loader
	npm install --save-dev svg-url-loader   //配置svg图标
	npm install --save-dev vue-loader vue-template-compiler  //用来解析vue组件 .vue结尾的
	npm install --save-dev vue-router 安装路由
 
 
 
 
 
 
 
 





----------------------------------
安装：npm init(初始化)
            npm install webpack --save-dev

简单打包 webpack hello.js hello.bunble.js

引用别的文件：require("文件名");
引用css文件   require("style-loader!,css-loader!.style.css")  这样才能打包
css-loader是为webpack可以处理css文件
style-loader 吧处理完的文件插入到页面的style标签里面
亦可以在命令行里面处理 不在写代码的时候加style-loader 和css-loader

eg:webpack hello.js hello.bundle.js --module-bind 'css=style-loader!css-loader'

要处理css文件需要安装 npm install css-loader style-loader

自动更新：--watch

eg:webpack hello.js hello.bundle.js --module-bind 'css=style-loader!css-loader' --watch

配置文件 （配置完后直接运行 webpack 就行了不需要加啥）;
配置文件名为 webpack.config.js
内容：（根据官网api 有可能会有不一样）
最基本的配置 需要什么--modile-bind 得在package.json里配置

    module.exports={
        entry:"./src/script/main.js",//被打包的文件
      // 有三中写法  为了解决两个不互相依赖又想打包在一起的两个文件  2. ['url1','url2']  3 entry: {
       // page1: "./page1",//大部分用在多页开发的时候
        //    page2: ["./entry1", "./entry2"]
        //}, 

        output:{//输出信息
                path:__dirname+'/dist/js',  //这个必须加上__dirname+"/..."
                filename:'bundel.js'   //打包后的文件名  //如果用的是对象的时候不能用这种 需要用占位符  看官网
        }
    }

 <script src="dist/js/bundel.js"></script> //由于生成的文件名有可能是版本号 所以需要解决这个问题
 需要用到webpack的一个插件  安装：  npm install html-webpack-plugin --save-dev
安装完之后需要配置webpack.config.js

输出进度条和颜色：webpack --progress --colors

安装本地服务器：npm install webpack-dev-server -g  （好处：代码更厚后浏览器会自动刷新）
运行服务器：webpack-dev-server --progress --colors


