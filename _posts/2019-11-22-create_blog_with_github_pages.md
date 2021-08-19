---
layout: post
title: "SpringBoot在线教育项目"
date:   2021-8-8
tags: [geek]
comments: true
author: 李斌
---

# 尚硅谷项目 谷粒学院
@[toc]
## Day01	项目介绍和Mybatis-plus
按照视频进度每天写一篇笔记同时每天的代码也会上传码云平台，争取完完整整做完这个项目，希望可以学到有用的东西！！！
### 项目介绍：

#### 1 什么是在线教育

#### 1.1 基本概述

在线教育顾名思义，是以网络为介质的教学方式，通过网络，学员与教师即使相隔万里也可以开展教学活动；此外，借助网络课件，学员还可以随时随地进行学习，真正打破了时间和空间的限制，对于工作繁忙，学习时间不固定的职场人而言网络远程教育是最方便不过的学习方式。

#### 1.2 发展潜力

所有人离不开教育：早期教育、课外辅导、少儿英语、职业教育、出国留学、商学院、移民服务……而在信息化爆发式发展的趋势下，在线教育越来越凸显出优势：

1）在线教育可以突破时间和空间的限制，提升了学习效率；

2）在线教育可以跨越因地域等方面造成的教育资源不平等分配，使教育资源共享化，降低了学习的门槛。

基于在线教育的特点和优势，网络学校受到越来越多人的认可，各类新兴的网校及相关网站也不断涌现。显然，这代表着网校已经逐渐走进大众的生活并成为一种学习的主流趋势。因此很多人开始选择在线教育，特别是白领一族和大学生们。仅2012年一年，中国在线教育市场份额已经达到723亿元，且在线教育用户呈规模性放大。

#### 1.3 适用行业

具体来说在线培训学习系统可适合于：

1）政府：现今我们的政府也提倡学习型组织，不断变化的政策环境、不断出现的新事物对政府公务员提出了更高的要求，而且政府机构的网络资源较佳，“在线培训系统”对公务员学习新知识和提高素质有很大帮助，更关键的是政府机构是垂直管理体制，只要在一个领域中创建并维护一套知识库，就可以让整个领域共享这宝贵的知识财富。

2）学校：随着网络的兴起，各大中学校可通过建立网上学校，加强学校、老师、学生之间的相互交流沟通，提高教学质量，亦可建立公共教学资源库，建设精品课程，宣传学校的教育实力。

3）行业：许多行业知识库体系庞大，专业多且层次深，因此行业一直注重知识和经验的积累，但这些宝贵的知识财富散落在各地，并没有利用和共享，因此，充分利用现有资源就能够创建一套丰富的知识库体系，让整个行业受益。

4）企业：企业的知识库体系通常是企业的核心竞争力，使用“在线教育培训系统”，企业能够创建自己的知识库体系，并允许企业内部员工随时随地学习和分享这些知识。不断提升的员工素质和不断积累的企业知识库是企业能够保持长久的竞争力的关键。对于大型企业，还可以为合作伙伴及客户创建远程学习平台，提升和考核合作伙伴的专业技能并降低服务和支持成本。

### 项目采用技术：

项目采用前后端分离

* 前端：
  * VUE
  * element-ui
  * node.js
  * axios
* 后端：
  * SpringBoot
  * SpringCloud
  * Mybatis-Plus
  * Spring security
  * redis
  * maven
  * jwt
  * easyExcel
  * OAuth2
* 其他技术：
  * 阿里云OSS
  * 阿里云视频点播
  * 阿里云短信服务
  * 微信支付和登录
  * docker
  * git
  * Jenkins

### Mybatis-Plus学习

#### 1.insert插入操作

```java

@SpringBootTest

public class CRUDTests {

    @Autowired
    private UserMapper userMapper;
    @Test
    public void testInsert(){
        User user = new User();
        user.setName("Helen");
        user.setAge(18);
        user.setEmail("55317332@qq.com");
        int result = userMapper.insert(user);
        System.out.println(result); //影响的行数
        System.out.println(user); //id自动回填
    }
}
```

#### 2.主键生成策略

>
>
>**（1）ID_WORKER**
>
>MyBatis-Plus默认的主键策略是：ID_WORKER  *全局唯一ID*
>
>**（2）ID_WORKER_str**
>
>用于字符串类型的主键
>
>**（2）自增策略**
>
>- 要想主键自增需要配置如下主键策略
>
>- - 需要在创建数据表的时候设置主键自增
>
>  - 实体字段中配置 @TableId(type = IdType.AUTO)
>
>    ```java
>    @TableId(type = IdType.AUTO)
>    private Long id;
>    ```
>
>    

>
>
>其余的类型看以下代码可以了解
>
>```java
>@Getter
>public enum IdType {
>    /**
>     * 数据库ID自增
>     */
>    AUTO(0),
>    /**
>     * 该类型为未设置主键类型
>     */
>    NONE(1),
>    /**
>     * 用户输入ID
>     * 该类型可以通过自己注册自动填充插件进行填充
>     */
>    INPUT(2),
>    /* 以下3种类型、只有当插入对象ID 为空，才自动填充。 */
>    /**
>     * 全局唯一ID (idWorker)
>     */
>    ID_WORKER(3),
>    /**
>     * 全局唯一ID (UUID)
>     */
>    UUID(4),
>    /**
>     * 字符串全局唯一ID (idWorker 的字符串表示)
>     */
>    ID_WORKER_STR(5);
>    private int key;
>    IdType(int key) {
>        this.key = key;
>    }
>}
>```
>
>
>
>

#### 3.自动填充

项目中经常会遇到一些数据，每次都使用相同的方式填充，例如记录的创建时间，更新时间等。

我们可以使用MyBatis Plus的自动填充功能，完成这些字段的赋值工作：

>
>
>**（1）数据库表中添加自动填充字段**
>
>在User表中添加datetime类型的新的字段 create_time、update_time
>
>​	**(2)在实体类上添加注解**
>
>```java
>@Data
>public class User {
>    ......
>    @TableField(fill = FieldFill.INSERT)
>    private Date createTime;
>    //@TableField(fill = FieldFill.UPDATE)
>    @TableField(fill = FieldFill.INSERT_UPDATE)
>    private Date updateTime;
>}
>```
>
>**（3）实现元对象处理器接口**
>
>**注意：不要忘记添加 @Component 注解**
>
>```java
>
>@Component
>public class MyMetaObjectHandler implements MetaObjectHandler {
>    private static final Logger LOGGER = LoggerFactory.getLogger(MyMetaObjectHandler.class);
>    @Override
>    public void insertFill(MetaObject metaObject) {
>        LOGGER.info("start insert fill ....");
>        this.setFieldValByName("createTime", new Date(), metaObject);
>        this.setFieldValByName("updateTime", new Date(), metaObject);
>    }
>    @Override
>    public void updateFill(MetaObject metaObject) {
>        LOGGER.info("start update fill ....");
>
>      this.setFieldValByName("updateTime", new Date(), metaObject);
>    }
>
>}
>
>```
>
>
#### 4.乐观锁

