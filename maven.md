### Maven 介绍

---

#### 什么是 Maven[ˈmeɪvn]

Maven 是一个项目管理工具, 它包含了一个项目对象模型(POM: Project Object Model), 一组标准集合, 一个项目生命周期(Project Lifecycle) , 一个依赖管理系统(Dependency Management System), 和用来运行定义在生命周期阶段(phase)中插件(plugin)目标的逻辑.

#### Maven 可以解决什么问题

1. 我们需要引用各种 jar 包, 尤其是比较大的工程, 引用的 jar 包往往有几十个乃至上百个, 每用到一种 jar 包, 都需要手动引入工程目录, 而且经常遇到各种让人抓狂的 jar 包冲突、版本冲突
2. 我们写好的 Java 文件, 电脑不可能完全读懂, 需要将它编译成二进制字节码. 这项工作可以通过各种集成开发工具帮我们完成, Eclipse、IDEA 等都可以将代码即时编译. 当然, 如果有时间, 可以使用记事本来敲代码, 然后通过命令行 javac 命令等一个个的去编译
3. 世界上没有不存在 bug 的代码, 计算机喜欢 bug. 为了减少 bug, 在写完了代码之后, 我们需要写一些单元测试, 然后一个个的运行来检验代码质量
4. 我们需要将代码与各种配置文件、资源整合到一起, 定型打包, 如果是 web 项目, 还需要将之发布到服务器, 供人蹂躏

现在有一种工具 Maven, 可以把你从上面的繁琐工作中解放出来, 能帮你构建工程, 管理 jar 包, 编译代码, 还可以帮你自动运行单元测试, 打包, 生成报表, 甚至可以帮你部署项目, 生成 Web 站点.

#### Maven 的优势举例

运行一个 Web 项目文件, 就必须将项目所依赖的一些 jar 包添加到工程项目中, 否则项目就运行不了. 是想如果具有相同架构的十个项目, 那么我们就需要将这一份 jar 包复制到十个工程中, 导致最终的 CRM 项目文件极其的大. 但如果我们使用 Maven 工程来构建, 会发现总体上工程的大小会小很多.

```Java
// 依赖管理: maven工程对jar包的管理过程

// 传统的web工程crm jar包在项目中

// maven开发的crm项目jar包不在项目中, 而是存储了一个jar包的地址坐标, 指向jar包仓库(代码可重用)
```

#### 项目的一键构建

运行一个项目, 需要经过编译、测试、运行、打包、安装、部署等一系列过程. 而构建指的就是项目从编译、测试、运行、打包、安装、部署整个过程都交给 maven 进行管理.

一键构建即是指整个构建过程, 使用 maven 一个命令便可以轻松完成整个工作

**Maven 规范化构建流程如下:**

```java
// maven 将项目构建的过程进行标准化, 每个阶段使用一个命令完成, 下图展示构建过程的一些阶段

// 清理 --> 编译 --> 测试 --> 报告 --> 打包 --> 部署
```



### Maven 的安装

---

#### Maven 软件的下载

