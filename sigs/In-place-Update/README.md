# In-place Update
In-place Update，中文意思为：原地更新，是openGauss内核新增的一种存储模式。openGauss内核当前使用的行引擎采用的是Append Update（追加更新）模式，该模式在INSERT，DELETE，HOT UPDATE（页面内更新）的场景下，有较好的表现。但是，对于非HOT UPDATE场景，垃圾回收不够高效。 

In-place Update存储模式提供“原地更新”能力，主要思路是将最新版本的“有效数据”和历史版本的“垃圾数据”分离存储。将最新版本的“有效数据”存储在数据页面上，而单独开辟一段UNDO空间，用于统一管理历史版本的“垃圾数据”，因此数据空间不会由于频繁更新而膨胀，垃圾回收效率更高。通过NUMA-Ware的UNDO子系统设计，使得UNDO子系统在多核平台上高效扩展。同时通过对元组和数据页面结构的重新设计，减少存储空间的占用。采用多版本索引技术，解决索引膨胀问题，彻底去除autovacuum机制，提升存储空间的回收复用效率。

在此基础上，openGauss融合存储引擎提供了一套数据访问抽象。基于这层抽象，openGauss内核统一架构支持多种存储模式，让openGauss内核可以适应更多的业务场景和工作负载。与此同时，也将在In-place Update 存储模式上构筑闪回、分区表、全局索引以及逻辑复制等企业级能力。


# 组织会议

- 公开的会议时间：北京时间 每双周二 17:00-18:00

# 成员

### Maintainer列表
- 王江[@wang-jingle](https://gitee.com/wang-jingle)，*wangjiang16@huawei.com*
- 李强[@powerqy](https://gitee.com/powerqy)，*powerqy@gmail.com*
- 吴岳川[@wuyuechuan](https://gitee.com/wuyuechuan)，*wuych9@mail2.sysu.edu.cn*

### Committer列表
- 杨维强[@yangweiqiang](https://gitee.com/yangweiqiang)，*wqyang@cmbchina.com*
- 孙腾腾[@tengtengsun](https://gitee.com/tengtengsun)，*suntengteng@cmbchina.com*
- 周伟[@pascal_zhou](https://gitee.com/pascal_zhou)，*pascal_zhou@cmbchina.com*
- 吴斯亮[@wu-siliang](https://gitee.com/wu-siliang)，*wusiliang@cmbchina.com*
- 林科旭[@kexulin](https://gitee.com/kexulin)，*linkexu66@outlook.com*
- Sherman Lau[@ming_opengauss](https://gitee.com/ming_opengauss) *sherman.lau@huawei.com*
- Ronen Grosman[@roneng](https://gitee.com/roneng) *ronen.grosman@huawei.com*


# 联系方式

- [邮件列表](https://mailweb.opengauss.org/postorius/lists/inplaceupdate.opengauss.org/)


# 仓库清单

仓库地址：
- https://gitee.com/opengauss/openGauss-server
- https://gitee.com/opengauss/openGauss-third_party

