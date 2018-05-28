## 我的名片相关

### 获取我的名片信息
#### URL
get api/v1/my_card/

#### 请求参数
| 参数       | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| token | true | string |  令牌 token |
| user_id | false | string |  用户id, 如果有的话则覆盖 token, 以该用户我的名片的信息为主 |

#### 返回结果
```
{
	id: number // 令牌 Token
	avatar: string // 头像
	name: string // 姓名
	academic_title: string // 职称
	background_cover: string // 封面背景
	background_music: string // 音乐资源 url
	content: string // 4个格子的内容，返回自定义 json 字符串
	qr_code: string // 二维码
	phone: string // 手机联系号码
	introduction: string // 个人签名
	products_and_service: string // 产品及服务
	theme: {
		id: number // 主题 id
		name: string // 主题名称
	}
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
| user_id | false | string |  用户id, 如果有的话则覆盖 token, 以该用户的精选文章为主 |
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
| theme_id | false | number | 主题 id |

#### 返回结果
```
{
	message: string 
	error_code: number // 错误代码
}
```

---
### 获取我的名片主题样式
#### URL
get api/v1/my_card/themes/

#### 请求参数
无

#### 返回结果
```
	list: [
		{
			id: number // 主题 id
			name: string // 主题名称
			cover: string // 主题封面 url
		},
		...,
		...
		],
	error_code: number // 错误代码


```

