<div align="center">

[![English](https://img.shields.io/badge/English-gray?style=for-the-badge)](README.md) [![简体中文](https://img.shields.io/badge/简体中文-blue?style=for-the-badge)](README_CN.md)

</div>

# PixVision | 像素视觉

> 基于 Vue 3 + Spring Boot 3 + FastAPI 构建的全栈数字艺术创作与分享平台，集成 AI 内容审核、实时消息、多模块架构。

[![Java](https://img.shields.io/badge/Java-17-orange?style=flat-square&logo=openjdk)]()
[![Spring Boot](https://img.shields.io/badge/Spring_Boot-3.3-green?style=flat-square&logo=springboot)]()
[![Vue](https://img.shields.io/badge/Vue-3.5-brightgreen?style=flat-square&logo=vuedotjs)]()
[![Vite](https://img.shields.io/badge/Vite-7-purple?style=flat-square&logo=vite)]()
[![FastAPI](https://img.shields.io/badge/FastAPI-0.136-blue?style=flat-square&logo=fastapi)]()
[![Python](https://img.shields.io/badge/Python-3.14-blue?style=flat-square&logo=python)]()
[![MySQL](https://img.shields.io/badge/MySQL-8-blue?style=flat-square&logo=mysql)]()
[![Redis](https://img.shields.io/badge/Redis-7-red?style=flat-square&logo=redis)]()


---

## 技术栈

| 层级 | 技术 | 版本 | 说明 |
|------|------|------|------|
| 前端框架 | Vue 3 (Composition API) | 3.5 | 核心 UI 框架，使用 `<script setup>` |
| 构建工具 | Vite | 7.3 | 开发服务器与生产构建 |
| 状态管理 | Pinia | 3.0 | 集中式状态存储 |
| 路由 | Vue Router | 5.0 | SPA 路由管理 |
| 动画引擎 | GSAP | 3.14 | ScrollTrigger、stagger 动画 |
| 轮播组件 | Swiper | 12.1 | 触摸滑动组件 |
| CSS 预处理器 | Sass | 1.98 | SCSS 样式 |
| 后端框架 | Spring Boot | 3.3 | RESTful API 服务 |
| 安全认证 | Spring Security + JWT | — | 无状态令牌认证 |
| ORM | Spring Data JPA / Hibernate | — | 数据库访问层 |
| 辅助服务 | FastAPI | 0.136+ | AI 审核与账号检测 |
| AI 集成 | OpenAI SDK | 1.3+ | 大模型内容审核 |
| 数据库 | MySQL | 8.0+ | 主数据存储 |
| 缓存 | Redis | 7+ | 会话缓存与限流 |
| HTTP 客户端 | httpx | 0.28+ | Python 异步 HTTP |

---

## 快速开始

### 环境要求

- **Git**（支持子模块）
- **JDK 17+** + **MySQL 8.0+** + **Node.js 20+** + **Python 3.14+** + **Redis 7+**

### 克隆项目

```bash
# 克隆项目（含子模块）
git clone --recurse-submodules https://github.com/Abyss-PlayerEG/PixVision.git

# 或者已克隆后初始化子模块
git submodule update --init --recursive
```

### 配置说明

所有配置文件存放在 `~/.pix_vision/`（Linux/Mac）或 `%USERPROFILE%\.pix_vision\`（Windows）。

```
~/.pix_vision/
├── application.yml          # Spring Boot 主配置
├── python-server-conf.json  # FastAPI AI 服务配置
├── config/                  # 其他配置
├── data/                    # 数据存储
├── key/                     # 密钥文件
└── log/                     # 日志目录
```

#### Spring Boot 后端配置（`application.yml`）

```yaml
server:
  port: 1899

cors:
  allowed-origin: "*"  # 开发环境用 *，生产环境填具体域名

spring:
  datasource:
    url: jdbc:mysql://<主机地址>:3306/db_pix_vision?allowPublicKeyRetrieval=true&useSSL=false
    username: <数据库用户>
    password: <数据库密码>
  data:
    redis:
      host: localhost
      port: 6379
      timeout: 5000
      database: 0
  mail:
    host: smtp-relay.brevo.com
    port: 587
    from: bot@bot.playereg.top
    username: <SMTP用户名>
    password: <SMTP授权码>

mu-ying-secure:
  jwt-secret: <使用openssl生成>
  salt: <自定义盐值>
```

#### FastAPI AI 服务配置（`python-server-conf.json`）

```json
{
  "ai": {
    "api_key": "sk-xxx",
    "model": "deepseek-v4-flash",
    "base_url": "https://api.deepseek.com",
    "timeout": 3
  },
  "bilibili": {
    "SESSDATA": "可选"
  }
}
```

| 字段 | 说明 |
|------|------|
| `ai.api_key` | DeepSeek/OpenAI API Key |
| `ai.model` | 模型名称 |
| `ai.base_url` | API 地址 |
| `bilibili.SESSDATA` | B站登录凭证（可选） |

#### 前端配置

子模块初始化后查看 `PixVisionPage/config/` 目录。

### 开发模式

```bash
# 终端 1：启动后端（Spring Boot）
cd PixVisionServer && mvn spring-boot:run

# 终端 2：启动前端（Vite 开发服务器）
cd PixVisionPage && pnpm install && pnpm dev

# 终端 3：启动 AI 服务（FastAPI）
cd PixVisionPyServer && uv run python -m app.main
```

---

## 界面预览

| 首页 | 创作工具 | 画廊 |
|:----:|:--------:|:--------:|
| ![首页](screenshots/home.png) | ![创作工具](screenshots/creation-tools.png) | ![画廊](screenshots/gallery.png) |

| 用户主页 | 更多内容 | 聊天私信 |
|:--------:|:--------:|:----------:|
| ![用户主页](screenshots/user-profile.png) | ![更多内容](screenshots/more-content.png) | ![聊天私信](screenshots/chat-messages.png) |

| 管理员端 | 创作中心 | 认证页 |
|:--------:|:--------:|:--------:|
| ![管理员端](screenshots/admin-panel.png) | ![创作中心](screenshots/creation-center.png) | ![认证](screenshots/authentication.png) |

---

## 作者

- **PlayerEG** — gaster@vip.playereg.top
- 贡献者：blue_sky_ks、suliusu

## 许可证

本项目基于 [MIT 许可证](LICENSE) 开源。

(c) 2025 PixVision. All Rights Reserved.
