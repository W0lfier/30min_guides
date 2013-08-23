# 零售行业优惠规则分析
## 1 优惠规则5要素
### 1.1 满足优惠条件的动作
这个要素，是指触发优惠规则的动作，主要包括买和满两种。

__注__：

- 在数学上，买是满的一种特殊情况，只不过做文本串分析时，要同时考虑到这两种文本描述。
- 在电商行业，触发优惠的动作还包括：晒单、微博分享、微信关注、给好评、收藏等行为，这里我只叙述与商品和订单相关的，与营销行为相关的暂忽略。
- 抽奖，中奖要看运气，所以这时也暂不讨论

#### 1.1.1 买
只要买就优惠，如买赠（买1送1）、买立减（买此商品立减5元）

#### 1.1.2 满
如满88减18


### 1.2 优惠条件作用对象
这个要素，是指满的对象（上文已解释，买其实是满的一种特殊情况，故此处叙述时合并），满什么条件，主要有三种：

#### 1.2.1 订单金额（抵扣前金额）
如满88元减18元

#### 1.2.2 实付金额（抵扣后金额）
如实付100元再返20元代金券

#### 1.2.3 商品数量
如买二送三，满2件每件165元，39元任选三件


### 1.3 优惠方式
这个要素是指，商家以什么方式给予消费者优惠。

#### 1.3.1 减
在订单金额中减去部分金额，如满减，买立减，实付减

#### 1.3.2 折
订单金额或者商品单价打个折扣。如满188打8折，第二件半价。

折其实也是减的一种特殊情况，做文本串分析时当两种情况

#### 1.3.3 送/赠
订单中赠送，或者订单完成后再赠送。如买1送1，买奶粉送奶瓶，买奶粉送京券

#### 1.3.4 换购
满99元即可加1元换购超值礼品

### 1.4 回馈内容
#### 1.4.1 现金
- 满减、满折就是减了现金

#### 1.4.2 可折算成现金几无使用限制的卡/券/积分
- 赠送天猫积分、集分宝也等于赠送现金
- 京券、京东积分也等于现金

#### 1.4.3 同主体商品
这条是指，赠送的商品与消费者购买的商品是同一个商品（可能保质期和生产批次略有不同，但总体上价值是一样的）

如一号店的德运全脂牛奶，买一升，赠一升，属于赠送同主体的商品。

#### 1.4.4 其它小赠品
如买鞋送袜子，买奶粉送奶粉勺。

把同主体商品拿出来单独说，和其它小赠品区分开，是因为同主体商品有利于计算实际到手价，德运全指牛奶买1送1，就等于是5折了，但如果买1升德运牛奶送5克奥利奥饼干，就不方便衡量饼干的价值进而计算到手价。

#### 1.4.5 不可折算成现金的卡/券/积分
- 送有限制条件的满减券、折扣券
- 送一号店积分
- 送淘金币
- 送航空公司里程等等

这类回馈有的价值较高（如有限制条件的券），有的如同鸡肋（如淘金币、一号店积分）不好统一衡量价值，也不能拿来参与到手价计算


### 1.5 是否有限制
是否有限制也影响到手价的计算

#### 1.5.1 有限制
- 满150减15，每个订单仅限使用一次
- 买1送1，每个收货地址仅限5件
- 实付200再返10元，最高返200元

#### 1.5.2 无限制
这个不多解释了

## 2 常用优惠规则
上述5个因素，排列组合最多超过200种，但考虑到有些组合不可能存在，如“回馈内容”中的两种“赠品”只可能和“优惠方式”中的“送赠”组合，而不可能和“折、减”组合，实际常用的优惠方式约为几十种（有无限制我就不一一罗列了，读者朋友自行把下面优惠规则总数乘以二）：

### 2.1 减折类（6种）
满折类的优惠条件主要是满N件和满N元，一般不会跟“实付xx元”搭配：

- 买立减（买一件）
- 买立折（买一件）
- 满N件减x元 
- 满N件打x折
- 满N元减x元
- 满N元打x折

#### 2.2 送（可折算现金）卡/券/积分、不可折算现金的卡/券/积分、其它小赠品（12种）
- 买即送（买一件）
- 满N件送xx
- 满N元送xx
- 实付N元送xx

在有的促销文案里，送虚拟卡券积分也叫满返。

以上四种场景乘以赠送的三种东西，就是12种。

#### 2.3 换购（4种）
- 买此商品即享换购资格
- 满N件即享换购资格
- 满N元即享换购资格
- 实付N元即享换购资格

#### 2.4 送同主体商品（3种）
- 买N送M
- 满N元再送M件
- 实付N元再送M件