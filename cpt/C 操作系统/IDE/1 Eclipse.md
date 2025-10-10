

https://www.eclipse.org/
hyh1175561641@gmail.com
hyh@1175561641


# Eclipse

https://www.eclipse.org/getting_started/
https://help.eclipse.org/
https://www.runoob.com/eclipse/eclipse-tutorial.html
https://help.eclipse.org/latest/index.jsp

https://eclipse.dev/m2e/ Maven support

cdt
1.新建MINGW_HOME变量，值为你的MinGW的安装目录，比如我的安装目录是在D:\software\MinGW

2.在PATH变量里加入%MINGW_HOME%\bin;

3.新建LIBRARY_PATH变量，如果有的话，在值中加入%MINGW_HOME%\lib

4.新建C_INCLUDEDE_PATH变量，值设为%MINGW_HOME%\include

5.新建CPLUS_INCLUDE_PATH变量，值设为%MINGW_HOME%\lib\gcc\mingw32\4.8.1\include\c++;

(这一个我只添加了一个就可以了。网上有很多教程添加的比我多： %MINGW_HOME%\lib\gcc\mingw32\4.8.1\include\c++\mingw32\bits;%MINGW_HOME%\lib\gcc\mingw32\4.8.1\include\c++\backward;%MINGW_HOME%\include;%MINGW_HOME%\lib\gcc\mingw32\4.8.1\include-fixed）

6.把msys的目录添加到path中，%MINGW_HOME%\msys\1.0\bin;

本人对于MinGW的目录非常不清楚，希望有哪位知道的同僚告知下。





# eclipse



容器管理软件
docker pull portainer/portainer-ce:latest
docker run -d --name=Portainer  -p 9000:9000 -v /root/docker/portainer-ce:/data -v /var/run/docker.sock:/var/run/docker.sock portainer/portainer-ce:latest




数据库和数据库可视化管理器
docker pull phpmyadmin/phpmyadmin
docker run -d --name phpmyadmin -e PMA_HOST=192.168.154.232 -e PMA_PORT=3306 -p 80:80 phpmyadmin
开启数据库时，有可选服务器地址的input选项框
docker run -d --name phpmyadmin -e PMA_ARBITRARY=1 -p 80:80 phpmyadmin


docker run -itd --name mysql8 -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 mysql:8
docker run -d -p 3306:3306 --name mysql 
-v /mysqldata/mysql/log:/var/log/mysql  
-v /mysqldata/mysql/data:/var/lib/mysql  
-v /mysqldata/mysql/conf:/etc/mysql 
-e MYSQL_ROOT_PASSWORD=root   mysql:8

mysql -h 192.168.0.103 -uroot -p123456

