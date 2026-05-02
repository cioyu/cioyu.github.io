# cioyu.github.io — Cioyu 的个人博客

基于 **Vue 3 + Vite 7 + vue-router 5** 构建的个人博客站点，部署在 [blog.cioyu.top](https://blog.cioyu.top)。

## 技术栈

| 类别 | 技术 |
|------|------|
| 框架 | Vue 3 |
| 路由 | vue-router 5 |
| 构建 | Vite 7 |
| 部署 | GitHub Actions → GitHub Pages |

## 命令

```sh
# 安装依赖
yarn

# 启动开发服务器（热重载）
yarn dev

# 生产构建
yarn build

# 本地预览生产构建
yarn preview
```

## 项目结构

```
src/
├── main.js          # 应用入口
├── App.vue          # 首页（博主介绍、Linux 折腾历程、学习方向、联系方式）
└── router/
    └── index.js     # 路由配置
```

## 部署

推送 `main` 分支后，GitHub Actions 自动构建并部署到 GitHub Pages。
