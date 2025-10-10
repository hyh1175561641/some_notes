

# Package java.lang

https://docs.oracle.com/javase/8/docs/api/index.html?java/lang/package-summary.html

## 装箱拆箱
```java
//装箱拆箱
//byte short int     long float double char boolean
//Byte Short Integer Long Float Double Character Boolean

//Number: public abstract class Number    extends Object implements Serializable
//Byte:      public final class Byte      extends Number implements Comparable<Byte>
//Short:     public final class Short     extends Number implements Comparable<Short>
//Integer:   public final class Integer   extends Number implements Comparable<Integer>
//Long:      public final class Long      extends Number implements Comparable<Long>
//Float:     public final class Float     extends Number implements Comparable<Float>
//Double:    public final class Double    extends Number implements Comparable<Double>
//Character: public final class Character extends Object implements Serializable, Comparable<Character>
//Boolean:   public final class Boolean   extends Object implements Serializable, Comparable<Boolean>

Integer i = new Integer(123);
String toString()//转为字符串
Integer valueOf("123");//这个函数可以传入很多类型的值，然后转化为对应的类型
int parseInt("100")//把String转换成基本类型
int intValue()//拆箱，返回int类型的值
int a = new Integer(100)//拆箱，把引用类型赋值给基本类型
int b = a + new Integer(100)//基本类型和引用类型能混合运算

Character c = new Character('a')//不能传入双引号字符串""
Boolean b = new Boolean("TrUe")//true不区分大小写，初次之外所有值都属于false

```


```java
//String: public final class String extends Object implements Serializable, Comparable<String>, CharSequence
//两种方法调用函数，一种是调用静态方法，一种是new引用类型
String.valueOf(byte[],offset,count)//字节数组转字符串，起始位置和长度
new String(byte[],off,len)//字节数组转字符串，起始位置和长度
String.valueOf(char[],offset,count)//字符数组转字符串，起始位置和长度
byte[] b="aaaa".getBytes()//把字符串转为字节数组

length()//字符串的长度
equals(String)//比较两个字符串是否相等
equalsIgnoreCase()//忽略大小写比较字符串
toLowerCase()//转小写
toUpperCase()//转大写
concat(String)//字符串拼接
indexOf("a")//找第一个字符，返回索引值
indexOf("a",formindex)//寻找第一个索引，从第几个开始寻找
lastIndexOf("a")//最后一个索引
lastIndexOf("a",formindex)//最后一个索引，从指定位置开始找起
substring(beginindex,endindex)//子字符串，开始位置结束位置
String trim()//去掉前后空格
String[] split(" ")//字符串分割，返回字符数组，指定字符是首字母会分割出空字符，指定字符是末尾字母不会分割出空字符

```


```java
//StringBuffer是可变字符串，遇到频繁更改拼接字符串时，使用StringBuffer
//StringBuffer和StringBuilder在用法上一样，StringBuffer是线程安全的效率低，StringBuilder是线程不安全的效率高
//StringBuffer: public final class StringBuffer extends Object implements Serializable, CharSequence
//StringBuilder: public final class StringBuilder extends Object implements Serializable, CharSequence

StringBuffer strbuff = new StringBuffer()//默认16长度的数组
StringBuffer strbuff = new StringBuffer(12)//指定默认长度12的数组
StringBuffer strbuff = new StringBuffer("String")//字符串长度+16长度
StringBuffer append("aaa")//追加字符串，返回this
StringBuffer insert(offset,str)//指定位置插入内容，返回this
int length()//返回字符串长度

```

```java
//System: public final class System extends Object
System.out // 返回一个PrintStream类
System.in // 返回一个InputStream类
System.exit(1);//退出虚拟机结束程序

String System.getProperty("file.encoding")//返回文件的字符编码


```


```java
//Math: public final class Math extends Object
Math.PI = 3.1415926548
Math.abs(-1);//绝对值
Math.max(100,10)//最大值
Math.min(100,10)//最小值
Math.random()//返回0-1的小数
(int)Math.random()*10//得到0-9的整数


```


