# Trojan 多用户管理系统 - 项目总结 (Summary.md)

## 1. 项目概述
本项目是一个基于 Go 语言开发的 Trojan 协议多用户管理面板，旨在提供简便的安装、用户管理、流量统计及 Web 控制台功能。

## 2. 核心架构
- **后端 (Backend)**: Go 1.21+, 使用 `gin` 框架提供 RESTful API。
- **前端 (Frontend)**: 基于 Vue 3 + Vite 的单页面应用 (SPA)，源码位于 `Jrohy/trojan-web`。
- **数据持久化**: 支持 MySQL (MariaDB) 或 LevelDB。
- **集成方式**: 前端编译产物 (index.html, static/) 通过 `go:embed` 嵌入到后端的二进制文件中。

## 3. 目录结构
- `main.go`: 程序入口。
- `cmd/`: CLI 命令行逻辑 (cobra 实现)，包含 `start`, `stop`, `web`, `update` 等子命令。
- `web/`: 
    - `web.go`: 路由配置与静态资源嵌入逻辑。
    - `templates/`: **(当前关键点)** 静态资源存放处，目前仅包含占位符，需补全。
    - `controller/`: API 业务逻辑处理。
- `trojan/`: 核心业务逻辑，包括安装、证书申请、服务管理等。
- `asset/`: 存放安装脚本、Dockerfile、Systemd 服务文件等资源。

## 4. 关键流程分析
- **安装过程**: 运行 `install.sh` -> 下载二进制 -> 配置环境 -> 启动服务。
- **Web 访问**: 后端启动 Gin 服务 -> 监听 443 端口 -> 访问时返回嵌入的 `index.html`。
- **自动化构建**: `.github/workflows/` 下配置了 Docker 推送和 GitHub Release 自动发布。

## 5. 当前存在的问题
- **资源部分本地化**: 已将 `acme.sh` 安装脚本、`systemctl` 适配脚本以及 `trojan-web.service` 全部同步并集成到项目 `asset/` 目录中。程序已实现了后端关键依赖的内置资源分发。
- **前端资源现状**: 本仓库不单独维护前端编译后的静态资源（`web/templates` 下保持为空）。Web 控制面板的功能依赖于外部构建或特定的部署流程，当前编译产物以 404 返回为预期行为（若未进行外部集成）。
- **配置一致性**: 确保了 `install.sh`、`build.sh` 和内部 Go 代码中的所有仓库引用均指向 `dujiepeng/trojan`，保证了分发渠道的独立性。

## 6. 后续行动指南
- **补全前端**: 找回并集成 `Jrohy/trojan-web` 的编译产物。
- **地址迁移**: 将所有硬编码的 `Jrohy/trojan` 替换为 `dujiepeng/trojan`。
- **持续集成**: 优化构建脚本，确保每次发布都包含最新的前端包。
