# Cloudflare Pages 部署指南

## 当前文件结构

```
D:\我的文件\网页\你被骗了\
├── index.html   ← 入口页面（自动播放视频）
└── video.mp4   ← 视频文件（约50MB）
```

## 部署步骤

### 方法一：通过 Cloudflare Dashboard 上传

1. 访问 https://pages.cloudflare.com 并登录
2. 点击 **Create a project** → **Upload direct**
3. 上传 `index.html` 和 `video.mp4` 两个文件
4. 项目名称填 `你被骗了`（或任意名称）
5. 构建命令留空，生产分支选 `production`
6. 点击 **Save and Deploy**

> ⚠️ 免费版 Cloudflare Pages 单文件最大 **100MB**，视频约50MB，完全没问题。

---

### 方法二：通过 Wrangler CLI 部署

```bash
# 1. 安装 Wrangler
npm install -g wrangler

# 2. 登录 Cloudflare
npx wrangler login

# 3. 进入网站目录
cd "D:\我的文件\网页\你被骗了"

# 4. 部署
npx wrangler pages deploy .
```

---

## 关于自动播放

- 页面加载后视频会**自动静音播放**（绕过浏览器自动播放限制）
- 如果浏览器拦截了自动播放，**点击页面任意位置**即可解除限制
- 视频会循环播放

## 关于域名

部署完成后，Cloudflare 会分配一个免费子域名，例如：
`https://xxxxx.pages.dev`

如果你有自定义域名，可以在该项目的 **Custom domains** 设置中添加。
