# Changelog

## [v1.2.9] - 2025-12-24
### 修改内容
- 集成 GitHub Actions 自动化发布流程：现在只需推送以 `v` 开头的版本标签，系统将自动完成 amd64 和 arm64 二进制文件的编译，并发布到 GitHub Releases。
- 修复并优化了 Release 构建参数，支持在程序中显示正确的版本号。

修改人: Antigravity
修改时间: 2025-12-24
修改版本: v1.2.9

## [v1.2.8] - 2025-12-24
### 修改内容
- 修复 `util/command.go` 中的 `RunWebShell` 函数，增加网络请求失败时的错误处理，防止程序发生空指针崩溃（Panic）。
- 解决由于缺少 `web/templates` 目录导致 `go build` 编译失败的问题。

修改人: Antigravity
修改时间: 2025-12-24
修改版本: v1.2.8

## [v1.2.7] - 2025-12-24
### 修改内容
- 修复 `trojan/install.go` 中的 Docker 安装源，切换为官方 `get.docker.com`，解决 Ubuntu 等系统下的安装 404 问题。

修改人: Antigravity
修改时间: 2025-12-24
修改版本: v1.2.7

## [v1.2.6] - 2025-12-24
### 修改内容
- 增强 `install.sh` 脚本健壮性：增加对 GitHub API 获取版本号失败的检查。
- 增加下载二进制文件时的错误检测，防止将报错信息误存为可执行文件。

修改人: Antigravity
修改时间: 2025-12-24
修改版本: v1.2.6

## [v1.2.5] - 2025-12-24
### 修改内容
- 在 `README.md` 中增加了明确的卸载操作说明。
- 优化了 README 中的部分代码块描述。

修改人: Antigravity
修改时间: 2025-12-24
修改版本: v1.2.5

## [v1.2.4] - 2025-12-24
### 修改内容
- 全局将仓库地址从 `Jrohy/trojan` 替换为 `dujiepeng/trojan`。
- 全局将分支名称从 `master` 替换为 `main`。
- 修复 `install.sh` 中的硬编码 URL，确保安装和更新指向正确的库。
- 更新 Docker 镜像名称为 `dujiepeng/trojan`。
- 更新 README 中的徽章和链接。

修改人: Antigravity
修改时间: 2025-12-24
修改版本: v1.2.4

## [v1.2.3] - 2025-12-24
### 修改内容
- 更新 `README.md` 中的一键安装脚本指令，指向新的 GitHub 仓库地址 `dujiepeng/trojan`。
- 将安装命令从 `source <(curl -sL ...)` 更改为 `bash <(curl -sL ...)` 格式。

修改人: Antigravity
修改时间: 2025-12-24
修改版本: v1.2.3
