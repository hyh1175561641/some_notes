# 分布式文件系统

分布式文件系统 (Distributed File System) 是一个软件/软件服务器，这个软件可以用来管理文件。但这个软件所管理的文件通常不是在一个服务器节点上，而是在多个服务器节点上，这些服务器节点通过网络相连构成一个庞大的文件存储服务器集群，这些服务器都用于存储文件资源，通过分布式文件系统来管理这些服务器上的文件。

常见的分布式文件系统有：FastDFS、GFS、HDFS、Lustre 、Ceph 、GridFS 、mogileFS、TFS等。Minio系统

书籍 https://pan.baidu.com/share/init?surl=Fpj0Jdu1Xl6HZty667sVNA?pwd=d2bi

# FastDFS文件服务器

https://github.com/happyfish100
https://zhuanlan.zhihu.com/p/502923836
https://segmentfault.com/a/1190000018251300

开源的轻量级分布式文件系统,用于解决大多数据存储和负载均衡等问题.
支持HTTP协议传输文件(Nginx),对文件内容做Hash处理,节约磁盘空间,支持负载均衡,整体性能较好,适用于中小型系统

FastDFS的两个角色
跟踪服务器Tracker: 主要是调度工作,起到负载均衡的作用,它是客户端与存储服务器交互的枢纽.
存储服务器Storage: 主要提供容量和备份的服务,存储服务器是以组(Group)为单位,每个组内可以有多台存储服务器,数据互为备份.文件及属性(Meta Data)都保存在该服务器上.

tracker和storage可以是一个或多个服务器.在tracker或storage的集群中,任何时候都可以从中删除服务器,对线上服务没有任何影响.tracker集群中的服务器是点对点的.


```bash
# 安装
cd ~/caibh/fdfs-package # 存到该目录下
# 下载libfastcommon、fastdfs、fastdfs-nginx-module
wget https://github.com/happyfish100/libfastcommon/archive/V1.0.39.tar.gz -SO libfastcommon.tar.gz
wget https://github.com/happyfish100/fastdfs/archive/V5.11.tar.gz -SO fastdfs.tar.gz
wget https://github.com/happyfish100/fastdfs-nginx-module/archive/V1.20.tar.gz -SO fastdfs-nginx-module.tar.gz
# 解压
tar -xf xxx.tar.gz

# 安装libfastcommon
cd ~/caibh/fdfs-package
cd libfastcommon-1.0.39
./make.sh
./make.sh install

# 安装 fastdfs
cd ~/caibh/fdfs-package
cd fastdfs-5.11
./make.sh
./make.sh install

# 安装后的程序在/usr/bin
which fdfs_trackerd
/usr/bin/fdfs_trackerd

# 配置后的文件在/etc/fdfs
cd ~/caibh/fdfs-package/fastdfs-5.11
ls /etc/fdfs
client.conf.sample storage_ids.conf.sample  tracker.conf.sample storage.conf.sample

# 但是这些配置文件是不全的，而且都是模板，所以需要从fastdfs包中拷贝过来，并修改配置：
cd ~/caibh/fdfs-package/fastdfs-5.11/conf
ls
anti-steal.jpg  client.conf  http.conf  mime.types  storage.conf  storage_ids.conf  tracker.conf
sudo cp ~/caibh/fdfs-package/fastdfs-5.11/conf/* /etc/fdfs



```


