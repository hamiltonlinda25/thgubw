杏彩官网地址【Q-——333307——】杏彩官网地址【 辋芷《888yx●vip》 】
杏彩官网地址【Q-——333307——】杏彩官网地址【 辋芷《888yx●vip》 】

 从零到一：如何用Github Pages搭建个人技术博客（2025最全指南）

还在羡慕技术大牛拥有自己的独立博客？其实，借助 Github Pages，你完全可以从零开始，免费搭建一个属于自己的技术分享阵地。今天，我们就来聊聊如何用 Github 完成从代码托管到博客上线的全流程。

 为什么选择Github Pages？

在搭建之前，我们先明确优势：免费、支持自定义域名、直接关联 Git 版本控制，且无需自己购买服务器。对于任何开发者来说，这都是成本最低的起步方案。

 搭建步骤详解

 第一步：创建仓库
登录你的 Github 账号，新建一个仓库，仓库名必须遵循格式：`用户名.github.io`。这是Github识别个人站点域名的唯一标准。

 第二步：选择框架
目前最流行的静态博客框架是 Hexo 和 Hugo。以Hexo为例，在本地安装Node.js后，通过命令行工具 `npm install -g hexo-cli` 即可完成环境配置。这一步是很多新手卡壳的地方，建议按官方文档逐行执行。

 第三步：部署上线
在仓库的Settings页面找到 Pages 设置项。在 "Branch" 下拉菜单中，选择主分支（通常是 `main`），点击保存。约1分钟后，你的博客地址 `用户名.github.io` 即可访问。

 如何让博客被搜索引擎收录？

GitHub 上的博客默认对百度爬虫并不友好。想要被百度收录，需要在仓库根目录添加一个 `robots.txt` 文件，并在其中声明：

```text
User-agent: Baiduspider
Disallow:
```

同时，建议在 `head` 标签中加入百度站点验证的 `meta` 标签。这一步能极大提升你在百度搜索结果中的曝光率。

 最佳实践与小技巧

1.  基于Git的分支管理：建议使用 `dev` 分支写作，`main` 分支发布，保持提交记录干净。
2.  图床管理：图片切勿直接打包进仓库，推荐使用 Gitee 图床或OSS，避免仓库体积过大拖慢加载速度。
3.  绑定自有域名：如果觉得默认域名不好记，可以在域名服务商处解析CNAME记录至 `用户名.github.io`。

---

如果你在搭建过程中遇到报错，比如“404页面找不到”或“部署失败”，欢迎在评论区留下你的报错截图，我会第一时间为你排查。如果你正在使用 Github 做其他有趣的项目，也欢迎分享你的仓库地址，我们下期见！

相关推荐：

https://github.com/wallacedavid3/hkosvm/blob/main/2026%E5%AE%98%E6%96%B9%E8%AE%BF%E8%B0%88%EF%BC%9AOD%E4%BD%93%E8%82%B2%E5%BC%80%E6%88%B7%E6%B3%A8%E5%86%8C_%E5%BD%9D%E6%83%AB%E9%A6%81%E4%BA%A2%E7%9B%96YZUCC.md

<img src="https://i.postimg.cc/tC3ypH6h/xingcai1-00011.png" />

相关推荐：

https://github.com/wallacedavid3/hkosvm/commit/73e47d31573be735a2fa4cff84f5d9bf56819148

<img src="https://i.postimg.cc/RZTMQzVh/xingcai1-00001.png" />
相关推荐：

https://github.com/middletoncrystal4897/mezabv/blob/main/2026%E5%AE%98%E7%BD%91%E4%B8%93%E8%AE%BF%EF%BC%9AOD%E4%BD%93%E8%82%B2%E5%BC%80%E6%88%B7%E5%AE%98%E6%96%B9_%E8%BF%9F%E7%A9%B6%E5%AF%BF%E4%B8%B6%E8%8F%B2CQESM.md

<img src="https://i.postimg.cc/m2fRvrPL/xingcai1-00010.png" />
相关推荐：

https://github.com/middletoncrystal4897/mezabv/commit/bd5d04d9a8599ceb6873b92463ceee9040f2b267

<img src="https://i.postimg.cc/tC3ypH6h/xingcai1-00011.png" />

资讯来源：新华网、人民网、央视新闻、中新网、凤凰网、澎湃新闻、界面新闻、新浪新闻、搜狐网、财新网、观察者网、第一财经等主流平台，以独树一帜的观察视角与扎实的深度报道能力，在资讯领域收获广泛关注。
