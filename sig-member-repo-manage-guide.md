## SIG组信息维护指导文档

> 本文档是一个指导文档，旨在帮助社区参与者理解如何查询/维护SIG组的相关数据\
> **SIG组**这一概念可参考 [Readme](./sigs/README.md)\
> SIG组的相关数据存储在代码托管平台上，以代码仓库的形式归档维护


### SIG组信息的代码仓库结构


```yaml

opengauss/tc
|   architecture.png
|   CONTRIBUTING.md
|   gauss_relationship.md
|   gauss_relationship.yaml
|   LICENSE
|   maillist_mapping.yaml
|   OWNERS
|   README.en.md
|   README.md
|   repos.yaml
|   sig-member-repo-manage-guide.md
|   sigs.yaml
|   
+---.gitee
|       
+---repos
|   |   README.md
|   |   
|   \---opengauss
|       \---openGauss-server
|               OM.yaml
|               Tools.yaml
|               
\---sigs                      # SIG组数据的归档目录
    |   README.en.md          # SIG组的英文介绍文档
    |   README.md             # SIG组的中文介绍文档
    |   
    +---Connectors            # 对应 Connectors SIG 组
    |   |   OWNERS            # Connectors SIG 的 maintainers 和 committers
    |   |   README.md
    |   |   sig-info.yaml     # Connectors SIG 的 maintainers 和 committers、及其管理的仓库信息
    |   |                     # 当只存在sig-info.yaml文件时，以sig-info.yaml为准
    |   |                     # 当OWNERS和sig-info.yaml文件都存在时，以sig-info.yaml为准
    |   |   
    |   \---opengauss         # 此文件夹对应 Connectors SIG 管理的组织
    |       \---i             # 仓库按首字母归类管理
    |       |    infra.yaml   # 一个代码仓一个yaml文件
    |       \---o
    |       |    openGauss-connector-jdbc.yaml
    |       |    openGauss-sqlarchemy.yaml
    |               
    +---...                   # 省略s剩余的SIG组    
```

在这个目录，我们举了一个`Connectors` SIG组的案例。

在这个SIG组，我们需要关注以下三类文件：

1. OWNERS文件展示SIG组管理人员信息，不过我们不再推荐这种方式维护SIG组管理人员信息， 而是使用sig-info.yaml文件进行记录，详见：*如何维护 sig-info 的 YAML 文件* 章节
   
2. 同时对于SIG组的代码仓，我们也会建一个YAML文件进行描述，并以代码仓首字母作为文件夹进行分类。上例中，infra代码仓即放在了 `i`文件夹，描述内容便在`infra.yaml`文件，详见： `如何维护代码仓 YAML 文件` 章节
   
3. 社区可能存在一个代码仓被多个SIG组托管。当我们在查看这类代码仓是由哪些人托管，需要去各个SIG组查看相应的sig-info.yaml文件，显然这种方式是不明智的。 为了方便查看，我们在根目录建了`repo`文件夹，存放这一类代码仓的描述文件。当然这个文件不需要管理员手动更改，我们会通过机器人自动从SIG目录下的代码仓
   描述文件读取。关于如何解读该文件，我们将在 `关于一个代码仓被多个 SIG 组管理` 进行详细介绍

----

# 如何维护 sig-info 的 YAML 文件

在 openGauss 开源社区，我们使用 YAML 文件管理各个专项兴趣小组（SIG）成员和代码仓的映射关系。为了确保信息的准确性与一致性，维护这些 YAML 文件是每个 SIG 成员的共同责任。本章节将帮助您了解如何参与到 YAML 文件的维护中。

## 1. 文件结构与内容概述

每个 SIG 都有一个对应的 YAML 文件（例如：上述目录结构中，SIG/Connectors 下的 sig-info.yaml 文件），文件中包含以下几个主要部分：

- **name**: SIG 的名称
- **description**: SIG 的描述，简要说明该 SIG 负责的领域或主题
- **mailing_list**: SIG 的邮件列表
- **meeting_url**: SIG 定期会议的链接（如果有）
- **mature_level**: SIG 的成熟度，分为 `startup`、`mature` 等
- **maintainers**: SIG 的维护人员列表，包含 Gitee ID、姓名、所属组织、邮箱等信息
- **repositories**: SIG 管理的代码仓，包含代码仓名称和对应的提交人员（Committers）

对于`repositories`字段：
- **repo**: 代码仓列表。
- **committers**: 提交人员信息

例如：
```yaml
name: Connectors
description: The Connectors team is Responsible for the planning, development and maintenance of database drivers
mailing_list: connectors@opengauss.org
meeting_url: NA
mature_level: startup
maintainers:
  - id: pike*****
    name: tian*****
    organization: huawei
    email: tian*****@huawei.com
  - id: jus*****
    name: zho*****
    organization: huawei
    email: zb.*****@huawei.com
  - ...
repositories:
  - repo:
      - openGauss-server
      - openGauss-third_party
    committers:
      - id: pike*****
        name: tian*****
        email: tian*****@huawei.com
      - id: trave*****
        organization: enm*****
        name: a*****
        email: bin.*****@enmotech.com
      - ...
  - repo:
    - opengauss/A-Tune
    - opengauss/A-Tune-UI11111
    - opengauss/A-Tune-Collector
    - opengauss/prefetch_tuning
```
这是一个比较典型的例子。从这个例子不难发现:
1. 一个SIG组的`maintainers`可以是多人
2. `repositories`下的代码仓可以挂多个成员
3. `repositories`下的代码仓可以不挂成员，这些代码仓默认由`maintainers`共同管理