# Package java.util

https://docs.oracle.com/javase/8/docs/api/index.html?java/util/package-summary.html

```java
//Scanner: public final class Scanner extends Object implements Iterator<String>, Closeable
Scanner sc = new Scanner(System.in);
String name = sc.next();
int age = sc.nextInt();

```

```java
//Random: public class Random extends Object implements Serializable
Random random = new Random(100)//构造方法传入一个种子
int nextInt(10)//获取0-10之间的随机整数

```

```java
//Calendar: public abstract class Calendar extends Object implements Serializable, Cloneable, Comparable<Calendar>
Calendar cale = new Calendar()//这个类是抽象的，不能实例化
Calendar cale = Calendar.getInstance()//获取 java.util.GregorianCalendar 对象
Calendar.YEAR
Calendar.MONTH//0-Jan 1-Feb
Calendar.DATE
Calendar.DAY_OF_MONTH
//1-Sunday 2-Monday 3-Tuesday 6-Friday
Calendar.DAY_OF_WEEK//一周中的第几天
Calendar.DAY_OF_YEAR//一年中的第几周

//设定具体的字段
cale.set(Calendar.YEAR,2022)
cale.set(Calendar.MONTH,0)//一月
cale.set(Calendar.DATE,1)//一日

```
        
```java
//Date: public class Date extends Object implements Serializable, Cloneable, Comparable<Date>
Date date = new Date()
long getTime()//System.currentTimeMillis()方法返回的结果一样，单位是毫秒，除以1000等于秒
SimpleDateFormat sf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss")
String formatDate = sf.format(date);

public class DateUtil {
    public static String dateToString(Date date) {
        SimpleDateFormat df = new SimpleDateFormat("yyyy-MM-dd");
        return df.format(date);}
    public static Date stringToDate(String string) throws ParseException {
        SimpleDateFormat sf = new SimpleDateFormat("yyyy-MM-dd");
        return sf.parse(string);}
}
```


```java
//properties文件
public static void main(String[] args) throws IOException {
    InputStream inputStream = Proper.class.getClassLoader().getResourceAsStream("jdbc.properties");
    Properties properties = new java.util.Properties();
    properties.load(inputStream);
    System.out.println(properties.getProperty("jdbc.driver"));
    System.out.println(properties.getProperty("jdbc.url"));
    System.out.println(properties.getProperty("jdbc.username"));
    System.out.println(properties.getProperty("jdbc.password"));
    
    ResourceBundle resourceBundle = ResourceBundle.getBundle("jdbc");
    System.out.println(resourceBundle.getString("jdbc.driver"));
    System.out.println(resourceBundle.getString("jdbc.url"));
    System.out.println(resourceBundle.getString("jdbc.username"));
    System.out.println(resourceBundle.getString("jdbc.password"));
}




```


## Collection

```java
//Iterator <- Collection <- List <- ArrayList,LinkedList
//Iterator <- Collection <- Set <- HashSet,TreeSet
//Iterator <- Collection <- Map <- HashMap,TreeMap
//Collection是接口 操作一组不唯一无序的对象
//Collections是算法类,提供了对集合进行排序，遍历等多种算法
//List 接口操作一组不唯一，有序的对象
//Set 接口操作一组唯一，无序的对象，添加重复数据，会用equals比较是否存在
//Map 接口操作一组键值对对象，提供Key到Value的映射

//ArrayList 遍历访问效率高 插入删除效率低 实现了长度可变 内存分配连续的空间
//LinkedList 插入删除效率高 遍历访问效率低 采用链表存储方式
//HashSet接口存储一组唯一，无序的对象

//Iterator: public interface Iterator<E>
//Collection: public interface Collection<E>
//Collections: public class Collections extends Object extends Iterable<E>

//List: public interface List<E> extends Collection<E>
//ArrayList: public class ArrayList<E> extends AbstractList<E> implements List<E>, RandomAccess, Cloneable, Serializable
//LinkedList: public class LinkedList<E> extends AbstractSequentialList<E> implements List<E>, Deque<E>, Cloneable, Serializable

//Set: public interface Set<E> extends Collection<E>
//HashSet: public class HashSet<E> extends AbstractSet<E> implements Set<E>, Cloneable, Serializable
//TreeSet: public class TreeSet<E> extends AbstractSet<E> implements NavigableSet<E>, Cloneable, Serializable

//Map: public interface Map<K,V>
//Map.Entry: public static interface Map.Entry<K,V>
//HashMap: public class HashMap<K,V> extends AbstractMap<K,V> implements Map<K,V>, Cloneable, Serializable
//TreeMap: public class TreeMap<K,V> extends AbstractMap<K,V> implements NavigableMap<K,V>, Cloneable, Serializable



```