```bash
# 修改配置 192.168.56.101
sudo vi /etc/fdfs/tracker.conf：跟踪服务器配置文件
# the tracker server port
port=22122
# the base path to store data and log files
base_path=/home/caibh/fdfs
# which group to upload file
# when store_lookup set to 1, must set store_group to the group name
store_group=group2
# HTTP port on this tracker server
http.server_port=9270


sudo vi /etc/fdfs/storage.conf：存储服务器配置文件
# storage所属的组
group_name=group1
# the storage server port
port=23000
# the base path to store data and log files
base_path=/home/caibh/fdfs
# store_path#, based 0, if store_path0 not exists, it's value is base_path
# the paths must be exist
store_path0=/home/caibh/fdfs
#store_path1=/home/caibh/fdfs2
# tracker服务器，虽然是同一台机器上，但是不能写127.0.0.1。这项配置可以出现一次或多次
tracker_server=192.168.56.101:22122
# the port of the web server on this storage server
http.server_port=8888


sudo vi /etc/fdfs/client.conf：测试配置文件
# the base path to store log files
base_path=/home/caibh/fdfs/client
# tracker_server can ocur more than once, and tracker_server format is
#  "host:port", host can be hostname or ip address
tracker_server=192.168.56.101:22122
#HTTP settings
http.tracker_server_port=9270


sudo vi /etc/fdfs/mod_fastdfs.conf：
# the base path to store log files
base_path=/tmp
# FastDFS tracker_server can ocur more than once, and tracker_server format is
#  "host:port", host can be hostname or ip address
# valid only when load_fdfs_parameters_from_tracker is true
tracker_server=191.8.1.77:22122
# the port of the local storage server
# the default value is 23000
storage_server_port=23000
# the group name of the local storage server
group_name=group1
# store_path#, based 0, if store_path0 not exists, it's value is base_path
# the paths must be exist
# must same as storage.conf
store_path0=/home/caibh/fdfs
#store_path1=/home/yuqing/fastdfs1


配置过程中有几点要注意：
确保配置中用到的目录已经创建了。比如~/fdfs/client、~/fdfs/data、~/fdfs/logs
确保各种配置文件之间引用的端口一直。比如：
mod_fastdfs.conf文件中tracker_server的端口应该跟tracker.conf中port一致；
mod_fastdfs.conf文件中storage_server_port的端口应该跟跟storage.conf中port一致；
其他配置或文件虽然不用修改，但是fastdfs-nginx-module模块会用到：
anti-steal.jpg
http.conf
mime.types


# 启动tracker和storage服务
# 启动,启动时需要创建文件夹,/home目录下的文件夹,然后用find寻找log文件
/usr/bin/fdfs_trackerd /etc/fdfs/tracker.conf restart
/usr/bin/fdfs_storaged /etc/fdfs/storage.conf restart
# linux启动方式
/sbin/service fdfs_trackerd start
/sbin/service fdfs_storaged start
# 查看日志
tail -n10 ~/fdfs/logs/trackerd.log
tail -n10 ~/fdfs/logs/storaged.log
# 如果日志显示有错误信息，需要根据信息来查找错误原因

# 查看状态
fdfs_monitor /etc/fdfs/storage.conf

# 测试上传文件
# fdfs_test client.conf upload jpgfile
fdfs_test /etc/fdfs/client.conf upload /develop/fastdfs/test_file/LiuLangDiQiu.jpg

```

