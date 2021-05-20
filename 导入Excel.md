<h1 align ="center">Ambition平台后端通用Excel导入</h1>

## 一、概述

​		采用hutool工具来实现excel导入功能，支持导入`xls`和`xlsx`。

## 二、使用示例

### 1、后台代码

```
@ApiOperation("组织数据导入")
@PostMapping("/dataImport")
public Result dataImport(@RequestParam("file") MultipartFile multipartFile) throws IOException {
    List<Organization> list = ExcelImport.importExcel(multipartFile, Organization.class);

    list.forEach(System.out::println);
    return Result.success();
}
```

### 2、说明

- 导入包`import com.fuyaogroup.fone.common.base.importer.ExcelImport;`

- 导入excel列标题默认是实体类属性名称，如果有配置提示语，则标题可以修改为提示语。提示语需要到平台`系统管理-提示语维护`页面添加维护，格式：`label.实体类(首字母小写).属性名称`

  ![image-20210514161259355](https://gitee.com/mars-gzj/picBed/raw/master/20210514161306.png)

- 时间格式根据当前用户时区转换参考

  ```
  SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
  TimeZone timeZone = RequestHelper.getCurrentTimeZone();
  if (StringUtils.isEmpty(timeZone)){
      timeZone = TimeZone.getTimeZone("GMT+8:00");
  }
  sdf.setTimeZone(timeZone);
  Organization organization = list.get(0);
  Date t = organization.getUserDefinitionEnableDate();
  String str = sdf.format(t);
  System.out.println("str==" + str);
  SimpleDateFormat simpleDateFormat = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
  organization.setUserDefinitionEnableDate(simpleDateFormat.parse(str));
  System.out.println(organization);
  ```

  

  



