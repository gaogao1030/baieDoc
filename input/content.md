## 内容中心相关

### 获取文章列表
#### URL
get api/v1/articles

#### 请求参数
| 参数 | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| tag | false| string| 文章标签: 默认为 all. |
| page | false | string | 当前页码 |
| per\_page| false | string | 每页多少个 |
| show_level | true | inter | 展示等级 1、经销商可见 2、非经销商可见 |
| sort | false | string | 排序方式: [forward, reverse] |

#### 返回结果
```
{
  list: [
  	{
		id: number // 文章id
    	title: string // 文章标题
    	created_at: datetime // 文章创建时间
    	cover: string // 文章封面 url
    	read_count: number // 阅读数
    	repost_count: number // 转载数
    	tags: [
      		{
		 		name: // tag 标签名
      		},
    	...,
    	...]
  },
  ...,
  ...
  ],
  error_code: string // 错误代码
}
```

### 获取文章详情
#### URL
get api/v1/articles/:article\_id

#### 请求参数
| 参数 | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| article\_id | true | string| 文章id |

#### 返回结果
```
{
	id: number // 文章id
    title: string // 文章标题
    created_at: datetime // 文章创建时间
    cover: string // 文章封面 url
    show_leveal: number // 展示等级
    read_count: number // 阅读数
    repost_count: number // 转载数
    content: string // 文章内容
    cretor: string // 文章创建人
    latest_editor: string // 文章最近修改人
    tags: [
      {
			name: // tag 标签名
      },
      ...,
      ...
    ],
    error_code: string // 错误代码
}
```

### 创建文章
#### URL
post api/v1/articles

#### 请求参数
| 参数 | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| title | true | string| 文章标题 |
| cover | true | string | 文章封面 url |
| content | true | string | 文章内容 |
| token | true | string | 令牌 |


#### 返回结果
```
{
	message: string // 消息
	error_code: string // 错误代码
}
```

### 编辑文章
#### URL
put api/v1/articles/:article\_id

#### 请求参数
| 参数 | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| article\_id | true | string| 文章id |
| token | true | string | 令牌 |

#### 返回结果
```
{
	message: string // 消息
	error_code: string // 错误代码
}
```

### 删除文章
#### URL
delete api/v1/articles/:article\_id

#### 请求参数
| 参数 | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| article\_id | true | string| 文章id |
| token | true | string | 令牌 |

#### 返回结果
```
{
	message: string // 消息
	error_code: string // 错误代码
}
```

### 批量删除文章
#### URL
delete api/v1/articles/

#### 请求参数
| 参数 | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| article\_ids | true | array | 文章id集合 |
| token | true | string | 令牌 |

#### 返回结果
```
{
	message: string // 消息
	error_code: string // 错误代码
}
```

### 获取案例列表
#### URL
get api/v1/cases

#### 请求参数
| 参数 | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| tag | false | string| 案例标签: 默认为 all. |
| page | false | string | 当前页码 |
| per\_page| false | string | 每页多少个 |
| sort | false | string | 排序方式: [forward, reverse]|

#### 返回结果
```
{
	list: [
	{
		id: number // 案例id
	},
	...,
	...
	],
	error_code: string // 错误代码
}
```
### 获取案例详情
#### URL
get api/v1/cases/:case\_id

#### 请求参数
| 参数 | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| case\_id | true | string| 案例id |

#### 返回结果
```
{
	id: number, // 案例id
	error_code: string // 错误代码
}
```


---
### 获取标签
#### URL
get api/v1/tags

#### 请求参数
| 参数       | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| type | true | string |  标签类型: [article, case] |

#### 返回结果
```
{
	type: number // 标签类型
	name: string // 标签名称
	weight: number // 权重
	error_code: number // 错误代码
}
```
---

