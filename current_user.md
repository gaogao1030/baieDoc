## 当前登录用户相关

### 获取用户基础信息
#### URL
get api/v1/users/my/profile

#### 请求参数
| 参数       | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| token   | true | string |  Token令牌 |


#### 返回结果
```
{
  id: number, // 用户ID
  is_franchiser: boolean, // 是否经销商
  academic_title: string, // 职称
  nickname: string, // 昵称
  avatar: string, // 用户头像URL
  phone: string, // 手机号
  balance: number, // 余额
  error_code: number // 错误代码
}
```

---

### 更新用户基础信息
#### URL
post api/v1/users/my/profile

#### 请求参数
| 参数       | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| token | true | string |  Token令牌 |
| academic\_tittle | false | string | 职称 |
| nickname | false | string| 昵称 |
| avatar | false | string | 头像 |
| phone | false| string | 手机号 |

#### 返回结果
```
{
  message: string, // 消息说明
  error_code: number // 错误代码
}
```

---

### 获取用户当前购买的套餐
#### URL
get api/v1/users/my/purchase\_plan/current

#### 请求参数
| 参数       | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| token   | true | string |  Token令牌 |

#### 返回结果
```
{
  id: number, // 套餐id
  name: string, // 套餐名称
  desc: string, // 套餐描述
  price: number, // 套餐价格
  duration: number, // 套餐期限
  expired_date: datetime, // 会员到期时间
  is_expired: boolean, // 会员是否过期
  brokerage_ratio: number, // 佣金比例
  feedback_days: number, // 回馈天数
  created_at: datetime, // 该套餐购买时间
  error_code: number // 错误代码
}
```
 
---

### 获取通过该用户分享的购买链接用户购买套餐的列表
#### URL
get api/v1/users/my/shared\_purchase\_plans/

#### 请求参数
| 参数       | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| token | true | string | Token令牌 |
| page | false | number | 页数 |
| per\_page | false | number | 每页多少个 |

#### 返回结果
```
{
  list: [
    {
      name: string, // 套餐名称
      desc: string, // 套餐描述
      price: number, // 套餐价格
      purchase_user_id: number // 购买用户id
      created_at: datetime // 该套餐购买时间
    },
    ...,
    ...
  ],
  page: number, // 当前页码
  per_page: number, // 每页多少个
  error_code: number // 错误代码
}
```

#### URL
get api/v1/users/my/shared\_purchase\_plans/:plan\_id

#### 请求参数
| 参数       | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| token | true | string | Token令牌 |
| plan\_id | true | string | 套餐id |

#### 返回结果
```
{
  id: number, // 套餐id
  name: string, // 套餐名称
  desc: string, // 套餐描述
  price: number, // 套餐价格
  duration: number, // 套餐期限
  expired_date: datetime, // 会员到期时间
  brokerage_ratio: number, // 佣金比例
  feedback_days: number, // 回馈天数
  purchase_user_id: number, // 购买用户id
  created_at: datetime, // 该套餐购买时间
  error_code: number // 错误代码
}
```

---
### 获取用户余额
#### URL
get api/v1/users/my/wallet/balance

#### 请求参数
| 参数       | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| token | true | string | Token令牌 |


#### 返回结果
```
{
  balance: number, // 余额
  error_code: number // 错误代码
}
```

---
### 获取用户交易记录
#### URL
get api/v1/users/my/wallet/transaction\_records

#### 请求参数
| 参数       | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| token | true | string | Token令牌 |
| page | false | number | 页数 |
| per\_page | false | number | 每页多少个 |

#### 返回结果
```
{
  list: [
    {
      id: number, // 交易记录id
      transaction_amount: number, // 交易金额
      operation_type: string, // 操作类型
      created_time: datetime, // 交易时间
      remark: string // 备注
    },
    ...,
    ...
  ]
  error_code: number // 错误代码
}

```
#### URL
get api/v1/users/my/wallet/transaction\_records/:record\_id

#### 请求参数
| 参数       | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| token | true | string | Token令牌 |
| record\_id | true | string | Token令牌 |

#### 返回结果
```
{
  id: number, // 交易记录id
  transaction_amount: number, // 交易金额
  operation_type: string, // 操作类型
  created_time: datetime, // 交易时间
  remark: string, // 备注
  error_code: number // 错误代码
}
```
---

### 用户提现资格认证
#### URL
post api/v1/users/my/identification/withdraw\_cash

#### 请求参数
| 参数       | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| token | true | string | Token令牌 |
| name | true | string | 开户人姓名 |
| bank | true | string | 开户银行 |
| branch\_bank | true | string | 支行 |
| card\_number | true | string | 银行卡号 |
| phone | true | string | 银行预留手机号 |


#### 返回结果
```
{
  message: string, // 消息
  error_code: number // 错误代码
}
```

---
