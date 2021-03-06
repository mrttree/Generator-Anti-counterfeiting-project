# 母线防伪溯源项目
## 项目由来
在数据中心建设过程中，有一种叫做母线的重要设备，母线是指用高导电率的铜（铜排）、铝质材料制成的，用以传输电能，具有汇集和分配电力能力的产品，是电站或变电站输送电能用的总导线。母线系统的建设所花费可占机房建设的五分之一以上，而母线产品的品质是否达标、建设过程中的安装是否规范，对使用单位是十分重要的。任何一环出现问题，都可能导致母线爆炸。因此，对母线的防伪、溯源以及建设过程中的监察就显得十分重要。
本项目即以此为背景，根据区块链技术实现相关的功能。
## 项目简介
本项目利用Hyperledger 底层通过Fabric来组建相应的系统，通过ChainCode来实现母线上下游各个单位生产数据的写入、查询。

同时利用了go语言的web框架beego来搭建前后端的联系。本系统大体思路即：
1. 前端通过表单提交数据来确定功能，以及相关数据传入beego路由
2. beego路由通过自身功能将表单数据序列化，发送至Fabric-SDK的功能函数，由chaincode将其传入区块链。
3. 区块链中的数据返回后，经过chaincode传出至beego路由，而后表现在前端

## 后端架构
![channel示意图](https://github.com/mrttree/Generator-Anti-counterfeiting-project/channel示意图.png)
* 涉及的查询功能主要有：
  1. 母线零件的产品质量认证状态查询
  2. 母线产品质量认证进行查询
  3. 母线安装过程中的安装质量查询
  4. 物流状态查询
* 涉及的写入功能主要有：
  1. 母线零件生产单位及母线单位写入产品基本状态
  2. 物流单位写入物流状态
  3. 质检单位写入母线零件、母线、安装过程质量监察情况
  4. 建设单位写入物流接收时母线状态
  5. 使用单位写入验收情况
* 涉及的相关单位有：
  1. 使用单位
  2. 数据机房建设单位（即母线安装单位）
  3. 母线生产单位（即工厂）
  4. 母线零件生产单位
  5. 质量监察单位（包括工厂质检单位、建设过程监理单位以及政府相关质量监察单位等）
  6. 运输单位
  7. 保险公司
## 运行方式
linux系统在完成相关环境配置后直接运行`./restart.sh`

部分模块因业务隔离不清除，因此未能够完成，后期持续更新，本项目以安装单位业务为主。

 
