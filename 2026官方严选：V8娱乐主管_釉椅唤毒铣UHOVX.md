V8娱乐主管【Q-——333307——】V8娱乐主管【 辋芷《888yx●vip》 】
V8娱乐主管【Q-——333307——】V8娱乐主管【 辋芷《888yx●vip》 】

 如何用 GitHub Actions 自动部署个人博客？一篇搞定 CI/CD 实战

> 手把手教你通过 GitHub Actions 实现 Push 即部署，告别手动上传服务器。

你是不是还在手动 `npm run build`，然后又把 `dist` 文件夹拖进服务器？2025年了，这种做法真的过时了。作为开发者，不掌握 GitHub Actions 自动化流水线，相当于守着宝库还在用铁锹挖煤。

本文将带你从零搭建一个 Hugo/Hexo/VuePress 通用的自动部署工作流，全程只需复制粘贴，并且完全免费。

---

 第一步：理解核心逻辑

GitHub Actions 是 GitHub 推出的 CI/CD 服务。它的工作原理很简单：当你的仓库发生特定事件（比如 `push` 到 `main` 分支），它会自动触发一个虚拟机的运行环境，执行你预先定义好的工作流脚本。

对于个人博客而言，这个逻辑就是：
1. `push` 源码到仓库。
2. Actions 虚拟机拉取最新代码。
3. 安装依赖并构建静态文件。
4. 通过 SSH 将文件推送到你的云服务器或使用 GitHub Pages 托管。

---

 第二步：直接可用的配置文件

在你的项目根目录下创建一个 `.github/workflows/deploy.yml` 文件，内容如下：

```yaml
name: Deploy Blog

on:
  push:
    branches: [ main ]

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: '20'
      - name: 安装依赖
        run: npm install
      - name: 构建项目
        run: npm run build
      - name: 部署到服务器
        uses: easingthemes/ssh-deploy@v5.0.3
        with:
          SSH_PRIVATE_KEY: ${{ secrets.SSH_PRIVATE_KEY }}
          ARGS: "-rlgoDzvc -i --delete"
          SOURCE: "public/"
          REMOTE_HOST: ${{ secrets.REMOTE_HOST }}
          REMOTE_USER: ${{ secrets.REMOTE_USER }}
          TARGET: "/var/www/blog"
```

注意：如果你用的是 Hexo，`SOURCE` 需要改成 `public/`；如果是 VuePress，则改为 `docs/.vitepress/dist/`。

---

 第三步：配置 Secrets 密钥

这是最容易踩坑的地方。你需要打开仓库的 `Settings` -> `Secrets and variables` -> `Actions`，添加三个密钥：

- SSH_PRIVATE_KEY：你的服务器私钥（即 `id_rsa` 文件内容）。
- REMOTE_HOST：服务器 IP 地址。
- REMOTE_USER：服务器登录用户名（建议 `root` 或创建的专用用户）。

---

 第四步：提交并验证

将 YAML 文件推送到远程仓库后，点击仓库顶部的 Actions 标签页，你会看到工作流已经开始运行。若绿色对勾出现，说明部署成功。

互动引导：如果你在这个流程中遇到 `Permission denied` 或 `构建失败`，欢迎在评论区留下你的报错截图。我整理了关于 Nginx 静态缓存策略 以及 如何给服务器配置免费的 SSL 证书 的后续教程——如果你需要，点赞本篇文章，超过 50 我将立刻发布深度避坑指南。

相关推荐：

https://github.com/millerdonna9312/pwnxnv/blob/main/2026%E5%AE%98%E7%BD%91%E4%B8%93%E8%AE%BF%EF%BC%9AV8%E5%A8%B1%E4%B9%90app_%E6%B8%A4%E6%95%B2%E5%B9%B8%E5%90%88%E7%A3%90PCCQR.md

<img src="https://i.postimg.cc/J7sVTRgT/V8-00010.png" />

相关推荐：

https://github.com/millerdonna9312/pwnxnv/commit/21d9311f6eb33fb25083b492954edfa8ce57ee5f

<img src="https://i.postimg.cc/hGspn7JM/V8-00003.png" />
相关推荐：

https://github.com/hamiltonlinda25/thgubw/blob/main/%E7%95%85%E6%B8%B8%E6%96%87%E6%B5%B7%E9%80%90%E6%A2%A6%EF%BC%9AV8%E5%B9%B3%E5%8F%B0%E6%B3%A8%E5%86%8C_%E5%90%90%E6%8D%85%E9%9D%A1%E5%87%B3%E6%AC%A3RLLGH.md

<img src="https://i.postimg.cc/SKg3rPf5/V8-00018.png" />
相关推荐：

https://github.com/hamiltonlinda25/thgubw/commit/1f0abe33812ce34a58e58116dc704c16cd90f74c

<img src="https://i.postimg.cc/90Rpy8Ls/V8-00008.png" />

资讯来源：新华网、人民网、央视新闻、中新网、凤凰网、澎湃新闻、界面新闻、新浪新闻、搜狐网、财新网、观察者网、第一财经等主流平台，以独树一帜的观察视角与扎实的深度报道能力，在资讯领域收获广泛关注。
