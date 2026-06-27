<div align="center">

[![English](https://img.shields.io/badge/English-blue?style=for-the-badge)](README.md) [![简体中文](https://img.shields.io/badge/简体中文-gray?style=for-the-badge)](README_CN.md)

</div>

# PixVision | 像素视觉

> A full-stack digital art creation and sharing platform built with Vue 3, Spring Boot 3, and FastAPI, featuring AI-powered content moderation, real-time messaging, and multi-module architecture.

[![Java](https://img.shields.io/badge/Java-17-orange?style=flat-square&logo=openjdk)]()
[![Spring Boot](https://img.shields.io/badge/Spring_Boot-3.3-green?style=flat-square&logo=springboot)]()
[![Vue](https://img.shields.io/badge/Vue-3.5-brightgreen?style=flat-square&logo=vuedotjs)]()
[![Vite](https://img.shields.io/badge/Vite-7-purple?style=flat-square&logo=vite)]()
[![FastAPI](https://img.shields.io/badge/FastAPI-0.136-blue?style=flat-square&logo=fastapi)]()
[![Python](https://img.shields.io/badge/Python-3.14-blue?style=flat-square&logo=python)]()
[![MySQL](https://img.shields.io/badge/MySQL-8-blue?style=flat-square&logo=mysql)]()
[![Redis](https://img.shields.io/badge/Redis-7-red?style=flat-square&logo=redis)]()


---

## Tech Stack

| Layer | Technology | Version | Description |
|-------|------------|---------|-------------|
| Frontend Framework | Vue 3 (Composition API) | 3.5 | Core UI framework with `<script setup>` |
| Build Tool | Vite | 7.3 | Dev server & production bundler |
| State Management | Pinia | 3.0 | Centralized state store |
| Routing | Vue Router | 5.0 | SPA route management |
| Animation Engine | GSAP | 3.14 | ScrollTrigger, stagger animations |
| Carousel | Swiper | 12.1 | Touch slider component |
| CSS Preprocessor | Sass | 1.98 | SCSS styling |
| Backend Framework | Spring Boot | 3.3 | RESTful API server |
| Security | Spring Security + JWT | — | Stateless token authentication |
| ORM | Spring Data JPA / Hibernate | — | Database access layer |
| Auxiliary Service | FastAPI | 0.136+ | AI moderation & account detection |
| AI Integration | OpenAI SDK | 1.3+ | LLM-powered content audit |
| Database | MySQL | 8.0+ | Primary data storage |
| Cache | Redis | 7+ | Session cache & rate limiting |
| HTTP Client | httpx | 0.28+ | Async HTTP for Python service |

---

## Quick Start

### Prerequisites

- **Git** (with submodule support)
- **JDK 17+** + **MySQL 8.0+** + **Node.js 20+** + **Python 3.14+** + **Redis 7+**

### Clone Project

```bash
# Clone with submodules
git clone --recurse-submodules https://github.com/Abyss-PlayerEG/PixVision.git

# Or initialize submodules after cloning
git submodule update --init --recursive
```

### Configuration

All configurations are stored in `~/.pix_vision/` (Linux/Mac) or `%USERPROFILE%\.pix_vision\` (Windows).

```
~/.pix_vision/
├── application.yml          # Spring Boot config
├── python-server-conf.json  # FastAPI AI service config
├── config/                  # Other configs
├── data/                    # Data storage
├── key/                     # Key files
└── log/                     # Log files
```

#### Spring Boot Backend (`application.yml`)

```yaml
server:
  port: 1899

cors:
  allowed-origin: "*"  # Use * for dev, specific domain for production

spring:
  datasource:
    url: jdbc:mysql://<host>:3306/db_pix_vision?allowPublicKeyRetrieval=true&useSSL=false
    username: <username>
    password: <password>
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
    username: <smtp-username>
    password: <smtp-password>

mu-ying-secure:
  jwt-secret: <generate-with-openssl>
  salt: <custom-salt>
```

#### FastAPI AI Service (`python-server-conf.json`)

```json
{
  "ai": {
    "api_key": "sk-xxx",
    "model": "deepseek-v4-flash",
    "base_url": "https://api.deepseek.com",
    "timeout": 3
  },
  "bilibili": {
    "SESSDATA": "optional"
  }
}
```

| Field | Description |
|-------|-------------|
| `ai.api_key` | DeepSeek/OpenAI API Key |
| `ai.model` | Model name |
| `ai.base_url` | API endpoint URL |
| `bilibili.SESSDATA` | Bilibili login token (optional) |

#### Frontend Config

See `PixVisionPage/config/` directory after submodule init.

### Development Mode

```bash
# Terminal 1: Start Backend (Spring Boot)
cd PixVisionServer && mvn spring-boot:run

# Terminal 2: Start Frontend (Vite dev server)
cd PixVisionPage && pnpm install && pnpm dev

# Terminal 3: Start AI Service (FastAPI)
cd PixVisionPyServer && uv run python -m app.main
```

---

## Screenshots

| Home | Creation Tools | Gallery |
|:----:|:--------:|:--------:|
| ![Home](screenshots/home.png) | ![Creation Tools](screenshots/creation-tools.png) | ![Gallery](screenshots/gallery.png) |

| User Profile | More Content | Chat |
|:--------:|:--------:|:----------:|
| ![User Profile](screenshots/user-profile.png) | ![More Content](screenshots/more-content.png) | ![Chat](screenshots/chat-messages.png) |

| Admin Panel | Creation Center | Authentication |
|:--------:|:--------:|:--------:|
| ![Admin Panel](screenshots/admin-panel.png) | ![Creation Center](screenshots/creation-center.png) | ![Auth](screenshots/authentication.png) |

---

## Author

- **PlayerEG** — gaster@vip.playereg.top
- Contributors: blue_sky_ks, suliusu

## License

This project is open-sourced under the [MIT License](LICENSE).

(c) 2025 PixVision. All Rights Reserved.
