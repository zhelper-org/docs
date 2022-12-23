# 关于 zhelper 业务调整的说明

基于安全、用户体验、维护成本等多方面的考虑，我们决定停止对旧版网站的维护，请您迁移到新版 zhelper search。

[您可以在这里读到更多 zhelper search 相关信息](/search)

## zhelper search 与 zhelper V4、V5 的区别

- zhelper search 是**一个“没有任何功能的网站”**：如果您直接打开 zhelper search，会发现什么都做不了。不能搜索、更不能下载。
- zhelper search 是**一个“全能的网站”**：zhelper search 兼容多个搜索接口，包括之前的 V4、V5 搜索接口，也包括更多其他（符合API规范的）搜索接口。
- zhelper search **必须要配置才能使用**：您**必须**告诉 zhelper search 用哪个搜索接口，zhelper search 才能工作。
- zhelper search 是一个**很简单的网站**：它所做的唯一的事情就是——把您的搜索的关键词发给搜索接口，然后把搜索接口返回的结果整理成人类可以阅读的形式展现出来。

[关于 zhelper search 的具体使用请参考本文](/search)

## 之后 zhelper V4、V5 还会维护吗？

zhelper V4、V5 搜索界面将不在维护，我们也没有时间精力进一步维护了。但是 zhelper V4、V5 后端（API 接口）相关代码已经开源，欢迎各位开发、部署。

按我们的计划，在您看到本页面的时候，zhelper V4、V5 搜索页面应该已经打不开了，zhelper V4 API 接口应该也不能使用了（下载已经找到 zlib.download 部署，搜索找了 mibooks.tk 部署），zhelper V5 接口应该还能用（还没有找到下家。。。），之后这些项目都将转为由网友自行部署。实属无奈之举，请谅解。