```java
//Collections
Collections.min()//最小的值
Collections.max()//最大的值
Collections.reverse()//逆序
Collections.sort()//排序算法，这个函数所依赖判断依据是Comparable接口
public class Aaa implements Comparable{
    public int compareTo(Object o){/*判断大小，返回0 1 -1*/}}



```


```java
// ArrayList
boolean add(Object o);//在末尾添加元素
void add(int index,Object o);//在指定索引处插入元素
boolean remove(Object o);//从列表删除元素
Object remove(int index);//删除指定元素
void clear();//删除所有元素

//toArray()方法用Object[]接收
//Object[] o = new Object[arraylist.size()];
//o = arraylist.toArray();
Object[] toArray(); //ArrayList集合转数组 返回Object类型
// T[] t = new T[arraylist.size()];声明新数组
// arraylist.toArray(t);集合变成数组
<T> T[] toArray(T[] a); //ArrayList集合转数组 返回泛型数组

int size();//返回元素个数
boolean contains(Object o);//判断是否存在指定元素
boolean isEmpty();//判断集合是否为空
Object get(int index);//返回指定索引的元素，需要强制类型转换
int indexOf(Object o);//返回第一次出现的索引
int lastIndexOf(Object o);//返回最后一次出现的索引
Object set(int index, Object o);//替换指定索引的值，并返回被覆盖的值

```


```java
//LinkedList
void  addFirst(Object o);//在列表首部添加元素
void  addLast(Object o);//在列表尾部添加元素
Object  getFirst();//返回第一个元素
Object  getLast();//返回最后一个元素
Object  removeFirst();//删除并返回第一个元素
Object  removeLast();//删除并返回最后一个元素

```

```java
//Set
Set<String> set = new Set<>();//构造方法
boolean add()//添加元素
boolean remove()//删除元素
int size()//返回元素个数


```

```java
//Map
Map<K,V> map = new HashMap<>();//构造方法，指定键值对类型
V put(K,V)//添加键值对
V get(K)//获取指定键的值
V remove(K)//删除指定键的键值对
void clear()//清空map
boolean isEmpty()//判断是否为空
Set<K> keySet()//返回键的集合
Collection<V> values()//返回值的集合
int size()//返回键值对的个数
boolean containsKey(key)//验证是否存在指定key,根据equals判断
boolean containsValue(value)//验证是否存在指定value,根据equals判断

//Map.Entry<K,V>表示一对键值对
Set<Map.Entry<K,V>> entrySet()//返回键值对的集合
for(Map.Entry<K,V> kv: map.entrySet())
kv.getKey()
kv.getValue()

```