**主要适用场景：**当要更新一条记录的时候，希望这条记录没有被别人更新，也就是说实现线程安全的数据更新

**乐观锁实现方式：**

- 取出记录时，获取当前version
- 更新时，带上这个version
- 执行更新时， set version = newVersion where version = oldVersion
- 如果version不对，就更新失败

实现步骤：

* 现在数据库中增加一个version字段

* 在实体类中也增加一个version并且加上@version注解

* ***在 MybatisPlusConfig 中注册 Bean***

  创建配置类：

  ```java
  public class MybatisPlusConfig {
      /**
       * 乐观锁插件
       */
      @Bean
      public OptimisticLockerInterceptor optimisticLockerInterceptor() {
          return new OptimisticLockerInterceptor();
      }
  }
  ```

* 测试乐观锁

  ```java
  在测试类中测试
       //先查找数据 按照id查找
          User user = userMapper.selectById(16);
          //再修改
          user.setUsername("李斌6");
          //测试乐观锁失败
  //        user.setVersion(user.getVersion()-1);
          int i = userMapper.updateById(user);
  ```

  #### 5.select

  * 根据id查询记录：selectById		

  * 通过多个id批量查询：selectBatchIds(Arrays.asList(1, 2, 3))

  * 简单的组合查询：通过map

    ```java
     HashMap<String, Object> map = new HashMap<>();
        map.put("name", "Helen");
        map.put("age", 18);
        List<User> users = userMapper.selectByMap(map);
    ```

  #### 6.分页

  ```java
  Page<User> page = new Page<>(1,3);
          userMapper.selectPage(page,null);
          //通过user对象获取分页数据
          long current = page.getCurrent();//获取当前页
          long pages = page.getPages();//获取总页数
          List<User> records = page.getRecords();//获取所有数据
          long total = page.getTotal();//获取一共有多少条数据
          long size = page.getSize();//获取每页显示记录数
          System.out.println(current);
          System.out.println(pages);
          System.out.println(records);
          System.out.println(total);
          System.out.println(size);
  ```

  #### 7.delete 

  * 根据id删除：deleteById()

  * 根据id批量删除：deleteBatchIds(Arrays.asList(8, 9, 10))

  * 简单的条件组合删除

    ```java
    HashMap<String, Object> map = new HashMap<>();
        map.put("name", "Helen");
        map.put("age", 18);
        int result = userMapper.deleteByMap(map);
    ```

  * 逻辑删除

    ```java
    1.在数据库中添加一个字段表示状态 比如添加一列deleted
    2.在实体类中创建对应的实体 并且加上注解@TableLogic
    3.如果是高版本的MP可以省略 自动写入了
     @Bean
    public ISqlInjector sqlInjector() {
        return new LogicSqlInjector();
    }
    4.测试：如果想查询到逻辑删除的信息需要自己编写SQL语句
    @Test
    public void testLogicDelete() {
        int result = userMapper.deleteById(1L);
        System.out.println(result);
    }
    ```

    

#### 复杂条件查询

如果想进行复杂条件查询，那么需要使用条件构造器 Wapper，涉及到如下方法

* **1、delete**

* **2、selectOne**

* **3、selectCount**

* **4、selectList**

* **5、selectMaps**

* **6、selectObjs**

* **7、update**

```java
 QueryWrapper<User> wrapper  = new QueryWrapper<>();
        wrapper.ge("id",3);
        List<User> users = userMapper.selectList(wrapper);
        System.out.println(users);
```

| ge 大于等于          | gt 大于                  | le 小于等于             |
| -------------------- | ------------------------ | ----------------------- |
| lt 小于              | eq 相等                  | ne 不相等               |
| between 包含大小边界 | notbetween不包含大小边界 | like 模糊查询左右两边+% |
| likeLeft 左边+%      | likeRight右边+%          | or                      |
| and                  |                          |                         |



==详细讲解==：

https://blog.csdn.net/m2606707610/article/details/104503626
## day02 项目开启



#### 数据库构建

建立一个名为guli的数据库，导入数据库文件

#### 工程搭建

* 创建父工程：

  **创建sprigboot工程guli-parent**

  在idea开发工具中，使用 Spring Initializr 快速初始化一个 Spring Boot 模块，版本使用：2.2.1.RELEASE

* 删除父工程的src目录 ：

  配置 pom.xml

  修改版本为 ：2.2.1.RELEASE

