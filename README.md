<h1 align ="center">Ambition平台后端通用Excel导出</h1>

## 一、概述

​		Excel导出是企业应用标配功能，在有查询的界面都会有导出的功能，导出一般都是excel文件，一般情况下，我们会开发两个接口，一个用来查询，一个用来导出，两个接口逻辑几乎一样，查询接口可能有分页功能，可以指定页码查询指定页码的数据，导出是先把所有符合条件的数据查询出来再导出，除了这个区别外，两个接口所有的业务逻辑应该保持一致，才能做到用户导出的数据就是用户在系统中查询出来的数据。既然逻辑都一样，只有页码的差别，如果有方案可以做到一个接口里是最好的，平台excel导出方案就是基于这个目标设计。

## 二、依赖

​		项目如果添加了fone的依赖就无需再额外添加依赖，fone依赖如下

```
<parent>
     <artifactId>fone-sdk-parent</artifactId>
     <groupId>com.fuyaogroup</groupId>
     <version>{fone-version}</version>
 </parent>
```

## 三、使用

### 1、接口改造

原查询的接口controller定义如下：

![image-20210429134026127](https://gitee.com/mars-gzj/picBed/raw/master/20210429134033.png)

修改为：

![image-20210429134441914](https://gitee.com/mars-gzj/picBed/raw/master/20210429134441.png)

### 2、说明

- 方法增加参数`ServletWebRequest request`

  导入包`import org.springframework.web.context.request.ServletWebRequest;`

- `@GetMapping`增加导出请求

  增加`原有请求路径/export`

- 增加注解`@Export`

  1. `value:`导出的文件名，如果名称没有后缀会自动添加`.xls`的后缀，支持导出`xls`和`xlsx`
  2. `classPath:`导出实体的类全路径

### 3、实体类属性注解

​		使用`@ExcelColumn`注解可以配置实体类导出哪些属性，使用方式如：

![image-20210430160620480](https://gitee.com/mars-gzj/picBed/raw/master/20210430160620.png)

​		使用`getDeclaredFields`方法获取实体类的属性，如要导出父类的属性，则需要在子类中重写父属性，并加上`@ExcelColumn`注解。

## 四、导出

​		默认限制导出10万条数据，如需修改可以在`fone-gateway.yaml`中修改配置

```
exportExcel:
 maxCount: 100000
```

导出结果如下：

![image-20210430160733407](https://gitee.com/mars-gzj/picBed/raw/master/20210430160733.png)

​		标题需要到平台`系统管理-提示语维护`页面添加维护，格式：`label.实体类(首字母小写).属性名称`