### 功能描述
本模板用于通过寄云 PaaS 平台，在您的私有 / 公有云快速搭建 Java SE 应用运行环境；简化您的程序代码的上传配置流程；根据负载及系统资源使用情况，自动伸缩应用节点的数量，轻松实现自动运维。

### 操作步骤
1. 指定您的云账户信息；
2. 指定运行应用环境的主机配置信息；
3. 指定您的程序代码获取路径；（目前支持通过 GitHub 项目路径获取，和通过 URL 获取 zip 源码包两种方式）  
`https://github.com/neucloud-ncae/ncae-example-java`  
`http://neucloud.oss-cn-beijing.aliyuncs.com/softwares/ncae/ncae-example-java-master.zip`
4. 指定您程序后端数据库的 JDBC 连接字符串；（此步骤可选，这些选项默认为空值）
5. 执行部署操作；
6. 部署执行成功后，根据平台提供的方式登录服务器，完成您所上传应用的后续配置。

### 环境说明
- 本平台配置包含一个 Nginx 服务器，该服务器用作反向代理，向您的应用程序提供缓存的静态内容并传递请求。
- 本平台包含常用的生成工具，允许您在服务器上执行生成操作。这些工具包括：`ant` `maven2` `gradle`。
- 您可以在应用部署时指定外部数据库连接，该配置将以环境变量的形式传入应用服务器，您可以使用 `System.getenv("JDBC_CONNECTION_STRING")` 读取该环境变量。
- 如果您要在部署时编译 Java 类并在您环境中运行其他生成构建的命令，请在应用程序源包中包含一个 `Buildfile` 文件（文件名区分大小写）。
- 本平台通过 Supervisor 服务来运行并守护您所部署的应用，您需要在上传的代码包或项目路径中包含一个 `Procfile` 文件（文件名区分大小写）来告知 Supervisor 您的应用运行所需执行的启动命令。应用所监听的端口可以在部署时指定，该配置将以变量的形式传入您的 Java 应用，您可以通过在应用程序代码中调用 `System.getProperty("PORT")` 访问此变量。
- 关于 `Buildfile` 和 `Procfile` 的使用方法，请参见我们提供的[**演示代码**](https://github.com/neucloud-ncae/ncae-example-java)。
