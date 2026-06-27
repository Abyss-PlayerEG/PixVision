# PixVision

**像素视觉** — 数字艺术创作与分享平台

[![Vue](https://img.shields.io/badge/Vue-3.5-brightgreen)](https://vuejs.org/)
[![Spring Boot](https://img.shields.io/badge/Spring_Boot-3.3.0-brightgreen)](https://spring.io/projects/spring-boot)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.136+-blue)](https://fastapi.tiangolo.com/)
[![License](https://img.shields.io/badge/License-MIT-yellow)](LICENSE)

---

## 界面预览

| 首页 | 创作工具 | 首页画廊 |
|:----:|:--------:|:--------:|
| ![首页](screenshots/1.png) | ![创作工具](screenshots/3.png) | ![画廊](screenshots/2.png) |

| 用户主页 | 更多内容 | 聊天私信 |
|:--------:|:--------:|:----------:|
| ![用户主页](screenshots/4.png) | ![更多内容](screenshots/5.png) | ![聊天私信](screenshots/8.png) |

| 管理员端 | 创作中心 |
|:--------:|:--------:|
| ![管理员端](screenshots/7.png) | ![创作中心](screenshots/6.png) |

---

## 项目结构

本项目采用 Git Submodules 组织，包含以下子模块：

| 模块 | 说明 | 技术栈 |
|------|------|--------|
| [PixVisionServer](PixVisionServer) | 后端服务 | Java 17 / Spring Boot 3.3 |
| [PixVisionPyServer](PixVisionPyServer) | 辅助服务 | Python 3.14 / FastAPI |
| [PixVisionPage](PixVisionPage) | 前端应用 | Vue 3 / Vite 7 / GSAP |

## 快速开始

```bash
# 克隆项目（含子模块）
git clone --recurse-submodules https://github.com/Abyss-PlayerEG/PixVision.git

# 或者已克隆后初始化子模块
git submodule update --init --recursive
```

## 作者

- PlayerEG — gaster@vip.playereg.top
- 贡献者：blue_sky_ks

## 许可证

本项目基于 MIT 许可证开源。
