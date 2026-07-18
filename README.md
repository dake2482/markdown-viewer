# Markdown 浏览器

一个零依赖、单文件的 Markdown 本地预览器。将 Markdown 文件拖进浏览器，即可在本机完成渲染与阅读。

线上地址：<http://43.159.50.227/markdown-viewer.html>

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
├── markdown-viewer.html  # 完整应用，样式与脚本均内嵌
└── README.md             # 中文使用与维护说明
```

## 部署

当前生产页面部署在腾讯云服务器 `tengxun`：

```text
/root/ArianaRealm/public/markdown-viewer.html
```

该路径只是现有静态托管位置，本项目不依赖 Ariana Realm 的业务代码。后续维护以本仓库为唯一源码来源：先在仓库修改和验证，再将 `markdown-viewer.html` 部署到静态托管位置，最后检查公开 URL 和文件哈希。

## 验证

检查 HTML 语法与关键功能后，可核对本地文件和线上响应是否一致：

```bash
shasum -a 256 markdown-viewer.html
curl -fsS http://43.159.50.227/markdown-viewer.html | shasum -a 256
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
