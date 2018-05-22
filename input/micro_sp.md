## 微单页文章库

### 获取我的单页文章库列表
#### URL
get api/v1/micro_sp/my/article\_libaries 

#### 请求参数
| 参数       | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| token | true | string | 令牌 Token |
| page | false | boolean | 页码 |
| per_page | false | boolean | 页数 |

#### 返回结果
```
{
	count: number // 所有文章总计数
	lists: [
		{
			id: number // 文章库 id
			name: string // 库名称
			count: number // 该文章库所属文章总计数
		},
		...,
		...
	],
	error_code: string // 错误代码
}
```
---

### 获取微单页文章库详情
#### URL
get api/v1/micro_sp/my/article\_libaries/:id/articles/

#### 请求参数
| 参数       | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| token | true | string | 令牌 Token |
| id | true | string | 文章库 id, id 为 0 是查询全部文章 |
| filter | true | string | 过滤器, 枚举 [repost, draft, publish, all]|
| page | false | boolean | 页码 |
| per_page | false | boolean | 页数 |

#### 返回结果
```
{	
	id: number // 文章库 id
	name: // 文章库名称
	count: // 该文章库下所属文章总数
	list: [
		{
			id: number, // 文章 id
			title: string, // 文章标题
			cover: string, // 文章封面图
			is_top: boolean, // 是否置顶
			status: string, // 状态枚举 [draft, publish], 文章只能处于草稿或发布状态
			read_count: number // 阅读数
			repost_count: number // 转载数
			repost_article_id: number, // 转载文章 id
			created_at: datetime, //创建时间
			updated_at: datetime, //修改时间
		},
		...,
		...
	],
	error_code: string // 错误代码
}
```

---

### 创建微单页文章
#### URL
post api/v1/micro_sp/my/article\_libaries/:id/articles/

#### 请求参数
| 参数       | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| token | true | string | 令牌 Token |
| id | true | string | 文章库 id |
| article\_id| true| number | 文章 id |
| title | false | string | 文章标题 |
| status | false | string | 枚举 ['draft', 'publish'] |
| share\_title | false| string | 文章分享标题 |
| cover | false| string | 封面图 url |
| item\_ids | false | array | 组件顺序， 比如 [5,3,1]， 组件 id 为 5 排队首，3 排其次， 1 排队末 |
| publisher\_info | false | string | 发布人信息 |
| is\_display\_copyright | false| boolean | 是否显示版权声明 |
| is\_display\_publisher | false | boolean | 是否显示发布人信息 |


#### 返回结果
```
{
	message: string
	error_code: string // 错误代码
}
```

---

### 获取微单页文章库文章详情
#### URL
get api/v1/micro_sp/my/article\_libaries/:id/articles/:article\_id

#### 请求参数
| 参数       | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| token | true | string | 令牌 Token |
| id | true | string | 文章库 id |

#### 返回结果
```
{	
	id: number, // 文章 id
	article_libary_id: 文章库 id
	title: string, // 文章标题
	share_title: string, // 分享标题
	cover: string, // 文章封面图
	type: string, // 文章类型枚举 [blank, enlist], 空白页或空白页
	status: string, // 状态枚举 [draft, publish], 文章只能处于草稿或发布状态
	is_top: boolean, // 是否置顶
	is_display_copyright: boolean, // 是否显示版权声明
	is_display_publisher: boolean, // 是否显示发布人信息
	publisher_info: string, // 发布人信息
	read_count: number // 阅读数
	repost_count: number // 转载数
	repost_article_id: number, // 转载文章 id
	created_at: datetime, // 创建时间
	updated_at: datetime, // 修改时间
	items: [ 
		{
			id: number, // 组件 id
			type: string, // 组件类型枚举 [text, image, link, phone, qrcode, advertisement, case]
			content: string // 返回自定的 json 字符串
		},
		...,
		...
	]
	error_code: string // 错误代码
}
```
---

### 更新微单页文章库文章
#### URL
put api/v1/micro_sp/my/article\_libaries/:id/articles/:article\_id

#### 请求参数
| 参数       | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| token | true | string | 令牌 Token |
| id | true | string | 文章库 id |
| article\_id| true| number | 文章 id |
| title | false | string | 文章标题 |
| status | false | string | 枚举 ['draft', 'publish'] |
| share\_title | false| string | 文章分享标题 |
| cover | false| string | 封面图 url |
| item\_ids | false | array | 组件顺序， 比如 [5,3,1]， 组件 id 为 5 排队首，3 排其次， 1 排队末 |
| publisher\_info | false | string | 发布人信息 |
| is\_display\_copyright | false| boolean | 是否显示版权声明 |
| is\_display\_publisher | false | boolean | 是否显示发布人信息 |
| article\_libary\_id| false| boolean| 文章库 id, 用来移动文章到文章库|
 
#### 返回结果
```
{
	message: string
	error_code: string // 错误代码
}
```
---

### 删除微单页文章库文章
#### URL
delete api/v1/micro_sp/my/article\_libaries/:id/articles/:article\_id

#### 请求参数
| 参数       | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| token | true | string | 令牌 Token |
| id | true | string | 文章库 id |
| article\_id | false | number | 文章 id |
| article\_ids| false | array | 文章 id 数组，用于批量删除。 |
 
#### 返回结果
```
{
	message: string
	error_code: string // 错误代码
}
```

---

### 创建微单页文章库
#### URL
post api/v1/micro_sp/my/article\_libaries 

#### 请求参数
| 参数       | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| token | true | string | 令牌 Token |
| name | true | string | 名称 |

#### 返回结果
```
{
	message: string,
	error_code: string // 错误代码
}
```
---

