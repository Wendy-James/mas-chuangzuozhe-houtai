# Vue 2 管理后台练习（酒店客房管理场景）

这是一个基于 Vue 2 和 Element UI 的后台管理前端项目。项目场景为酒店客房管理，覆盖登录、角色入口、路由菜单、表格列表、表单增删改查、上传组件和基础图表组件。

该仓库适合作为管理后台工程结构练习：重点整理路由组织、请求拦截、模块化页面、CRUD 交互和后端接口协作方式。

## 技术栈

- Vue 2
- Vue Router
- Element UI
- Axios
- ECharts
- Vue CLI

## 架构与数据流

```text
Vue pages / components
  -> Vue Router routes
  -> Axios http client
  -> /nodejs63qva API base path
  -> backend service (not included in this repository)
```

### Authentication Flow

- 登录页根据角色选择对应业务表。
- 登录成功后将 `Token`、`role`、`sessionTable`、`adminName` 写入本地存储。
- Axios 请求拦截器会把 `Token` 放入请求头。
- 如果后端返回 `code = 401`，前端跳转回登录页。

## API Contract

模块接口遵循统一的 REST-like 命名方式。后端不在本仓库内，需要另行提供。

| Operation | Path Pattern |
|---|---|
| 分页列表 | `/{module}/page` |
| 详情 | `/{module}/info/{id}` |
| 新增 | `/{module}/save` |
| 更新 | `/{module}/update` |
| 删除 | `/{module}/delete` |
| 登录 | `/{module}/login?username={username}&password={password}` |
| 当前会话 | `/{module}/session` |

## Modules

- 用户
- 客房信息
- 订房信息
- 续房信息
- 换房信息
- 退房信息
- 费用信息
- 配置

## 目录说明

- `src/views/`：页面视图，包含登录、首页、用户中心和业务模块页面。
- `src/views/modules/`：后台管理模块，例如用户、客房、订房、费用等页面。
- `src/components/`：布局和通用组件。
- `src/router/`：静态路由配置。
- `src/store/`：Vuex 状态管理。
- `src/utils/`：请求、存储、校验和工具方法。
- `src/assets/`：图片、样式和背景资源。

## 常用命令

安装依赖：

```bash
npm install
```

本地启动：

```bash
npm run serve
```

生产构建：

```bash
npm run build
```

代码检查：

```bash
npm run lint
```

## 后端依赖

本仓库只包含前端代码。运行完整业务流程需要准备兼容上述接口约定的后端服务。

当前前端默认 API base path 为：

```text
/nodejs63qva
```

本地开发时，需要根据 `vue.config.js` 的代理配置连接后端。

## 测试现状

- 当前仓库没有单元测试或 E2E 测试。
- 可通过 `npm run lint` 做基础代码检查。
- 后续可以补充接口 mock、组件测试和关键流程 E2E 测试。

## 已知限制

- 后端服务不在本仓库内，无法单独完成真实登录和 CRUD 请求。
- Vue 2、Element UI、node-sass 等依赖版本偏旧。
- 部分资源和页面结构适合作为课程设计/练习项目，不应视为生产级后台模板。
- 如接入真实地图、上传或第三方服务，应将密钥迁移到环境变量并限制使用范围。

## 下一步

- 补充 mock API，支持无后端预览核心页面。
- 为登录、请求拦截、列表查询和表单提交增加测试。
- 增加页面截图和模块说明。
- 整理路由与菜单配置，减少重复代码。
- 补充部署说明和环境变量说明。