```bash
# 安装fastdfs-nginx-module
# 下载nginx-1.15.1并解压,下载fastdfs-nginx-module并解压

# 编译之前需要修改配置文件,否则会报错找不到头文件
vim fastdfs-nginx-module-1.20/src/config
ngx_module_incs="/usr/include/fastdfs /usr/include/fastcommon/"
CORE_INCS="$CORE_INCS /usr/include/fastdfs /usr/include/fastcommon/"
# 配置文件中还能修改参数宏FDFS_OUTPUT_CHUNK_SIZE,FDFS_MOD_CONF_FILENAME
CFLAGS="$CFLAGS -D_FILE_OFFSET_BITS=64 -DFDFS_OUTPUT_CHUNK_SIZE='256*1024' -DFDFS_MOD_CONF_FILENAME='\"/etc/fdfs/mod_fastdfs.conf\"'"
# 再将fastdfs-nginx-module/src/mod_fastdfs.conf复制到/etc/fdfs/下

# 安装nginx
cd nginx-1.15.1
./configure --add-module=/home/yuqing/fastdfs-nginx-module/src
make; make install

# 开启nginx之前,先配置路由,在合适的地方加入配置
vim /usr/local/nginx/conf/nginx.conf
# config for fastdfs-nginx-module
server {
    listen 8777;
    location /M00 {
        root ~/fdfs/data;
        ngx_fastdfs_module;
    }
}

# 找到nginx命令
/usr/local/nginx/sbin/nginx # 打开nginx
/usr/local/nginx/sbin/nginx -s stop # 关闭nginx
ps -ef | grep nginx

# 访问内容,上传一个图片或者一个视频
http://192.168.56.101:8777/M00/00/00/wKg4ZWPka8WAE4dLBUSodZ5HXr8886.mp4


# 一键开启fastdfs脚本
vim fastdfs.sh
chmod u+x fastdfs.sh
systemctl stop firewalld
/usr/bin/fdfs_trackerd /etc/fdfs/tracker.conf restart
/usr/bin/fdfs_storaged /etc/fdfs/storage.conf restart
ps -ef | grep fdfs
/usr/local/nginx/sbin/nginx


```



# JavaClient

```java



```






