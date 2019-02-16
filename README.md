# fullstack

## Bugs

### 'Uncaught Error: [HMR] Hot Module Replacement is disabled.'

- 在 webpack-dev-server 后面添加 '--hot --inline'

### webpack-dev-server 默认是刷新网页，而非热更新，如何实现热更新

- 在 config.devServer 配置中添加一项：'hotOnly: true'，热更新被 dev-server 的自动刷新给盖过了

### 空格 + \ 可以在命令行里换行

### git init 命令 就可以把项目变成一个 git 的仓库

### husky: 可以在 commit 前做一个钩子，先执行预制的命令

### github 绿格子不显示解决办法： git config user.email 查看邮箱是不是 github 上默认的邮箱

- 修改命令：git config --global user.email "chengrui.xjw@gmail.com"

### 将远程 git 仓库里的指定分支拉取到本地（本地不存在的分支）

- 修改命令：`git checkout -b 本地分支名 origin/远程分支名`
- 如拉取不成功，首先执行 git fetch 命令
- 删除远程分支：`git push origin -d 远程分支名`
- 删除本地分支： `git branch -d 本地分支` （在 master 中）
- 合并某分支到当前分支：`git merge 被合并的分支名`
- 分支改名： `git branch -m (非当前：原分支名) 新分支名`

### You should not use <Link> outside a <Router> `server-entry.js`

- 原因：由于 App.js export 的是一个数组，所以 Link 标签被暴露，需要用一个 Router 标签包裹
- 解决：`import StaticRouter` 去包裹 `<App />`

### Javascript 语法规范错误提示代码

https://www.jianshu.com/p/b02f6b15cd09

### axios.post 上传字段 得到 status === 200 ,但返回的数据 success: false

- 未解决

### mobx warning: there are multiple mobx instances active...

- 有多个 mobx 实例被启动了
- `externals: Object.keys(require('../package.json').dependencies)`

### 使用了 externals 配置项后，出现 Cannot find module 'react'

-

### react-helmet

- 用于 每个页面 title 的设置

---

## 项目基本目录结构

### views

- views 目录用于存放项目功能模块的页面，需要根据路由配置情况分割子级目录

### config

- config 目录存放一些配置目录，比如第三方类库引用，路由配置等

### store

- store 目录用于存放项目 store 相关的文件，包括数据获取的封装等

### components

- components 目录用于存放非业务组件，或者在多个业务间都需要用到的公用组件

---

## 路由

### 什么是路由

路由是用来区分一个网站不用功能模块的地址，浏览器通过访问同一站点下的不同路由，来访问网站不同的功能。同样路由也让开发者区分返回的内容

### 如何做前端路由

HTML5 API 中的 history 能够让我们控制 url 跳转之后并不刷新页面，而是交给我们的 JS 代码进行相应操作。在 history api 出现之前，我们可以使用 hash 跳转来实现

---

## store

伴随着 React 一起诞生的，是 facebook 推出的一套前端数据流方案，叫做 flux，在其中数据存储的地方，叫做 store，flux 又叫做单项数据流

### Mobx

Mobx 是 flux 实现的后起之秀，其以更简单的使用和更少的概念，让 flux 使用起来变得更加简单。相比 Redux 有 mutation、action、dispatch 等概念，Mobx 则更符合对一个 store 增删改查的操作概念

### cnodejs.org/api

## 服务端渲染优化

### 路由跳转

使用者可能从任意路由进入我们的网站，所以在服务端中也必须处理路由的跳转，在返回给客户端的时候就是指定页面

### store 数据同步

每个页面会有对应的数据，在服务端渲染时已经请求过对应数据，所以要让客户端知道这些数据，在客户端渲染的时候直接使用，而不是通过 API 再次请求，造成浪费。
