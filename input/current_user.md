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
  error_code: number, // 错误代码
  vipExpiry: date, //会员到期时间
  isVip: boolean //是否VIP
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

#### 返回结果
```
{
  message: string, // 消息说明
  error_code: number // 错误代码
}
```
 
---

### 获取其他用户通过该用户分享的文章链接购买套餐的列表以及回馈佣金及天数
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
      id: number, // 套餐id
      name: string, // 套餐名称
      desc: string, // 套餐描述
      price: number, // 套餐价格
      brokerage_get: number, // 获赠回馈佣金
      feedback_days_get: number, // 获赠回馈天数
      purchase_user_id: number, // 购买用户id
      purchase_user_name: string, // 购买用户昵称
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
get api/v1/users/my/wallet/transaction\_records/:id

#### 请求参数
| 参数       | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| token | true | string | Token令牌 |
| id | true | string | 记录id |

#### 返回结果
```
{
  id: number, // 交易记录id
  balance: number, // 余额
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
