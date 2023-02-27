# FlinkRealTimeDataWarehouse
实时数仓学习过程中代码记录

## 1.实时数仓分层
**计算框架：** Flink

**存储框架：** Kafak （可以实时读取&实时写入）

**ODS:** 原始数据层【Kafka】每过来一条数据，读取加工并处理；

**DIM:** 公共维度层【Hbase】事实表通过主键获取一条维表数据（永久存储，主键查询）

**DWD:** 数据明细层【Kafka】每过来一条数据，读取分组累加处理；

**DWS:** 汇总数据层【ClickHouse】每过来一条数据，读取重新分组累加处理；

**ADS:** 数据应用层【不落盘，接口模块查询ClickHouse的Sql】读取最终结果展示