# JavaUtil
```java

public class FastDFS {
    public static void main(String[] args) {
        fileUpload();
    }

    /**
     * 文件上传
     */
    public static void fileUpload() {
        try {
            //获取StorageClient对象
            StorageClient sc = getStorageClient();

            //local_filename为需要上传的文件的绝对路径
            //file_ext_name为需要上传的文件的扩展名
            //meta_list为需要上传的文件的属性信息 通常为null 即不用上传
            //返回值为String[] strings[0]为组名(如group1) strings[1]为远程文件名(如M00/00/00/wKi-g2NFYm6AYYnwAAEXDUO_9AI243.png)
            //此返回值很重要 建议存入数据库
            String[] result = sc.upload_file("D:/001.png", "png", null);

            for (String s : result) {
                System.out.println(s);
            }
        } catch (IOException | MyException e) {
            e.printStackTrace();
        }
    }

    /**
     * 文件下载
     */
    public static void fileDownload() {
        try {
            //获取StorageClient对象
            StorageClient sc = getStorageClient();

            //group_name为需要下载的文件的组名
            //remote_filename为需要下载的文件的远程文件名
            //local_filename为需要下载的文件保存到哪个位置的绝对路径名
            //返回值为int 若为0则表示下载成功 其它值都表示下载失败
            int result = sc.download_file("group1",
                    "M00/00/00/wKi-g2NFYm6AYYnwAAEXDUO_9AI243.png",
                    "D:/002.png");

            System.out.println(result);
        } catch (IOException | MyException e) {
            e.printStackTrace();
        }
    }

    /**
     * 文件删除
     */
    public static void fileDelete() {
        try {
            //获取StorageClient对象
            StorageClient sc = getStorageClient();

            //group_name为需要删除的文件的组名
            //remote_filename为需要删除的文件的远程文件名
            //返回值为int 若为0则表示删除成功 其它值都表示删除失败
            int result = sc.delete_file("group1",
                    "M00/00/00/wKi-g2NFYm6AYYnwAAEXDUO_9AI243.png");

            System.out.println(result);
        } catch (IOException | MyException e) {
            e.printStackTrace();
        }
    }

    /**
     * 获取StorageClient对象
     * @return StorageClient对象
     */
    public static StorageClient getStorageClient() {
        StorageClient sc = null;
        try {
            //读取fastdfs的配置文件以将所有的tracker_server地址读取到内存中
            //默认从classpath中读取
            ClientGlobal.init("fdfs_client.conf");

            //创建TrackerClient对象以获取TrackerServer对象与StorageServer对象
            TrackerClient tc = new TrackerClient();
            TrackerServer ts = tc.getTrackerServer();
            StorageServer ss = tc.getStoreStorage(ts);

            //通过TrackerServer对象与StorageServer对象来获取StorageClient对象
            //使用StorageClient对象以实现对文件的操作
            sc = new StorageClient(ts, ss);
        } catch (IOException | MyException e) {
            e.printStackTrace();
        }
        return sc;
    }
}




public class FastDFSUtil {

    /**
     * 文件上传
     */
    public static String[] fileUpload(byte[] file_buff, String file_ext_name, NameValuePair[] meta_list) {
        try {
            //获取StorageClient对象
            StorageClient sc = getStorageClient();

            //file_buff为需要上传的文件的字节数组
            //file_ext_name为需要上传的文件的扩展名
            //meta_list为需要上传的文件的属性信息 通常为null 即不用上传
            //返回值为String[] strings[0]为组名(如group1) strings[1]为远程文件名(如M00/00/00/wKi-g2NFYm6AYYnwAAEXDUO_9AI243.png)
            //此返回值很重要 建议存入数据库
            String[] result = sc.upload_file(file_buff, file_ext_name, meta_list);

            return result;
        } catch (IOException | MyException e) {
            e.printStackTrace();
        }
        return null;
    }

    /**
     * 文件下载
     */
    public static byte[] fileDownload(String group_name, String remote_filename) {
        try {
            //获取StorageClient对象
            StorageClient sc = getStorageClient();

            //group_name为需要下载的文件的组名
            //remote_filename为需要下载的文件的远程文件名
            //返回值为int 若为0则表示下载成功 其它值都表示下载失败
            byte[] result = sc.download_file(group_name, remote_filename);

            return result;
        } catch (IOException | MyException e) {
            e.printStackTrace();
        }
        return null;
    }

    /**
     * 文件删除
     */
    public static Integer fileDelete(String group_name, String remote_filename) {
        try {
            //获取StorageClient对象
            StorageClient sc = getStorageClient();

            //group_name为需要删除的文件的组名
            //remote_filename为需要删除的文件的远程文件名
            //返回值为int 若为0则表示删除成功 其它值都表示删除失败
            int result = sc.delete_file(group_name, remote_filename);

            return result;
        } catch (IOException | MyException e) {
            e.printStackTrace();
        }
        return null;
    }

    /**
     * 获取StorageClient对象
     * @return StorageClient对象
     */
    public static StorageClient getStorageClient() {
        StorageClient sc = null;
        try {
            //读取fastdfs的配置文件以将所有的tracker_server地址读取到内存中
            //默认从classpath中读取
            ClientGlobal.init("fdfs_client.conf");

            //创建TrackerClient对象以获取TrackerServer对象与StorageServer对象
            TrackerClient tc = new TrackerClient();
            TrackerServer ts = tc.getTrackerServer();
            StorageServer ss = tc.getStoreStorage(ts);

            //通过TrackerServer对象与StorageServer对象来获取StorageClient对象
            //使用StorageClient对象以实现对文件的操作
            sc = new StorageClient(ts, ss);
        } catch (IOException | MyException e) {
            e.printStackTrace();
        }
        return sc;
    }
}


```

