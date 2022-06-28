#kiwi-auto-router

# 一、简介
vue自动路由生成
### kiwi-auto-router 基于VueRouter自动化路由

# 二、使用方法
### 安装

```sh
npm i kiwi-auto-router
```

### webpack 使用 （vue-cli4为例）
```html
const autoRouter = require('kiwi-auto-router/lib/router-webpack-plugin')
configureWebpack(config) {
config.plugins = [
...config.plugins,
// eslint-disable-next-line new-cap
new autoRouter({
pages: 'src/views/autoRouter',
importPrefix: '@/views/autoRouter',
routePath: 'src/router/routes.js'
})
]
}
```

| 属性            | 描述                                                                                           | 类型   | 是否必选 | 默认值         |
| --------------- | ---------------------------------------------------------------------------------------------- | ------ | -------- | -------------- |
| pages           | 需要自动生成文件的目录                                                                         | String | 否       |                | 'src/views' |
| importPrefix    | import 引入页面文件的前缀目录                                                                  | String | 否       | '@/views'      |
| layout          | 处理成布局文件的文件名                                                                   | String | 否       | '\_layout.vue' |
| routePath       | 路由生成的文件目录，如果设置了则会在当前项目指定目录生成路由文件，否则可以从`kiwi-auto-route`导入 kiwi-auto-router/lib/routes | String | 否       | 无             |


其中`meta`为`vue-router`配置的`meta`属性一致
写在每个组件的export default {}中
```
meta: {
    title: '系统管理',
    icon: 'form',
    permissionArray: [1, 2, 3],
    sortIndex: 1,
    newTime: '2022-05-20'
  }
```


```

#### 路由文件配置

```js
// 路由初始化
import routes from './routes'

const createRouter = () => new Router({
  mode: 'history', // require service support
  base: process.env.BASE_URL,
  scrollBehavior: () => ({ y: 0 }),
  routes
})

```

# 三、版本信息
1.0.0 init porject