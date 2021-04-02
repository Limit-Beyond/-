启动程序的目录-bin

配置文件的目录-etc

![image-20210402202356379](C:\Users\73610\AppData\Roaming\Typora\typora-user-images\image-20210402202356379.png)

在etc文件夹下找到nexus-default.properties文件修改端口号

![image-20210402202559686](C:\Users\73610\AppData\Roaming\Typora\typora-user-images\image-20210402202559686.png)

1.安装nexus服务

```
nexus.exe /install nexus3
```

2.启动nexus服务

```
nexus.exe /run nexus3
```

3.访问地址

127.0.0.1:8888

nexus3默认账号 admim

![image-20210402205316340](C:\Users\73610\AppData\Roaming\Typora\typora-user-images\image-20210402205316340.png)

密码在admin.password中。

登录之后，修改密码。（本人改成了123456，方便记录）

![image-20210402205405451](C:\Users\73610\AppData\Roaming\Typora\typora-user-images\image-20210402205405451.png)

1.maven settings.xml中配置私服信息

```
<!-- 配置私服 -->
<server>
    <id>nexus</id>
    <username>admin</username>
    <password>123456</password>
</server>
```

2.创建自己的代理仓库（远程中央仓库）

![image-20210402210421653](C:\Users\73610\AppData\Roaming\Typora\typora-user-images\image-20210402210421653.png)

![image-20210402210507299](C:\Users\73610\AppData\Roaming\Typora\typora-user-images\image-20210402210507299.png)

设置代理仓库信息：
![image-20210402210803637](C:\Users\73610\AppData\Roaming\Typora\typora-user-images\image-20210402210803637.png)

3.创建hosted，本地存储。（和官方仓库一样能够提供本地私库功能）

![image-20210402210927039](C:\Users\73610\AppData\Roaming\Typora\typora-user-images\image-20210402210927039.png)



![image-20210402211030382](C:\Users\73610\AppData\Roaming\Typora\typora-user-images\image-20210402211030382.png)

配置pom.xml

```
 <distributionManagement>
        <repository>
            <id>nexus</id>
            <name>Nexus Release Repository</name>
            <url>http://localhost:8888/repository/maven-releases/</url>
        </repository>
        <snapshotRepository>
            <id>nexus</id>
            <name>Nexus Snapshot Repository</name>
            <url>http://localhost:8888/repository/maven-snapshots/</url>
        </snapshotRepository>
    </distributionManagement>
```



错误排查：

1.Could not open SCManager

以管理员身份运行  cmd

```
nexus.exe /install nexus3
```

![image-20210402204113043](C:\Users\73610\AppData\Roaming\Typora\typora-user-images\image-20210402204113043.png)