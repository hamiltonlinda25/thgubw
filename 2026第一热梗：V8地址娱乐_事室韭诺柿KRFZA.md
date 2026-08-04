V8地址娱乐【Q-——333307——】V8地址娱乐【 辋芷《888yx●vip》 】
V8地址娱乐【Q-——333307——】V8地址娱乐【 辋芷《888yx●vip》 】

 用 GitHub Actions 自动化部署静态博客，我踩过这 5 个坑

> 写博客最烦的不是内容，而是「发布」这一步。  
> 手打命令、反复上传、忘记构建……这些体验，应该都懂。  
> 后来我把部署流程交给了 GitHub Actions，世界瞬间清净了。

GitHub Actions 是 GitHub 自带的 CI/CD 工具，已经成了不少前端开发者自动部署静态博客的首选方案。  
尤其是配合 VuePress、VitePress、Hexo、Hugo 这类静态站点生成器，能实现「推送代码即发布」的全自动化体验。

但在实际使用过程中，我踩了不少坑。今天挑 5 个典型的写出来，希望能帮你少走弯路。

---

 一、workflow 文件写错位置，白跑一整天

第一次用 Actions 时，最容易犯的错误——  
把 `.yml` 文件放在了项目根目录，而不是 `.github/workflows/` 下。  

GitHub 只识别 `.github/workflows/` 目录下的 action 配置。  
目录结构大概是这样的：

```
your-blog/
└── .github/
    └── workflows/
        └── deploy.yml
```

检查一下，如果你发现页面一直没有跑 action，先看看路径对不对。

---

 二、权限没开，报错提示 `Permission denied`

部署到 GitHub Pages 时，需要 push 到 `gh-pages` 分支，必须显式开启工作流的写权限。

在仓库 `Settings -> Actions -> General` 里，把 Workflow permissions 改成：  
✅ `Read and write permissions`  

否则，你会在日志里看到一个很迷的错误：

```
remote: Permission to git@github.com:xxx/blog.git denied.
```

---

 三、Pages 分支没配对，页面一直 404

很多人把博客文件 push 到了 `gh-pages` 分支，但仓库 Pages 设置却还指向 `main` 分支。  
所以部署看似成功，但访问域名永远 404。

请在仓库 `Settings -> Pages` 中，把 Source 设置为：

```
Deploy from a branch
Branch: gh-pages
```

或者直接用 GitHub Actions 官方提供的 `actions/deploy-pages@v4`，省心省力，不用手动配置分支。

---

 四、Node 版本不一致，构建莫名失败

有些依赖只支持特定版本 Node，但 Actions 默认环境可能是最新版或旧版，容易触发兼容性报错。

解决办法是锁定动作版本：

```yaml
- uses: actions/setup-node@v4
  with:
    node-version: 18
```

建议和你本地构建时的 Node 版本保持完全一致，这样能大幅减少“本地跑的好好的，一到线上就挂”的问题。

---

 五、想用缓存加速构建，但老是命中失败

每次跑 action 都重新安装依赖，耗时可以从几分钟拉到十几分钟。  
解决办法是加一层 `actions/cache`：

```yaml
- uses: actions/cache@v3
  with:
    path: ~/.npm
    key: ${{ runner.os }}-node-${{ hashFiles('/package-lock.json') }}
```

如果你用的是 pnpm，还可以直接用 `pnpm/action-setup` 的内置缓存，识别度更好。

---

 六、小建议：多看看 action 日志

记住，日志永远是排查问题的第一入口。  
如果部署失败，点开 Actions 页面，看具体是哪一步标红，再针对性搜索关键词。  
一般 80% 的问题都能在 GitHub 官方文档里找到答案。

---

自动部署不是玄学，是对细节的理解。  
希望这一篇文章能帮你缩短从「提交」到「上线」的最后一步。

---

如果你现在也在用 GitHub Actions 部署博客，欢迎留言吐槽你踩过的坑 👇  
我也在考虑下一篇写「如何用 Actions 自动备份数据库到远程仓库」，感兴趣的话点个赞让我知道。

相关推荐：

https://github.com/stoneconnor94/facjpk/blob/main/2026%E6%9D%83%E5%A8%81%E6%89%8B%E5%86%8C%EF%BC%9AV8%E7%BD%91%E5%9D%80%E7%BD%91%E5%9D%80_%E7%AB%BF%E5%90%AD%E8%B0%B0%E7%BD%95%E6%B7%8CIWZAB.md

<img src="https://i.postimg.cc/2ysxGQJ5/V8-00009.png" />

相关推荐：

https://github.com/stoneconnor94/facjpk/commit/142909c26fd967a7289b2fe3e3d9f543218ca89b

<img src="https://i.postimg.cc/P5kgrYxk/V8-00014.png" />
相关推荐：

https://github.com/nguyenmark0/dznovc/blob/main/2026%E5%AE%98%E7%BD%91%E7%88%86%E7%82%B9%EF%BC%9AV8%E7%BD%91%E5%9D%80%E7%99%BB%E5%BD%95_%E8%BF%98%E7%AB%99%E8%99%91%E6%BD%AE%E7%97%9BKXDZS.md

<img src="https://i.postimg.cc/5tbnDmt0/V8-00001.png" />
相关推荐：

https://github.com/nguyenmark0/dznovc/commit/2393962f840ed0db521f627beb5687e1d61fbc9b

<img src="https://i.postimg.cc/nzw2jbGZ/V8-00006.png" />

资讯来源：新华网、人民网、央视新闻、中新网、凤凰网、澎湃新闻、界面新闻、新浪新闻、搜狐网、财新网、观察者网、第一财经等主流平台，以独树一帜的观察视角与扎实的深度报道能力，在资讯领域收获广泛关注。
