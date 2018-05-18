## 用户相关(取消)

### 登录
#### URL
post api/v1/users/sign\_in

#### 请求参数
| 参数       | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| login | true | string |  会员名或手机号 |
| password | true | string | 密码 |

#### 返回结果
```
{
	token: string, // 令牌 Token
	message: string, // 消息说明
	error_code: number // 错误代码
}
```
---
### 重置密码
#### URL
post api/v1/users/reset\_password

#### 请求参数
| 参数       | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| phone | true | string |  手机号 |
| sms_code | true | string | 验证码 |
| password | true | string | 密码 |
| password_confirm | true | string | 密码确认 |

#### 返回结果
```
{
  	
  	
  	token: string, // 令牌 Token
	message: string, // 消息说明
	error_code: number // 错误代码
}
```
---

### 注册
#### URL
post api/v1/users/sign\_up

#### 请求参数
| 参数       | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| phone | true | string |  手机号 |
| sms_code | true | string | 验证码 |

#### 返回结果
```
{
	token: string, // 令牌 Token
	message: string, // 消息说明
	error_code: number // 错误代码
}
```
---

### 手机验证码登录
#### URL
post api/v1/users/sign\_in\_with\_mobile

#### 请求参数
| 参数       | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| phone | true | string |  手机号 |
| sms_code | true | string | 验证码 |


#### 返回结果
```
{
	token: string, // 令牌 Token
	message: string, // 消息说明
	error_code: number // 错误代码
}
```

---

### 手机验证码获取
#### URL
post api/v1/users/sms\_code/get

#### 请求参数
| 参数       | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| phone | true | string |  手机号 |

#### 返回结果
```
{
	message: string, // 消息说明
	error_code: number // 错误代码
}
```

---