# Package java.io
https://docs.oracle.com/javase/8/docs/api/index.html?java/io/package-summary.html
```java
// 流是一组有序的数据序列，先进先出
//字节流 输入输出字节流InputStream,OutputStream
//      文件字节流 FileInputStream,FileOutputStream
// 字符流 读取写入 Reader,Writer
//       文件读取写入 FileReader,FileWriter
// 可以指定编码 InputStreamReader OutputStreamWriter
// 单行读取写入 BufferedReader BufferedWriter
// 数据流输入输出 DataInputStream DataOutputStream
// 对象输入输出 ObjectInputStream ObjectOutputStream

//继承关系
//File: public class File extends Object implements Serializable, Comparable<File>

//InputStream:  public abstract class InputStream extends Object implements Closeable
//OutputStream: public abstract class OutputStream extends Object implements Closeable, Flushable
//FileInputStream:  public class FileInputStream extends InputStream
//FileOutputStream: public class FilterOutputStream extends OutputStream

//Reader: public abstract class Reader extends Object implements Readable, Closeable
//Writer: public abstract class Writer extends Object implements Appendable, Closeable, Flushable
//FileReader: public class FileReader extends InputStreamReader
//FileWriter: public class FileWriter extends OutputStreamWriter

//InputStreamReader: public class InputStreamReader extends Reader
//OutputStreamWriter: public class OutputStreamWriter extends Writer

//BufferedReader: public class BufferedReader extends Reader
//BufferedWriter: public class BufferedWriter extends Writer

//DataInputStream:  public class DataInputStream  extends FilterInputStream  implements DataInput
//DataOutputStream: public class DataOutputStream extends FilterOutputStream implements DataOutput

//ObjectInputStream: public class ObjectInputStream  extends InputStream  implements ObjectInput,  ObjectStreamConstants
//ObjectOutputStream:public class ObjectOutputStream extends OutputStream implements ObjectOutput, ObjectStreamConstants

```

```java
// PrintStream类
import java.io.PrintStream;
PrintStream.println(); // 和下面的写法相同
System.out.println();
```
```java
File file = new File("file.txt");//构造方法，写入路径
boolean isFile()//判断是否是文件，没有文件或目录都返回false
boolean isDirectory()//判断是否是目录，没有目录或文件返回false
boolean exists()//文件或目录是否存在，没有这个名字的文件或目录可以调用createNewFile()

String getPath()//获取路径，一般是构造方法输入的路径
String getAbsolutePath()//获取绝对路径
String getName()//获取文件名
long length()//获取文件的大小，单位是字节
        
boolean createNewFile()//创建文件
boolean delete()//删除文件

```

```java
InputStream is;//这个类为抽象类，这个类的子类，读取内容用这种方法
OutputStream os;//这个类为抽象类，它的子类写入内容用这种方法
byte[] bytes = new bute[1024];
int i=0; while((i=is.read())!=-1){os.write(i)}
int i=0; while((i=is.read(bytes))!=-1){os.write(bytes)}
int i=0; while((i=is.read(bytes,0,bytes.length))!=-1){os.write(bytes,0,i)}

```

```java
FileInputStream fis = new FileInputStream("file.txt");
int available()//可以从流中读取到的字节长度
int read()//读取一个字节，返回对应的数值
int read(byte[])//把内容读取到数组中，返回内容的长度
int read(bute[],off,len)//把内容复制到数组的指定位置和长度，返回内容的长度
void close()//关闭流

FileOutputStream fos = new FileOutputStream("file.txt",true);//构造方法，后面写true是追加模式
void write(int)//通过输出流，写入对应的字符
void write(byte[])//将字节数组写入到文件
void write(bute[],off,len)//将指定位置和长度的内容写入到文件
void close()//关闭流

byte[] bts = new byte[5];
int i=0; while((i=fis.read(bts,0,bts.length))!=-1)sout(new String(bts,0,i))//输出读取到的字符
int i=0; while((i=fis.read(bts,0,bts.length))!=-1)fos.write(bts,0,i)//复制文件



```

```java
//字符读取
FileReader reader = new FileReader("file.txt");//构造方法，传入文件路径
int read()//读取一个字符，强制转型为char类型
int read(char[] c)//把内容放到数组中，返回读取到的字符长度
int read(char[] c,int off, int len)//把内容读取到数组中，起始位置和写入长度，off+len不超过数组长度
void close()//使用结束后必须关闭流

FileWriter writer = new FileWriter("file.txt");
void write(int)//写入文件内容
void write(String)//将字符串写入文件
void write(String,off,len)//指定字符串的索引和长度，写入到文件
flush()//写完内容刷缓冲区



//示例
FileReader reader = new FileReader("file.txt");//构造方法，传入文件路径
int i=0; while((i=reader.read())!=-1)(//通过遍历i输出整个文件的字符)
System.out.print((char)i);//强制转换成char类型
System.out.printf("%c",i);//读取一个字符，读到文件结尾时等于-1

char[] c=new char[5];//数组存储一段字符
int i=0; while((i=reader.read(c))!=-1)//遍历数组读取整个文件
    print(String.valueOf(c,0,i));

char[] c=new char[5];
int i=0; while((i=reader.read(c,0,c.length))!=-1)//放入时候指定位置和长度
    print(String.valueOf(c,0,i));//输出时也指定位置和长度
```

