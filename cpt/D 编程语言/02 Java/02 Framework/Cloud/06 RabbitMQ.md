




31预取值还没看




# RabbitMQ

https://www.rabbitmq.com
https://www.rabbitmq.com/download.html
https://www.rabbitmq.com/documentation.html


2007年发布,是一个在AMQP(高级消息队列协议)基础上完成的,可复用的企业消息系统,是当前最主流的消息中间件之一.性能好时效性微秒级,社区活跃度高,界面管理十分方便,中小型公司优先选择功能比较完备的RabbitMQ.
优点:由于Erlang语言的高并发特性,性能较好,吞吐量到万级,MQ功能比较完备,健壮,稳定,易用,跨平台,支持多种语言,如Python,Ruby,.NET,Java,JMS,C,PHP,ActionScript,XMPP,STOMP等,支持AJAX文档齐全,开源提供的管理界面非常棒,用起来很好用,社区活跃度高,更新频率相当高.
缺点:商业版需要收费,学习成本高



RabbitMQ是基于Erlang语言开发的开源消息通信中间件

Publisher发布者 -> (exchange交换机 -> queue消息队列)VirtualHost虚拟机Broker -> Consumer消费者

Connection: publisher/consumer/broker之间的TCP连接
Channel: 与MQ通信的工具,作为轻量级的Connection减少了操作系统建立TCP连接的开销

Virtualhost: 虚拟主机,是对queue,exchange等资源的逻辑分组,出于多用户和安全考虑,把AMQP划分到一个虚拟分组中.

Broker: 接受和分发消息的应用,RabbitMQ Server就是Message Broker.
Exchange: 路由消息到队列中,匹配routing key,分发消息到queue中,常用的类型有:direct(point-to-point),topic(publish-subscribe)and fanout(multicast)
Queue: 缓存消息.
Binding: exchange和queue之间的虚拟连接,binding中可以包含routing key,Binding信息被保存到exchange中查询表中,用于message的分发依据.

Producer 发布者
Consumer 消费者

消息应答: 消息在收到时,告诉RabbitMQ已被处理,RabbitMQ则删除该消息,如果消息中断,则丢失.保证消息不丢失.
自动应答: 在高吞吐量和数据传输安全方面做权衡,容易丢失数据.仅适用于高效并以某种速率能够处理这些消息的情况下使用.
手动应答: 手动发送ACK确认.
消息重新入队: 如果消息由于某些原因丢失(通道关闭,连接关闭TCP连接丢失),未发送ACK确认,会将消息重新入队,可能会由其他消费者处理.


# 安装

两个包的下载地址,过段时间链接可能有变
https://github.com/rabbitmq/rabbitmq-server/releases?page=11
https://github.com/rabbitmq/erlang-rpm/releases?page=15

```bash
erlang-21.3.1-1.el7.x86_64.rpm
rabbitmq-server-3.8.8-1.el7.noarch.rpm


# install erlang and rabbitmq
rpm -ivh erlang.rpm
yum install socat logrotate -y
rpm -ivh rabbitmq.rpm

# 设置开机自动启动
chkconfig rabbitmq-server on
# 启动服务 停止重启状态
/sbin/service rabbitmq-server start
/sbin/service rabbitmq-server stop
/sbin/service rabbitmq-server restart
/sbin/service rabbitmq-server status

# 开启web管理插件
rabbitmq-plugins enable rabbitmq_management
http://192.168.0.101:15672 默认账号密码guest guest

# 查看当前用户和角色
rabbitmqctl list_users
# 设置用户
rabbitmqctl add_user admin 123
# 设置角色
rabbitmqctl set_user_tags admin administrator

# 设置用户权限,用户具有/vhost1这个资源的配置,写,读权限
rabbitmqctl set_permissions [-p <vhostpath>] <user> <conf> <write> <read>
rabbitmqctl set_permissions -p "/" admin ".*" ".*" ".*"


# docker rabbitmq添加账户
docker exec -it rabbitmq /bin/bash
rabbitmq-plugins enable rabbitmq_management # 开启登录页管理
rabbitmqctl add_user admin 123 # 添加账户
rabbitmqctl set_user_tags admin administrator # 赋予administrator角色
rabbitmqctl set_permissions -p / admin ".*" ".*" ".*" # 赋予权限
rabbitmqctl list_users # 查看角色
rabbitmq-server restart # 重启rabbitmq,不要重启容器


```






