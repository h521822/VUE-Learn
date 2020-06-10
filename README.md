# VUE搭建步骤
## 工具准备
### VS code
- 下载包

[官网下载](https://code.visualstudio.com/Download)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200407214450575.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2hlMTcyMDczNjc1,size_16,color_FFFFFF,t_70)
- 将默认英文改为中文
`Ctrl+Shift+P`
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200407214629640.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2hlMTcyMDczNjc1,size_16,color_FFFFFF,t_70)

- 安装常用插件
```
Chinese (Simplified) Language Pack for Visual Studio Code
ESLint			代码格式
Vetur
TortoiseSVN				SVN小乌龟
python
```

### node js

-  下载包
下载地址：`https://nodejs.org/en/download/`
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200407213925998.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2hlMTcyMDczNjc1,size_16,color_FFFFFF,t_70)

- 环境变量配置
配置环境变量后，验证是否成功
```
node -v
npm -v
```

### 安装淘宝镜像，可提升效率 http://npm.taobao.org/
> npm install -g cnpm –registry=https://registry.npm.taobao.org
cnpm -v 	检查安装成功


## 搭建vue项目环境
1. 全局安装vue-cli

> npm install --global vue-cli
2. 进入你的项目目录，创建一个基于 webpack 模板的新项目: vue init webpack 项目名
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200610231143779.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2hlMTcyMDczNjc1,size_16,color_FFFFFF,t_70)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200610211058971.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2hlMTcyMDczNjc1,size_16,color_FFFFFF,t_70)

- 说明：
> Vue build ==> 打包方式，回车即可；
Install vue-router ==> 是否要安装 vue-router，项目中肯定要使用到 所以Y 回车；
Use ESLint to lint your code ==> 是否需要 js 语法检测 可是代码更工整 所以 y 回车；
Set up unit tests ==> 是否安装 单元测试工具 目前我们不需要 所以 n 回车；
Setup e2e tests with Nightwatch ==> 是否需要 端到端测试工具 目前我们不需要 所以 n 回车；

3. 进入项目,安装依赖
> cnpm i
4. 启动服务	npm run dev
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200610213436941.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2hlMTcyMDczNjc1,size_16,color_FFFFFF,t_70)

## VUE目录简介
- build：构建脚本目录
1. build.js   ==>  生产环境构建脚本；
2. check-versions.js   ==>  检查npm，node.js版本；
3. utils.js   ==>  构建相关工具方法；
4. vue-loader.conf.js   ==>  配置了css加载器以及编译css之后自动添加前缀；
5. webpack.base.conf.js   ==>  webpack基本配置；
6. webpack.dev.conf.js   ==>  webpack开发环境配置；
7. webpack.prod.conf.js   ==>  webpack生产环境配置；
- config：项目配置
8. dev.env.js   ==>  开发环境变量；
9. index.js   ==>  项目配置文件；
10. prod.env.js   ==>  生产环境变量；
- node_modules：npm 加载的项目依赖模块
- src：这里是我们要开发的目录，基本上要做的事情都在这个目录里。里面包含了几个目录及文件：
1. assets：资源目录，放置一些图片或者公共js、公共css。这里的资源会被webpack构建；
2. components：组件目录，我们写的组件就放在这个目录里面；
3. router：前端路由，我们需要配置的路由路径写在index.js里面；
4. App.vue：根组件；
5. main.js：入口js文件；
- static：静态资源目录，如图片、字体等。不会被webpack构建
- index.html：首页入口文件，可以添加一些 meta 信息等
- package.json：npm包配置文件，定义了项目的npm脚本，依赖包等信息
- README.md：项目的说明文档，markdown 格式
- .xxxx文件：这些是一些配置文件，包括语法配置，git配置等
## 开始我们的第一个vue项目
1. 在components目录下新建一个views目录，里面写我们的vue组件
	1. 开始我们的第一个组件：
	2. 在views目录下新建First.vue
```
<template>
    <div class="first-app">
        {{msg}}
    </div>
</template>

<script>
export default {
  name: 'First',
  data () {
    return {
      msg: 'Welcome to FirstApp'
    }
  }
}
</script>

<style>

</style>

```
	3. 在router目录下的index.js里面配置路由路径
```
import Vue from 'vue'
import Router from 'vue-router'
import HelloWorld from '@/components/HelloWorld'
import First from '@/components/views/First'

Vue.use(Router)

export default new Router({
  routes: [
    {
      path: '/',
      name: 'HelloWorld',
      component: HelloWorld
    },{
      path: '/first',
      name: 'First',
      component: First
    }
  ]
})

```



参考博客：
- vue搭建
> https://www.cnblogs.com/hellman/p/10985377.html
- 代码自动格式化
> https://blog.csdn.net/weixin_41187842/article/details/90173279