```java
BufferedReader bufreader = new BufferedReader(reader);//构造方法，传Reader的值 
String readLine()//读取一行

BufferedWriter bufwriter = new BufferedWriter(writer)//构造方法，传Writer的值
void write(char[],off,len)//写入一段指定位置和长度的字符数组
void write(int)//写入一个字符
void write(String,off,len)//写入一个指定位置和长度的字符串
void newLine()//换行，会根据操作系统的不同选择winCRLF\r\n macCR\r linuxLF\n


//示例
FileReader reader = new FileReader("file.txt");
BufferedReader bufreader = new BufferedReader(reader);
String row; while((row = bufreader.readLine())!=-1)
    System.out.println(row);

```

```java
//打开文本文件指定字符集
FileInputStream fis = new FileInputStream("file.txt");
InputStreamReader isr = InputStreamReader(fis,"UTF-8");//这里指定字符集
BufferedReader br = new BufferedReader(isr);
String row; while((row = br.readLine()) != null)
    System.out.println(row);//读取一行

//上面的流一个套一个，关闭的时候按照逆序关闭
if(br!=null)br.close();
if(isr!=null)isr.close();
if(fis!=null)fis.close();

OutputStreamWriter osw = new OutputStreamWriter(OutputStream,"UTF-8")//指定字符集

```

```java
DataInputStream(InputStream)
int read()//返回一字节的内容
DataOutputStream(OutputStream)
void write(int)//写入一个字节

```

```java
//序列化，反序列化的类必须实现Serializable接口
//public class Object1 implements Serializable必须实现Serizlizable接口
//不参与序列化的字段需要transient声明
ObjectInputStream(new FileInputStream("file.txt"))
void readObject()//返回一字节的内容
Object1 obj1=(Object1)ois.readObject()//把文件内的内容读取到对象中

ObjectOutputStream(new FileOutputStream("file.txt"))
void writeObject(int)//写入一个字节
oos.writeObject(new Object1(val1,val2,val3))//把对象输出到文件中

```




# Package java.net
https://docs.oracle.com/javase/8/docs/api/index.html?java/net/package-summary.html

在网络通行协议下，实现网络互连的不同计算机上运行的程序间可以进行数据交换。
网络编程的三要素：IP地址 端口 协议
端口号的取值范围是0-65535，一般使用1024以上的端口号，如果端口号被占用会导致程序启动失败


```java

//InetAddress: public class InetAddress extends Object implements Serializable
//ServerSocket: public class ServerSocket extends Object implements Closeable
//Socket: public class Socket extends Object implements Closeable
//DatagramSocket: public class DatagramSocket extends Object implements Closeable
//DatagramPacket: public final class DatagramPacket extends Object

```

```java
// InetAddress // 这个类表示一个IP地址
static InetAddress InetAddress.getLocalHost();// 获取本机地址
static InetAddress InetAddress.getByName("");//获取本机地址
static InetAddress InetAddress.getByName("www.baidu.com"); // 通过域名获取地址
static InetAddress InetAddress.getByName("112.80.248.76"); // 通过IP获取地址
String getHostName(); // 获取主机名
byte[] getAddress(); // 获取IP地址
String getHostAddress(); // 获取IP地址
boolean isReachable(5000); // 测试该地址是否可达,5000毫秒之内,类似于ping


// Socket TCP连接
Socket socket = new Socket("", 1234);
OutputStream outputStream = socket.getOutputStream();
DataOutputStream out = new DataOutputStream(outputStream);
out.writeUTF("hello");
socket.close();

// ServerSocket 服务器连接
ServerSocket serverSocket = new ServerSocket(1234);
serverSocket.setSoTimeout(100000);
Socket server = serverSocket.accept();
DataInputStream in = new DataInputStream(server.getInputStream());
System.out.println(in.readUTF());
server.close();
serverSocket.close();

```

