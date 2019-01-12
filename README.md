# fullstack

## Bugs

- 'Uncaught Error: [HMR] Hot Module Replacement is disabled.'
  在 webpack-dev-server 后面添加 '--hot --inline'

- webpack-dev-server 默认是刷新网页，而非热更新，如何实现热更新
  在 config.devServer 配置中添加一项：'hotOnly: true'，热更新被 dev-server 的自动刷新给盖过了

- 空格 + \ 可以在命令行里换行

- git init 命令 就可以把项目变成一个 git 的仓库

- husky: 可以在 commit 前做一个钩子，先执行预制的命令