## 2. 角色与权限说明
从上例我们不难看出，在一个SIG组一共有两个角色，分别是`maintainers`和`committers`

1. `maintainers`是本SIG组最高权限的管理人员，对于本SIG组新增`maintainer`或者`committers`、代码仓PR（包括本SIG组无`committers`看管的代码仓）
   的合入等操作都有着提出或者审批的权限
   
2. 有时候一个SIG组会有多个代码仓，而仅靠`maintainers`是无法及时管理这么多仓库的，于是我们将SIG组下代码仓PR合入的权限下发给`committers`成员，将SIG组下的代码仓
   划分成多个小组，小组内的代码仓由这个小组内的`committers`成员进行管理；而对于一些代码仓，没有分配任何`committers`，那么将由本SIG组`maintainers`管理


## 3. sig-info 信息的维护
有时我们需要更新SIG组成员或代码仓信息，当然任何人都有权限提交修改的PR，但是审批权限仅本SIG组的`maintainers`才有。如需增改SIG组成员，还需要征得到被增改的组员的同意。
我们还会通过机器人做一系列的检查，譬如修改的代码仓社区是否存在，修改的成员id是否真实有效。最后，还需管理本代码仓的管理人员同意，提交的修改PR才会被合入，修改才会生效。

---

# 如何维护代码仓 YAML 文件
在 openGauss 开源社区，我们使用 YAML 文件管理SIG组下的所有代码仓，并在YAML文件对代码仓进行了描述、并进行文件级别的权限控制，在文件夹。例如openGauss社区Connectors SIG组的infra代码仓，
我们在 *./sigs/Connectors/opengauss/i* 目录下建了描述文件infra.yaml

## 1. 文件结构与内容概述

每个代码仓都有一个YAML文件对本代码仓进行描述，YAML文件主要有如下字段：

- **name**: 代码仓名称
- **description**: 代码仓描述
- **branches**:  展示代码仓所有分支及其类型\
   **name**:  分支名\
   **type**:  分支类型，如 protected、public
- **type**: 代码仓类型
- **files**: 代码仓按照文件进行权限划分

其中`files`有如下字段：
- **file**: 代码仓文件，列表
- **owner**: 成员信息

例如：
```yaml
name: openGauss-connector-jdbc
description: openGauss jdbc connector
branches:
  - name: master
    type: protected
type: public
files:
  - file:
    - openGauss-server/liteom
    - openGauss-server/liteom/upgrade_common.sh
    - ...
    owner:
    - id: d*****
      organizaiton: huawei
      name: cao*****
      email: cao*****@huawei.com
    - id: xio*****
      organizaiton: huawei
      name: yao*****
      email: xiong*****@yeah.net
  - file:
    ...
```

从上例我们可以看到，本YAML文件通过更细颗粒度权限的划分，使`owner`对代码仓以文件夹或者文件进行权限管控。上一章节 sig-info YAML文件`repositories`字段是以代码仓为维度对`committers`赋权，
本章节则对上一规则做了补充。对于已经进行权限划分文件和目录，我们严格按照本YAML文件进行权限管理；对于未写入本YAML的目录或文件，由`committers`进行权限管控。


## 2. YAML 信息的维护
有时我们需要更新修改代码仓信息或者文件权限，在修改者提交PR后（任何人都可以提交PR），但是审批权限仅限于本SIG组的`maintainers`或者本代码仓的`committers`。如果修改了人员信息，仍旧需要征得被修改人的同意。
我们还会通过机器人做一系列的检查，譬如修改的代码仓社区是否存在，修改的成员id是否真实有效。最后，同样得还需管理本代码仓的管理人员同意，提交的修改PR才会被合入，修改才会生效。

---
# 关于一个代码仓被多个 SIG 组管理
原则上我们只允许一个代码仓被一个SIG组管理，但有时也存在一个代码仓被多个SIG组管理且无法避免。社区管理人员在查看这个代码仓权限管理内容时，还需要去每个SIG组找到对应的代码仓，
然后再对所有包括该代码仓的YAML文件的信息整合。显然，这种方式不够直观，且对社区管理人员造成了不必要的工作量。因为我们在`repos/opengauss`目录下单独对这类代码仓的权限信息
进行了展示，该文件仅供展示，不支持修改。

## 1. 文件结构与内容展示


|文件或目录 | 所属SIG组 | 所属OWNERS id|
|----|----|----|
|openGauss-server/liteom |OM | ds*** <br> xia**** <br> ... |
| openGauss-server/liteom/upgrade_common.sh |OM | ds*** <br> xia**** <br> ...  |
| ... |.. | ... |
|  openGauss-server/contrib |Tools | xs*** |
| ... |.. | ... |



# 总结

维护 SIG 的 YAML 文件是 openGauss 社区的重要工作之一，确保文件内容准确、及时更新有助于社区的顺利运行。如果您有任何疑问或需要帮助，请随时联系相关 SIG 成员或社区的管理人员。