```java

// DatagramSocket DatagramPacket UDP数据传输组合

// DatagramSocket 基于UDP协议的Socket
DatagramSocket datagramSocket = new DatagramSocket(); //客户端随机端口
DatagramSocket datagramSocket = new DatagramSocket(10086);//服务器接收数据端口
datagramSocket.send(datagramPacket); //发送数据
datagramSocket.receive(datagramPacket);//接受数据
datagramSocket.close(); //关闭连接
// DatagramPacket 数据报包
byte[] bytes = "Hello".getBytes(); // 打包数据
new DatagramPacket(bytes, bytes.length, InetAddress.getLocalHost(),1234);//服务器端口
byte[] bytes = new byte[1024]; //缓存区
new DatagramPacket(bytes, bytes.length);//数据报包
new String(dp.getData(),0,dp.getLength()); // 查看缓存区


//案例，两个信息同步显示
//send
DatagramSocket ds = new DatagramSocket();
BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
String line;
while ((line = br.readLine()) != null) {
	if("886".equals(line))break;
	byte[] bys = line.getBytes();
	InetAddress address = InetAddress.getByName("192.168.56.1");
	DatagramPacket dp = new DatagramPacket(bys, bys.length, address, 10086);
	ds.send(dp);
}   ds.close();
//receive
DatagramSocket ds = new DatagramSocket(10086);
while(true) {
    byte[] bys = new byte[1024];
    DatagramPacket dp = new DatagramPacket(bys,bys.length);
    ds.receive(dp);
    System.out.println(new String(dp.getData(),0,dp.getLength()));
}

// 另一个案例
//服务器准备
DatagramSocket server = new DatagramSocket(1234);//服务器接收数据端口
byte[] bytes = new byte[1024];
DatagramPacket receive = new DatagramPacket(bytes, bytes.length);
//客户端
DatagramSocket client = new DatagramSocket(1235); //客户端随机端口
byte[] send = "faafafa".getBytes();
DatagramPacket dpsend = new DatagramPacket(send, send.length, InetAddress.getLocalHost(), 1234);
client.send(dpsend);
//服务器接收数据
server.receive(receive);
System.out.println(new String(receive.getData(), 0, receive.getLength()));
client.close();
server.close();

```

```java

// 客户端上传文件
public class ClientDemo {
    public static void main(String[] args) throws IOException {
        //创建客户端Socket对象
        Socket s = new Socket("127.0.0.1", 10010);
        //封装文本文件的数据
        BufferedReader br = new BufferedReader(new FileReader("pom.xml"));
        //封装输出流写数据
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(s.getOutputStream()));
        String line;
        while ((line = br.readLine()) != null) {
            bw.write(line);
            bw.newLine();
            bw.flush();
        }
        s.shutdownOutput();
        //接收反馈
        BufferedReader brClient = new BufferedReader(new InputStreamReader(s.getInputStream()));
        //等待读取数据
        String data = brClient.readLine();
        System.out.println("服务器反馈: " + data);
        br.close();
        s.close();
    }
}

//服务端接收文件
public class ServerDemo {
    public static void main(String[] args) throws IOException {
        //创建服务器Socket对象
        ServerSocket ss = new ServerSocket(10010);
        while(true){
            //监听每一个客户端,开启一个线程
            Socket s = ss.accept();
            //为每一个客户端开启一个线程
            new Thread(new ServerThread(s)).start();
        }
    }
}

//服务端依赖的类
public class ServerThread implements Runnable {
    private Socket s;
    public ServerThread(Socket s) {
        this.s = s;
    }
    @Override
    public void run() {
        try {
            //接收数据写到文本文件
            BufferedReader br = new BufferedReader(new InputStreamReader(s.getInputStream()));
            //解决名称冲突问题
            int count = 0;
            File file = new File("Copy" + count + ".xml");
            while (file.exists()) {
                count++;
                file = new File("Copy" + count + ".xml");
            }
            BufferedWriter bw = new BufferedWriter(new FileWriter(file));
            String line;
            while ((line = br.readLine()) != null) {
                bw.write(line);
                bw.newLine();
                bw.flush();
            }
            //给出反馈
            BufferedWriter bwServer = new BufferedWriter(new OutputStreamWriter(s.getOutputStream()));
            bwServer.write("文件上传成功!");
            bwServer.newLine();
            bwServer.flush();
            s.close();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}

```






