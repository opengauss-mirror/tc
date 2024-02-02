# 专项兴趣小组（Special Interest Groups，简称SIG）

SIG工作目标为针对特定的一个或多个主题建立社区项目，并推动各项目输出交付成果。各SIG的成立都需经TC决策，并建立治理规则，明确规定该SIG的职责，内容应包括但不限于其职责范围、沟通方式、维护人员任免（Maintainer、Committer等）、业务范围（代码库、目录等）等信息。同时，各SIG内部沟通信息必须在openGauss社区范围内公开，以确保其他SIG的社区成员可以找到讨论、会议和决策等相关记录。

## SIG组运作规则

SIG组应该在gitee建立自己的主页，包含必需的内容，SIG组可以根据实际情况定制适合自己的规则，模板如下：


### xx SIG组主要负责事项

xx SIG的主要责任是负责openGauss社区xx模块的开发和维护...


### xx SIG组会议

公开的视频会议时间：北京时间双周X下午，14:00~16:00，请订阅https://opengauss.org/zh/community/onlineCommunication/ ，以获取相关会议通知

### 会议纪要归档

xx SIG历次会议纪要均做归档，详情请查询历史会议纪要归档etherpad

### 成员

**Maintainer：**
| 姓名| GiteeID           | 邮件地址  |
| :-------------: |:--------:| :-----|
|xx | [@Cyj10727](https://gitee.com/Cyj10727)| jieky.cai@huawei.com|
|xx |[@wang-jingle](https://gitee.com/wang-jingle)|wangjiang16@huawei.com|
|xx  | [@flowill](https://gitee.com/flowill)|  f.fengwei@huawei.com|

**Commiter:**
| 姓名| GiteeID           | 邮件地址  |
| :-------------: |:--------:| :-----|
|xx| [@xiong_xjun](https://gitee.com/xiong_xjun) | xiong_xiaojun@yeah.net|
|xx| [@willloong](https://gitee.com/willloong) | 1259931895@qq.com|
|xx|[@llzx373](https://gitee.com/llzx373) | llzx373@hotmail.com|
|xx|[@zhang_xubo](https://gitee.com/zhang_xubo) | 2578876417@qq.com|

### Maintainer职责：
- 负责看护SIG项目架构设计、保证SIG项目架构代码质量，拥有SIG项目的代码检视和合入代码权限，定期组织、召集社区SIG项目组例会，代表SIG参加技术委员会组织的活动和会议。

### xx SIG Maintainer竞选流程及原则
由maintainer和SIG成员提名（个人先向以上成员提出申请），xx成员提名（个人先向以上成员提出申请），xx sig评审
- 作为Committer至少3个月，自荐或者由现有Maintainer、TC提名，并且没有其他TC和Maintainer反对。
- 个人或者所属团队，连续6个月以上对社区有持续贡献，且至少有一个特性为版本关键特性（存在于release notes）
- 持续参加xx sig例会，近6个月与会率70%以上
- 对版本xx sig管理有突出贡献（自我举证）

### xx SIG Maintianer变更流程及原则
主动提出或者xx sig提出，在sig评审
- 主动退出或者连续3次以上无故不参与xx SIG例会
- 个人或者所属团队，连续6个月无社区贡献

### Committer职责：
- 负责代码检视、保证SIG项目代码质量，拥有SIG项目的代码检视和合入代码权限，定期参加Maintainer组织的SIG项目组例会。

### xx SIG Committer竞选流程及原则
由maintainer和SIG成员提名（个人先向以上成员提出申请），xx sig评审
- 作为openGauss社区Contributor至少3个月，由Maintainer或Committer提名，并且没有其他Maintainer和Committer反对。
- 需要独立完成至少一个功能或修复一个重大Bug
- 持续参加xx sig例会，近6个月与会率70%以上
- 对版本xx sig有突出贡献（自我举证）

### xx SIG Committer变更流程及原则
主动提出或者xx sig提出，在sig评审
- 主动退出或者连续3次以上无故不参与xx SIG例会
- 连续6个月无社区贡献

### 联系方式
| SIG ID| Gitee 访问链接           | 邮件地址  |
| :-------------: |:--------:| :-----|
|xx SIG|[xx](https://gitee.com/opengauss/release-management/)|xx|



### 项目清单

Repository地址：https://gitee.com/opengauss/release-management
...



## 现有SIG组
* 各SIG成员应包含一至两名Maintainer，多名Committer及Contributor。openGauss社区SIG包括：

    | SIG名称 | 职责范围 |
    | :------- | :--------------- |
    | SQLEngine | 负责openGauss社区SQL引擎的开发和维护。 |
    | StorageEngine | 负责openGauss社区存储引擎的开发和维护。 |
    | Connectors | 负责openGauss社区Connectors的开发和维护。 |
    | Tools | 负责openGauss社区工具的开发和维护。 |
    | Docs | 负责openGauss社区文档的开发和维护。 |
    | Infra | 负责openGauss社区基础设施的开发和维护。 |
    | Security | 负责openGauss社区安全的开发和维护。 |
    | OM | 负责openGauss社区部署和维护。 |
    | AI | 负责openGauss社区AI的开发和维护。 |
    | IoT | 负责openGauss社区IoT能力的开发和维护。 |
    | In-place Update | 负责openGauss社区in-place update的开发和维护。 |
    | GIS | 负责openGauss社区地理信息系统的开发和维护。 |
    | CloudNative | 负责openGauss社区云原生方向的开发和维护。 |
    | SecurityTechnology | 负责openGauss社区数据库安全技术的开发和维护。 |
    | Certification | 负责openGauss认证流程、测试套件的定义和开发。 |
    | Plugin | 负责openGauss插件机制的规划、管理、开发等。 |
    | Blockchain | 探讨区块链的业务场景，研究区块链的核心技术问题。 |
    | DCF | 负责openGauss社区分布式一致性框架DCF的开发和维护。 |
    | QA | 负责openGauss社区版本质量相关的开发和维护。 |
    | Graph | 负责openGauss社区统一存储和查询的知识图谱数据管理功能。 |
    | ReleaseManagement | 社区协同各SIG maintainer，规划openGauss社区版本的发布工作，为最终的竞争力目标达成负责. |
    | CM | 负责openGauss社区公共组件，包括集群管理、共享存储、分布式一致性框架、分布式配置中心等的开发和维护。 |
