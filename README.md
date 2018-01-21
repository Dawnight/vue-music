## vueApp
### 提交记录
#### 第1次提交:项目初始化和基本配置
+ 记录: 
  + 项目初始化配置完成
  + 引入已经写好的`stylus`样式
  + 载入`stylus`和`stylus-loader`
  + 对`webpack.base.conf.js`的引用路径进行简单配置
+ 项目初始化: `vue init webpack vue-app`
+ 关于使用`stylus`
  + 安装`stylus@0.54.5 stylus-loader@2.1.1`到`package.json`文件
  + 不需要手动载入`loader`，安装完成后，项目会自动载入`stylus`和`stylus-loader`，不会报错

+ 路径引用
  + A文件要引用B文件，可以直接使用相对路径引用
  + 与课程标准一致的是修改`build/webpack.base.conf.js`文件
  + 在导出的`module`的`resolve`里添加`'common': resolve('src/common')`
```
resolve: {
    extensions: ['.js', '.vue', '.json'],
    alias: {
      '@': resolve('src'),
      'common': resolve('src/common')
    }
  },
```
#### 第2次提交:显示logo和标题
+ 下载依赖
  + `babel-polyfill@6.2.0`和`fastclick@1.0.6`
+ 载入`main.js`中载入依赖
  + `babel-polyfill`转换ES6语法
  + `fastclick`依赖包的目的是，将触屏时间延迟为300ms
```javascript
import 'babel-polyfill'

import fastclick from 'fastclick'

fastclick.attach(document.body)
```
+ 主页面`index.html`的移动端适应
```html
    <meta name="viewport" content="width=device-width,initial-scale=1.0,maximum-scale=1.0,minimum-scale=1.0,user-scalable=no">
```
+ 修改`build/webpack.base.conf.js`文件，添加`'components': resolve('src/components')`
+ 创建`m-header`组件，显示logo和标题
+ 注意：
  + 需要在`m-header`组件内加入`m-header`类名，以显示样式
  + `m-header`组件不直接使用`header`命名，是因为自定义的组件名不能与HTML自身的标签名相同，不然会报错

#### 第3次提交:页面路由及整体框架
+ 创建四个组件`rank`，`recommend`，`search`，`singer`
+ 创建盛放这个四个组件的容器`tab`，并配置显示路由
+ 在`router/index.js`中配置路由

#### 第4次提交:封装`jsonp`方法
+ 下载安装`jsonp@0.2.1`
+ 封装两个方法，一个是跨域`jsonp`请求，一个是解析参数

#### 第5次提交:利用`jsonp`获取数据
+ 封装一个获取推荐的`getRecommend`的方法
+ 将一些固定的获取`jsonp`数据的信息放在专门的`config.js`文件中
+ 在`recommend.vue`中调用`getRecommend`这个方法
+ 调用的时候，记得修改`build/webpack.base.conf.js`文件，添加`'api': resolve('src/api')`

#### 第6次提交:制作`slider`轮播图
+ 创建`dom.js`库函数，检测dom元素是否含有某一个类名`slider-item`
+ 修改`build/webpack.base.conf.js`文件，添加`'base': resolve('src/base')`
+ 在`recommend`组件内部引入`slider`组件
+ 将利用`jsonp`获取到的数据，循环遍历到`slider`组件内部
+ 在`slider`组件自身中，利用`better-scroll`依赖包使得`slider`达到轮播图的效果，具体参考`slider`组件的代码，略复杂



