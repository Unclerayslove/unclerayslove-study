# 秒杀系统

## 1.秒杀系统

### 1.1秒杀场景

- 电商抢购限量商品
- 卖周董（某某）演唱会/科比中国行的门票
- 火车票抢票 12306

### 1.2为什么要做个系统

接受高并发访问和下单的考验；需要一套完整的流程保护措施

- 严格防止超卖：不能超库存
- 防止黑产
- 保证用户体验：高并发下，网页打不开，支付不成功，购物车进不去

### 1.3保护措施有哪些

- ==乐观锁防止超卖==
- 令牌桶限流
- Redis缓存
- 消息队列异步处理订单



## 2.防止超卖

### 2.1数据库表

~~~sql
-- ----------------------------
-- Table structure for stock
-- ----------------------------
DROP TABLE IF EXISTS `stock`;
CREATE TABLE `stock` (
	`id` INT(11) UNSIGNED NOT NULL AUTO_INCREMENT,
	`name` VARCHAR(50) NOT NULL DEFAULT '' COMMENT '名称',
	`count` INT(11) NOT NULL COMMENT '库存',
	`sale` INT(11) NOT NULL COMMENT '已售',
	`version` INT(11) NOT NULL COMMENT '乐观锁，版本号',
	PRIMARY KEY(`id`)
)ENGINE=INNODB DEFAULT CHARSET=utf8;

-- -------------------------------
-- Table structure for stock_order
-- -------------------------------
DROP TABLE IF EXISTS `stock_order`;
CREATE TABLE `stock_order` (
	`id` INT(11) UNSIGNED NOT NULL AUTO_INCREMENT,
	`sid` INT(11) NOT NULL COMMENT '库存ID',
	`name` VARCHAR(30) NOT NULL DEFAULT '' COMMENT '商品名称',
	`create_time` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP COMMENT '创建时间',
	PRIMARY KEY(`id`)
)ENGINE=INNODB DEFAULT CHARSET=utf8;
~~~

