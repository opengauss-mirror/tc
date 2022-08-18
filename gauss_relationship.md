# Configuration guide 
for gauss_relationship.yaml

## case1
Set some owners for the same files in gauss_relationship.yaml.
```yaml
# example
sigs:
- name: OM
  sig_label: sig/om
  sig_link: https://gitee.com/opengauss/tc/tree/master/sigs/OM
  files:
  - file:
    - openGauss-server/liteom
    - openGauss-server/liteom/upgrade_common.sh
    - openGauss-server/liteom/opengauss_lite.conf
    - openGauss-server/liteom/upgrade_config.sh
    - openGauss-server/liteom/install.sh
    - openGauss-server/liteom/uninstall.sh
    - openGauss-server/liteom/upgrade_GAUSSV5.sh
    - openGauss-server/liteom/upgrade_errorcode.sh
    owner:
    - gitee_id: someone # 测试用例1
      organizaiton: example
      name: fakename
      email: fake@fake.com
    - gitee_id: someone2 # 测试用例2
      organizaiton: example2
      name: fakename2
      email: fake2@fake.com
  repos:
  - repo:
    - openGauss-OM
    - openGauss-server
    owner:
```

## case2
Set some owners for the same repositories in gauss_relationship.yaml.
```yaml
# example
sigs:
- name: OM
  sig_label: sig/om
  sig_link: https://gitee.com/opengauss/tc/tree/master/sigs/OM
  files:
  - file:
    - openGauss-server/liteom
    - openGauss-server/liteom/upgrade_common.sh
    - openGauss-server/liteom/opengauss_lite.conf
    - openGauss-server/liteom/upgrade_config.sh
    - openGauss-server/liteom/install.sh
    - openGauss-server/liteom/uninstall.sh
    - openGauss-server/liteom/upgrade_GAUSSV5.sh
    - openGauss-server/liteom/upgrade_errorcode.sh
    owner:
  repos:
  - repo:
    - openGauss-OM
    - openGauss-server
    owner: 
    - gitee_id: someone # 测试用例1
      organizaiton: example
      name: fakename
      email: fake@fake.com
    - gitee_id: someone2 # 测试用例2
      organizaiton: example2
      name: fakename2
      email: fake2@fake.com
```

## case3
Set some owners for the different files in gauss_relationship.yaml.
```yaml
# example
sigs:
- name: OM
  sig_label: sig/om
  sig_link: https://gitee.com/opengauss/tc/tree/master/sigs/OM
  files:
  - file:
    - openGauss-server/liteom
    - openGauss-server/liteom/upgrade_common.sh
    - openGauss-server/liteom/opengauss_lite.conf
    - openGauss-server/liteom/upgrade_config.sh
    - openGauss-server/liteom/install.sh
    owner:
    - gitee_id: someone # 测试用例1
      organizaiton: example
      name: fakename
      email: fake@fake.com
  - file:
    - openGauss-server/liteom/uninstall.sh
    - openGauss-server/liteom/upgrade_GAUSSV5.sh
    - openGauss-server/liteom/upgrade_errorcode.sh
    owner:
    - gitee_id: someone2 # 测试用例2
      organizaiton: example2
      name: fakename2
      email: fake2@fake.com
  repos:
  - repo:
    - openGauss-OM
    - openGauss-server
    owner:
```

## case4
Set some owners for the different repositories in gauss_relationship.yaml.
```yaml
# example
sigs:
- name: OM
  sig_label: sig/om
  sig_link: https://gitee.com/opengauss/tc/tree/master/sigs/OM
  files:
  - file:
    - openGauss-server/liteom
    - openGauss-server/liteom/upgrade_common.sh
    - openGauss-server/liteom/opengauss_lite.conf
    - openGauss-server/liteom/upgrade_config.sh
    - openGauss-server/liteom/install.sh
    - openGauss-server/liteom/uninstall.sh
    - openGauss-server/liteom/upgrade_GAUSSV5.sh
    - openGauss-server/liteom/upgrade_errorcode.sh
    owner:
  repos:
  - repo:
    - openGauss-OM
    owner: 
    - gitee_id: someone # 测试用例1
      organizaiton: example
      name: fakename
      email: fake@fake.com
  - repo:
    - openGauss-server
    owner:
    - gitee_id: someone2 # 测试用例2
      organizaiton: example2
      name: fakename2
      email: fake2@fake.com
```

## case5
Just add some files or repositories information in gauss_relationship.yaml.
```yaml
# example
sigs:
- name: OM
  sig_label: sig/om
  sig_link: https://gitee.com/opengauss/tc/tree/master/sigs/OM
  files:
  - file:
    - openGauss-server/liteom
    - openGauss-server/liteom/upgrade_common.sh
    - openGauss-server/liteom/opengauss_lite.conf
    - openGauss-server/liteom/upgrade_config.sh
    - openGauss-server/liteom/install.sh
    - openGauss-server/liteom/uninstall.sh
    - openGauss-server/liteom/upgrade_GAUSSV5.sh
    - openGauss-server/liteom/upgrade_errorcode.sh
    - openGauss-server/xxx/xxx/fake.sh # 测试用例1
    - openGauss-server/xxx/xxx/fake2.sh # 测试用例2
    owner:
  repos:
  - repo:
    - openGauss-OM
    - openGauss-server
    - fakerepository # 测试用例3
    - fakerepository2 # 测试用例4
    owner:
```