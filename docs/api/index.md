虽然 zhelper search 以及 zhelper TGBot 原则上可以对接任何后端进行检索，但由于精力有限，目前仍然主要是对书籍类数据进行适配。如有其他类型数据需求可以向我们提交。

约定：
- API 后端地址统一记为`https://api.exmaple.com`。
- 按照传统，所有示例代码使用 python 展示。
- 数据应当使用 Json 进行传递。

## 书籍类规范

### Full API

最主要的 API 类型。

#### search

请求代码

```python
json_data = {
    # 关键词，应当可以用空格分隔，建议使用 meilisearch 或者 elasticsearch 作为后端
    'keyword': '三体',
    # 页码，一般来说每页应当设置 20 条结果
    'page': 1,
    # 是否开启敏感词模式，如果接口对国内开放，建议提供此选项
    'sensitive': False,
}

# api 地址为 /api/search
response = requests.post('https://api.exmaple.com/api/search/', json=json_data)
```

返回值示例。

数据以列表形式存储在 `data` 中，书源`source`和 ID `id` 构成唯一标记值，在进一步的请求中作为获取依据。需要返回 `hits` 作为前端翻页参考。

如某一字段缺失，则返回`null`。

```json
{
  "data": [
    {
      "title": "三体",
      "author": "刘慈欣",
      "publisher": "",
      "isbn": "9787536692930",
      "extension": "pdf",
      "filesize": 4706425,
      "year": "",
      "id": 2817721,
      "source": "zlibrary"
    },
    {
      "title": "三体",
      "author": "刘慈欣",
      "publisher": "",
      "isbn": null,
      "extension": "txt",
      "filesize": 399897,
      "year": "",
      "id": 3483639,
      "source": "zlibrary"
    },
    {
      "title": "三体",
      "author": "刘慈欣",
      "publisher": "重庆出版社",
      "isbn": "9787536692930",
      "extension": "pdf",
      "filesize": 165383382,
      "year": "2008",
      "id": 5241719,
      "source": "zlibrary"
    },
    {
      "title": "三体",
      "author": "刘慈欣",
      "publisher": "",
      "isbn": null,
      "extension": "epub",
      "filesize": 2134513,
      "year": "2011",
      "id": 5552637,
      "source": "zlibrary"
    },
    {
      "title": "三体",
      "author": "刘慈欣",
      "publisher": "",
      "isbn": null,
      "extension": "azw3",
      "filesize": 386569,
      "year": "2011",
      "id": 5732339,
      "source": "zlibrary"
    },
    {
      "title": "三体",
      "author": "刘慈欣",
      "publisher": "重庆出版社",
      "isbn": null,
      "extension": "pdf",
      "filesize": 13713550,
      "year": "2012",
      "id": 5814476,
      "source": "zlibrary"
    },
    {
      "title": "三体",
      "author": "刘慈欣",
      "publisher": "epub掌上书苑",
      "isbn": null,
      "extension": "epub",
      "filesize": 2135075,
      "year": "2011",
      "id": 6165958,
      "source": "zlibrary"
    },
    {
      "title": "三体",
      "author": "刘慈欣",
      "publisher": "epub掌上书苑",
      "isbn": null,
      "extension": "mobi",
      "filesize": 4632483,
      "year": "2011",
      "id": 6196050,
      "source": "zlibrary"
    },
    {
      "title": "三体",
      "author": "刘慈欣",
      "publisher": "epub掌上书苑",
      "isbn": null,
      "extension": "mobi",
      "filesize": 3336354,
      "year": "2011",
      "id": 11552744,
      "source": "zlibrary"
    },
    {
      "title": "三体",
      "author": "刘慈欣 & chenjin5.com",
      "publisher": "chenjin5.com 海量电子书免费下载",
      "isbn": null,
      "extension": "azw3",
      "filesize": 611342,
      "year": "2011",
      "id": 11896657,
      "source": "zlibrary"
    },
    {
      "title": "三体",
      "author": "刘慈欣 & chenjin5.com [刘慈欣 & chenjin5.com]",
      "publisher": "chenjin5.com 海量电子书免费下载",
      "isbn": null,
      "extension": "epub",
      "filesize": 331077,
      "year": "2011",
      "id": 11903485,
      "source": "zlibrary"
    },
    {
      "title": "三体",
      "author": "刘慈欣 & chenjin5.com",
      "publisher": "chenjin5.com 海量电子书免费下载",
      "isbn": null,
      "extension": "mobi",
      "filesize": 589795,
      "year": "2011",
      "id": 11913070,
      "source": "zlibrary"
    },
    {
      "title": "三体",
      "author": "刘慈欣",
      "publisher": "epub掌上书苑",
      "isbn": null,
      "extension": "mobi",
      "filesize": 3333653,
      "year": "2011",
      "id": 11993964,
      "source": "zlibrary"
    },
    {
      "title": "三体",
      "author": "刘慈欣",
      "publisher": "epub掌上书苑",
      "isbn": null,
      "extension": "azw3",
      "filesize": 3417755,
      "year": "2011",
      "id": 15425721,
      "source": "zlibrary"
    },
    {
      "title": "三体",
      "author": "刘慈欣",
      "publisher": "",
      "isbn": "9787229042066",
      "extension": "azw3",
      "filesize": 386573,
      "year": "2011",
      "id": 15959349,
      "source": "zlibrary"
    },
    {
      "title": "三体",
      "author": "劉慈欣",
      "publisher": "早川書房",
      "isbn": null,
      "extension": "txt",
      "filesize": 989016,
      "year": "",
      "id": 16310451,
      "source": "zlibrary"
    },
    {
      "title": "三体",
      "author": "刘慈欣",
      "publisher": "",
      "isbn": "9787229042066",
      "extension": "mobi",
      "filesize": 602933,
      "year": "2011",
      "id": 16337681,
      "source": "zlibrary"
    },
    {
      "title": "三体",
      "author": "刘慈欣",
      "publisher": "",
      "isbn": "9787229042066",
      "extension": "mobi",
      "filesize": 602601,
      "year": "2011",
      "id": 16530802,
      "source": "zlibrary"
    },
    {
      "title": "三体",
      "author": "原著：刘慈欣",
      "publisher": "",
      "isbn": null,
      "extension": "pdf",
      "filesize": 1242036,
      "year": "",
      "id": 16566326,
      "source": "zlibrary"
    },
    {
      "title": "三体",
      "author": "刘慈欣",
      "publisher": "epub掌上书苑",
      "isbn": null,
      "extension": "epub",
      "filesize": 2135060,
      "year": "2011",
      "id": 16566339,
      "source": "zlibrary"
    }
  ],
  "hits": 900
}
```

#### detail（可选）