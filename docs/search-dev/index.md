项目地址


## 多语言支持

通过 `language` 提供支持。目前已经有中文和 English 两个选项，欢迎贡献其他语言！

## 传入 API

目前 zhelper search 支持以 `location.search` 形式传入 API 信息，之后 TGBot 也会跟进相关功能。传入 API 示例：

```
https://search.zhelper.net/?[{"name":"exmaple","url":"https://api.exmaple.com","type":"full","sensitive":false,"detail":true}]
```

- 至少应当有以上 5 个字段。
- `name`：在前端展示的 API 名称
- `url`：API 请求的 `baseurl`
- `type`：API 类型，有 `full` 和 `light` 可选，详见 API 规范
- `sensitive`：是否开启敏感词模式，建议默认开启
- `detail`：API 是否有 `detail` 接口（是否需要请求此接口），详见 API 规范
- 多个 API 可以以列表的形式传入
- 使用 JSON 格式解析，请保证符合规范。