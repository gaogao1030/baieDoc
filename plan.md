## 套餐相关

### 获取会员套餐列表
#### URL
get api/v1/plans

#### 请求参数
无

#### 返回结果
```
{
	list: [
		{
			id: number, // 套餐id
			name: string, // 套餐名称
			desc: string, // 套餐描述
			price: number, // 套餐价格
			duration: number, // 套餐期限
			error_code: number // 错误代码
		},
		...,
		...
	]
}
```

### 购买套餐
#### URL
post api/v1/plans/purchase

#### 请求参数
| 参数       | 必选 | 类型   | 说明 |
| --------- | ---- | ------ | ----|
| token | true | string | Token令牌 |
| plan_id | true | number | 套餐id |
| article_id | true | number | 推广文章id |
| pay_type| false | number | 支付方式，不传的话应有个默认值。例如 wechat |

#### 返回结果
```
{
	message: string // 消息
	error_code: number // 错误代码
}
```

---












