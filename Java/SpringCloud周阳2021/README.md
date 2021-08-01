### 1、SpringCloud相关知识点

@Configuration+@Bean注解，将第三方的对象注入到容器中，之后就可以通过@Autowired注入

controller层增加数据，传入对象需要加@RequestBody注解，才能正常添加数据到数据库



工程重构：系统中有重复部分，entity中的实体类对象不需要每个微服务中都写



服务之间通过RestTemplate进行test风格的互相调用



### 2、Eureka服务注册中心

Eureka服务注册中心、服务提供者、消费者之间是一个三角形的结构

Eureka端口7001  Consumer80   Provider8001

Eureka注册中心(server)、服务提供者(client)的mainboot上都要加上eureka的注解

eureka集群：互相注册，保证高可用



Eureka7001、Eureka7002，修改映射host文件。服务端的实例名称需要设置不同

@Value可以从yml配置文件中获取到值



使用@LoadBalanced注解赋予RestTemplate负载均衡的能力，使服务集群高可用

之后介绍的Ribbon负载均衡也能实现轮询



Eureka自我保护：某时刻一个微服务不可用，Eureka不会立刻清理，依旧会对该微服务信息进行保存。防止因网络故障，导致误删除微服务

关闭自我保护，微服务故障，立即删除微服务



### 3、Zookeeper服务注册中心

SpringCloud整合Zookeeper替代Eureka

Zookeeper服务提供者加上@EnableDiscoveryClient注解

@RequestMapping url地址请求访问

zookeeper是临时节点



public static final String 进行常量命名，变量名为大写



### 4、Consul服务注册中心

服务提供者、消费者注册进consul

CAP

C：强一致性   A：可用性   P：分区容错性

AP(Eureka)   淘宝首先保证高可用性，而不是强一致性

ZP(Zookeeper/Consul)

