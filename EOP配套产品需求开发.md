# EOP配套产品需求开发

## EOP配套产品导入

### 1增加业务模型

后台管理页面增加业务模型`EOP配套产品` 

![image-20210328172519639](https://gitee.com/mars-gzj/picBed/raw/master/20210328172519.png)

增加模型

![image-20210328172705479](https://gitee.com/mars-gzj/picBed/raw/master/20210328172705.png)

### 2持久模型

增加持久模型`PM-EOP配套产品`

![image-20210328175035678](https://gitee.com/mars-gzj/picBed/raw/master/20210328175036.png)

增加表字段

![image-20210328175131481](https://gitee.com/mars-gzj/picBed/raw/master/20210328175131.png)

### 3表单模型

增加表单模型`FM-EOP配套产品`

![image-20210328180627602](https://gitee.com/mars-gzj/picBed/raw/master/20210328180627.png)

新增表单，自动关联添加的持久模型

![image-20210328180822210](https://gitee.com/mars-gzj/picBed/raw/master/20210328180822.png)

### 4视图模型

#### 4.1添加视图模型

增加视图模型`VM-EOP配套产品导入`

![image-20210328181227941](https://gitee.com/mars-gzj/picBed/raw/master/20210328181228.png)

添加视图，关联表单模型，视图类型选择`异步查询列表`（选择后双击退出）

![image-20210328181640586](https://gitee.com/mars-gzj/picBed/raw/master/20210328181640.png)

#### 4.2修改视图源码

修改视图源码，修复页面滚动条无法滚动

![image-20210328185349963](https://gitee.com/mars-gzj/picBed/raw/master/20210328185350.png)

将`setScroll(formId);`修改为`setScroll();`

#### 4.3发布视图模型

打开发布页面

![image-20210328181833364](https://gitee.com/mars-gzj/picBed/raw/master/20210328181833.png)

发布页面配置，发布到`仓库管理-库存管理`下

![image-20210328182445994](https://gitee.com/mars-gzj/picBed/raw/master/20210328182446.png)

### 5前台配置权限

#### 5.1添加角色

角色信息页面增加角色`EOP配套产品导入`

![image-20210328182927445](https://gitee.com/mars-gzj/picBed/raw/master/20210328182927.png)

#### 5.2分配权限

为新加的角色分配菜单`EOP配套产品导入`的访问权限

![image-20210328183223582](https://gitee.com/mars-gzj/picBed/raw/master/20210328183223.png)

#### 5.3用户增加角色

为账号132119添加角色`EOP配套产品导入`

![image-20210328183509657](https://gitee.com/mars-gzj/picBed/raw/master/20210328183509.png)

### 6前台访问

前台页面访问新加的菜单`EOP配套产品导入`

![image-20210328183856061](https://gitee.com/mars-gzj/picBed/raw/master/20210328183856.png)

### 7多语言配置

将上面页面中带问号的名称，添加多语言配置

![image-20210328184100845](https://gitee.com/mars-gzj/picBed/raw/master/20210328184100.png)

依次将页面上带问号的添加多语言配置，刷新页面后中文显示正常。