# 加密

```java
import java.security.MessageDigest;
import java.util.UUID;
public class PasswordUtil {
    //md5加密处理 aaa->47BCE5C74F589F4867DBD57E9CA9F808
    private static String md5(String s) {
        try {
            // MessageDigest是封装md5算法的工具对象还支持SHA算法
            MessageDigest md = MessageDigest.getInstance("MD5");
            //通过digest拿到的任意字符串,得到的bates都是等长的
            byte[] bytes = md.digest(s.getBytes("utf-8"));
            return toHex(bytes);
        } catch (Exception e) {
            throw new RuntimeException(e);
        }
    }

    private static String toHex(byte[] bytes) {
        //toHex的字符串把二进制转换成十六进制
        final char[] HEX_DIGITS = "0123456789ABCDEF".toCharArray();
        StringBuilder ret = new StringBuilder(bytes.length * 2);
        //循环判断是为了补位操作
        for (int i = 0; i < bytes.length; i++) {
            ret.append(HEX_DIGITS[(bytes[i] >> 4) & 0x0f]);
            ret.append(HEX_DIGITS[bytes[i] & 0x0f]);
        }
        return ret.toString();
    }

    //生成随机字符串 长度为8 fb22119e
    public static String salt() {
        //使用UUID通用唯一识别码,取第一个-前面的值
        UUID uuid = UUID.randomUUID();
        String[] arr = uuid.toString().split("-");
        return arr[0];
    }

    //对密码进行加密加盐操作 E10ADC3949BA59ABBE42c52c5056E057F20F883E
    public static String encodeDefaultSalt(String password) {
        //加密
        String hexPwd = md5(password);
        //生成盐
        String salt = salt();
        System.out.println("salt ：" + salt);
        //加盐操作
        StringBuilder builder = new StringBuilder(hexPwd);
        builder.insert(18, salt);
        //返回加密加盐后的字符串
        return builder.toString();
    }

    public static String encode(String password, String salt) {
        //加密  密码 指定salt E10ADC3949BA59ABBEd363cf1d56E057F20F883E
        String hexPwd = md5(password);
        //加盐操作
        StringBuilder builder = new StringBuilder(hexPwd);
        builder.insert(18, salt);
        //返回加密加盐后的字符串
        return builder.toString();
    }

    //校对密码是否匹配，匹配则返回true
    public static boolean match(String password, String dbPassword) {
        StringBuilder builder = new StringBuilder(dbPassword);
        //去盐操作，生成md5加密后原始字符
        builder.replace(18, 26, "");
        //加密新密码，生成md5加密字符
        password = md5(password);
        //校对加密字符与原始字符是否匹配
        return password.equals(builder.toString());
    }
}

```







# 进制转换器

```java
    /*private*/ static String toHex(byte[] bytes) {
        //toHex的字符串把二进制转换成十六进制
        final char[] HEX_DIGITS = "0123456789ABCDEF".toCharArray();
        StringBuilder ret = new StringBuilder(bytes.length * 2);
        //循环判断是为了补位操作
        for (int i = 0; i < bytes.length; i++) {
            ret.append(HEX_DIGITS[(bytes[i] >> 4) & 0x0f]);
            ret.append(HEX_DIGITS[bytes[i] & 0x0f]);
        }
        return ret.toString();
    }

```
