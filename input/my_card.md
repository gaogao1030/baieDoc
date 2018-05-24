## 我的名片相关

### 获取我的名片信息
#### URL
get api/v1/my_card/:id

#### 请求参数
| 参数       | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| token | true | string |  令牌 token |
| id | true | number | 我的名片模版 id |\

#### 返回结果
```
{
	id: number // 令牌 Token
	cover: string // 封面背景 url
	avatar: string // 头像
	name: string // 姓名
	academic_title: string // 职称
	background_cover: string // 封面背景
	background_music: string // 音乐资源 url
	content: string // 4个格子的内容，返回自定义 json 字符串
	qr_code: string // 二维码
	phone: string // 手机联系号码
	introduction: string // 个人签名
	product_and_service: string // 产品及服务
}
```

---
### 获取我的名片下的精选文章
#### URL
get api/v1/my\_card/best\_articles

#### 请求参数
| 参数       | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| token | true | string |  令牌 token |
| page | false | number | 第几页 |
| per_page| false | number | 每页多少个 |

#### 返回结果
```
{
	lists:[{
		id: number // 文章 id
		title: string // 文章标题
		cover: string // 文章封面 url
		updated_at: datetime // 文章更新时间 
		created_at: datetime // 文章创建时间
	},
	...,
	...]
}
```

---

### 更新我的名片信息
#### URL
put api/v1/my_card/

#### 请求参数
| 参数       | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| token | true | string |  令牌 token |
| avatar | false | string | 头像 url |
| name | false | string | 姓名 |
| academic_title | false | string | 职称 |
| background_cover | false | string | 封面背景 url |
| background_music | false | string | 音乐资源 url |
| content | false | string | 4个格子的内容， 自定义 json 字符串 |
| qr_code | false | string| 二维码 |
| phone | false | string | 手机联系方式 |
| introduction | false | string | 个人签名 |
| product_and_serveice | false | string | 产品及服务 |

#### 返回结果
```
{
	message: string 
	error_code: number // 错误代码
}
```

---

---

---

---