```java

@Component
public class FastDFSUtil {
    @Autowired
    private FastFileStorageClient fastFileStorageClient;
    @Autowired
    private AppendFileStorageClient appendFileStorageClient;
    @Autowired
    private RedisTemplate<String, String> redisTemplate;
    private static final String PATH_KEY = "path-key:";
    private static final String UPLOADED_SIZE_KEY = "uploaded-size-key:";
    private static final String UPLOADED_NO_KEY = "uploaded-no-key:";
    private static final String DEFAULT_GROUP = "group1";
    private static final int SLICE_SIZE = 1024 * 1024 * 2;

    @Value("${fdfs.http.storage-addr}")
    private String httpFdfsStorageAddr;

    public String getFileType(MultipartFile file) {
        if (file == null) {
            throw new ConditionException("非法文件！");
        }
        String fileName = file.getOriginalFilename();
        int index = fileName.lastIndexOf(".");
        return fileName.substring(index + 1);
    }

    //上传
    public String uploadCommonFile(MultipartFile file) throws Exception {
        Set<MetaData> metaDataSet = new HashSet<>();
        String fileType = this.getFileType(file);
        StorePath storePath = fastFileStorageClient.uploadFile(file.getInputStream(), file.getSize(), fileType, metaDataSet);
        return storePath.getPath();
    }

    public String uploadCommonFile(File file, String fileType) throws Exception {
        Set<MetaData> metaDataSet = new HashSet<>();
        StorePath storePath = fastFileStorageClient.uploadFile(new FileInputStream(file),
                file.length(), fileType, metaDataSet);
        return storePath.getPath();
    }

    //上传可以断点续传的文件
    public String uploadAppenderFile(MultipartFile file) throws Exception {
        String fileType = this.getFileType(file);
        StorePath storePath = appendFileStorageClient.uploadAppenderFile(DEFAULT_GROUP, file.getInputStream(), file.getSize(), fileType);
        return storePath.getPath();
    }

    //上传可以断点续传的文件
    public void modifyAppenderFile(MultipartFile file, String filePath, long offset) throws Exception {
        appendFileStorageClient.modifyFile(DEFAULT_GROUP, filePath, file.getInputStream(), file.getSize(), offset);
    }

    public String uploadFileBySlices(MultipartFile file, String fileMd5, Integer sliceNo, Integer totalSliceNo) throws Exception {
        if (file == null || sliceNo == null || totalSliceNo == null) {
            throw new ConditionException("参数异常！");
        }
        String pathKey = PATH_KEY + fileMd5;
        String uploadedSizeKey = UPLOADED_SIZE_KEY + fileMd5;
        String uploadedNoKey = UPLOADED_NO_KEY + fileMd5;
        String uploadedSizeStr = redisTemplate.opsForValue().get(uploadedSizeKey);
        Long uploadedSize = 0L;
        if (!StringUtil.isNullOrEmpty(uploadedSizeStr)) {
            uploadedSize = Long.valueOf(uploadedSizeStr);
        }
        if (sliceNo == 1) { //上传的是第一个分片
            String path = this.uploadAppenderFile(file);
            if (StringUtil.isNullOrEmpty(path)) {
                throw new ConditionException("上传失败！");
            }
            redisTemplate.opsForValue().set(pathKey, path);
            redisTemplate.opsForValue().set(uploadedNoKey, "1");
        } else {
            String filePath = redisTemplate.opsForValue().get(pathKey);
            if (StringUtil.isNullOrEmpty(filePath)) {
                throw new ConditionException("上传失败！");
            }
            this.modifyAppenderFile(file, filePath, uploadedSize);
            redisTemplate.opsForValue().increment(uploadedNoKey);
        }
        // 修改历史上传分片文件大小
        uploadedSize += file.getSize();
        redisTemplate.opsForValue().set(uploadedSizeKey, String.valueOf(uploadedSize));
        //如果所有分片全部上传完毕，则清空redis里面相关的key和value
        String uploadedNoStr = redisTemplate.opsForValue().get(uploadedNoKey);
        Integer uploadedNo = Integer.valueOf(uploadedNoStr);
        String resultPath = "";
        if (uploadedNo.equals(totalSliceNo)) {
            resultPath = redisTemplate.opsForValue().get(pathKey);
            List<String> keyList = Arrays.asList(uploadedNoKey, pathKey, uploadedSizeKey);
            redisTemplate.delete(keyList);
        }
        return resultPath;
    }

    public void convertFileToSlices(MultipartFile multipartFile) throws Exception {
        String fileType = this.getFileType(multipartFile);
        //生成临时文件，将MultipartFile转为File
        File file = this.multipartFileToFile(multipartFile);
        long fileLength = file.length();
        int count = 1;
        for (int i = 0; i < fileLength; i += SLICE_SIZE) {
            RandomAccessFile randomAccessFile = new RandomAccessFile(file, "r");
            randomAccessFile.seek(i);
            byte[] bytes = new byte[SLICE_SIZE];
            int len = randomAccessFile.read(bytes);
            String path = "/Users/hat/tmpfile/" + count + "." + fileType;
            File slice = new File(path);
            FileOutputStream fos = new FileOutputStream(slice);
            fos.write(bytes, 0, len);
            fos.close();
            randomAccessFile.close();
            count++;
        }
        //删除临时文件
        file.delete();
    }

    public File multipartFileToFile(MultipartFile multipartFile) throws Exception {
        String originalFileName = multipartFile.getOriginalFilename();
        String[] fileName = originalFileName.split("\\.");
        File file = File.createTempFile(fileName[0], "." + fileName[1]);
        multipartFile.transferTo(file);
        return file;
    }

    //删除
    public void deleteFile(String filePath) {
        fastFileStorageClient.deleteFile(filePath);
    }

    public void viewVideoOnlineBySlices(HttpServletRequest request,
                                        HttpServletResponse response,
                                        String path) throws Exception {
        FileInfo fileInfo = fastFileStorageClient.queryFileInfo(DEFAULT_GROUP, path);
        long totalFileSize = fileInfo.getFileSize();
        String url = httpFdfsStorageAddr + path;
        Enumeration<String> headerNames = request.getHeaderNames();
        Map<String, Object> headers = new HashMap<>();
        while (headerNames.hasMoreElements()) {
            String header = headerNames.nextElement();
            headers.put(header, request.getHeader(header));
        }
        String rangeStr = request.getHeader("Range");
        String[] range;
        if (StringUtil.isNullOrEmpty(rangeStr)) {
            rangeStr = "bytes=0-" + (totalFileSize - 1);
        }
        range = rangeStr.split("bytes=|-");
        long begin = 0;
        if (range.length >= 2) {
            begin = Long.parseLong(range[1]);
        }
        long end = totalFileSize - 1;
        if (range.length >= 3) {
            end = Long.parseLong(range[2]);
        }
        long len = (end - begin) + 1;
        String contentRange = "bytes " + begin + "-" + end + "/" + totalFileSize;
        response.setHeader("Content-Range", contentRange);
        response.setHeader("Accept-Ranges", "bytes");
        response.setHeader("Content-Type", "video/mp4");
        response.setContentLength((int) len);
        response.setStatus(HttpServletResponse.SC_PARTIAL_CONTENT);
        HttpUtil.get(url, headers, response);
    }

    //下载文件
    public void downLoadFile(String url, String localPath) {
        fastFileStorageClient.downloadFile(DEFAULT_GROUP, url,
                new DownloadCallback<String>() {
                    @Override
                    public String recv(InputStream ins) throws IOException {
                        File file = new File(localPath);
                        OutputStream os = new FileOutputStream(file);
                        int len = 0;
                        byte[] buffer = new byte[1024];
                        while ((len = ins.read(buffer)) != -1) {
                            os.write(buffer, 0, len);
                        }
                        os.close();
                        ins.close();
                        return "success";
                    }
                });
    }
}


```





# Docker

```bash


# 下载fastdfs
docker pull morunchang/fastdfs
# 运行tracker
docker run -d --name tracker --net=host morunchang/fastdfs sh tracker.sh
# 运行storage
docker run -d --name storage --net=host -e TRACKER_IP=<your tracker server address>:22122 -e GROUP_NAME=<group name> morunchang/fastdfs sh storage.sh

# 使用的网络模式是–net=host, 替换为你机器的Ip即可
# 是组名，即storage的组
# 如果想要增加新的storage服务器，再次运行该命令，注意更换 新组名

```













