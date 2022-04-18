1.vue-cli脚手架
2.node + webpack + 淘宝镜像

node_modules文件夹：项目依赖文件夹

public文件夹： 一般放置一些静态资源，需要注意，放在public文件夹中的静态资源，webpack打包时会原封不动打包到dist文件夹中

src文件夹（程序员源代码文件夹）：
    assets文件夹： 一般也是放置静态资源（一般放置多个组件公用的静态资源），需要注意，放置在assets文件夹里面的静态资源，在webpack打包的时候，webpack会把静态资源当做一个模块，打包在JS文件里面
    compunents文件夹： 一般放置的是费路由组件（全局组件）
    App.vue： 唯一的根组件，Vue当中的组件（.vue）
    main.js：程序入口文件，也是程序最先执行的文件

    babel.config.js：配置文件（babel相关）

    package.json文件：记录项目信息，项目中有哪些依赖，项目怎么运行

    package-lock.json：缓存文件

    README.md说明性文件

2 项目的其他配置
2.1 项目运行起来，浏览器自动打开

  "scripts": {
    "serve": "vue-cli-service serve --open",
    "build": "vue-cli-service build",
    "lint": "vue-cli-service lint"
  },

  2.2 eslint检验功能关闭
  在根目录下创建一个vue.config.js文件，令lintOnSave=false
  比如声明变量，但是未使用。eslint会报错
  module.exports = {
  //关闭eslint
  lintOnSave: false
}

  2.3 配置别名
  src文件夹简写方法，配置别名。@
  {
  "compilerOptions": {
    "baseUrl": "./",
    "paths": {
      "@/*": [
        "src/*"
      ]
    }
  },
  "exclude": [
    "node_modules",
    "dist"
  ]
}

运行时出现了使用npm run serve 命令后，出现
Error: error:0308010C:digital envelope routines::unsupported

解决方法是：在命令行运行代码
set NODE_OPTIONS=--openssl-legacy-provider
之后运行npm run serve就行了



3 项目路由分析
vue-router
前端所谓路由： kv键值对
key: URL(地址栏中的地址)
value：相应的路由组件
注意：项目上中下结构

路由组建：Home首页路由组件，Search路由组件，login登陆首页，Register注册路由
非路由组件：
Hearder、Footer（在首页和搜索页面有，在登陆和注册页面没有）

4 完成非路由组件Header与Footer业务
在项目中，不再以HTML+CSS为主  主要搞业务和逻辑

在开发项目的时候：
1.书写静态页面
2.拆分组件
3.获取服务器的数据动态展示
4.完成相应的动态业务逻辑

注意1：创建组件的时候，组件结构+组建样式+图片资源都要准备好
注意2：项目采用less样式，浏览器不识别less样式，需要通过less、less-loader进行处理less，把less样式变为CSS样式，浏览器才可以识别

注意： 如果想让组件识别less样式，需要在style标签的身上加上lang属性 lang=less

4.1 使用组件的步骤
-创建或者定义
-引入
-注册
-使用

5. vue-router
路由组件的搭建，路由组建有四个：home,Search、login以及Register

使用npm install --save vue-router进行路由安装


-从components文件夹：经常放置的非路由组件（公用全局组件）
--pages|views文件夹：经常放置路由组件

5.1 配置路由项目当中配置的路由一般放置在router文件夹中

5.2 总结：路由组件和非路由组件的区别？？？？？？？？？
1.路由组件一般放置在pages|views文件夹，费路由组件一般放置在components文件夹中
2.路由组件需要在router文件夹中进行注册（使用的即为组件的名字），费路由组件使用的时候一般使用标签的进行使用
3.注册完路由，不管路由组件还是非路由组件身上都有$route和$routes


$route：获取路由信息【路径、query等信息】
$router：进行编程式导航，进行路由跳转


5.3 路由的跳转
路由的跳转有两种方式：
声明式导航router-link
编程式导航：$router.push|replace

声明式导航能做的，编程式导航都能做，但是编程式导航还可以做一些其他的业务逻辑




6. Footer组件显示与隐藏     v-if || v-show
   在home和search显示
   在登陆和注册隐藏
第一种方法： 根据组件身上的￥route获取当前路由的信息，童工路由路径判断Footer显示与隐藏
第二种方法：配置路由的时候，可以给路由添加元信息{meta}（show），路由配置对象，它的key不能乱写



8 路由传参
路由传参的几种写法
 params参数： 属于路径中的一部分，需要注意，在配置路由的时候，需要占位
 query参数：不输于路径的一部分，类似于Ajax中的queryString /home?k=v&kv=,不需要占位

 //搜索按钮的传递参数
    //第一种：字符串形式


拆分组件
HTML+CSS+图片



9.在项目中，经常会有API文件夹，放关于axios有关内容

10、接口统一管理


11.轮播图的使用

(1)引入依赖的包（swiper.js|swiper.css）
(2)页面的结构必须要有
(3)初始化swiper实例



在工作中，最重要的是完成功能，先完成功能之后再进行功能优化

















详情页面开发
点击商品详情的图片是，跳转到详情页面，在路由调转的时候，需要带上产品的id给详情页面


项目还是要一步一步做的