表结构

bmi_basic_library

bmi_basic_library_version

bmi_tag

bmi_basic_library_version_tag

列表展示实现思路

查bmi_basic_library id,library_name,以及bmi_basic_library_version所需要的字段（例如功能备注等） left join

bmi_basic_library_version on bmi_basic_library.latest_version_id

=bmi_basic_library_version.id

得到的结果

库Id 编号 基础库 最新版本号 功能 标签 版本id 备注 os必备 等的list

















循环上面的list

标签字段展示

根据versionid 去查标签字段的列表

查 bmi_basic_library_version_tag tag_id left join bmi_tag on

bmi_basic_library_version_tag.id=bmi_tag.id

当versin_id=latest_version_id     

```sql
SELECTE  *from 
```