![\[外链图片转存失败,源站可能有防盗链机制,建议将图片保存下来直接上传(img-tUxug3WZ-1623155705309)(C:\Users\ww\Desktop\笔记\img\image-20210608194001938.png)\]](https://img-blog.csdnimg.cn/20210608203514716.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzUxNDQzNDU5,size_16,color_FFFFFF,t_70)


* ```java
  <artifactId> 节点后面添加  pom类型
  <artifactId>guli-parent</artifactId>
  <packaging>pom</packaging>
  ```

* **在pom.xml中添加依赖的版本**

```java
 <dependencyManagement>
        <dependencies>
            <!--Spring Cloud-->
            <dependency>
                <groupId>org.springframework.cloud</groupId>
                <artifactId>spring-cloud-dependencies</artifactId>
                <version>Hoxton.RELEASE</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
            <dependency>
                <groupId>org.springframework.cloud</groupId>
                <artifactId>spring-cloud-alibaba-dependencies</artifactId>
                <version>${cloud-alibaba.version}</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
            <!--mybatis-plus 持久层-->
            <dependency>
                <groupId>com.baomidou</groupId>
                <artifactId>mybatis-plus-boot-starter</artifactId>
                <version>${mybatis-plus.version}</version>
            </dependency>
            <!-- velocity 模板引擎, Mybatis Plus 代码生成器需要 -->
            <dependency>
                <groupId>org.apache.velocity</groupId>
                <artifactId>velocity-engine-core</artifactId>
                <version>${velocity.version}</version>
            </dependency>
            <!--swagger-->
            <dependency>
                <groupId>io.springfox</groupId>
                <artifactId>springfox-swagger2</artifactId>
                <version>${swagger.version}</version>
            </dependency>
            <!--swagger ui-->
            <dependency>
                <groupId>io.springfox</groupId>
                <artifactId>springfox-swagger-ui</artifactId>
                <version>${swagger.version}</version>
            </dependency>
            <!--aliyunOSS-->
            <dependency>
                <groupId>com.aliyun.oss</groupId>
                <artifactId>aliyun-sdk-oss</artifactId>
                <version>${aliyun.oss.version}</version>
            </dependency>
            <!--日期时间工具-->
            <dependency>
                <groupId>joda-time</groupId>
                <artifactId>joda-time</artifactId>
                <version>${jodatime.version}</version>
            </dependency>
            <!--xls-->
            <dependency>
                <groupId>org.apache.poi</groupId>
                <artifactId>poi</artifactId>
                <version>${poi.version}</version>
            </dependency>
            <!--xlsx-->
            <dependency>
                <groupId>org.apache.poi</groupId>
                <artifactId>poi-ooxml</artifactId>
                <version>${poi.version}</version>
            </dependency>
            <!--文件上传-->
            <dependency>
                <groupId>commons-fileupload</groupId>
                <artifactId>commons-fileupload</artifactId>
                <version>${commons-fileupload.version}</version>
            </dependency>
            <!--commons-io-->
            <dependency>
                <groupId>commons-io</groupId>
                <artifactId>commons-io</artifactId>
                <version>${commons-io.version}</version>
            </dependency>
            <!--httpclient-->
            <dependency>
                <groupId>org.apache.httpcomponents</groupId>
                <artifactId>httpclient</artifactId>
                <version>${httpclient.version}</version>
            </dependency>
            <dependency>
                <groupId>com.google.code.gson</groupId>
                <artifactId>gson</artifactId>
                <version>${gson.version}</version>
            </dependency>
            <!-- JWT -->
            <dependency>
                <groupId>io.jsonwebtoken</groupId>
                <artifactId>jjwt</artifactId>
                <version>${jwt.version}</version>
            </dependency>
            <!--aliyun-->
            <dependency>
                <groupId>com.aliyun</groupId>
                <artifactId>aliyun-java-sdk-core</artifactId>
                <version>${aliyun-java-sdk-core.version}</version>
            </dependency>
            <dependency>
                <groupId>com.aliyun.oss</groupId>
                <artifactId>aliyun-sdk-oss</artifactId>
                <version>${aliyun-sdk-oss.version}</version>
            </dependency>
            <dependency>
                <groupId>com.aliyun</groupId>
                <artifactId>aliyun-java-sdk-vod</artifactId>
                <version>${aliyun-java-sdk-vod.version}</version>
            </dependency>
            <dependency>
                <groupId>com.aliyun</groupId>
                <artifactId>aliyun-sdk-vod-upload</artifactId>
                <version>1.4.11</version>
            </dependency>
            <dependency>
                <groupId>com.aliyun</groupId>
                <artifactId>aliyun-sdk-vod-upload</artifactId>
                <version>${aliyun-sdk-vod-upload.version}</version>
            </dependency>
            <dependency>
                <groupId>com.alibaba</groupId>
                <artifactId>fastjson</artifactId>
                <version>${fastjson.version}</version>
            </dependency>
            <dependency>
                <groupId>org.json</groupId>
                <artifactId>json</artifactId>
                <version>${json.version}</version>
            </dependency>
            <dependency>
                <groupId>commons-dbutils</groupId>
                <artifactId>commons-dbutils</artifactId>
                <version>${commons-dbutils.version}</version>
            </dependency>
            <dependency>
                <groupId>com.alibaba.otter</groupId>
                <artifactId>canal.client</artifactId>
                <version>${canal.client.version}</version>
            </dependency>
        </dependencies>
    </dependencyManagement>
```

* 版本锁定

  ```java
  <properties>
          <java.version>1.8</java.version>
          <guli.version>0.0.1-SNAPSHOT</guli.version>
          <mybatis-plus.version>3.0.5</mybatis-plus.version>
          <velocity.version>2.0</velocity.version>
          <swagger.version>2.7.0</swagger.version>
          <aliyun.oss.version>2.8.3</aliyun.oss.version>
          <jodatime.version>2.10.1</jodatime.version>
          <poi.version>3.17</poi.version>
          <commons-fileupload.version>1.3.1</commons-fileupload.version>
          <commons-io.version>2.6</commons-io.version>
          <httpclient.version>4.5.1</httpclient.version>
          <jwt.version>0.7.0</jwt.version>
          <aliyun-java-sdk-core.version>4.3.3</aliyun-java-sdk-core.version>
          <aliyun-sdk-oss.version>3.1.0</aliyun-sdk-oss.version>
          <aliyun-java-sdk-vod.version>2.15.2</aliyun-java-sdk-vod.version>
          <aliyun-java-vod-upload.version>1.4.11</aliyun-java-vod-upload.version>
          <aliyun-sdk-vod-upload.version>1.4.11</aliyun-sdk-vod-upload.version>
          <fastjson.version>1.2.28</fastjson.version>
          <gson.version>2.8.2</gson.version>
          <json.version>20170516</json.version>
          <commons-dbutils.version>1.7</commons-dbutils.version>
          <canal.client.version>1.1.0</canal.client.version>
          <docker.image.prefix>zx</docker.image.prefix>
          <cloud-alibaba.version>0.2.2.RELEASE</cloud-alibaba.version>
      </properties>
  ```

#### service层搭建

* 在父工程guli-parent下面创建模块service

* **选择 maven类型，点击下一步**
* **输入模块名称 service，下一步完成创建**
* 添加模块类型是pom

```java
<artifactId>service</artifactId>
<packaging>pom</packaging>
```

* 添加项目需要的依赖

  ```java
   <dependencies>
          <dependency>
              <groupId>com.example</groupId>
              <artifactId>service-base</artifactId>
              <version>0.0.1-SNAPSHOT</version>
          </dependency>
          <dependency>
              <groupId>com.example</groupId>
              <artifactId>common-utils</artifactId>
              <version>0.0.1-SNAPSHOT</version>
          </dependency>
  <!--        <dependency>-->
  <!--            <groupId>org.springframework.cloud</groupId>-->
  <!--            <artifactId>spring-cloud-starter-netflix-ribbon</artifactId>-->
  <!--        </dependency>-->
  <!--        &lt;!&ndash;hystrix依赖，主要是用  @HystrixCommand &ndash;&gt;-->
  <!--        <dependency>-->
  <!--            <groupId>org.springframework.cloud</groupId>-->
  <!--            <artifactId>spring-cloud-starter-netflix-hystrix</artifactId>-->
  <!--        </dependency>-->
  <!--        &lt;!&ndash;服务注册&ndash;&gt;-->
  <!--        <dependency>-->
  <!--            <groupId>org.springframework.cloud</groupId>-->
  <!--            <artifactId>spring-cloud-starter-alibaba-nacos-discovery</artifactId>-->
  <!--        </dependency>-->
  <!--        &lt;!&ndash;服务调用&ndash;&gt;-->
  <!--        <dependency>-->
  <!--            <groupId>org.springframework.cloud</groupId>-->
  <!--            <artifactId>spring-cloud-starter-openfeign</artifactId>-->
  <!--        </dependency>-->
          <dependency>
              <groupId>org.springframework.boot</groupId>
              <artifactId>spring-boot-starter-web</artifactId>
          </dependency>
          <!--mybatis-plus-->
          <dependency>
              <groupId>com.baomidou</groupId>
              <artifactId>mybatis-plus-boot-starter</artifactId>
          </dependency>
          <!--mysql-->
          <dependency>
              <groupId>mysql</groupId>
              <artifactId>mysql-connector-java</artifactId>
          </dependency>
          <!-- velocity 模板引擎, Mybatis Plus 代码生成器需要 -->
          <dependency>
              <groupId>org.apache.velocity</groupId>
              <artifactId>velocity-engine-core</artifactId>
          </dependency>
          <!--swagger-->
          <dependency>
              <groupId>io.springfox</groupId>
              <artifactId>springfox-swagger2</artifactId>
          </dependency>
          <dependency>
              <groupId>io.springfox</groupId>
              <artifactId>springfox-swagger-ui</artifactId>
          </dependency>
          <!--lombok用来简化实体类：需要安装lombok插件-->
          <dependency>
              <groupId>org.projectlombok</groupId>
              <artifactId>lombok</artifactId>
          </dependency>
          <!--xls-->
          <dependency>
              <groupId>org.apache.poi</groupId>
              <artifactId>poi</artifactId>
          </dependency>
          <dependency>
              <groupId>org.apache.poi</groupId>
              <artifactId>poi-ooxml</artifactId>
          </dependency>
          <dependency>
              <groupId>commons-fileupload</groupId>
              <artifactId>commons-fileupload</artifactId>
          </dependency>
          <!--httpclient-->
          <dependency>
              <groupId>org.apache.httpcomponents</groupId>
              <artifactId>httpclient</artifactId>
          </dependency>
          <!--commons-io-->
          <dependency>
              <groupId>commons-io</groupId>
              <artifactId>commons-io</artifactId>
          </dependency>
          <!--gson-->
          <dependency>
              <groupId>com.google.code.gson</groupId>
              <artifactId>gson</artifactId>
          </dependency>
          <dependency>
              <groupId>junit</groupId>
              <artifactId>junit</artifactId>
              <version>4.12</version>
          </dependency>
      </dependencies>
  ```

* 搭建service-edu模块

* **在service下面service-edu模块中创建配置文件**

* **resources目录下创建文件 application.properties**

* ```java
  # 服务端口
  server.port=8001
  ## 服务名
  #spring.application.name=service-edu
  # 环境设置：dev、test、prod
  spring.profiles.active=dev
  #返回json的全局时间格式
  spring.jackson.date-format=yyyy-MM-dd HH:mm:ss
  spring.jackson.time-zone=GMT+8
  # mysql数据库连接
  spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
  spring.datasource.url=jdbc:mysql://localhost:3306/guli_edu?serverTimezone=GMT%2B8
  spring.datasource.username=root
  spring.datasource.password=ROOT6562
  #mybatis日志
  mybatis-plus.configuration.log-impl=org.apache.ibatis.logging.stdout.StdOutImpl创建MP代码生成器
  ```

#### 创建代码生成器

* 在test/java目录下创建包com.atguigu.eduservice，创建代码生成器：CodeGenerator.java

* ```java
          // 1、创建代码生成器
          AutoGenerator mpg = new AutoGenerator();
  
          // 2、全局配置
          GlobalConfig gc = new GlobalConfig();
          //输出目录
          String projectPath = System.getProperty("user.dir");
          gc.setOutputDir("D:\\IdeaProjects\\guli_parent\\Service\\Service_edu" + "/src/main/java");
          //作者信息
          gc.setAuthor("libin");
          gc.setOpen(false); //生成后是否打开资源管理器
          gc.setFileOverride(false); //重新生成时文件是否覆盖
          gc.setServiceName("%sService");	//去掉Service接口的首字母I
          gc.setIdType(IdType.ID_WORKER); //主键策略
          gc.setDateType(DateType.ONLY_DATE);//定义生成的实体类中日期类型
          gc.setSwagger2(true);//开启Swagger2模式
  
          mpg.setGlobalConfig(gc);
  
          // 3、数据源配置
          DataSourceConfig dsc = new DataSourceConfig();
          dsc.setUrl("jdbc:mysql://localhost:3306/guli_edu?serverTimezone=GMT%2B8");
          dsc.setDriverName("com.mysql.cj.jdbc.Driver");
          dsc.setUsername("root");
          dsc.setPassword("ROOT6562");
          dsc.setDbType(DbType.MYSQL);
          mpg.setDataSource(dsc);
  
          // 4、包配置
          PackageConfig pc = new PackageConfig();
          pc.setModuleName("edu"); //模块名
          pc.setParent("com.example.demo");
          pc.setController("controller");
          pc.setEntity("entity");
          pc.setService("service");
          pc.setMapper("mapper");
          mpg.setPackageInfo(pc);
  
          // 5、策略配置
          StrategyConfig strategy = new StrategyConfig();
          strategy.setInclude("edu_teacher");
          strategy.setNaming(NamingStrategy.underline_to_camel);//数据库表映射到实体的命名策略
          strategy.setTablePrefix(pc.getModuleName() + "_"); //生成实体时去掉表前缀
  
          strategy.setColumnNaming(NamingStrategy.underline_to_camel);//数据库表字段映射到实体的命名策略
          strategy.setEntityLombokModel(true); // lombok 模型 @Accessors(chain = true) setter链式操作
  
          strategy.setRestControllerStyle(true); //restful api风格控制器
          strategy.setControllerMappingHyphenStyle(true); //url中驼峰转连字符
  
          mpg.setStrategy(strategy);
  
  
          // 6、执行
          mpg.execute();
  ```

#### 编写后台管理api接口

##### **编写controller代码**

```java
@Autowired
private TeacherService teacherService;
@GetMapping
public List<Teacher> list(){
    return teacherService.list(null);
}
```

##### **创建SpringBoot配置类**

```java
创建config包，创建MyBatisPlusConfig.java
@Configuration
@EnableTransactionManagement
@MapperScan("com.example.demo.edu.mapper")
public class MyBatisPlusConfig {

}
```

##### **创建SpringBoot启动类**

```java
@SpringBootApplication
public class EduApplication {
    public static void main(String[] args) {
        SpringApplication.run(EduApplication.class, args);
    }
}
```

##### **运行启动类**

访问http://localhost:8001/eduservice/teacher

得到json数据

##### 统一返回的json时间格式

```properties
#返回json的全局时间格式
spring.jackson.date-format=yyyy-MM-dd HH:mm:ss
spring.jackson.time-zone=GMT+8
```

#### 讲师逻辑删除功能

* ```java
  MyBatisPlusConfig中配置
  /**
        * 逻辑删除插件
        */
  @Bean
  public ISqlInjector sqlInjector() {
      return new LogicSqlInjector();
  }
  ```



#### Swagger2配置

##### 介绍

```text
前后端分离开发模式中，api文档是最好的沟通方式。
Swagger 是一个规范和完整的框架，用于生成、描述、调用和可视化 RESTful 风格的 Web 服务。
及时性 (接口变更后，能够及时准确地通知相关前后端开发人员)
规范性 (并且保证接口的规范性，如接口的地址，请求方式，参数及响应格式和错误信息)
一致性 (接口信息一致，不会出现因开发人员拿到的文档版本不一致，而出现分歧)
可测性 (直接在接口文档上进行测试，以方便理解业务)
```

##### 配置Swagger2

* **创建common模块**
* **在guli-parent下创建模块common**

* **在common中引入相关依赖**

* ```java
   <dependencies>
          <dependency>
              <groupId>org.springframework.boot</groupId>
              <artifactId>spring-boot-starter-web</artifactId>
              <scope>provided </scope>
          </dependency>
          <!--mybatis-plus-->
          <dependency>
              <groupId>com.baomidou</groupId>
              <artifactId>mybatis-plus-boot-starter</artifactId>
              <scope>provided </scope>
          </dependency>
          <!--lombok用来简化实体类：需要安装lombok插件-->
          <dependency>
              <groupId>org.projectlombok</groupId>
              <artifactId>lombok</artifactId>
              <scope>provided </scope>
          </dependency>
          <!--swagger-->
          <dependency>
              <groupId>io.springfox</groupId>
              <artifactId>springfox-swagger2</artifactId>
              <scope>provided </scope>
          </dependency>
          <dependency>
              <groupId>io.springfox</groupId>
              <artifactId>springfox-swagger-ui</artifactId>
              <scope>provided </scope>
          </dependency>
          <!-- redis -->
          <dependency>
              <groupId>org.springframework.boot</groupId>
              <artifactId>spring-boot-starter-data-redis</artifactId>
          </dependency>
          <!-- spring2.X集成redis所需common-pool2
          <dependency>
              <groupId>org.apache.commons</groupId>
              <artifactId>commons-pool2</artifactId>
              <version>2.6.0</version>
          </dependency>-->
      </dependencies>
  ```

* 在common下面创建子模块service-base

* 在模块service-base中，创建swagger的配置类

* ```java
  创建包com.explome.servicebase.config，创建类SwaggerConfig
      package com.example.servicebase.config;
  
  import com.google.common.base.Predicates;
  import org.springframework.context.annotation.Bean;
  import org.springframework.context.annotation.Configuration;
  import springfox.documentation.builders.ApiInfoBuilder;
  import springfox.documentation.builders.PathSelectors;
  import springfox.documentation.service.ApiInfo;
  import springfox.documentation.service.Contact;
  import springfox.documentation.spi.DocumentationType;
  import springfox.documentation.spring.web.plugins.Docket;
  import springfox.documentation.swagger2.annotations.EnableSwagger2;
  
  @Configuration
  @EnableSwagger2
  public class SwaggerConfig {
      @Bean
      public Docket webApiConfig(){
          return new Docket(DocumentationType.SWAGGER_2)
                  .groupName("谷粒学院Api")
                  .apiInfo(webApiInfo())
                  .select()
                  .paths(Predicates.not(PathSelectors.regex("/admin/.*")))
                  .paths(Predicates.not(PathSelectors.regex("/error.*")))
                  .build();
      }
  
      private ApiInfo webApiInfo(){
          return new ApiInfoBuilder()
                  .title("网站-课程中心API文档")
                  .description("本文档描述了课程中心微服务接口定义")
                  .version("1.0")
                  .contact(new Contact("Helen", "http://atguigu.com", "55317332@qq.com"))
                  .build();
      }
  
  }
  ```

* 在模块service模块中引入service-base

* ```java
   <dependency>
              <groupId>com.example</groupId>
              <artifactId>service-base</artifactId>
              <version>0.0.1-SNAPSHOT</version>
   </dependency>
  ```

* **在service-edu启动类上添加注解，进行测试**

* ```jaav
  @ComponentScan(basePackages = {"com.example"})
  ```

##### 定义接口说明和参数说明

```java
定义在类上：@Api
定义在方法上：@ApiOperation
定义在参数上：@ApiParam
@Api(description="讲师管理")
@RestController
@RequestMapping("/admin/edu/teacher")
public class TeacherAdminController {
    @Autowired
    private TeacherService teacherService;
    @ApiOperation(value = "所有讲师列表")
    @GetMapping
    public List<Teacher> list(){
       return teacherService.list(null);
    }
    @ApiOperation(value = "根据ID删除讲师"
    @DeleteMapping("{id}")
    public boolean removeById(
            @ApiParam(name = "id", value = "讲师ID", required = true)
            @PathVariable String id){
        return teacherService.removeById(id);
    }
}
```

#### 统一返回数据格式

##### 介绍

项目中我们会将响应封装成json返回，一般我们会将所有接口的数据格式统一， 使前端(iOS Android, Web)对数据的操作更一致、轻松。

一般情况下，统一返回数据格式没有固定的格式，只要能描述清楚返回的数据状态以及要返回的具体数据就可以。但是一般会包含状态码、返回消息、数据这几部分内容

例如，我们的系统要求返回的基本数据格式如下：

```json
{
  "success": true,
  "code": 20000,
  "message": "成功",
  "data": {
    "items": [
      {
        "id": "1",
        "name": "刘德华",
        "intro": "毕业于师范大学数学系，热爱教育事业，执教数学思维6年有余"
      }
    ]
  }
}
```

**没有返回数据：**

```json
{
  "success": true,
  "code": 20000,
  "message": "成功",
  "data": {}
}
```

因此，我们定义统一结果

```json
{
  "success": 布尔, //响应是否成功
  "code": 数字, //响应码
  "message": 字符串, //返回消息
  "data": HashMap //返回数据，放在键值对中
}
```

##### 创建统一结果返回类

* 在common模块下创建子模块common-utils

* **创建接口定义返回码**

* ```java
  public interface ResultCode {
      public static Integer SUCCESS = 20000;
      public static Integer ERROR = 20001;
  }
  ```

* **创建结果类**

* ```java
  package com.example.commonutils;
  
  import io.swagger.annotations.ApiModelProperty;
  import lombok.Data;
  
  import java.util.HashMap;
  import java.util.Map;
  
  @Data
  public class R {
      @ApiModelProperty(value = "是否成功")
      private Boolean success;
      @ApiModelProperty(value = "返回码")
      private Integer code;
      @ApiModelProperty(value = "返回消息")
      private String message;
      @ApiModelProperty(value = "返回数据")
      private Map<String, Object> data = new HashMap<String, Object>();
      private R(){}
      public static R ok(){
          R r = new R();
          r.setSuccess(true);
          r.setCode(ResultCode.SUCCESS);
          r.setMessage("成功");
          return r;
      }
      public static R error(){
          R r = new R();
          r.setSuccess(false);
          r.setCode(ResultCode.ERROR);
          r.setMessage("失败");
          return r;
      }
      public R success(Boolean success){
          this.setSuccess(success);
          return this;
      }
      public R message(String message){
  
          this.setMessage(message);
          return this;
      }
  
      public R code(Integer code){
  
          this.setCode(code);
          return this;
      }
      public R data(String key, Object value){
          this.data.put(key, value);
          return this;
      }
  
      public R data(Map<String, Object> map){
          this.setData(map);
          return this;
      }
  }
  
  ```

##### 统一返回结果使用

* 在service模块中添加依赖

* ```java
  <dependency>
      <groupId>com.atguigu</groupId>
      <artifactId>common_utils</artifactId>
      <version>0.0.1-SNAPSHOT</version>
  </dependency>
  ```

* 修改Controller中的返回结果

* ```java
  @ApiOperation(value = "所有讲师列表")
  @GetMapping
  public R list(){
      List<Teacher> list = teacherService.list(null);
      return R.ok().data("items", list);
  }
  ```

#### 分页和条件查询

##### 分页

* MyBatisPlusConfig中配置分页插件

* ```java
  /**
       * 分页插件
       */
      @Bean
      public PaginationInterceptor paginationInterceptor() {
          return new PaginationInterceptor();
      }
  ```

* 分页Controller方法

* ```
   /**
       * 分页查询
       */
      @GetMapping("/selectPage/{current}/{count}")
      public R findByPage(@PathVariable Long current,
                           @PathVariable Long count
                          ){
          Page<Teacher> teacherPage = new Page<>(current,count);
          teacherService.page(teacherPage, null);
          //获取全部数据
          List<Teacher> records = teacherPage.getRecords();
          //获取总页数
          long total = teacherPage.getTotal();
          Map<String,Object> map = new HashMap<>();
          map.put("records",records);
          map.put("total",total);
          return R.ok().data("items",map);
      }
  ```

* Swagger中测试

##### 条件查询

根据讲师名称name，讲师头衔level、讲师入驻时间gmt_create（时间段）查询

* 创建查询对象

* 在实体类创建

* ```java
  import lombok.Data;
  
  import java.io.Serializable;
  
  @ApiModel(value = "Teacher查询对象", description = "讲师查询对象封装")
  @Data
  public class TeacherQuery implements Serializable {
      private static final long serialVersionUID = 1L;
      @ApiModelProperty(value = "教师名称,模糊查询")
      private String name;
      @ApiModelProperty(value = "头衔 1高级讲师 2首席讲师")
      private Integer level;
      @ApiModelProperty(value = "查询开始时间", example = "2019-01-01 10:10:10")
      private String begin;//注意，这里使用的是String类型，前端传过来的数据无需进行类型转换
      @ApiModelProperty(value = "查询结束时间", example = "2019-12-01 10:10:10")
      private String end;
  }
  ```

* controller层

* ```java
   /**
       * 组合条件查询
       */
      @PostMapping("/pageQuery/{current}/{count}")
      public R PageQuery(@PathVariable int current,
                         @PathVariable int count ,
                         @RequestBody(required = false) TeacherQuery teacherQuery){
          //先实现分页
          Page<Teacher> teacherPage = new Page<>(current,count);
          QueryWrapper<Teacher> wrapper = new QueryWrapper();
          String name = teacherQuery.getName();
          Integer level = teacherQuery.getLevel();
          String begin = teacherQuery.getBegin();
          String end = teacherQuery.getEnd();
          //当名字不为空
          if (!StringUtils.isEmpty(name)){
              wrapper.like("name",name);
          }
          if (!StringUtils.isEmpty(level)){
              wrapper.eq("level",level);
          }
          if (!StringUtils.isEmpty(begin)){
              wrapper.ge("gmt_create",begin);
          }
          if (!StringUtils.isEmpty(end)){
              wrapper.le("gmt_create",end);
          }
          teacherService.page(teacherPage, wrapper);
          //获取全部数据
          List<Teacher> records = teacherPage.getRecords();
          //获取总页数
          long total = teacherPage.getTotal();
          Map<String,Object> map = new HashMap<>();
          map.put("records",records);
          map.put("total",total);
          return R.ok().data("items",map);
      }
  ```

* Swagger2中测试

#### 增加和修改

##### 自动填充封装

* 在service-base模块中添加**创建包handler，创建自动填充类 MyMetaObjectHandler**

* ```java
  package com.example.servicebase.config.Handler;
  
  
  import com.baomidou.mybatisplus.core.handlers.MetaObjectHandler;
  import org.apache.ibatis.reflection.MetaObject;
  import org.springframework.stereotype.Component;
  
  import java.util.Date;
  
  @Component
  public class MyMetaObjectHandler implements MetaObjectHandler {
      @Override
      public void insertFill(MetaObject metaObject) {
          this.setFieldValByName("gmtCreate", new Date(), metaObject);
          this.setFieldValByName("gmtModified", new Date(), metaObject);
      }
      @Override
      public void updateFill(MetaObject metaObject) {
          this.setFieldValByName("gmtModified", new Date(), metaObject);
      }
  }
  ```

* 在实体类添加自动填充注解

* ```
  @TableField(fill = FieldFill.INSERT)
  @TableField(fill = FieldFill.INSERT_UPDATE)
  ```

##### **controller方法定义**

* 新增

* ```java
  /**
       * 添加讲师
       */
      @PostMapping("/addTeacher")
      public R addTeacher(@RequestBody Teacher teacher){
          teacherService.save(teacher);
          return R.ok();
      }
  ```

* 根据id修改

* ```java
   /**
       * 修改数据
       */
      @PostMapping("/UpdateTeacher")
      public R UpdateTeacher(@RequestBody Teacher teacher){
          //先根据id查询 后修改
          boolean b = teacherService.updateById(teacher);
          if (b){
              return R.ok();
          }
          else {
              return R.error();
          }
      }
  ```

  ##  Day03 前端学习

### Vue

* 下载VSCode 下载地址 https://code.visualstudio.com/

* 安装三个插件

  * Chinese Languae
  * Live Serve
  * Veture

* 创建项目

  * 首先创建一个空文件夹
  * 打开文件夹后，选择“文件 -> 将工作区另存为...”，为工作区文件起一个名字，存储在刚才的文件夹下即可

* ES6学习

* >
  >
  ># 一、ECMAScript 6 简介
  >
  >ECMAScript 6.0（以下简称 ES6）是 JavaScript 语言的下一代标准，已经在 2015 年 6 月正式发布了。它的目标，是使得 JavaScript 语言可以用来编写复杂的大型应用程序，成为企业级开发语言。
  >
  >## 1、ECMAScript 和 JavaScript 的关系
  >
  >一个常见的问题是，ECMAScript 和 JavaScript 到底是什么关系？
  >
  >要讲清楚这个问题，需要回顾历史。1996 年 11 月，JavaScript 的创造者 Netscape 公司，决定将 JavaScript 提交给标准化组织 ECMA，希望这种语言能够成为国际标准。次年，ECMA 发布 262 号标准文件（ECMA-262）的第一版，规定了浏览器脚本语言的标准，并将这种语言称为 ECMAScript，这个版本就是 1.0 版。
  >
  >因此，ECMAScript 和 JavaScript 的关系是，前者是后者的规格，后者是前者的一种实现（另外的 ECMAScript 方言还有 Jscript 和 ActionScript）
  >
  >## 2、ES6 与 ECMAScript 2015 的关系
  >
  >ECMAScript 2015（简称 ES2015）这个词，也是经常可以看到的。它与 ES6 是什么关系呢？
  >
  >2011 年，ECMAScript 5.1 版发布后，就开始制定 6.0 版了。因此，ES6 这个词的原意，就是指 JavaScript 语言的下一个版本。
  >
  >ES6 的第一个版本，在 2015 年 6 月发布，正式名称是《ECMAScript 2015 标准》（简称 ES2015）。
  >
  >2016 年 6 月，小幅修订的《ECMAScript 2016 标准》（简称 ES2016）如期发布，这个版本可以看作是 ES6.1 版，因为两者的差异非常小，基本上是同一个标准。根据计划，2017 年 6 月发布 ES2017 标准。
  >
  >因此，ES6 既是一个历史名词，也是一个泛指，含义是 5.1 版以后的 JavaScript 的下一代标准，涵盖了 ES2015、ES2016、ES2017 等等，而 ES2015 则是正式名称，特指该年发布的正式版本的语言标准。本书中提到 ES6 的地方，一般是指 ES2015 标准，但有时也是泛指“下一代 JavaScript 语言”。
  >
  >
  >
  ># 二、基本语法
  >
  >ES标准中不包含 DOM 和 BOM的定义，只涵盖基本数据类型、关键字、语句、运算符、内建对象、内建函数等通用语法。
  >
  >本部分只学习前端开发中ES6的最少必要知识，方便后面项目开发中对代码的理解。
  >
  >## 1、let声明变量
  >
  >创建 let.html
  >
  >1
  >
  >```
  >// var 声明的变量没有局部作用域
  >```
  >
  >2
  >
  >```
  >// let 声明的变量  有局部作用域
  >```
  >
  >3
  >
  >```
  >{
  >```
  >
  >4
  >
  >```
  >var a = 0
  >```
  >
  >5
  >
  >```
  >let b = 1
  >```
  >
  >6
  >
  >```
  >}
  >```
  >
  >7
  >
  >```
  >console.log(a)  // 0
  >```
  >
  >8
  >
  >```
  >console.log(b)  // ReferenceError: b is not defined
  >```
  >
  >1
  >
  >```
  >// var 可以声明多次
  >```
  >
  >2
  >
  >```
  >// let 只能声明一次
  >```
  >
  >3
  >
  >```
  >var m = 1
  >```
  >
  >4
  >
  >```
  >var m = 2
  >```
  >
  >5
  >
  >```
  >let n = 3
  >```
  >
  >6
  >
  >```
  >let n = 4
  >```
  >
  >7
  >
  >```
  >console.log(m)  // 2
  >```
  >
  >8
  >
  >```
  >console.log(n)  // Identifier 'n' has already been declared
  >```
  >
  >**2、const声明常量（只读变量）**
  >
  >创建 const.html
  >
  >1
  >
  >```
  >// 1、声明之后不允许改变    
  >```
  >
  >2
  >
  >```
  >const PI = "3.1415926"
  >```
  >
  >3
  >
  >```
  >PI = 3  // TypeError: Assignment to constant variable.
  >```
  >
  >1
  >
  >```
  >// 2、一但声明必须初始化，否则会报错
  >```
  >
  >2
  >
  >```
  >const MY_AGE  // SyntaxError: Missing initializer in const declaration
  >```
  >
  >## 3、**解构赋值**
  >
  >创建 解构赋值.html
  >
  >解构赋值是对赋值运算符的扩展。
  >
  >他是一种针对数组或者对象进行模式匹配，然后对其中的变量进行赋值。
  >
  >在代码书写上简洁且易读，语义更加清晰明了；也方便了复杂对象中数据字段获取。
  >
  >1
  >
  >```
  >//1、数组解构
  >```
  >
  >2
  >
  >```
  >// 传统
  >```
  >
  >3
  >
  >```
  >let a = 1, b = 2, c = 3
  >```
  >
  >4
  >
  >```
  >console.log(a, b, c)
  >```
  >
  >5
  >
  >```
  >// ES6
  >```
  >
  >6
  >
  >```
  >let [x, y, z] = [1, 2, 3]
  >```
  >
  >7
  >
  >```
  >console.log(x, y, z)
  >```
  >
  >1
  >
  >```
  >//2、对象解构
  >```
  >
  >2
  >
  >```
  >let user = {name: 'Helen', age: 18}
  >```
  >
  >3
  >
  >```
  >// 传统
  >```
  >
  >4
  >
  >```
  >let name1 = user.name
  >```
  >
  >5
  >
  >```
  >let age1 = user.age
  >```
  >
  >6
  >
  >```
  >console.log(name1, age1)
  >```
  >
  >7
  >
  >```
  >// ES6
  >```
  >
  >8
  >
  >```
  >let { name, age } =  user//注意：结构的变量必须是user中的属性
  >```
  >
  >9
  >
  >```
  >console.log(name, age)
  >```
  >
  >## 4、模板字符串
  >
  >创建 模板字符串.html
  >
  >模板字符串相当于加强版的字符串，用反引号 `,除了作为普通字符串，还可以用来定义多行字符串，还可以在字符串中加入变量和表达式。
  >
  >1
  >
  >```
  >// 1、多行字符串
  >```
  >
  >2
  >
  >```
  >let string1 =  `Hey,
  >```
  >
  >3
  >
  >```
  >can you stop angry now?`
  >```
  >
  >4
  >
  >```
  >console.log(string1)
  >```
  >
  >5
  >
  >```
  >// Hey,
  >```
  >
  >6
  >
  >```
  >// can you stop angry now?
  >```
  >
  >1
  >
  >```
  >// 2、字符串插入变量和表达式。变量名写在 ${} 中，${} 中可以放入 JavaScript 表达式。
  >```
  >
  >2
  >
  >```
  >let name = "Mike"
  >```
  >
  >3
  >
  >```
  >let age = 27
  >```
  >
  >4
  >
  >```
  >let info = `My Name is ${name},I am ${age+1} years old next year.`
  >```
  >
  >5
  >
  >```
  >console.log(info)
  >```
  >
  >6
  >
  >```
  >// My Name is Mike,I am 28 years old next year.
  >```
  >
  >1
  >
  >```
  >// 3、字符串中调用函数
  >```
  >
  >2
  >
  >```
  >function f(){
  >```
  >
  >3
  >
  >```
  >return "have fun!"
  >```
  >
  >4
  >
  >```
  >}
  >```
  >
  >5
  >
  >```
  >let string2 = `Game start,${f()}`
  >```
  >
  >6
  >
  >```
  >console.log(string2);  // Game start,have fun!
  >```
  >
  >## 5、声明对象简写
  >
  >创建 声明对象简写.html
  >
  >1
  >
  >```
  >const age = 12
  >```
  >
  >2
  >
  >```
  >const name = "Amy"
  >```
  >
  >3
  >
  >```
  >
  >```
  >
  >4
  >
  >```
  >// 传统
  >```
  >
  >5
  >
  >```
  >const person1 = {age: age, name: name}
  >```
  >
  >6
  >
  >```
  >console.log(person1)
  >```
  >
  >7
  >
  >```
  >
  >```
  >
  >8
  >
  >```
  >// ES6
  >```
  >
  >9
  >
  >```
  >const person2 = {age, name}
  >```
  >
  >10
  >
  >```
  >console.log(person2) //{age: 12, name: "Amy"}
  >```
  >
  >## 6、定义方法简写
  >
  >创建 定义方法简写.html
  >
  >1
  >
  >```
  >// 传统
  >```
  >
  >2
  >
  >```
  >const person1 = {
  >```
  >
  >3
  >
  >```
  >sayHi:function(){
  >```
  >
  >4
  >
  >```
  >   console.log("Hi")
  >```
  >
  >5
  >
  >```
  >}
  >```
  >
  >6
  >
  >```
  >}
  >```
  >
  >7
  >
  >```
  >person1.sayHi();//"Hi"
  >```
  >
  >8
  >
  >```
  >
  >```
  >
  >9
  >
  >```
  >
  >```
  >
  >10
  >
  >```
  >// ES6
  >```
  >
  >11
  >
  >```
  >const person2 = {
  >```
  >
  >12
  >
  >```
  >sayHi(){
  >```
  >
  >13
  >
  >```
  >   console.log("Hi")
  >```
  >
  >14
  >
  >```
  >}
  >```
  >
  >15
  >
  >```
  >}
  >```
  >
  >16
  >
  >```
  >person2.sayHi()  //"Hi"
  >```
  >
  >## 7、对象拓展运算符
  >
  >创建 对象拓展运算符.html
  >
  >拓展运算符（...）用于取出参数对象所有可遍历属性然后拷贝到当前对象。
  >
  >```
  >// 1、拷贝对象
  >```
  >
  >```
  >let person1 = {name: "Amy", age: 15}
  >```
  >
  >```
  >let someone = { ...person1 }
  >```
  >
  >```
  >console.log(someone)  //{name: "Amy", age: 15}
  >```
  >
  >```
  >// 2、合并对象
  >```
  >
  >```
  >let age = {age: 15}
  >```
  >
  >```
  >let name = {name: "Amy"}
  >```
  >
  >```
  >let person2 = {...age, ...name}
  >```
  >
  >```
  >console.log(person2)  //{age: 15, name: "Amy"}
  >```
  >
  >**8、箭头函数**
  >
  >创建 箭头函数.html
  >
  >箭头函数提供了一种更加简洁的函数书写方式。基本语法是：`参数 => 函数体`
  >
  >1
  >
  >```
  >// 传统
  >```
  >
  >```
  >var f1 = function(a){
  >```
  >
  >```
  >return a
  >```
  >
  >```
  >}
  >```
  >
  >```
  >console.log(f1(1))
  >```
  >
  >```
  >// ES6
  >```
  >
  >```
  >var f2 = a => a
  >```
  >
  >```
  >console.log(f2(1))
  >```
  >
  >```
  >// 当箭头函数没有参数或者有多个参数，要用 () 括起来。
  >```
  >
  >```
  >// 当箭头函数函数体有多行语句，用 {} 包裹起来，表示代码块，
  >```
  >
  >```
  >// 当只有一行语句，并且需要返回结果时，可以省略 {} , 结果会自动返回。
  >```
  >
  >```
  >var f3 = (a,b) => {
  >```
  >
  >```
  >let result = a+b
  >```
  >
  >```
  >return result
  >```
  >
  >```
  >}
  >```
  >
  >```
  >console.log(f3(6,2))  // 8
  >```
  >
  >```
  >// 前面代码相当于
  >```
  >
  >```
  >var f4 = (a,b) => a+b
  >```
  >
  >箭头函数多用于匿名函数的定义



* 复习Vue知识 博客里面有
* 下载node.js  注意==本项目使用的是13版本以下==



## Day04

* npm

  * 初始化项目：npm init -y

  * 修改为淘宝镜像

  * ```
    npm config set registry https://registry.npm.taobao.org 
    ```

* Babel

  * 介绍：将ES6代码转为ES5
  * 安装：npm install --global babel-cli
  * 查看版本 babel --version
  * 安装转码器：npm install --save-dev babel-preset-es2015

* vue-admin-template 

  - 本项目使用的框架

* 项目前端正式开始

  * 将vue-admin-template-master重命名为guli-admin
  * config/index.js中修改 可以修改端口号 port:9528
  * 运行项目 npm run dev

* 开始记录做项目的时候遇到的问题

  * 遇到的第一个问题 使用axios时 获取数据 没有获取到想要的数据
  * 原因：this.list = response.data.items错误 还需要获取具体的数据
  * 改正：this.list = response.data.items.records,

* 第二个问题：加入分页条后total一直为0 而且下面没有页码

  * 原因：表单上第一行有一个loadding那个东西 造成错误导致后面的数据无法加载
  * 解决办法：直接删除即可

* 第三个问题：当完成了添加和修改后 他们使用的同一个页面 当点击了修改再切换回添加后还是有数据回显

  * 解决办法：

    我们可以在watch中监听路由的变化，当路由变化时，重新调用created中的内容

    在init方法中我们判断路由的变化，如果是修改路由，则从api获取表单数据，

     如果是新增路由，则重新初始化表单数据

## 谷粒学院项目学习笔记

### 路由切换：

vue-router导航切换 时，如果两个路由都渲染同个组件，组件会重（chong）用,

组件的生命周期钩子（created）不会再被调用, 使得组件的一些数据无法根据 path的改变得到更新

因此：

1、我们可以在watch中监听路由的变化，当路由变化时，重新调用created中的内容

2、在init方法中我们判断路由的变化，如果是修改路由，则从api获取表单数据，

   如果是新增路由，则重新初始化表单数据

```java
<script>
import teacher from '@/api/edu/teacher'
const defaultForm = {
  name: '',
  sort: 0,
  level: '',
  career: '',
  intro: '',
  avatar: ''
}
export default {
  data() {
    return {
      teacher: defaultForm,
      saveBtnDisabled: false // 保存按钮是否禁用,
    }
  },
  watch: {
    $route(to, from) {
      console.log('watch $route')
      this.init()
    }
 },
  created() {
    console.log('created')
    this.init()
  },
  methods: {
    init() {
      if (this.$route.params && this.$route.params.id) {
        const id = this.$route.params.id
        this.fetchDataById(id)
      } else {
        // 使用对象拓展运算符 ... ，拷贝对象，而不是引用，将上面的defaultForm内容拷贝过来  上面内容的变化并不会影响拷贝内容
        // 否则新增一条记录后，defaultForm就变成了之前新增的teacher的值
        this.teacher = { ...defaultForm }
      }
    },
  }
}
</script>
```

