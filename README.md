> #### 作者主页：[舒克日记](https://blog.csdn.net/cativen)
>
>  简介：Java领域优质创作者、Java项目、学习资料、技术互助
>
> <b><font color=red>文中获取源码</font></b>

# 项目介绍

基于SpringBoot+Vue实现的超市管理系统采用前后端分离的架构方式，系统分为管理员、员工两种角色，实现了销售管理、人事管理、个人中心、库存管理、会员管理、系统管理、商品管理等功能模块

### 技术选型

开发工具：idea2020.3+Webstorm2020.3

运行环境：jdk1.8+maven3.6.0+MySQL5.7+nodejs14.21.3+redis

服务端技术：Springboot+Mybatis-Plus+redis

前端技术：html+css+Vue+axios+Element-UI

# 运行指导

idea导入源码空间站顶目教程说明(Vindows版)-ssm篇：

http://mtw.so/5MHvZq

源码看好后直接在网站付款下单即可，付款成功会自动弹出百度网盘链接，网站地址：[http://www.codegym.top](http://www.codegym.top/)。

其它问题请关注公众号：**IT小舟**,关注后发送消息即可，都会给您回复的。若没有及时回复请耐心等待，通常当天会有回复

# 运行截图

用户登录页 ![微信截图20240920232232](https://img-blog.csdnimg.cn/img_convert/665030b72e3eed4569f09384baca554f.png) 

主页

![微信截图20240920232325](https://img-blog.csdnimg.cn/img_convert/5e643b1a6eb3c1e0784b78f88efe937f.png)

销售主页

![微信截图20240920232331](https://img-blog.csdnimg.cn/img_convert/3357c938d446179609245fa8822930a9.png)

销售管理

![微信截图20240920232336](https://img-blog.csdnimg.cn/img_convert/07ceac10aee66170483668962774e5b8.png)

![微信截图20240920232341](https://img-blog.csdnimg.cn/img_convert/11b310a7ba90b0fdba2f2e3c636c95c1.png)

人事管理

![微信截图20240920232347](https://img-blog.csdnimg.cn/img_convert/1cdc4563a8c8556c28d84a534bcdcab2.png)

修改密码

![微信截图20240920232355](https://img-blog.csdnimg.cn/img_convert/dec92e3f8684222e83d8103a6ba177ba.png)

库存管理

![微信截图20240920232401](https://img-blog.csdnimg.cn/img_convert/d5f2c58a7271aca6783267ca4ba48ee2.png)

出库管理

![微信截图20240920232406](https://img-blog.csdnimg.cn/img_convert/e650967384ad0efcdf8b2bbb5b2464e5.png)

会员管理

![微信截图20240920232411](https://img-blog.csdnimg.cn/img_convert/4a8f3a55b31b8cfba1b58ece032616e0.png)

系统管理

![微信截图20240920232418](https://img-blog.csdnimg.cn/img_convert/4f6ece900125e608a1d9a6d6570b9e8c.png)

分类管理

![微信截图20240920232436](https://img-blog.csdnimg.cn/img_convert/157aa932a96803c702a6f8263056b374.png)

商品管理

![微信截图20240920232439](https://img-blog.csdnimg.cn/img_convert/325af181ac6537ecc1d6e894388c74f5.png)

积分管理

![微信截图20240920232445](https://img-blog.csdnimg.cn/img_convert/13079ed0a58dd978d5ec80f0efa02b74.png)

销售统计

![微信截图20240920232448](https://img-blog.csdnimg.cn/img_convert/a9d457294fabfb04999613016815d0aa.png)

###

### 账号地址及其他说明

1、地址说明

登录页:[http://localhost:9292/](http://localhost:9292/)

2、账号说明

管理员：13333333333/123456


### 代码

```
    public UserTenancyDO saveUserLoginLog(UserDO userDO) {
        UserTenancyDO userTenancyDO = buildUserLoginLogDO(userDO);
        if (userTenancyDO == null) {
            throw new BizException("401", "用户绑定的租户不可用");
        }
        UserLoginLogDO userLoginLogDO = new UserLoginLogDO();
        userLoginLogDO.setUserId(userDO.getId());
        userLoginLogDO.setTenantId(userTenancyDO.getTenantId());
        userLoginLogDO.setUserId(userDO.getId());
        userLoginLogDO.setCreatorId(userDO.getId());
        userLoginLogDO.setCreateTime(new Date().getTime());
        userLoginLogDO.setLoginType("login");
        userLoginLogMapper.insert(userLoginLogDO);
        return userTenancyDO;
    }
```