### 更新微单页文章库
#### URL
put api/v1/micro_sp/my/article\_libaries/:id

#### 请求参数
| 参数       | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| token | true | string | 令牌 Token |
| id | true | number | 文章库 id |
| name | true | string | 名称 |

#### 返回结果
```
{
	message: string,
	error_code: string // 错误代码
}
```

---

### 删除微单页文章库
#### URL
delete api/v1/micro_sp/my/article\_libaries

#### 请求参数
| 参数       | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| token | true | string | 令牌 Token |
| id | false | number | 文章库 id |
| ids | false | array | 文章库 ids |

#### 返回结果
```
{
	message: string,
	error_code: string // 错误代码
}
```

---

## 微单页案例资源库

### 获取我的案例库列表
#### URL
get api/v1/micro_sp/my/case\_libaries

#### 请求参数
| 参数       | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| token | true | string | 令牌 Token |
| page | false | boolean | 页码 |
| per_page | false | boolean | 页数 |

#### 返回结果
```
{
	id: number // 案例库 id
	count: number // 所有案例总计数
	lists: [
		{
			id: number // 案例 id
			koubei_case_id: number // 口碑案例id
			count: number // 该案例库所属案例总计数
		},
		...,
		...
	],
	current_page: number // 当前页码
	error_code: string // 错误代码
}
```

---
### 获取我的案例库详情
#### URL
get api/v1/micro_sp/my/case\_libaries/:id/cases

#### 请求参数
| 参数       | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| token | true | string | 令牌 Token |
| id | true | number | 案例库 id, id 为 0，取出全部案例 |
| page | false | boolean | 页码 |
| per_page | false | boolean | 页数 |

 
#### 返回结果
```
{
	id: number // 案例库 id
	name: string // 案例库名称
	count: number // 该案例库案例总计数	
	items: [
		{
			id: number //案例 id
			koubei_case_id: number // 口碑案例id
		},
		...,
		...
	],
	error_code: string // 错误代码
}
```

---
### 删除我的案例库
#### URL
delete api/v1/micro_sp/my/case\_libaries

#### 请求参数
| 参数       | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| token | true | string | 令牌 Token |
| id | false | number | 案例库 id |
| ids | false | array | 案例库 id 集合 |

 
#### 返回结果
```
{
	message: string,
	error_code: string // 错误代码
}
```

---
### 创建我的案例
#### URL
post api/v1/micro_sp/my/case\_libaries/:id/cases

#### 请求参数
| 参数       | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| token | true | string | 令牌 Token |
| id | true | number | 案例库 id |
| koubei\_case\_id | true | number| 口碑案例 id |

 
#### 返回结果
```
{
	message: string,
	error_code: string // 错误代码
}
```

---

### 更新我的案例
#### URL
put api/v1/micro_sp/my/case\_libaries/:id/cases/:case_id

#### 请求参数
| 参数       | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| token | true | string | 令牌 Token |
| id | true | number | 案例库 id |
| case_id | true | number | 案例 id |
| case_libary_id| false | number | 更新所属的案例库所使用的 id|
 
#### 返回结果
```
{
	message: string,
	error_code: string // 错误代码
}
```

---
### 删除我的案例
#### URL
delete api/v1/micro_sp/my/case\_libaries/:id/cases

#### 请求参数
| 参数       | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| token | true | string | 令牌 Token |
| id | true | number | 案例库 id |
| case_id | false | number | 案例 id |
| case_ids | false | array | 案例 id 集合， 批量删除 |
 
#### 返回结果
```
{
	message: string,
	error_code: string // 错误代码
}
```

---

## 组件部分

### 获取我的组件列表
#### URL
get api/v1/micro_sp/my/components

#### 请求参数
| 参数       | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| token | true | string | 令牌 Token |
| type | false | number | 组件类型枚举 [text, image, link, phone, qrcode, advertisement, case] |
| page | false | boolean | 页码 |
| per_page | false | boolean | 页数 |

#### 返回结果
```
{
	items: [ 
		{
			id: number, // 组件 id
			type: string, // 组件类型枚举 [text, image, link, phone, qrcode, advertisement, case]
			content: string // 返回自定的 json 字符串
		},
		...,
		...
	],
	error_code: string // 错误代码
}
```

---
### 创建我的组件
#### URL
post api/v1/micro_sp/my/components

#### 请求参数
| 参数       | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| token | true | string | 令牌 Token |
| type | true | string | 组件类型枚举 [text, image, link, phone, qrcode, advertisement, case] |
| content | true | string | 自定义 json 字符串|


#### 返回结果
```
{
	message: string
	error_code: string // 错误代码
}

```

---

### 获取我的组件详情
#### URL
get api/v1/micro_sp/my/components/:id

#### 请求参数
| 参数       | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| token | true | string | 令牌 Token |
| id | true | number | 组件 id |

#### 返回结果
```
{
	id: number, // 组件 id
	type: string, // 组件类型
	content: string // 返回自定的 json 字符串
	error_code: string // 错误代码
}
```

---

### 更新我的组件
#### URL
put api/v1/micro_sp/my/components/:id

#### 请求参数
| 参数       | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| token | true | string | 令牌 Token |
| id | true | number | 组件 id |
| content | false | string | 组件内容 | 

#### 返回结果
```
{ 
	message: string,
	error_code: string // 错误代码
}
```

---

### 删除我的组件
#### URL
delete api/v1/micro_sp/my/components/:id

#### 请求参数
| 参数       | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| token | true | string | 令牌 Token |
| id | false | number | 组件 id |
| ids | false | array | 组件 ids |

#### 返回结果
```
{
	message: string,
	error_code: string // 错误代码
}
```

---

