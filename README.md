<center><h1>weathertop</h1></center>

<h2>风云顶（Weathertop），指环王魔戒中一处地名，辛达语中称为阿蒙苏尔，是风云丘陵中最南端的山峰，它跟其他山岗稍稍分开。它顶端呈圆锥形，峰顶略显平坦。在指环王魔戒中放置了名为帕蓝提尔（Palantíri）的“真知晶石”，可用于远望和交流的一种黑色晶石。</h2>

<!-- TOC -->

- [1. 目录结构](#1-目录结构)
- [2. persistence-mybatis](#2-persistence-mybatis)
- [3. akkad-cloud入门](#3-akkad-cloud入门)
    - [3.1. Nacos配置中心](#31-nacos配置中心)
    - [3.2. Nacos注册中心](#32-nacos注册中心)
    - [3.3. 网关Gateway](#33-网关gateway)
    - [3.4. 熔断Hystream](#34-熔断hystream)
- [4. akkad-java](#4-akkad-java)
    - [4.1. 设计模式akkad-design](#41-设计模式akkad-design)
- [5. SpringBoot入门](#5-springboot入门)
    - [5.1. JWT整合](#51-jwt整合)
        - [5.1.1. JWT概念](#511-jwt概念)
        - [5.1.2. 应用场景](#512-应用场景)
        - [5.1.3. 特点](#513-特点)
        - [5.1.4. 结构](#514-结构)
            - [5.1.4.1. Header](#5141-header)
            - [5.1.4.2. Payload](#5142-payload)
            - [5.1.4.3. Signature](#5143-signature)
        - [5.1.5. 环境集成](#515-环境集成)
            - [5.1.5.1. 加入依赖包](#5151-加入依赖包)
            - [5.1.5.2. 自定义一个实体类](#5152-自定义一个实体类)
            - [5.1.5.3. 生成Token方法](#5153-生成token方法)
            - [5.1.5.4. 验证token返回数据](#5154-验证token返回数据)
        - [5.1.6. 基于Jwt登陆用户认证实战](#516-基于jwt登陆用户认证实战)
    - [5.2. springboot-generator自动生成代码](#52-springboot-generator自动生成代码)
    - [5.3. 消息Kafka](#53-消息kafka)
        - [5.3.1. 应用集成](#531-应用集成)
            - [5.3.1.1. 生产者](#5311-生产者)
            - [5.3.1.2. 消费者](#5312-消费者)
            - [5.3.1.3. 演示](#5313-演示)
- [6. Linux说明](#6-linux说明)
    - [6.1. 总体说明](#61-总体说明)
        - [6.1.1. 查看版本当前操作系统内核信息](#611-查看版本当前操作系统内核信息)
        - [6.1.2. 查看当前操作系统版本信息](#612-查看当前操作系统版本信息)
        - [6.1.3. 查看版本当前操作系统发行版信息](#613-查看版本当前操作系统发行版信息)
        - [6.1.4. 查看cpu相关信息，包括型号、主频、内核信息等](#614-查看cpu相关信息包括型号主频内核信息等)
    - [6.2. 系统配置](#62-系统配置)
        - [6.2.1. 内存](#621-内存)
        - [6.2.2. 磁盘](#622-磁盘)
    - [6.3. Linux优化](#63-linux优化)
        - [6.3.1. 运行级别Runlevel](#631-运行级别runlevel)
        - [6.3.2. systemd一统天下](#632-systemd一统天下)
    - [6.4. 开机时间优化](#64-开机时间优化)
        - [6.4.1. 查看开机时间](#641-查看开机时间)
        - [6.4.2. 查看具体的使用时间](#642-查看具体的使用时间)
        - [6.4.3. 启动项优化](#643-启动项优化)
        - [6.4.4. Selinux的优化](#644-selinux的优化)
        - [6.4.5. ssh的优化](#645-ssh的优化)
- [7. 消息MQ](#7-消息mq)
    - [7.1. Kafka](#71-kafka)
        - [7.1.1. kafka安装](#711-kafka安装)
        - [7.1.2. 编写配置文件](#712-编写配置文件)
        - [7.1.3. 启动](#713-启动)
        - [7.1.4. 创建Topic](#714-创建topic)
        - [7.1.5. 查看Topic](#715-查看topic)
- [8. elasticsearch](#8-elasticsearch)
- [9. zookeeper安装](#9-zookeeper安装)
    - [9.1. 下载](#91-下载)
    - [9.2. 配置安装](#92-配置安装)
- [10. hadoop学习](#10-hadoop学习)
    - [10.1. 伪分布式环境部署](#101-伪分布式环境部署)
        - [10.1.1. 创建用户组、用户](#1011-创建用户组用户)
        - [10.1.2. ssh安装配置免密登陆](#1012-ssh安装配置免密登陆)
        - [10.1.3. hadoop安装](#1013-hadoop安装)
            - [10.1.3.1. 下载](#10131-下载)
            - [10.1.3.2. 配置](#10132-配置)
        - [10.1.4. HBase安装](#1014-hbase安装)
            - [10.1.4.1. 单机HBase配置](#10141-单机hbase配置)
            - [10.1.4.2. 集群模式<待补充>](#10142-集群模式待补充)
        - [10.1.5. Phoenix安装](#1015-phoenix安装)
        - [10.1.6. hive安装](#1016-hive安装)

<!-- /TOC -->

# 1. 目录结构

~~~


|-- akkad-base                      ------------------------------基包
|   |-- base-persistence            ------------------------------持久层包
|   |   |-- persistence-mybatis     ------------------------------Mybatis持久层基包
|   |-- base-utils                  ------------------------------通用工具包
|-- akkad-cloud                     ------------------------------SpringCloud入门
|   |-- cloud-config                ------------------------------基于Nacos实现的配置中心
|-- akkad-handball                  ------------------------------样例
|   |-- handball-location           ------------------------------爬虫获取统计局区域样例
|   |-- handball-tess4j             ------------------------------OCR图片识别
|-- akkad-java                      ------------------------------JAVA学习
|   |-- akkad-design                ------------------------------设计模式
|   |-- akkad-socket                ------------------------------Scoket编程
|   |   |-- socket-client           ------------------------------Client端
|   |   |-- socket-server           ------------------------------Server端
|   |-- akkad-thread                ------------------------------多线程
|-- akkad-job                       ------------------------------基于XXL-JOB实现调度中心
|   |-- job-sms                     ------------------------------调度中心样例
|-- akkad-springboot                ------------------------------SPRINGBOOT入门
|   |-- springboot-async            ------------------------------异步
|   |-- springboot-atomikos         ------------------------------分布式事务
|   |-- springboot-jwt              ------------------------------JWT认证
|   |-- springboot-mq               ------------------------------异步MQ
|   |   |-- mq-kafka                ------------------------------Kafka实现
|   |   |   |-- kafka-client        ------------------------------消费者
|   |   |   |-- kafka-server        ------------------------------生产者
|-- akkad-webmagic                  ------------------------------
|   |-- src
|   |-- target
|-- doc
|   |-- image
|-- README.md
~~~

# 2. persistence-mybatis

基于Mybatis组件并结合泛型实现**BaseMapper、BaseService**，子类继承该类，即可拥有通用的CURD，减少重复编码的麻烦，提高开发效率。

- 分页组件是继承开源**com.github.pagehelper**

~~~
<dependency>
    <groupId>com.github.pagehelper</groupId>
    <artifactId>pagehelper-spring-boot-starter</artifactId>
    <version>1.2.3</version>
</dependency>
~~~

- 在应用中PageHelper.startPage即可，后面需要紧跟着持久层语句，否则分页失效

~~~
    public PageInfo<T> selectPage(PaginationInfo pgInfo, T t) {
        PageHelper.startPage(pgInfo.getPageNum(), pgInfo.getPageSize());
        List<T> lt = getMapper().getList(t);
        PageInfo<T> pageInfo = new PageInfo<T>(lt);
        return pageInfo;
    }
~~~

# 3. akkad-cloud入门

## 3.1. Nacos配置中心

Nacos 支持基于 DNS 和基于 RPC 的服务发现（可以作为springcloud的注册中心）、动态配置服务（可以做配置中心）、动态 DNS 服务。

`官方介绍`
~~~
Nacos 致力于帮助您发现、配置和管理微服务。Nacos 提供了一组简单易用的特性集，帮助您实现动态服务发现、服务配置管理、服务及流量管理。
Nacos 帮助您更敏捷和容易地构建、交付和管理微服务平台。 Nacos 是构建以“服务”为中心的现代应用架构(例如微服务范式、云原生范式)的服务基础设施。
~~~

- pom依赖包

~~~
<dependency>
    <groupId>com.alibaba.boot</groupId>
    <artifactId>nacos-config-spring-boot-starter</artifactId>
    <version>0.1.2</version>
</dependency>
~~~

- application.yml

~~~
nacos:
  config:
    server-addr: 123.206.118.219:8848
~~~

## 3.2. Nacos注册中心

## 3.3. 网关Gateway

## 3.4. 熔断Hystream

# 4. akkad-java

## 4.1. 设计模式akkad-design

点击即可查看[观察设计模式](akkad-java/akkad-design/Observer.md)详细介绍

# 5. SpringBoot入门

## 5.1. JWT整合

### 5.1.1. JWT概念

Json web token (JWT), 是为在网络应用环境间传递声明而执行的一种基于JSON的开放标准（(RFC 7519).定义了一种简洁的，自包含的方法用于通信双方之间以JSON对象的形式安全的传递信息。因为数字签名的存在，这些信息是可信的，JWT可以使用HMAC算法或者是RSA的公私秘钥对进行签名。

![JWT原理](doc/image/jwt/1.png)

### 5.1.2. 应用场景

身份认证在这种场景下，一旦用户完成了登陆，在接下来的每个请求中包含JWT，可以用来验证用户身份以及对路由，服务和资源的访问权限进行验证。由于它的开销非常小，可以轻松的在不同域名的系统中传递，所有目前在单点登录（SSO）中比较广泛的使用了该技术。 信息交换在通信的双方之间使用JWT对数据进行编码是一种非常安全的方式，由于它的信息是经过签名的，可以确保发送者发送的信息是没有经过伪造的。

### 5.1.3. 特点

- 简洁(Compact): 可以通过URL，POST参数或者在HTTP header发送，因为数据量小，传输速度也很快
- 自包含(Self-contained)：负载中包含了所有用户所需要的信息，避免了多次查询数据库
- 因为Token是以JSON加密的形式保存在客户端的，所以JWT是跨语言的，原则上任何web形式都支持。
- 不需要在服务端保存会话信息，特别适用于分布式微服务。

### 5.1.4. 结构

WT是由三段信息构成的，将这三段信息文本用.连接一起就构成了JWT字符串。

~~~
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiYWRtaW4iOnRydWV9.TJVA95OrM7E2cBab30RMHrHDcEfxjoYZgeFONFh7HgQ
~~~

JWT包含了三部分：
- Header 头部(标题包含了令牌的元数据，并且包含签名和/或加密算法的类型)
- Payload 负载 (类似于飞机上承载的物品)
- Signature 签名/签证

#### 5.1.4.1. Header

JWT的头部承载两部分信息：token类型和采用的加密算法

~~~
{ 
  "alg": "HS256",
   "typ": "JWT"
} 
~~~
声明类型:这里是jwt
声明加密的算法:通常直接使用 HMAC SHA256

#### 5.1.4.2. Payload

载荷就是存放有效信息的地方。
有效信息包含三个部分:
- 标准中注册的声明
- 公共的声明
- 私有的声明

#### 5.1.4.3. Signature

jwt的第三部分是一个签证信息，这个签证信息由三部分组成：
header (base64后的)
payload (base64后的)
secret
这个部分需要base64加密后的header和base64加密后的payload使用.连接组成的字符串，然后通过header中声明的加密方式进行加盐secret组合加密，然后就构成了jwt的第三部分。
密钥secret是保存在服务端的，服务端会根据这个密钥进行生成token和进行验证，所以需要保护好。

### 5.1.5. 环境集成

#### 5.1.5.1. 加入依赖包

~~~
    <dependency>
        <groupId>com.auth0</groupId>
        <artifactId>java-jwt</artifactId>
        <version>${JWT.VERSION}</version>
    </dependency>
~~~

#### 5.1.5.2. 自定义一个实体类

使用lombok简化实体类的编写

~~~
@Data
public class User {
    private Long userId;
    private String username;
    private int age;
    private int sex;


    public static User getAuther(){
        User auther = new User();
        auther.setUserId(1l);
        auther.setUsername("帅大叔");
        auther.setAge(24);
        auther.setSex(1);
        return auther;
    }
}
~~~

#### 5.1.5.3. 生成Token方法

~~~
public String createToken(Algorithm algorithm,Object data){
    String[] audience  = {"app","web"};
    return JWT.create()
            .withIssuer("rstyro")   //发布者
            .withSubject("test")    //主题
            .withAudience(audience)     //观众，相当于接受者
            .withIssuedAt(new Date())   // 生成签名的时间
            .withExpiresAt(DateUtils.offset(new Date(),2, Calendar.HOUR_OF_DAY))    // 生成签名的有效期,分钟
            .withClaim("data", JSON.toJSONString(data)) //存数据
            .withNotBefore(new Date())  //生效时间
            .withJWTId(UUID.randomUUID().toString())    //编号
            .sign(algorithm);
}
~~~

#### 5.1.5.4. 验证token返回数据

~~~
public Response getDataByToken(JwtDto jwtdto) throws Exception{
    Algorithm algorithm =null;
    DecodedJWT verify =null;
    if(StringUtils.isEmpty(jwtdto.getAlg())){
        throw new WeathertopRuntimeException(ResponseCode.ALGORITHM_CAN_NOT_NULL);
    }
    if("rs256".equalsIgnoreCase(jwtdto.getAlg())){
        algorithm = Algorithm.RSA256(CreateSecrteKey.getRSA256Key().getPublicKey(), null);
    }else {
        algorithm = Algorithm.HMAC256(SECRET);
    }
    JWTVerifier verifier = JWT.require(algorithm)
            .withIssuer("rstyro")
            .build();
    try {
        verify = verifier.verify(jwtdto.getToken());
    }catch (TokenExpiredException ex){
        throw new WeathertopRuntimeException(ResponseCode.TOKEN_EXPIRED);
    }catch (JWTVerificationException ex){
        throw new JWTVerificationException(ResponseCode.SIGN_VERIFI_ERROR.getMsg());
    }
    String dataString = verify.getClaim("data").asString();

    Response response = new Response();
    response.setData(JSON.parseObject(dataString,User.class));
    return response;
}
~~~

### 5.1.6. 基于Jwt登陆用户认证实战



## 5.2. springboot-generator自动生成代码




## 5.3. 消息Kafka

### 5.3.1. 应用集成

加入依赖包

~~~
    <dependency>
        <groupId>org.springframework.kafka</groupId>
        <artifactId>spring-kafka</artifactId>
    </dependency>
~~~

#### 5.3.1.1. 生产者

- application.yml

~~~
spring:
  kafka:
    bootstrap-servers: 192.168.147.129:9092
    producer:
      retries: 0
      batch-size: 16384
      buffer-memory: 33554432
      key-serializer: org.apache.kafka.common.serialization.StringSerializer
      value-serializer: org.apache.kafka.common.serialization.StringSerializer
      properties:
        linger.ms: 1
~~~

- 发送消息

~~~
@RequestMapping("/kafka")
@RestController
public class TestKafkaProducerController {

    private Logger LOG = LoggerFactory.getLogger(TestKafkaProducerController.class);

    @Autowired
    private KafkaTemplate<String, String> kafkaTemplate;

    @RequestMapping("/send")
    public Response send(){
        String topic = "wongs";
        User user = User.getAuther();
        Response response = new Response();
        response.setData(user);
        String data = JSONObject.toJSON(user).toString();
        ListenableFuture<SendResult<String, String>> future = kafkaTemplate.send(topic, data);
        future.addCallback(new ListenableFutureCallback<SendResult<String, String>>() {
            @Override
            public void onFailure(Throwable ex) {
                LOG.error("kafka sendMessage error, ex = {}, topic = {}, data = {}", ex, topic, data);
            }

            @Override
            public void onSuccess(SendResult<String, String> result) {
                LOG.info("kafka sendMessage success topic = {}, data = {}",topic, data);
            }
        });
        return response;
    }
}
~~~

#### 5.3.1.2. 消费者

- application.yml

~~~
spring:
  kafka:
    bootstrap-servers: 192.168.147.129:9092
    consumer:
      group-id: test-consumer-group
      enable-auto-commit: true
      auto-commit-interval: 1000ms
      key-deserializer: org.apache.kafka.common.serialization.StringDeserializer
      value-deserializer: org.apache.kafka.common.serialization.StringDeserializer
      properties:
        session.timeout.ms: 15000
~~~

- 监听

~~~
@Slf4j
@Component
public class TestConsumer {

    @KafkaListener(topics = {"wongs"})
    public void listen (ConsumerRecord<?, ?> record) throws Exception {
        Optional<?> kafkaMessage = Optional.ofNullable(record.value());
        if (kafkaMessage.isPresent()) {
            Object message = kafkaMessage.get();
            log.info("----------------- record =" + record);
            log.info("------------------ message =" + message);
        }
    }
}

~~~

#### 5.3.1.3. 演示

![MQ生产端](doc/image/kafka/04-kafka-server.png)

![MQ消费端](doc/image/kafka/03-kafka-client.png)

# 6. Linux说明

## 6.1. 总体说明

### 6.1.1. 查看版本当前操作系统内核信息

~~~
[root@localhost ~]# uname -a
Linux localhost.localdomain 3.10.0-1062.1.1.el7.x86_64 #1 SMP Fri Sep 13 22:55:44 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
~~~

### 6.1.2. 查看当前操作系统版本信息

~~~
[root@localhost ~]# cat /proc/version
Linux version 3.10.0-1062.1.1.el7.x86_64 (mockbuild@kbuilder.bsys.centos.org) (gcc version 4.8.5 20150623 (Red Hat 4.8.5-39) (GCC) ) #1 SMP Fri Sep 13 22:55:44 UTC 2019
~~~

### 6.1.3. 查看版本当前操作系统发行版信息

~~~
[root@localhost ~]# cat /etc/redhat-release
CentOS Linux release 7.7.1908 (Core)
~~~

### 6.1.4. 查看cpu相关信息，包括型号、主频、内核信息等

~~~

[root@localhost ~]# cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 94
model name	: Intel(R) Core(TM) i5-6300HQ CPU @ 2.30GHz
stepping	: 3
microcode	: 0xc6
cpu MHz		: 2303.999
cache size	: 6144 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 22
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ss syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon nopl xtopology tsc_reliable nonstop_tsc eagerfpu pni pclmulqdq ssse3 fma cx16 pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer xsave avx f16c rdrand hypervisor lahf_lm abm 3dnowprefetch invpcid_single ssbd ibrs ibpb stibp fsgsbase tsc_adjust bmi1 hle avx2 smep bmi2 invpcid rtm rdseed adx smap xsaveopt arat spec_ctrl intel_stibp flush_l1d arch_capabilities
bogomips	: 4607.99
clflush size	: 64
cache_alignment	: 64
address sizes	: 42 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 94
model name	: Intel(R) Core(TM) i5-6300HQ CPU @ 2.30GHz
stepping	: 3
microcode	: 0xc6
cpu MHz		: 2303.999
cache size	: 6144 KB
physical id	: 2
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 2
initial apicid	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 22
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ss syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon nopl xtopology tsc_reliable nonstop_tsc eagerfpu pni pclmulqdq ssse3 fma cx16 pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer xsave avx f16c rdrand hypervisor lahf_lm abm 3dnowprefetch invpcid_single ssbd ibrs ibpb stibp fsgsbase tsc_adjust bmi1 hle avx2 smep bmi2 invpcid rtm rdseed adx smap xsaveopt arat spec_ctrl intel_stibp flush_l1d arch_capabilities
bogomips	: 4607.99
clflush size	: 64
cache_alignment	: 64
address sizes	: 42 bits physical, 48 bits virtual
power management:

~~~

## 6.2. 系统配置

### 6.2.1. 内存
~~~
[root@localhost ~]# free -ml
              total        used        free      shared  buff/cache   available
Mem:           3770         124        3547          11          98        3473
Low:           3770         223        3547
High:             0           0           0
Swap:          2047           0        2047

~~~

### 6.2.2. 磁盘

~~~

[root@localhost ~]# df -h
文件系统                 容量  已用  可用 已用% 挂载点
devtmpfs                 1.9G     0  1.9G    0% /dev
tmpfs                    1.9G     0  1.9G    0% /dev/shm
tmpfs                    1.9G   12M  1.9G    1% /run
tmpfs                    1.9G     0  1.9G    0% /sys/fs/cgroup
/dev/mapper/centos-root   18G  8.9G  8.6G   51% /
/dev/sda1                497M  165M  332M   34% /boot
tmpfs                    378M     0  378M    0% /run/user/0

~~~

## 6.3. Linux优化

### 6.3.1. 运行级别Runlevel

- 查看运行级别的方法依旧使用
~~~
[root@localhost ~]# runlevel
N 3


[root@localhost ~]# ls -lh /usr/lib/systemd/system/runlevel*.target
lrwxrwxrwx. 1 root root 15 9月  30 18:00 /usr/lib/systemd/system/runlevel0.target -> poweroff.target
lrwxrwxrwx. 1 root root 13 9月  30 18:00 /usr/lib/systemd/system/runlevel1.target -> rescue.target
lrwxrwxrwx. 1 root root 17 9月  30 18:00 /usr/lib/systemd/system/runlevel2.target -> multi-user.target
lrwxrwxrwx. 1 root root 17 9月  30 18:00 /usr/lib/systemd/system/runlevel3.target -> multi-user.target
lrwxrwxrwx. 1 root root 17 9月  30 18:00 /usr/lib/systemd/system/runlevel4.target -> multi-user.target
lrwxrwxrwx. 1 root root 16 9月  30 18:00 /usr/lib/systemd/system/runlevel5.target -> graphical.target
lrwxrwxrwx. 1 root root 13 9月  30 18:00 /usr/lib/systemd/system/runlevel6.target -> reboot.target

~~~

- 设置运行级别

~~~
[root@localhost ~]# systemctl get-default multi-user.target
Invalid number of arguments.

~~~

- 查看运行级别

~~~
[root@localhost ~]# systemctl get-default
multi-user.target
~~~

### 6.3.2. systemd一统天下

查看系统启动文件的目录

~~~
[root@localhost ~]# ls /usr/lib/systemd/system
auditd.service                          initrd.target.wants                 rescue.target                                  systemd-halt.service
autovt@.service                         initrd-udevadm-cleanup-db.service   rescue.target.wants                            systemd-hibernate-resume@.service
basic.target                            iprdump.service                     rhel-autorelabel-mark.service                  systemd-hibernate.service
basic.target.wants                      iprinit.service                     rhel-autorelabel.service                       systemd-hostnamed.service
blk-availability.service                iprupdate.service 
~~~

## 6.4. 开机时间优化

### 6.4.1. 查看开机时间

~~~
[root@localhost ~]# systemd-analyze time
Startup finished in 1.375s (kernel) + 1.928s (initrd) + 3.233s (userspace) = 6.537s

~~~

### 6.4.2. 查看具体的使用时间

~~~
[root@localhost ~]# systemd-analyze blame
          1.439s dev-mapper-centos\x2droot.device
           653ms boot.mount
           604ms lvm2-pvscan@8:2.service
           391ms tuned.service
           362ms systemd-tmpfiles-clean.service
           360ms network.service
           236ms NetworkManager-wait-online.service
           119ms systemd-udev-trigger.service
           108ms systemd-vconsole-setup.service
~~~

### 6.4.3. 启动项优化

~~~

[root@localhost ~]# systemctl list-unit-files|egrep "^ab|^aud|^kdump|vm|^md|^mic|^post|lvm"  |awk '{print $1}'|sed -r 's#(.*)#systemctl disable &#g'|bash
Removed symlink /etc/systemd/system/multi-user.target.wants/auditd.service.
Removed symlink /etc/systemd/system/multi-user.target.wants/kdump.service.
Removed symlink /etc/systemd/system/sysinit.target.wants/lvm2-monitor.service.
Failed to execute operation: Unit name lvm2-pvscan@.service is missing the instance name.
Removed symlink /etc/systemd/system/basic.target.wants/microcode.service.
Removed symlink /etc/systemd/system/multi-user.target.wants/postfix.service.
Removed symlink /etc/systemd/system/sysinit.target.wants/lvm2-lvmetad.socket.
Removed symlink /etc/systemd/system/sysinit.target.wants/lvm2-lvmpolld.socket.

~~~

### 6.4.4. Selinux的优化

~~~
[root@localhost ~]# sed -i 's#SELINUX=enforcing#SELINUX=disabled#g' /etc/selinux/config
~~~

### 6.4.5. ssh的优化

/etc/ssh/sshd_config文件中修改<font color=red>GSSAPIAuthentication no、UseDNS no</font>，然后重启sshd服务即可。

# 7. 消息MQ

## 7.1. Kafka

### 7.1.1. kafka安装

[官方kafka_2.12-2.3.0下载](https://mirrors.tuna.tsinghua.edu.cn/apache/kafka/2.3.0/kafka_2.12-2.3.0.tgz)

<font color=red>**解压重命名等步骤略过，这些在Linux下通用操作，不懂问百度**</font>


### 7.1.2. 编写配置文件

修改/data/kafka/config/server.properties，主要有以下

~~~

host.name=192.168.147.132

broker.id=0
port=9092

listeners=PLAINTEXT://192.168.147.132:9092
advertised.listeners=PLAINTEXT://192.168.147.132:9092
log.dirs=/data/kafka/tmp/kafka-logs

zookeeper.connect=localhost:2181
~~~

### 7.1.3. 启动

方便的话，编写一个启动脚本，不然每次挨个启动Zookeeper和Kafka，甚是麻烦

kafkastart.sh

~~~

!/bin/sh

sh $zookeeper_home/bin/zkServer.sh start &

sleep 12

sh /data/app/kafka/bin/kafka-server-start.sh  /data/app/kafka/config/server.properties &

~~~

### 7.1.4. 创建Topic

~~~
sh kafka-topics.sh --create --zookeeper 192.168.147.129:2181 --replication-factor 1 --partitions 1 --topic wongs
~~~

![图片alt](doc/image/kafka/01-kafka-create-topic.png)

### 7.1.5. 查看Topic

~~~
sh kafka-topics.sh --list --zookeeper 192.168.147.129:2181
~~~

![图片alt](doc/image/kafka/02-kafka-list-topic.png)

# 8. elasticsearch

[详细查看elastic入门](akkad-springboot/springboot-elasticsearch/elastic.md)，介绍了安装，以及集成SpringBoot

# 9. zookeeper安装

## 9.1. 下载

[官方zookeeper下载](https://zookeeper.apache.org/releases.html)，下载ZooKeeper，目前最新的稳定版本为 3.5.5 版本，用户可以自行选择一个速度较快的镜像来下载即可.

这边演示用的版本**zookeeper-3.4.13.tar.gz**

~~~

[root@localhost download]$ mv /data/zookeeper-3.4.13/ ../app/zookeeper/

~~~


## 9.2. 配置安装

- `修改配置文件`

路径/data/zookeeper-3.4.13/conf/下的**zoo_sample.cfg** 改名为**zoo.cfg**

~~~

数据文件存放目录
dataDir=/data/zookeeper-3.4.13/data/tmp
日志存放目录
dataLogDir=/data/zookeeper-3.4.13/data/log

~~~

- `启动`

~~~
[root@localhost zookeeper]$ cd ../app/zookeeper/
[root@localhost zookeeper]$ sh bin/zkServer.sh start &
~~~

![图片alt](doc/image/zk/01-start.png)



# 10. hadoop学习

环境须知：
- CentOS7
- hadoop-3.1.2.tar.gz
- jdk8

Hadoop环境需要JAVA环境，所以首先得安装Java。

## 10.1. 伪分布式环境部署

### 10.1.1. 创建用户组、用户

~~~
[root@localhost app]$  groupadd dev
[root@localhost app]$  adduser hadoop
[root@localhost app]$  passwd hadoop
~~~

### 10.1.2. ssh安装配置免密登陆

~~~
[root@localhost app]$  su hadoop
[hadoop@localhost hadoop]$ ssh-keygen -t rsa
[hadoop@localhost hadoop]$ cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys
[hadoop@localhost hadoop]$ chmod 0600 ~/.ssh/authorized_keys
~~~

测试输入
~~~
[hadoop@localhost hadoop]$  ssh localhost
~~~

### 10.1.3. hadoop安装

#### 10.1.3.1. 下载

[Hadoop下载](https://mirrors.cnnic.cn/apache/hadoop/common/hadoop-3.1.2/hadoop-3.1.2.tar.gz)

~~~
[hadoop@localhost hadoop]$  wget https://mirrors.cnnic.cn/apache/hadoop/common/hadoop-3.1.2/hadoop-3.1.2.tar.gz

[hadoop@localhost hadoop]$  tar zxvf hadoop-3.1.2.tar.gz

[hadoop@localhost hadoop]$  mv hadoop-3.1.2/ /data/app/hadoop/
~~~

#### 10.1.3.2. 配置

- etc/hadoop/core-site.xml，configuration配置为
~~~
<configuration>
    <property>
        <name>fs.defaultFS</name>
        <value>hdfs://localhost:9000</value>
    </property>
</configuration>
~~~

- 设置环境变量

~~~
export HADOOP_HOME=/data/app/hadoop/
export HADOOP_CONF_DIR=$HADOOP_HOME/etc/hadoop/
export HADOOP_COMMON_LIB_NATIVE_DIR=$HADOOP_HOME/lib/native/
export HADOOP_OPTS="-Djava.library.path=$HADOOP_HOME/lib"
~~~

~~~
[hadoop@localhost hadoop]$  vi ~/.bashrc
[hadoop@localhost hadoop]$  source ~/.bashrc
~~~

- 设置JAVA_HOME
etc/hadoop/hadoop-env.sh
~~~
export JAVA_HOME=/data/app/jdk8
~~~

- 初始化 格式化HDFS

~~~
[hadoop@localhost hadoop]$ pwd
/data/app/hadoop
[hadoop@localhost hadoop]$ ./bin/hdfs namenode -format

~~~

- 启动NameNode和DataNode

~~~
[hadoop@localhost hadoop]$ ./sbin/start-dfs.sh
~~~

<font color=red>**输入地址查看：**<font/>http://192.168.147.132:9870/

![查看NameNode](doc/image/hadoop/1.png)

- 配置YARN

编辑etc/hadoop/mapred-site.xml，configuration配置为

~~~
<configuration>
    <property>
        <name>mapreduce.framework.name</name>
        <value>yarn</value>
    </property>
</configuration>
~~~

编辑etc/hadoop/yarn-site.xml，configuration配置为

~~~
<configuration>
    <property>
        <name>yarn.nodemanager.aux-services</name>
        <value>mapreduce_shuffle</value>
    </property>
</configuration>
~~~

- 启动YARN

~~~
[hadoop@localhost hadoop]$ ./sbin/start-yarn.sh
~~~

<font color=red>**输入地址查看：**<font/>http://192.168.147.132:8088/cluster
![查看YARN](doc/image/hadoop/2.png)

- 启动与停止
~~~
[hadoop@localhost hadoop]$ ./sbin/start-dfs.sh
[hadoop@localhost hadoop]$ ./sbin/start-yarn.sh

[hadoop@localhost hadoop]$ ./sbin/stop-dfs.sh
[hadoop@localhost hadoop]$ ./sbin/stop-yarn.sh
~~~

### 10.1.4. HBase安装

#### 10.1.4.1. 单机HBase配置

- conf/hbase-site.xml，configuration配置为

~~~
<configuration>
  <property>
    <name>hbase.rootdir</name>
    <value>hdfs://localhost:9012/hbase</value>
  </property>
  <property>
    <name>hbase.zookeeper.property.dataDir</name>
    <value>/home/hadoop/zookeeper</value>
  </property>
</configuration>
~~~

- 启动与关闭
~~~
[hadoop@localhost hbase]$   ./bin/start-hbase.sh

[hadoop@localhost hbase]$   ./bin/stop-hbase.sh
~~~

- jps查看

![查看NameNode](doc/image/hbase/1.png)

- 终端

~~~
[hadoop@localhost hbase]$   ./bin/hbase shell
~~~

- 禁用自带Zookeeper
conf/hbase-env.sh
~~~
[hadoop@localhost hbase]$   vi conf/hbase-env.sh
~~~

![查看NameNode](doc/image/hbase/2.png)

- 配置独立Zookeeper

这是官方文档推荐的做法，如果不拷贝 zoo.cfg，在 hbase-site.xml 中也可以对Zookeeper进行相关配置，但HBase会优先使用 zoo.cfg（如果有的话）的配置
~~~
[hadoop@localhost hbase]$   cp ../zookeeper/conf/zoo.cfg conf/
~~~

- hbase-site.xml配置

~~~
<property>
     <name>hbase.cluster.distributed</name>
     <value>true</value>
</property>
~~~

- 启动Zookeeper

~~~
[hadoop@localhost zookeeper]$ sh bin/zkServer.sh start
ZooKeeper JMX enabled by default
Using config: /data/app/zookeeper/bin/../conf/zoo.cfg
Starting zookeeper ... STARTED
~~~

#### 10.1.4.2. 集群模式<待补充>

### 10.1.5. Phoenix安装

版本要与HBase相匹配！

### 10.1.6. hive安装

[Hive下载](https://mirrors.tuna.tsinghua.edu.cn/apache/hive/hive-3.1.2/apache-hive-3.1.2-bin.tar.gz)

~~~
[hadoop@localhost hadoop]$  wget https://mirrors.tuna.tsinghua.edu.cn/apache/hive/hive-3.1.2/apache-hive-3.1.2-bin.tar.gz

[hadoop@localhost hadoop]$  tar zxvf apache-hive-3.1.2-bin.tar.gz

[hadoop@localhost hadoop]$  mv apache-hive-3.1.2 /data/app/haddop/
~~~