# 代码

消息模型
Basic Queue 基本消息队列
Work Queue 工作消息队列
Publish,Subscribe 发布订阅 
Fanout Exchange 广播
Direct Exchange 路由
Topic Exchange 主题


Hello World 消息队列
Work queues 工作消息队列
Publish/Subscribe 发布订阅
Routing 路由
Topics 主题
Request/reply/pattern
Publisher Confirms


```java

// com.rabbitmq:amqp-client:5.8.0 rabbitmq客户端依赖
// commons-io:commons-io:2.6 文件IO流依赖




```



# 基本消息队列

https://www.rabbitmq.com/tutorials/tutorial-one-java.html

Producer -> RabbitMQ -> Consumer
生产者发送单个消息,消费者接收消息并打印


```java
public class Producer {
    private final static String QUEUE_NAME = "hello";
    //生产者,目的是发送消息给队列
    public static void main(String[] argv) throws IOException, TimeoutException {
        //连接工厂
        ConnectionFactory connectionFactory = new ConnectionFactory();
        //设置连接参数
        connectionFactory.setHost("192.168.0.105");
        connectionFactory.setUsername("admin");
        connectionFactory.setPassword("123");
        //创建连接件
        Connection connection = connectionFactory.newConnection();
        //获取信道
        Channel channel = connection.createChannel();
        //生成队列,队列名称,是否持久化,是否消息共享,是否自动删除,其他参数
        channel.queueDeclare(QUEUE_NAME, false, false, false, null);
        //发送消息
        String message = "Hello World!";
        channel.basicPublish("", QUEUE_NAME, null, message.getBytes());
        System.out.println(" [x] Send '" + message + "'");
    }
}


public class Consummer {
    private final static String QUEUE_NAME = "hello";
    //消费者,接受消息
    public static void main(String[] args) throws IOException, TimeoutException {
        //连接工厂
        ConnectionFactory connectionFactory = new ConnectionFactory();
        //设置连接参数
        connectionFactory.setHost("192.168.0.105");
        connectionFactory.setUsername("admin");
        connectionFactory.setPassword("123");
        //创建连接件
        Connection connection = connectionFactory.newConnection();
        //获取信道
        Channel channel = connection.createChannel();
        //消息声明
        DeliverCallback deliverCallback = (consumerTag, delivery) -> {
            String message = new String(delivery.getBody());
            System.out.println("deliverCallback: " + message);
        };
        CancelCallback cancelCallback = consumerTag -> System.out.println("cancelCallback: 消息被中断");
        //消费者接收消息,消费队列名,是否自动应答,未成功回调,取消回调
        channel.basicConsume(QUEUE_NAME, true, deliverCallback, cancelCallback);
    }
}

```


# 工作消息队列
避免立即执行资源密集型任务,把任务封装为消息并将其发送到队列.通过轮询在两个接收者之间依次调用.

生产者大量发消息->队列->工作线程(多个线程同时处理)


