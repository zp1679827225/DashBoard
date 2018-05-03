# UseCase

---

### Full_Usecase

**用例UC1：顾客购票**

**范围：** 电影售票网站

**级别：** 用户目标

**主要参与者：** 用户

**涉众及其关注点：**

- 电影院：希望能够协调好各第三方购票平台与电影院之间的关系，避免出现购票冲突、场次不符等情况
- 第三方购票平台：希望能够准确地记录交易，满足顾客需求。希望确保记录了支付授权服务的支付票据。希望有一定的容错性，即使在某些服务器构建不可用时，也能够完成销售。希望能够自动、快速地更新账务和库存信息。希望从每笔交易中抽取提成。
- 用户：希望以最小代价完成购买活动并得到快速服务。希望便捷、清晰地看到所选择的电影院名称，电影类型、电影价格及其可选座位。希望得到购买凭证。
- 支付授权服务：希望接收到格式和协议正确的数字授权请求。希望准确计算对商店的应付款

**前置条件：** 第三方购票平台必须经过确认和认证

**成功保证(或后置条件)：** 存储销售信息。保证电影院与第三方购票平台电影票数据上的一致性。更新账务和库存信息。记录提成。生成票据。记录支付授权的批准。

**主成功场景(或基本流程)：**

1. 用户通过登录页面登录电影售票网站；
2. 用户通过注册页面注册电影售票网站会员；
3. 用户通过浏览主页了解当前正在上映与即将上映的电影情况；
4. 用户通过登录社区了解网友对电影及电影院的评价；
5. 用户通过购票选项可以选择电影院、电影类型、电影场次、座位；
6. 用户通过提交订单选项可以发送订单；
7. 电影售票网站锁定电影院对应座位；
8. 用户可以选择合适的付款方式进行付款；
9. 系统生成订单票据，包含电影场次、座位以及票价；
10. 电影售票网站向电影院付款，完成购票操作；
11. 用户到达电影院打印电影票。

**扩展：**

- *a. 用户在购票过程的任意时段意外断网或者浏览器闪退

  ​	i.    如果用户还未进行选位操作，则不保存用户操作信息；

  ​	ii.   如果用户已进行选位操作，则保存用户操作信息；

  ​        iii.  用户重新登录，系统恢复当前订单进度。

- 1a. 用户选择的电影院的对应场次已满

  ​        i.    弹窗告知用户该场次电影票售罄；

  ​        ii.   为用户推荐电影院同时间段的其它电影；

  ​        iii.  为用户推荐电影院同一电影的其他场次；

  ​        iv.  为用户推荐其它电影院的对应电影的同一场次。

- 2a.  多个用户同时选择同一电影院同一场次同个座位

  ​        i.    随机抽取其中一名用户，使其操作成功；

  ​        ii.   对其它用户采取弹窗告知：该座位已被预订

- 3a.   购票优惠提醒

  ​        i.     如果当前影院对应场次有优惠活动，则在当前金额处提醒用户；

  ​        ii.    如果用户有可用优惠券，则在订单界面的使用优惠券一栏提醒用户；

  ​        iii.   如果用户满足优惠条件，则在当前金额处提醒用户

- 4a.   系统友情提醒再次确认订单无误

  ​        i.      显示订单的所有信息，包括电影院名称、场次、电影票类型、价格、票数等；

- 5a.    取票时支付

  ​        i.       用户在前台出示订票凭证，付款后获取影票；

- 5b.    微信支付

  ​        i.       平台生成微信付款二维码

- 5c.    支付宝支付

  ​        i.       平台生成支付宝付款二维码

- 5d.   信用卡支付

  ​        i.      用户选择信用卡类型；

  ​        ii.      跳转至对应信用卡支付页面

- 6a. 送票上门服务

  ​        i.       该功能提供可选项；

  ​        ii.      用户填写地址、姓名、联系方式

**特殊需求：**

- 提供影票转让功能


- 支持文本显示的语言国际化

**技术与数据变元表：**

- 可以支持微信、支付宝、信用卡、现金付款

**发生频率：** 可能会不断地发生

**未决问题：**

- 电影转让功能导致黄牛党的介入的问题
- 用户恶意购票、退票问题
- 订单爆炸问题

### Casual_Usecase

1. Use Case：处理订单

   主成功场景：

   - 用户通过平台选择影院、电影、日期、座位并提交订单准备支付

   交替场景：

   - 用户所定场次已满，则告知用户订单产生失败
   - 用户未登录，则告知用户登录账户

2. Use Case：处理付款

   主成功场景：

   - 用户确认订单，选择支付方式，完成支付

   交替场景：

   - 用户账户余额不足，则告知用户付款失败
   - 用户没有在指定时间内付款，则告知用户订单已取消

### Brief_Usecase

1. Use Case：查看评价
   - Actor：用户
   - Type：Primary
   - Description：用户可以进入社区，查看电影或电影院的评分与评价，或者发布个人的评分与评价。
2. Use Case：查看订单
   - Actor：用户
   - Type：Primary
   - Description：用户可以进入个人界面查看订单，以查询自己的购买情况，包括电影院地址，场次信息，票价等