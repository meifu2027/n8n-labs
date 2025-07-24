# n8n 一键生成热门视频工作流

本项目是基于 [n8n](https://n8n.io) 实现的一键生成热门视频的自动化工作流，适用于学习和研究自动化视频生成的过程。

## 环境要求

在开始之前，请确保你已经安装了以下依赖：

- [Node.js](https://nodejs.org/)：推荐版本 **v24.4.1**（当前使用版本）
- [Docker](https://www.docker.com/)：推荐版本 **28.2.2, build e6534b4**（当前使用版本）
- 操作系统：**macOS**（本项目开发与测试环境为 MacBook Pro，Intel 芯片）

## 启动 n8n

使用以下命令通过 `npx` 启动 n8n：

```bash
npx n8n
```

## 启动视频生成容器

> 本项目使用第三方镜像 `gyoridavid/short-video-maker` 来生成视频。

### 使用 CPU 镜像（适用于大多数设备）

```bash
docker run -it --rm --name short-video-maker -p 3123:3123 \
  -e LOG_LEVEL=debug \
  -e PEXELS_API_KEY=563492ad6f91700001000001458XXX \
  gyoridavid/short-video-maker:latest-tiny
```

### 使用 NVIDIA GPU 镜像（需要具备 CUDA 支持的显卡）

```bash
docker run -it --rm --name shorts-video-maker -p 3123:3123 \
  -e PEXELS_API_KEY= \
  --gpus=all \
  gyoridavid/short-video-maker:latest-cuda
```

## 关于 API Key

`PEXELS_API_KEY` 是用于从 [Pexels](https://www.pexels.com/api/) 拉取免费素材的 API 密钥，你可以在 Pexels 官网注册账号后免费申请。

## 注意事项

- 本项目仅用于学习目的，请勿用于商业用途或违规使用。
- 视频素材版权归 Pexels 所有，请遵循其使用条款。

---
项目灵感来源于自动化视频内容创作需求，欢迎探索更多 n8n 工作流的可能性。