```java

public class Task01 {
    //生产者,发送大量消息
    //队列名称
    public static final String QUEUE_NAME = "hello";
    public static void main(String[] args) throws IOException, TimeoutException {
        Channel channel = RabbitMqUtils.getChannel();
        channel.queueDeclare(QUEUE_NAME, false, false, false, null);
        for (int i = 0; i < 100; i++) {
            String message = new String((i + 1) + "aaa");
            channel.basicPublish("", QUEUE_NAME, null, message.getBytes());
            System.out.println(" [x] Send '" + message + "'");
        }
    }
}


public class Work01 {
    //这是一个工作线程,消费者的其中一个线程
    public static final String QUEUE_NAME = "hello";
    //接受消息
    public static void main(String[] args) throws IOException, TimeoutException {
        Channel channel = RabbitMqUtils.getChannel();
        DeliverCallback deliverCallback = (consumerTag, delivery) -> {
            System.out.println("deliverCallback: " + new String(delivery.getBody()));
        };
        CancelCallback cancelCallback = (consumerTag) -> {
            System.out.println(consumerTag + "消息被中断");
        };
        System.out.println("C1等待接受消息...");
        //消息接收
        channel.basicConsume(QUEUE_NAME, true, deliverCallback, cancelCallback);
    }
}

public class Work02 {
    //这是一个工作线程,消费者的其中一个线程
    public static final String QUEUE_NAME = "hello";
    //接受消息
    public static void main(String[] args) throws IOException, TimeoutException {
        Channel channel = RabbitMqUtils.getChannel();
        DeliverCallback deliverCallback = (consumerTag, delivery) -> {
            System.out.println("deliverCallback: " + new String(delivery.getBody()));
        };
        CancelCallback cancelCallback = (consumerTag) -> {
            System.out.println(consumerTag + "消息被中断");
        };
        System.out.println("C2等待接受消息...");
        //消息接收
        channel.basicConsume(QUEUE_NAME, true, deliverCallback, cancelCallback);
    }
}

```



# 消息应答

```java
// multiple 手动应答的好处是可以批量应答并减少网络拥堵
// 批量应答指只接收最后一个值,不批量应答需要接收每一个参数的编号
// 第二个参数表示批量处理参数,true批量,false不批量
channel.basicAck(deliveryTag, true); 
channel.basicAck(); // 用于肯定确认,已知道该消息并且成功处理,可以丢弃了
channel.basicNack(); // 用于否定确认
channel.basicReject(); // 用于否定确认,比上一个否定确认少一个参数

//生产者发布若干条消息,其中一个消费者挂掉,另一个消费者可以处理未处理完的消息
public class Task01 {
    //生产者,发送大量消息
    //队列名称
    public static final String TASK_QUEUE_NAME = "hello";
    public static void main(String[] args) throws IOException, TimeoutException {
        Channel channel = RabbitMqUtils.getChannel();
        channel.queueDeclare(TASK_QUEUE_NAME, false, false, false, null);
        for (int i = 0; i < 2; i++) {
            String message = new String((i + 1) + "aaa");
            channel.basicPublish("", TASK_QUEUE_NAME, null, message.getBytes("UTF-8"));
            System.out.println(" [x] Send '" + message + "'");
        }
    }
}

public class Work01 {
    //这是一个工作线程,消费者的其中一个线程
    public static final String TASK_QUEUE_NAME = "hello";
    //接受消息
    public static void main(String[] args) throws Exception {
        Channel channel = RabbitMqUtils.getChannel();
        DeliverCallback deliverCallback = (consumerTag, delivery) -> {
            try {
                //C1处理消息较快
                Thread.sleep(1000 * 2);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            System.out.println("deliverCallback: " + new String(delivery.getBody()));
            //消息应答,前一个参数表示消息的标记,后一个参数表示是否批量
            channel.basicAck(delivery.getEnvelope().getDeliveryTag(), false);
        };
        CancelCallback cancelCallback = (consumerTag) -> {
            System.out.println(consumerTag + "消息被中断");
        };
        System.out.println("C1等待接受消息...");
        //手动应答
        boolean autoAck = false;
        channel.basicConsume(TASK_QUEUE_NAME, autoAck, deliverCallback, cancelCallback);
    }
}

public class Work02 {
    //这是一个工作线程,消费者的其中一个线程
    public static final String TASK_QUEUE_NAME = "hello";
    //接受消息
    public static void main(String[] args) throws IOException, TimeoutException {
        Channel channel = RabbitMqUtils.getChannel();
        DeliverCallback deliverCallback = (consumerTag, delivery) -> {
            try {
                //C2处理消息较慢
                Thread.sleep(1000 * 15);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            System.out.println("deliverCallback: " + new String(delivery.getBody()));
            channel.basicAck(delivery.getEnvelope().getDeliveryTag(), false);
        };
        CancelCallback cancelCallback = (consumerTag) -> {
            System.out.println(consumerTag + "消息被中断");
        };
        System.out.println("C2等待接受消息...");
        //手动应答
        boolean autoAck = false;
        channel.basicConsume(TASK_QUEUE_NAME, autoAck, deliverCallback, cancelCallback);
    }
}


```



