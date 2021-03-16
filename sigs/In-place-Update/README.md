# In-place Update
当前，为了支持MVCC，openGauss将旧的元组放在堆页面上，并且在没有快照引用这些旧数据时依靠Vacuum机制清理旧的元组。当前这种存储方式有以下两个问题：

- 堆页面存储了旧的元组, 浪费空间资源
- vacuum会进入不同页面进行清理操作, 带来性能和IO的问题

In-place Update引擎旨在通过原地更新解决数据和索引膨胀问题, 同时摆脱对Vacuum的依赖。


# 组织会议
- 公开的会议时间：北京时间，每周四下午，16点30~17点30

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

