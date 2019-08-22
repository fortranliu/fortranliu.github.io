---
layout: post
title:  "使用diff命令比较两个文件夹下文件的差异"
date:   2019-06-21 10:22
categories: 技术文档
tags: linux
---

#使用diff命令比较两个文件夹下文件的差异

```shell
diff -r -q dev/ ../code_updated/dev/
```

输出为哪些文件有差异：

```
Only in dev/: .DS_Store
Files dev/acc_pre.f90 and ../code_updated/dev/acc_pre.f90 differ
Files dev/acc_vsg.f90 and ../code_updated/dev/acc_vsg.f90 differ
Files dev/droplet_monitr.f90 and ../code_updated/dev/droplet_monitr.f90 differ
Files dev/droplet_wflow.f90 and ../code_updated/dev/droplet_wflow.f90 differ
Files dev/ice_acc.f90 and ../code_updated/dev/ice_acc.f90 differ
Files dev/ice_acc_2nd.f90 and ../code_updated/dev/ice_acc_2nd.f90 differ
Files dev/ice_acc_3rd.f90 and ../code_updated/dev/ice_acc_3rd.f90 differ
Files dev/ice_acc_3rd_3d.f90 and ../code_updated/dev/ice_acc_3rd_3d.f90 differ
Files dev/ice_lusgs.f90 and ../code_updated/dev/ice_lusgs.f90 differ
Files dev/ice_lusgs_non_conservation.f90 and ../code_updated/dev/ice_lusgs_non_conservation.f90 differ
Files dev/ice_output.f90 and ../code_updated/dev/ice_output.f90 differ
Files dev/ice_rk.f90 and ../code_updated/dev/ice_rk.f90 differ
Files dev/ice_rk_a.f95 and ../code_updated/dev/ice_rk_a.f95 differ
Files dev/ice_rk_t.f90 and ../code_updated/dev/ice_rk_t.f90 differ
Files dev/ice_split.f90 and ../code_updated/dev/ice_split.f90 differ
Files dev/para_wall_surf.f90 and ../code_updated/dev/para_wall_surf.f90 differ
Files dev/rhs_wflow.f90 and ../code_updated/dev/rhs_wflow.f90 differ
Only in dev/: tn_bc.f90
Only in dev/: tn_lusgs.f90
Only in dev/: tn_monitr.f90
Only in dev/: tn_wflow.f90
Only in dev/: tndqmom.f90
Files dev/usr_ice.f90 and ../code_updated/dev/usr_ice.f90 differ
```

继续对每个文件进行比较，输出对应文件差异所在：

```shell
diff dev/usr_ice.f90 ../code_updated/dev/usr_ice.f90 -y --suppress-common-lines -W 140
```

此时将以左右两列显示两个文件的差异。