# 分发
RabbitMQ默认是轮询分发,可以将其设置为不公平分发

```java
// 0轮询分发,1不公平分发
int prefetchCount = 1;
channel.basicQos(prefetchCount);

```


# 持久化

服务停止或者服务崩溃后消息不丢失,需要将队列和消息都标记为持久化.
持久化队列需要将原先的不持久化队列删除才能建立新的持久化队列.

```java

//生成队列,队列名称,是否持久化,是否消息共享,是否自动删除,其他参数
boolean durable = true; // 需要让queue持久化
channel.queueDeclare(QUEUE_NAME, durable, false, false, null);

//生产者发送消息持久化
channel.basicPublish("", TASK_QUEUE_NAME, MessageProperties.PERSISTENT_TEXT_PLAIN, message.getBytes("UTF-8"));


```

消息持久化





# Utils

```java
//此类为连接工厂创建信道的工具类
public class RabbitMqUtils {
  public static Channel getChannel() throws IOException, TimeoutException {
    ConnectionFactory connectionFactory = new ConnectionFactory();
    connectionFactory.setHost("192.168.0.105");
    connectionFactory.setUsername("admin");
    connectionFactory.setPassword("123");
    Connection connection = connectionFactory.newConnection();
    Channel channel = connection.createChannel();
    return channel;
  }
}

```


# heima

```java
// 基本消息队列
// 消息发布者
public class PublisherTest {
  @Test
  public void testSendMessage() throws IOException, TimeoutException {
    //建立连接
    ConnectionFactory factory = new ConnectionFactory();
    //设置连接参数
    factory.setHost("192.168.150.101");
    factory.setPort(5672);
    factory.setVirtualHost("/");
    factory.setUsername("itcast");
    factory.setPassword("123321");
    //建立连接
    Connection connection = factory.newConnection();
    //创建通道Channel
    Channel channel = conection.createChannel();
    //创建队列
    String cueueName = "simple.queue";
    channel.queueDeclare(queueName, false, false, false, null);
    //发送消息
    String message = "hello, rabbitmq!";
    channel.basicPublish("", queueName, null, message.getBytes());
    System.out.println("发送消息成功:{"+message+"}");
    //关闭通道和连接
    channel.close();
    connection.close();
  }
}

//消费者
public class ConsumerTest {
  public static void main(String[] args) throws IOException, TimeoutException {
    //建立连接
    ConnectionFactory factory = new ConnectionFactory();
    //设置连接参数,主机名,端口号,vhost,用户名,密码
    factory.setHost("192.168.150.101");
    factory.setPort(5672);
    factory.setVirtualHost("/");
    factory.setUsername("itcase");
    factory.setPassword("123321");
    //建立连接
    Connection connection = factory.newConection();
    //创建通道Channel
    Channel channel = connection.createChannel();
    //创建队列
    String queueName = "simple.queue";
    channel.queueDeclare(queueName, false, false, false, null);
    //订阅消息
    channel.basicConsume(queueName, true, new DefaultConsumer(channel){
      @Override
      public void handleDelivery(String consumerTag, Envelope envelope,
        AMQP.BasicProperties properties, byte[] body) throws IOException{
          //处理消息
          String message = new String(body);
          System.out.println("接收到消息:{"+message+"}");
        }
    });
    System.out.println("等待接收消息...");
  }
}

```




