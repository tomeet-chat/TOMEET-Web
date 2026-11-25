<div align="center">

# TOMEET Web

**TOMEET 社交 Agent 的双语 Next.js 16 Web 与 PWA 前端客户端。**

[![Live Preview](https://img.shields.io/badge/Live-rendez--web.vercel.app-111827.svg)](https://rendez-web.vercel.app)
[![Next.js](https://img.shields.io/badge/Next.js-16-000000.svg)](package.json)
[![React](https://img.shields.io/badge/React-19%20%7C%20TypeScript-2563EB.svg)](package.json)
[![Backend](https://img.shields.io/badge/Backend-TOMEET__Backend-10B981.svg)](https://github.com/toMeetADX/TOMEET_Backend)

[English](README.md) | **简体中文**

</div>

---

## 项目简介

**TOMEET Web** 是对话式社交 Agent [**TOMEET**](https://github.com/toMeetADX/TOMEET_Backend) 的响应式网页与 PWA 客户端，涵盖品牌落地页、基于 Supabase 的登录注册、Agent 实时对话界面（`AgentChat`）、个人中心（`ProfileHub`）、微信扫码接入（`WechatQrEntry`）以及完整中英双语体验。

## 核心特性

- **Agent 对话界面（`/[locale]/agent`）**：通过服务端代理路由 `/api/tomeet/[...path]` 安全连接后端 API，无需在浏览器暴露内部接口地址。
- **原生中英双语（`next-intl`）**：完整支持英文（`src/messages/en.json`）与中文（`src/messages/zh.json`）路由切换。
- **可安装 PWA 体验**：内置 `manifest.ts`、Service Worker（`public/sw.js`）、离线页（`public/offline.html`）和移动端安装引导（`InstallAppPrompt`）。
- **Supabase SSR 鉴权**：支持登录、注册、回调（`/api/auth/callback`）和会话中间件同步。
- **功能开关控制**：通过环境变量按需启用实验模块（`NEXT_PUBLIC_FOODIES_ENABLED`、`NEXT_PUBLIC_QR_SERVICE_ENABLED`）。
- **动效与视觉打磨**：采用 Next.js 16、Tailwind CSS v4、`@base-ui/react`、`shadcn/ui` 与 Framer Motion 构建。

## 技术栈

| 层级 | 技术选型 |
| --- | --- |
| 框架 | Next.js 16（App Router）、React 19、TypeScript |
| 样式与交互 | Tailwind CSS v4、shadcn/ui、`@base-ui/react`、Framer Motion、Lucide Icons |
| 状态与国际化 | Zustand、`next-intl` |
| 鉴权与后端 | Supabase SSR（`@supabase/ssr`），代理至 [TOMEET_Backend](https://github.com/toMeetADX/TOMEET_Backend) |
| 部署 | Vercel |

## 目录结构

```text
src/
├── app/
│   ├── [locale]/              # 双语页面：落地页、Agent 对话、个人中心、Foodies、登录/注册
│   ├── api/
│   │   ├── auth/              # Supabase 认证回调与登出路由
│   │   └── tomeet/[...path]/  # 服务端 API 代理（转发至 TOMEET_API_BASE_URL）
│   └── manifest.ts            # PWA 清单
├── components/                # AgentChat、Hero、Manifesto、ProfileHub、WechatQrEntry 等组件
├── i18n/                      # next-intl 路由与请求配置
├── lib/                       # Supabase 客户端/服务端封装、API 工具与功能开关
└── messages/                  # en.json 与 zh.json 双语词条
```

## 快速开始

### 1. 安装依赖

```sh
npm install
```

### 2. 配置环境变量

```sh
cp .env.local.example .env.local
```

按需填写 `.env.local`：

```env
NEXT_PUBLIC_SUPABASE_URL=https://your-project.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=your-anon-key

# 后端 API 地址（仅服务端读取，末尾不要加斜杠）
TOMEET_API_BASE_URL=http://localhost:4000

# 可选功能开关
NEXT_PUBLIC_FOODIES_ENABLED=false
NEXT_PUBLIC_QR_SERVICE_ENABLED=false
```

### 3. 启动开发服务

```sh
npm run dev
```

访问 [http://localhost:3000](http://localhost:3000)。提交 PR 前请确认校验通过：

```sh
npm run lint && npm run build
```

## 参与贡献

欢迎提交 UI 优化、移动端 PWA 适配、无障碍改进或双语文案润色！详见 [CONTRIBUTING.md](CONTRIBUTING.md)；涉及后端协议变更请同步参考 [TOMEET_Backend](https://github.com/toMeetADX/TOMEET_Backend)。