为了使用 Maven 管理工具, 我们首先要在[官网](https://maven.apache.org/)下载他的安装软件. 通过百度搜索 `Maven` 即可![截屏2021-02-14 上午10.45.42](https://cdn.jsdelivr.net/gh/Lummer-Li/image-bucket/image/20210214104551.png)

点击 Download 链接, 就可以直接进入到 Maven 软件的下载页面![截屏2021-02-14 上午10.49.27](https://cdn.jsdelivr.net/gh/Lummer-Li/image-bucket/image/20210214104928.png)

选择 `Binary zip archive` 的 `apache-maven-3.6.3-bin.zip` 安装下载即可

#### Maven 软件的安装

Mac 电脑进行以下环境变量配置

1. 打开终端(terminal), 键入 `vim ~/.bash_profile`
2. 在打开的文件中键入以下内容

```shell
# Setting PATH for Maven 3.6.3
export MAVEN_HOME=/usr/local/apache-maven-3.6.3
export PATH=$PATH:$MAVEN_HOME/bin
```

3. 保存退出
4. 在终端中输入 `mvn - v` 查看 maven 的版本, 如果有相关内容出现, 则配置成功, 否则请看以下步骤
5. 在终端中键入 `vim ~/.zshrc`
6. 在文件的尾末输入 `source ~/.bash_profile`

#### Maven 仓库的种类和彼此关系

![截屏2021-02-14 上午11.38.48](https://cdn.jsdelivr.net/gh/Lummer-Li/image-bucket/image/20210214113851.png)

仓库(放 jar 包用的)分三类

1. 本地仓库(**注意修改本地仓库的位置**)
2. 远程仓库(私服)
3. 中央仓库

#### Maven 标准目录结构

**Maven 项目分为以下几部分**

1. 核心代码部分
2. 配置文件部分
3. 测试代码部分
4. 测试配置文件

**项目名称**

1. src
2. config
3. resources

**Maven 项目标准目录结构**

1. src/main/java 目录 --> 核心代码部分
2. src/main/resources --> 配置文件部分
3. src/test/java 目录 --> 测试代码部分
4. src/test/resources --> 测试配置文件
5. src/main/webapp --> 页面资源, js、css、图片等等

#### Maven 常用命令

1. `mvn clean ` 清除编译信息
2. `mvn compile` 编译代码
3. `mvn test` 测试代码(包含编译代码)
4. `mvn package` 打包代码(pom 指向打包文件类型)(包含测试代码和编译代码)
5. `mvn install` 安装, 包含编译代码、测试代码、打包代码, 并且把最终生成的文件放在本地仓库中
6. `mvn deploy` 发布代码, 包含以上四个命令

#### Maven 生命周期

1. 清理生命周期: `mvn clean` 清除项目编译信息
2. 默认生命周期: `编译(compile)、测试(test)、打包(package)、安装(install)、发布(deploy)`
3. 站点生命周期(不常用)

#### Maven 概念模型图

![截屏2021-02-14 下午10.52.09](https://cdn.jsdelivr.net/gh/Lummer-Li/image-bucket/image/20210214225211.png)

#### IDEA 集成 Maven 插件

1. 打开 IDEA, 选择 Preferences
2. 搜索 Maven
3. 点击 Maven, 配置 Maven 本地的 home directory、settings file、local repository
4. 选择 Maven 下的 Runner, 在 VM Options 中加入参数 `-DarchetypeCatalog=internal`
5. 完成配置

#### Maven 工程使用阿里云镜像加载 jar 包

1. 打开 Maven 的 Setting.xml 文件
2. 在文件相应位置进行修改, 添加以下内容

```xml
<mirror>
  <id>aliyunmaven</id>
  <mirrorOf>*</mirrorOf>
  <name>aliyun</name>
  <url>https://maven.aliyun.com/repository/public</url>
</mirror>
```

![截屏2021-02-14 下午11.41.56](https://cdn.jsdelivr.net/gh/Lummer-Li/image-bucket/image/20210214234159.png)

3. 保存文件, 重启 IDEA, 即可完成

#### Maven 安装本地 jar 包文件进入本地仓库

1. 在[mvnrepository.com](https://mvnrepository.com/?__cf_chl_captcha_tk__=4760b49fe164ace718521007e9a060b10535ad5e-1613315312-0-Adq2Pww-CuXA01gc_Wg7FANAeyvq9ZGFa14BWpueInDV7DGSckXhqdgBkDTQuglm9cushQtj456fIGQMDrKNZizLCCPry9OH7Da14sqCBqDMHDkiKXWenBlFJRzzy8XNXAxfaVgOqql4Bh7QPD4PVR1S-bLCpsKHxDb9y7kYpzqIRTzJnZsj-yKXpImwGKNBIPZP4842pX3Pq4kwubxbtlQ3SPPsdA2G5NcA_6o5UDAPrEbMpuWGmkRB5A00VAVn3O1q-vAqt5uguBhWwsMik9rnyHfFdX3t2iRX6MW6bP72QNzBseXDTpdAvIwOZnb_xvCbZ-bGBdHXBBcSBqSyelMIMwiMceO3B8ViQ8g8CVw9MFOC-ooz2hoichDWmbZPXFZaAm-_3w7YYhv9g-UXtmm6U4Hjy7nzSlVTw6EFQSRouEPIsHODl-2MdiA2gJuhrt3KwqADZnqvOhvNhaGYofzatO25N6MeW6k3VgO1yem2g1VbAfQ52NdgLgXl2LZgnsiZ3MGYzNXZLSmmq1kWAwMa5tDePD0NF0mOCMOG89NHiHelFf6hH03TgMMGxeePuw6hXPIlFy0lhl4bNiKK38Y)官网查找相应的 jar 包文件
2. 选择相应的版本, 下载 jar 包文件到本地
3. 下载完毕后, 打开本地终端(terminal), 键入以下命令 `mvn install:install-file -Dfile=jar包本地位置信息 -DgroupId=jar包GroupId -DartifactId=jar包artifactId -Dversion=jar包版本号 -Dpackaging=jar`(相应信息皆在下载 jar 包的地方)
4. 点击回车, 即可安装完成

#### 使用骨架创建 Maven 的 Java 工程

1. 打开 IDEA, 创建新项目
2. 选择 Maven, 勾选 `Create from archetype`
3. 找到以下选项, 点击下一个![截屏2021-02-14 下午11.38.22](https://cdn.jsdelivr.net/gh/Lummer-Li/image-bucket/image/20210214233931.png)

4. 填写自己的 `GroupId` 和 `ArtifactId`, 点击下一个
5. 接着点击下一个
6. 填写项目名称, 选择项目位置, 即可完成 Maven 项目的创建
7. 手动添加 main 和 test 的 resources 测试文件夹, 并标记目录

#### 不使用骨架创建 maven 的 Java 工程(推荐使用)

1. 打开 IDEA, 创建新项目
2. 选择 Maven, 点击下一个
3. 填写自己的 `GroupId` 和 `ArtifactId`, 点击下一个
4. 点击完成即可
5. 创建可执行文件和 test 的 resources 测试文件夹, 并标记目录

#### 使用骨架创建 Maven 的 Web 工程

1. 打开 IDEA, 创建新项目
2. 选择 Maven, 勾选 `Create from archetype`
3. 找到以下选项, 点击下一个![截屏2021-02-14 下午11.38.22](https://cdn.jsdelivr.net/gh/Lummer-Li/image-bucket/image/20210215231927.png)

4. 填写自己的 `GroupId` 和 `ArtifactId`, 点击下一个
5. 接着点击下一个
6. 填写项目名称, 选择项目位置, 即可完成 Maven 项目的创建
7. 手动添加 main 的 java 源码文件夹, 并标记目录

#### Maven 工程 Servlet 实例之指定 Web

1. 在 `webapp` 文件夹下创建 `index.jsp` 文件
2. 在 `java` 文件夹下创建 Servlet 文件, 并在 `web.xml` 中添加相应的 <servlet> 和 <servlet-mapping> 标签, 填写相应的内容
3. 在  `pom.xml` 文件中添加  `Servlet ` 文件中所需  `jar包` 相应的依赖
4. 修改  `Servlet文件 ` , 导入相应的 `jar包` , 并填写所需内容

#### Maven 工程在运行 Tomcat 时可能遇到的问题

1. `jar包冲突`

```xml
<!-- 解决Maven工程中的jar包冲突, 以javax.servlet为例, 进行以下操作即可 -->
<dependency>
    <groupId>javax.servlet</groupId>
    <artifactId>servlet-api</artifactId>
    <version>2.5</version>
    <scope>provided</scope> <!-- 配置这一项，运行的时候不会重复导入servlet-api的jar包 -->
</dependency>
<!-- 即在 pom.xml 文件中, 添加上依赖的运行条件 -->
```

2. Maven 自身所带 Tomcat 版本过低, 与新版 JDK 不兼容

```xml
<!-- 解决Maven工程中Tomcat版本过低问题, 有以下两种解决方案 -->
(1)降低 JDK 版本
(2)配置新版Tomcat插件
<!-- 在 pom.xml 文件中, 添加所需插件 -->
<plugin>
    <groupId>org.apache.tomcat.maven</groupId>
    <artifactId>tomcat7-maven-plugin</artifactId>
    <version>2.2</version>
</plugin>
<!-- 并在 maven 的命令运行窗口进行以下操作 -->
<!-- mvn tomcat7:run -->
```

#### Maven 工程运行环境修改

1. Tomcat 环境修改
   - 在 `pom.xml` 文件中添加 <build><plugins><plugin><plugin><plugins><build> 标签

   - 在 `plugin标签` 中添加相应的内容

   ```xml
   <!--    指定版本 Tomcat 插件进行 Tomcat 运行 Web 工程项目    -->
   <plugin>
       <groupId>org.apache.tomcat.maven</groupId>
       <artifactId>tomcat7-maven-plugin</artifactId>
       <version>2.2</version>
     	<configuration>
         <port>8888</port>
     	</configuration>
   </plugin>
   ```

   - 在 maven 的命令运行窗口键入 `mvn tomcat7:run`

2. JDK 环境修改

   - 在 `pom.xml` 文件中添加 <build><plugins><plugin><plugin><plugins><build> 标签
   - 在 `plugin标签` 中添加相应的内容

   ```xml
   <!--    指定版本 JDK 插件进行编译    -->
   <plugin>
       <groupId>org.apache.maven.plugins</groupId>
       <artifactId>maven-compiler-plugin</artifactId>
       <configuration>
         <target>1.8</target>
         <source>1.8</source>
         <encoding>UTF-8</encoding>
       </configuration>
   </plugin>
   ```

#### 创建 Maven 的 Java 工程并连接 mysql 数据库

1. 打开 IDEA, 创建新项目
2. 选择 Maven, 点击下一个
3. 填写自己的 `GroupId` 和 `ArtifactId`, 点击下一个
4. 点击完成即可
5. 在 `pom.xml` 文件中添加需要的依赖
6. 在源码文件夹下设计连接mysql数据库并获取数据的 Java 类文件
7. 在测试文件夹中创建测试类进行测试
8. 得到结果

#### 依赖文件的使用范围

![截屏2021-02-17 下午5.02.53](https://cdn.jsdelivr.net/gh/Lummer-Li/image-bucket/image/20210217175056.png)

