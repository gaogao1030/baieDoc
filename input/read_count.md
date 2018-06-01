## 阅读数接口

### 增加内容中心文章阅读数
#### URL
put /api/v1/articles/{id}/read


#### 请求参数
| 参数       | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| id | true | string |  文章id |

#### 返回结果
```
{
	message: string, // 消息说明
	error_code: number // 错误代码
}
```
---

### 增加内容中心文章转载数
#### URL
put api/v1/users/reset\_password

#### 请求参数
| 参数       | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| id | true | string |  文章id |

#### 返回结果
```
{
	message: string, // 消息说明
	error_code: number // 错误代码
}
```
---

### 增加微单页文章阅读数
#### URL
put /api/v1/micro_sp/my/articles/{id}/read


#### 请求参数
| 参数       | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| id | true | string |  文章id |

#### 返回结果
```
{
	message: string, // 消息说明
	error_code: number // 错误代码
}
```

---
### 增加微单页文章转载数
#### URL
put /api/v1/micro_sp/my/articles/{id}/repost

#### 请求参数
| 参数       | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| id | true | string |  文章id |

#### 返回结果
```
{
	message: string, // 消息说明
	error_code: number // 错误代码
}
```
---

