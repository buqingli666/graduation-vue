# 味之轻舟 - 管理端（graduation-vue）

![项目](https://img.shields.io/badge/项目-味之轻舟-E95F3C?style=flat-square) ![角色](https://img.shields.io/badge/角色-管理端前端-42B883?style=flat-square) ![Vue](https://img.shields.io/badge/Vue-2.6-4FC08D?logo=vuedotjs&logoColor=white&style=flat-square) ![TypeScript](https://img.shields.io/badge/TypeScript-3.6-3178C6?logo=typescript&logoColor=white&style=flat-square) ![Element UI](https://img.shields.io/badge/Element_UI-2.x-409EFF?style=flat-square) ![ECharts](https://img.shields.io/badge/ECharts-5.x-AA344D?style=flat-square)

> 🚀 **「味之轻舟」** —— 一个完整的餐饮外卖点餐系统毕业设计项目，由 **后端服务 + 管理端 + 微信小程序** 三端组成。

## 🌐 项目生态（相关仓库）

本仓库是「味之轻舟」系统的**管理端**。完整系统由以下三个仓库组成，点击链接可跳转：

| 模块 | 说明 | 技术栈 | 仓库 |
| :---: | --- | --- | :---: |
| ⚙️ 后端服务 | 系统核心（RESTful API + WebSocket） | Spring Boot / MyBatis / MySQL / Redis / JWT | [`graduation-backend`](https://github.com/buqingli666/graduation-backend) |
| 📊 **管理端** | 商家后台（订单 / 菜品 / 统计） | Vue2 / TypeScript / Element UI / ECharts | [`graduation-vue`](https://github.com/buqingli666/graduation-vue) ⬅️ **当前** |
| 🛒 用户端 | 小程序点餐端 | uni-app / 微信小程序 / uni-ui | [`graduation-weixin`](https://github.com/buqingli666/graduation-weixin) |

---

## 一、项目简介

本仓库是「味之轻舟」系统的管理端，对接后端服务（`graduation-backend`）的 `/admin/**` 接口，并通过 **WebSocket** 接收「来单提醒」「客户催单」实时消息，进行可视化展示与交互。

主要功能页面：

- **登录**：管理员登录（JWT 鉴权）。
- **工作台（Dashboard）**：今日营业概览、订单列表、菜品/套餐统计。
- **数据统计**：营业额统计、用户统计、订单统计、销量 TOP10、数据概览与报表导出。
- **订单管理**：订单列表、订单详情、订单状态流转（接单/拒单/派送/完成等）。
- **套餐管理**：套餐列表、新增/编辑套餐（选择菜品组合）。
- **菜品管理**：菜品列表、新增/编辑菜品（含口味配置）。
- **分类管理**：菜品分类与套餐分类管理。
- **员工管理**：员工列表、新增/编辑员工、账号启停。

## 二、技术栈

| 分类 | 技术选型 |
| --- | --- |
| 框架 | Vue 2.6、TypeScript |
| 构建工具 | Vue CLI 3（`@vue/cli-service`） |
| UI 组件 | Element UI 2.x |
| 图表 | ECharts 5（数据统计可视化） |
| 状态管理 | Vuex + `vuex-module-decorators` + `vuex-persistedstate` |
| 路由 | Vue Router |
| 网络请求 | Axios |
| 样式 | SASS / SCSS、`normalize.css` |
| 工具 | nprogress（进度条）、js-cookie、moment、md5、`vue-svgicon` |
| 测试 | Jest（单元）、Cypress（E2E） |
| 代码规范 | ESLint + Prettier + `@vue/eslint-config-standard` |

> 本项目基于开源模板 [vue-typescript-admin-template](https://github.com/Armour/vue-typescript-admin-template) 二次开发。

## 三、项目结构

```
graduation-vue/
├── public/                 # 静态资源（index.html、favicon 等）
├── src/
│   ├── api/                # 后端接口封装（按模块拆分）
│   │   ├── category.ts
│   │   ├── charts.ts
│   │   ├── dish.ts
│   │   ├── employee.ts
│   │   ├── index.ts        # 工作台 / 统计 / 报表相关接口
│   │   ├── inform.ts       # WebSocket 通知
│   │   ├── order.ts
│   │   ├── setMeal.ts
│   │   └── users.ts
│   ├── assets/             # 图片 / 图标 / 登录页素材
│   ├── components/         # 公共组件（Breadcrumb、Charts、ImgUpload 等）
│   ├── icons/              # SVG 图标及自动生成的组件
│   ├── layout/             # 整体布局（侧边栏、顶栏、混入）
│   ├── store/              # Vuex 模块（modules）
│   ├── styles/             # 全局样式、变量、字体
│   ├── utils/              # 工具方法（request 封装、cookies、权限等）
│   ├── views/              # 页面
│   │   ├── login/          # 登录
│   │   ├── dashboard/      # 工作台（营业概览、订单列表、菜品/套餐统计）
│   │   ├── statistics/     # 数据统计（营业额/用户/订单/TOP10/概览）
│   │   ├── orderDetails/   # 订单管理
│   │   ├── setmeal/        # 套餐管理
│   │   ├── dish/           # 菜品管理
│   │   ├── category/       # 分类管理
│   │   ├── employee/       # 员工管理
│   │   └── inform/         # 来单 / 催单提醒
│   ├── App.vue
│   ├── main.ts             # 入口
│   ├── router.ts           # 路由配置
│   ├── permission.ts       # 路由守卫 / 权限控制
│   └── config.json
├── tests/                  # 单元测试
├── .env.development        # 开发环境变量（接口地址、WebSocket 地址）
├── .env.production         # 生产环境变量
├── vue.config.js           # 构建与 devServer 代理配置
├── Dockerfile              # 容器化构建
└── package.json
```

## 四、环境配置说明

关键环境变量位于 `.env.development`：

| 变量 | 说明 |
| --- | --- |
| `VUE_APP_BASE_API` | 请求基础路径（默认 `/api`，配合 devServer 代理） |
| `VUE_APP_URL` | 后端管理端地址（默认 `http://localhost:8080/admin`） |
| `VUE_APP_SOCKET_URL` | WebSocket 地址（默认 `ws://localhost:8080/ws/`） |
| `VUE_APP_DELETE_PERMISSIONS` | 是否删除权限（`true` 跳过权限校验） |

`vue.config.js` 中 `devServer` 监听 **8888** 端口，并将 `/api` 代理转发到 `VUE_APP_URL`（去除 `/api` 前缀）。

## 五、快速开始

### 环境要求

> ⚠️ **重要**：本项目对 Node 版本敏感，请使用 **Node.js v12.22.12** 运行，否则会出现依赖安装 / 编译报错等问题（详见 `instruction.txt`）。

建议使用 [nvm](https://github.com/nvm-sh/nvm) 切换版本：

```bash
nvm install 12.22.12
nvm use 12.22.12
```

### 安装依赖

```bash
npm install
# 或
yarn install
```

### 启动开发服务

```bash
npm run serve
```

启动后默认访问：`http://localhost:8888`。

> 启动前请确保后端服务（`graduation-backend`，端口 8080）已正常运行，否则接口请求与 WebSocket 连接会失败。

### 构建生产包

```bash
npm run build          # 生产环境
npm run build:uat      # UAT 环境
```

### 代码检查与测试

```bash
npm run lint           # ESLint 检查
npm run test:unit      # Jest 单元测试
npm run test:e2e       # Cypress 端到端测试
```

## 六、默认登录账号

管理端登录账号由后端数据库决定，默认：

- 账号：`admin`
- 密码：`123456`

（对应后端接口 `POST /admin/employee/login`）

## 七、相关仓库

本项目为「味之轻舟」系统的管理端，配套仓库：

- 后端服务：[graduation-backend](https://github.com/buqingli666/graduation-backend)
- 用户端（微信小程序）：[graduation-weixin](https://github.com/buqingli666/graduation-weixin)
