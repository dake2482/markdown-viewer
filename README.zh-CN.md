# Markdown 浏览器

<p align="center">
  <img src="assets/logo.png" width="112" height="112" alt="Markdown 浏览器图标">
</p>

<p align="center">
  <a href="README.md">English</a> | <b>简体中文</b>
</p>

一个零依赖、单文件的 Markdown 本地预览器。将 Markdown 文件拖进浏览器，即可在本机完成渲染与阅读。

![Markdown 浏览器 Logo](./assets/logo.png)

## 功能

- 拖拽或选择单个 `.md`、`.markdown`、`.mdown` 或文本文件
- 选择包含 Markdown 与图片资源的文件夹
- 渲染标题、段落、粗体、斜体、删除线、行内代码、代码块
- 渲染链接、图片、引用、有序/无序列表和表格
- 自动解析所选文件夹中的相对图片路径
- 响应式布局，适配桌面端和移动端

## 隐私

Markdown 文件通过浏览器 File API 在本地读取，应用本身没有上传接口。请注意：如果文档引用了远程图片或链接，浏览器仍可能访问对应的外部地址。

## 使用方法

### 直接打开

下载 [`markdown-viewer.html`](./markdown-viewer.html)，用现代浏览器打开，然后拖入 Markdown 文件。

### 本地 HTTP 预览

```bash
python3 -m http.server 8000
```

浏览器访问：

```text
http://127.0.0.1:8000/markdown-viewer.html
```

## 项目结构

```text
.
├── assets/
│   └── logo.png          # 512 × 512 品牌图标
├── apple-icon.png        # iOS 主屏幕图标
├── favicon.ico           # 浏览器标签页与书签图标
├── icon.png              # 192 × 192 高分辨率图标
├── markdown-viewer.html  # 完整应用，样式与脚本均内嵌
├── README.md             # 英文说明
└── README.zh-CN.md       # 中文使用与维护说明
```

## Logo

图标沿用页面的米白、墨绿和深蓝配色，以文件页、折角和双下箭头组成。大尺寸源图保存在 `assets/logo.png`，仓库同时提供 `favicon.ico`、`icon.png` 和 `apple-icon.png`。生产 HTML 将 32 × 32 PNG 直接内嵌为 favicon，避免依赖宿主站点的认证和静态资源路由。

## 部署

整个应用就是一个静态 HTML 文件，任何静态服务器都能托管：

```bash
# 示例：放到任意静态目录后
python3 -m http.server 8000
```

迁移或自托管时，同时部署 `markdown-viewer.html` 和标准图标文件（`favicon.ico`、`icon.png`、`apple-icon.png`）即可；HTML 内已内嵌 favicon，图标文件用于宿主站点需要独立静态资源的场景。

## 验证

检查 HTML 语法与关键功能后，可计算本地文件哈希用于部署前后核对：

```bash
shasum -a 256 markdown-viewer.html
```

## 已知边界

- 使用内置的轻量 Markdown 解析器，不保证覆盖完整 CommonMark/GFM 规范
- 选择文件夹时只打开找到的第一个 Markdown 文件
- 不提供编辑、保存、同步或多人协作功能
- 不执行 Markdown 中的原始 HTML 或脚本

## 维护约定

- 仓库内容是源码真相，服务器文件仅是部署副本
- 不在服务器上直接开发
- 发布前检查敏感信息、HTML 语法和浏览器行为
- 发布后验证公开页面状态与 SHA-256
