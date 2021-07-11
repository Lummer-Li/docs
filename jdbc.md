### JDBC

---

#### JDBC 的概述

##### 1.1 什么是 JDBC

JDBC(Java Data Base Connectivity.Java数据库连接), 是一种用于执行 SQL 语句的 Java API, 可以为多种关系型数据库提供统一访问, 它由一组用 Java 语言编写的类和接口组成.

##### 1.2 什么是数据库驱动

- 驱动: 两个设备(应用)之间通信的桥梁.

##### 1.3 为什么学习 JDBC

没有 JDBC 的时候, 如果现在要开发一套系统, 使用 Java 连接 MySQL 数据库, 那么这时候 Java 程序员需要了解 MySQL 驱动 API, 如果使用 Java 连接 Oracle 数据库, 那么这个时候 Java 程序员需要了解 Oracle 数据库驱动 API.

SUN 公司提供了一套统一的规范(接口), 然后各个数据库生产商提供这套接口的实现. 这套接口规范就是 JDBC 的规范.

#### JDBC 的入门

##### 2.1 JDBC 的环境准备

1. 创建数据库和表

   ```sql
   create database web_test3;
   use web_test3;
   create table user(
   	id int primary key auto_increment,
   	username varchar(20),
   	password varchar(20),
   	nickname varchar(20),
   	age int
   );
   insert into user values (null, 'aaa', '123', '小丽	', 34);
   insert into user values (null, 'bbb', '123', '小王	', 32);
   insert into user values (null, 'ccc', '123', '大黄	', 29);
   insert into user values (null, 'ddd', '123', '小明	', 31);
   ```

2. 创建项目, 引入 jar 包

   ![注意 Build Path](https://cdn.jsdelivr.net/gh/Lummer-Li/image-bucket/image/20210126221815.png)

3. JDBC 的代码实现

   - JDBC 的开发步骤

     - 第一步: 加载驱动
     - 第二步: 获得连接
     - 第三步: 基本操作
     - 第四步: 释放资源

   - JDBC 的代码实现

     ```java
     package com.itheima.jdbc.demo1;
     
     import java.awt.datatransfer.StringSelection;
     import java.sql.Connection;
     import java.sql.DriverManager;
     import java.sql.ResultSet;
     import java.sql.Statement;
     
     import com.mysql.cj.protocol.Resultset;
     
     public class JDBCDemo1 {
     	//	JDBC 的入门程序
     	public static void main(String[] args) throws Exception{
     		// 1. 加载驱动
     		Class.forName("com.mysql.cj.jdbc.Driver");
     		// 2. 获得连接
     		Connection connection =  DriverManager.getConnection("jdbc:mysql://localhost:3306/ceshi", "root", "2caxcazdgn");
     		// 3. 基本操作: 执行 SQL
     			// 3.1 获得执行 SQL 语句的对象
     		Statement statement = connection.createStatement();
     			// 3.2 编写 SQL 语句
     		String sql = "select * from blog";
     			// 3.3 执行 SQL 语句
     		ResultSet rs = statement.executeQuery(sql);
     			// 3.4 遍历结果集合
     		System.out.println("--------------------------------");
     		while (rs.next()) {
     			System.out.print(rs.getInt("id") + " ");
     			System.out.println(rs.getString("phone_number"));
     			System.out.println("--------------------------------");
     		}
     		// 4. 释放资源
     		rs.close();
     		statement.close();
     		connection.close();
     	}
     }
     ```

#### JDBC 的 API 详解之 DriverManager

##### 3.1 DriverManager: 驱动管理类

1. 作用一: 注册驱动

   如果需要注册驱动, 就会使用 Drivermanager.registerDriver(new Driver()); 但是查看源代码发现, 在代码中有一段静态代码块, 静态代码块已经调用了注册驱动的方法.

   - 如果在手动调用该方法注册驱动, 就会导致该驱动注册两次. 实际开发中一般会采用: 	

     ```java 
     Class.forName("com.mysql.cj.jdbc.Driver");
     ```

2. 作用二: 获得连接

   这个方法就是用来获得与数据库连接的方法, 这个方法有三个参数:

   - url: 与数据库连接的路径
   - user: 与数据库连接的用户名
   - password: 与数据库连接的密码
   - 主要关注的是 url 的写法: `jdbc:mysql://localhost:3306/ceshi`
     - Jdbc: 连接数据库的协议
     - mysql: 是 jdbc 的子协议
     - localhost: 连接的 MySQL 数据库服务器的主机地址.(连接是本机就可以写成 localhost), 如果连接的不是本机, 就需要写上连接主机的 IP 地址
     - 3306: MySQL 数据库服务器的端口号
     - ceshi: 数据库名称
     - 注意: 如果连接的是本机的路径, 可以简化为如下格式: `jdbc:mysql:///ceshi`

#### JDBC 的 API 详解之 Connection

##### 4.1 Connection: 与数据库连接对象

1. 作用一: 创建执行 SQL 语句的对象

   执行 SQL 语句对象

   - Statement: 执行 SQL
   - CallableStatement: 执行数据库中存储过程
   - PreparedStatement: 执行 SQL, 对 SQL 进行预处理. 解决 SQL 注入漏洞

2. 作用二: 管理事务

#### JDBC 的 API 详解之 Statement

##### 5.1 Statement: 执行 SQL

1. 作用一: 执行 SQL

   执行 SQL 的方法:

   - boolean execute(String sql);
     - 执行查询、修改、添加、删除的 SQL 语句
   - **ResultSet executeQuery(String sql);**
     - **执行查询(执行 select 语句)**
   - **int executeUpdate(String sql);**
     - **智慧型修改、添加、删除的 SQL 语句**

2. 作用二: 执行批处理

#### JDBC 的 API 详解之 ResultSet

##### 6.1 ResultSet: 结果集(通过 select 查询的结果)

1. 结果集的遍历: rs.next()
   - 结果集的原理
   - 代码实现
2. 结果集的获取
   - 结果集获取可以使用结果集中的: getXXX(): 方法通常都会有一个重载的方法
     - getXXX(int columnIndex);
     - getXXX(String  columnName);



#### JDBC 的资源释放

##### 7.1 JDBC 资源释放

JDBC 程序执行结束后, 将与数据库进行交互的对象释放掉, 通常是 ResultSet、Statement、Connection

这几个对象中尤其是 Connection 对象是非常稀有的, 这个对象一定要做到尽量晚创建, 尽早释放掉.

- 将资源释放的代码写入到 finally 的代码块中

- 资源释放的代码应该写的标准

  ```java 
  if(rs != null){
  	try{
  		rs.close();
  	}catch(SQLException sqlEx){
  		rs = null;
  		sqlEX.printStackTrace();
  	}
  }
  if(stmt != null){
  	try{
  		stmt.close();
  	}catch(SQLException sqlEx){
  		stmt = null;
  		sqlEX.printStackTrace();
  	}
  }
  ```

#### JDBC 的 CRUD 操作之保存操作

##### 8.1 保存操作代码实现

```java
package com.itheima.jdbc.demo2;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.Statement;

public class JDBCDemo2 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		
		Connection connection = null;
		Statement statement = null;
		
		try {
			// 注册驱动
			Class.forName("com.mysql.cj.jdbc.Driver");
			// 获得连接
			connection = DriverManager.getConnection("jdbc:mysql://localhost:3306/ceshi", "root", "2caxcazdgn");
			// 执行操作
			// 创建执行 SQL 语句对象
			statement = connection.createStatement();
			// 编写 SQL 语句
			String sql = "insert into blog(phone_number, verification, blog_password) values('123456', '123456', '123456')";
			// 执行 SQL 语句
			int num = statement.executeUpdate(sql);
			if(num > 0) {
				System.out.println("用户连接成功!!!");
			}
		}catch (Exception e) {
			// TODO: handle exception
			e.printStackTrace();
		}finally {
			// 资源释放
			if(statement != null) {
				try {
					statement.close();
				} catch (Exception e2) {
					// TODO: handle exception
					e2.printStackTrace();
				}
				statement = null;
			}
			if(connection != null) {
				try {
					connection.close();
				} catch (Exception e2) {
					// TODO: handle exception
					e2.printStackTrace();
				}
				connection = null;
			}
		}
	}

}

```

#### JDBC 的 CRUD 操作之修改操作

##### 9.1 修改操作代码实现

```java
package com.itheima.jdbc.demo2;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.Statement;

public class JDBCDemo2 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		
		Connection connection = null;
		Statement statement = null;
		
		try {
			// 注册驱动
			Class.forName("com.mysql.cj.jdbc.Driver");
			// 获得连接
			connection = DriverManager.getConnection("jdbc:mysql://localhost:3306/ceshi", "root", "2caxcazdgn");
			// 执行操作
			// 创建执行 SQL 语句对象
			statement = connection.createStatement();
			// 编写 SQL 语句
//			String sql = "insert into blog(phone_number, verification, blog_password) values('123456', '123456', '123456')";
			String sql = "update blog set blog_password = 654321 where id = 6";
			// 执行 SQL 语句
			int num = statement.executeUpdate(sql);
			if(num > 0) {
				System.out.println("用户修改成功!!!");
			}
		}catch (Exception e) {
			// TODO: handle exception
			e.printStackTrace();
		}finally {
			// 资源释放
			if(statement != null) {
				try {
					statement.close();
				} catch (Exception e2) {
					// TODO: handle exception
					e2.printStackTrace();
				}
				statement = null;
			}
			if(connection != null) {
				try {
					connection.close();
				} catch (Exception e2) {
					// TODO: handle exception
					e2.printStackTrace();
				}
				connection = null;
			}
		}
	}

}
```

#### JDBC 的 CRUD 操作之删除操作

##### 10.1 删除操作代码实现

```java
package com.itheima.jdbc.demo2;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.Statement;

public class JDBCDemo2 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		
		Connection connection = null;
		Statement statement = null;
		
		try {
			// 注册驱动
			Class.forName("com.mysql.cj.jdbc.Driver");
			// 获得连接
			connection = DriverManager.getConnection("jdbc:mysql://localhost:3306/ceshi", "root", "2caxcazdgn");
			// 执行操作
			// 创建执行 SQL 语句对象
			statement = connection.createStatement();
			// 编写 SQL 语句
//			String sql = "insert into blog(phone_number, verification, blog_password) values('123456', '123456', '123456')";
//			String sql = "update blog set blog_password = 654321 where id = 6";
			String sql = "delete from blog where id = 7";
			// 执行 SQL 语句
			int num = statement.executeUpdate(sql);
			if(num > 0) {
				System.out.println("用户删除成功!!!");
			}
		}catch (Exception e) {
			// TODO: handle exception
			e.printStackTrace();
		}finally {
			// 资源释放
			if(statement != null) {
				try {
					statement.close();
				} catch (Exception e2) {
					// TODO: handle exception
					e2.printStackTrace();
				}
				statement = null;
			}
			if(connection != null) {
				try {
					connection.close();
				} catch (Exception e2) {
					// TODO: handle exception
					e2.printStackTrace();
				}
				connection = null;
			}
		}
	}

}

```

#### JDBC 的 CRUD 操作之查询操作

##### 11.1 查询多条记录

```java 
package com.itheima.jdbc.demo2;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.Statement;

public class JDBCDemo2 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		
		Connection connection = null;
		Statement statement = null;
		ResultSet rSet = null;
		try {
			// 注册驱动
			Class.forName("com.mysql.cj.jdbc.Driver");
			// 获得连接
			connection = DriverManager.getConnection("jdbc:mysql://localhost:3306/ceshi", "root", "2caxcazdgn");
			// 执行操作
			// 创建执行 SQL 语句对象
			statement = connection.createStatement();
			// 编写 SQL 语句
//			String sql = "insert into blog(phone_number, verification, blog_password) values('123456', '123456', '123456')";
//			String sql = "update blog set blog_password = 654321 where id = 6";
//			String sql = "delete from blog where id = 7";
			String sql = "select * from blog";
			// 执行 SQL 语句
			rSet = statement.executeQuery(sql);
			while (rSet.next()) {
				System.out.println(rSet.getInt("id") + " " + rSet.getString("blog_password"));
			}
		}catch (Exception e) {
			// TODO: handle exception
			e.printStackTrace();
		}finally {
			// 资源释放
      if(rSet != null) {
				try {
					rSet.close();
				} catch (Exception e2) {
					// TODO: handle exception
					e2.printStackTrace();
				}
				rSet = null;
			}
			if(statement != null) {
				try {
					statement.close();
				} catch (Exception e2) {
					// TODO: handle exception
					e2.printStackTrace();
				}
				statement = null;
			}
			if(connection != null) {
				try {
					connection.close();
				} catch (Exception e2) {
					// TODO: handle exception
					e2.printStackTrace();
				}
				connection = null;
			}
		}
	}

}

```

##### 11.2 查询一条记录

```java
package com.itheima.jdbc.demo2;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.Statement;

public class JDBCDemo2 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		
		Connection connection = null;
		Statement statement = null;
		ResultSet rSet = null;
		try {
			// 注册驱动
			Class.forName("com.mysql.cj.jdbc.Driver");
			// 获得连接
			connection = DriverManager.getConnection("jdbc:mysql://localhost:3306/ceshi", "root", "2caxcazdgn");
			// 执行操作
			// 创建执行 SQL 语句对象
			statement = connection.createStatement();
			// 编写 SQL 语句
//			String sql = "insert into blog(phone_number, verification, blog_password) values('123456', '123456', '123456')";
//			String sql = "update blog set blog_password = 654321 where id = 6";
//			String sql = "delete from blog where id = 7";
			String sql = "select * from blog where id = 8";
			// 执行 SQL 语句
			rSet = statement.executeQuery(sql);
			if(rSet.next()) {
				System.out.println(rSet.getInt("id") + " " + rSet.getString("blog_password"));
			}
		}catch (Exception e) {
			// TODO: handle exception
			e.printStackTrace();
		}finally {
			// 资源释放
			if(rSet != null) {
				try {
					rSet.close();
				} catch (Exception e2) {
					// TODO: handle exception
					e2.printStackTrace();
				}
				rSet = null;
			}
			if(statement != null) {
				try {
					statement.close();
				} catch (Exception e2) {
					// TODO: handle exception
					e2.printStackTrace();
				}
				statement = null;
			}
			if(connection != null) {
				try {
					connection.close();
				} catch (Exception e2) {
					// TODO: handle exception
					e2.printStackTrace();
				}
				connection = null;
			}
		}
	}

}

```

#### JDBC 的工具类的抽取

##### 12.1 抽取一个 JDBC 的工具类

因为传统 JDBC 的开发, 注册驱动、获得连接、释放资源这些代码都是重复的. 所以可以将重复的代码提取到一个类中来完成.

```java 
package com.itheima.jdbc.utils;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.Statement;

public class JDBCUtils {
	private static final String driverClassName;
	private static final String url;
	private static final String username;
	private static final String password;

	static {
		driverClassName = "com.mysql.cj.jdbc.Driver";
		url = "jdbc:mysql:///ceshi";
		username = "root";
		password = "2caxcazdgn";
	}
	
	// 注册驱动
	public static void loadDriver() {
		try {
			Class.forName(driverClassName);
		} catch (Exception e) {
			e.printStackTrace();
		}
	}
	
	// 获得连接
	public static Connection getConnection() {
		Connection connection = null;
		try {
			loadDriver();
			connection = DriverManager.getConnection(url, username, password);
		} catch (Exception e) {
			e.printStackTrace();
		}
		return connection;
	}
	
	// 释放资源
	public static void release(Statement statement, Connection connection) {
		// 资源释放
		if(statement != null) {
			try {
				statement.close();
			} catch (Exception e2) {
				// TODO: handle exception
				e2.printStackTrace();
			}
			statement = null;
		}
		if(connection != null) {
			try {
				connection.close();
			} catch (Exception e2) {
				// TODO: handle exception
				e2.printStackTrace();
			}
			connection = null;
		}	
	}
	public static void release(ResultSet rSet, Statement statement, Connection connection) {
		// 资源释放
		if(rSet != null) {
			try {
				rSet.close();
			} catch (Exception e2) {
				// TODO: handle exception
				e2.printStackTrace();
			}
			rSet = null;
		}
		if(statement != null) {
			try {
				statement.close();
			} catch (Exception e2) {
				// TODO: handle exception
				e2.printStackTrace();
			}
			statement = null;
		}
		if(connection != null) {
			try {
				connection.close();
			} catch (Exception e2) {
				// TODO: handle exception
				e2.printStackTrace();
			}
			connection = null;
		}
	}
	
}

```

##### 12.2 测试工具类

```java
package com.itheima.jdbc.demo3;

import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.Statement;

import com.itheima.jdbc.utils.JDBCUtils;

public class JDBCDemo3 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Connection connection = null;
		Statement statement = null;
		ResultSet rSet = null;
		
		try {
			// 获得连接
			connection = JDBCUtils.getConnection();
			// 创建执行 SQL 语句的对象
			statement = connection.createStatement();
			// 编写 SQL 语句
			String sql = "select * from blog";
			// 执行查询
			rSet = statement.executeQuery(sql);
			// 遍历结果集
			while(rSet.next()) {
				System.out.println(rSet.getInt("id") + " " + rSet.getString("blog_password"));
			}
		} catch (Exception e) {
			e.printStackTrace();
		}finally {
			JDBCUtils.release(rSet, statement, connection);
		}
		
	}

}

```

#### JDBC 的配置信息提取到配置文件

##### 13.1 配置文件

- 属性文件
  - 格式: 扩展名是 .properties
  - 内容: key=value
- XML 文件

##### 13.2 提取信息到配置文件

- 定义一个配置文件 

```java
driverClassName = com.mysql.cj.jdbc.Driver
url = jdbc:mysql://localhost:3306/ceshi
username = root
password = 2caxcazdgn
```

##### 13.3 在工具类中解析属性文件

- 获取到具体内容为常量赋值

```java
static {
		// 获取属性文件中的内容
		Properties properties = new Properties();
		try {
			properties.load(new FileInputStream("src/db.properties"));
		} catch (FileNotFoundException e) {
			e.printStackTrace();
		}catch (IOException e) {
			e.printStackTrace();
		}
		
		driverClassName = properties.getProperty("driverClassName");
		url = properties.getProperty("url");
		username = properties.getProperty("username");
		password = properties.getProperty("password");
	}
```

#### JDBC 的 SQL 注入漏洞

##### 14.1 什么是 SQL 注入漏洞

在早期的互联网上 SQL 注入漏洞普遍存在, 有一个网站, 用户需要注入, 用户注册以后根据用户名和密码完成登陆, 假设现在已经用户名被其他人知道了, 但是其他人不知道你的密码, 也可以登录到网站上进行相应的操作

##### 14.2 演示 SQL 注入漏洞

- 基本登陆功能实现

```java 
package com.itheima.jdbc.demo4;

import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.Statement;

import com.itheima.jdbc.utils.JDBCUtils;

public class UserDao {

	public boolean login(String username, String password) {
		Connection connection = null;
		Statement statement = null;
		ResultSet rSet = null;
		
		// 定义一个变量
		boolean flag = false;
		try {
			// 获得连接
			connection = JDBCUtils.getConnection();
			// 完成登陆功能
			// 创建执行 SQL 语句的对象
			statement = connection.createStatement();
			// 编写 SQL 语句
			String sql = "select * from blog where phone_number = '" + username + "' and blog_password = '" + password + "'";
			// 执行 SQL 语句
			rSet = statement.executeQuery(sql);
			if(rSet.next()) {
				// 说明根据用户名和密码可以查询到这条记录
				flag = true;
			}
		} catch (Exception e) {
			e.printStackTrace();
		}finally {
			JDBCUtils.release(rSet, statement, connection);
		}
		
		return false;
	}
}

```

- 演示 SQL 注入漏洞
  - 输入用户名
    - aaa'or'1=1 密码随意
    - aaa'--          密码随意

```java
package com.itheima.jdbc.demo4;

public class JDBCDemo4 {
	
	public static void main(String[] args) {
		UserDao userDao = new UserDao();
		
//		boolean flag = userDao.login("15830233129' or '1=1", "123sadasdas456");
		boolean flag = userDao.login("15830233129' -- ", "123sadasdas456");

		
		if(flag) {
			System.out.println("登录成功");
		}else {
			System.out.println("登录失败");
		}
	}

}
```

#### JDBC 的 SQL 注入漏洞的分析和解决

##### 15.1 SQL 注入漏洞分析

```
演示 SQL 注入漏洞

- 输入用户名
  - aaa'or'1=1 密码随意
  - aaa'--     密码随意
  
原因: 
	- 在变量中存在SQL的关键字
  	- or
  	- --
```

##### 15.2 SQL 注入漏洞解决

需要采用 PreparedStatement 对象解决 SQL 注入漏洞. 这个对象将 SQL 预先进行编译, 使用 ? 作为占位符. ? 代表的内容是 SQL 所固定的, 



```java 
package com.itheima.jdbc.demo4;

import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.Statement;

import com.itheima.jdbc.utils.JDBCUtils;

public class UserDao {
	
	public boolean login(String username, String password) {
		Connection connection = null;
		PreparedStatement statement = null;
		ResultSet rSet = null;
		
		// 定义一个变量
		boolean flag = false;
		try {
			// 获得连接
			connection = JDBCUtils.getConnection();
			// 完成登陆功能
			// 创建执行 SQL 语句的对象
			
			// 编写 SQL 语句
			String sql = "select * from blog where phone_number = ? and blog_password = ?";
			statement = connection.prepareStatement(sql);
			// 设置参数
			statement.setString(1, username);
			statement.setString(2, password);
			System.out.println(sql);
			// 执行 SQL 语句
			rSet = statement.executeQuery();
			if(rSet.next()) {
				// 说明根据用户名和密码可以查询到这条记录
				flag = true;
			}
		} catch (Exception e) {
			e.printStackTrace();
		}finally {
			JDBCUtils.release(rSet, statement, connection);
		}
		
		return flag;
	}

}

```

#### JDBC 的 CRUD 操作之 PreparedStatement 的保存操作

##### 16.1 保存操作代码实现

```java
package com.itheima.jdbc.demo5;

import java.sql.Connection;
import java.sql.PreparedStatement;

import com.itheima.jdbc.utils.JDBCUtils;

public class JDBCDmeo5 {

	public static void main(String[] args) {
		
		Connection connection = null;
		PreparedStatement pStatement = null;
		try {
			// 获得连接
			connection = JDBCUtils.getConnection();
			
			// SQL 语句
			String sql = "insert into blog values(null, ?, ?, ?)";
			
			// 预编译 SQL
			pStatement = connection.prepareStatement(sql);
			
			// 设置参数
			pStatement.setString(1, "12367876");
			pStatement.setString(2, "wuyanzhengma ");
			pStatement.setString(3, "0987654321");

			// 执行 SQL 
			int num = pStatement.executeUpdate();
			
			if(num > 0) {
				System.out.println("保存成功");
			}
			
		} catch (Exception e) {
			e.printStackTrace();
		}finally {
			JDBCUtils.release(pStatement, connection);
		}
	}
	
}

```

#### JDBC 的 CRUD 操作之 PreparedStatement 的修改操作

##### 17.1 修改操作代码实现

```java
package com.itheima.jdbc.demo6;

import java.sql.Connection;
import java.sql.PreparedStatement;

import com.itheima.jdbc.utils.JDBCUtils;

public class JDBCDemo6 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		
		Connection connection = null;
		PreparedStatement pStatement = null;
		try {
			connection = JDBCUtils.getConnection();
			
			String sql = "update blog set password = ? where id = 3";
			
			pStatement = connection.prepareStatement(sql);
			
			pStatement.setString(1, "000000");
			
			int num = pStatement.executeUpdate();
			
			if(num > 0) {
				System.out.println("修改成功");
			}
		} catch (Exception e) {
			e.printStackTrace();
		} finally {
			JDBCUtils.release(pStatement, connection);
		}
	}

}

```

#### JDBC 的 CRUD 操作之 PreparedStatement 的删除操作

##### 18.1 删除操作的代码实现

```java
package com.itheima.jdbc.demo7;

import java.sql.Connection;
import java.sql.PreparedStatement;

import com.itheima.jdbc.utils.JDBCUtils;

public class JDBCDemo7 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		
		Connection connection = null;
		PreparedStatement pStatement = null;
		
		try {
			connection = JDBCUtils.getConnection();
			
			String sql = "delete from blog where id = ?";
			
			pStatement = connection.prepareStatement(sql);
			
			pStatement.setInt(1, 15);
			
			int num = pStatement.executeUpdate();
			
			if(num > 0) {
				System.out.println("删除成功");
			}
		} catch (Exception e) {
			// TODO: handle exception
			e.printStackTrace();
		}finally {
			JDBCUtils.release(pStatement, connection);
		}

	}

}
```

#### JDBC 的 CRUD 操作之 PreparedStatement 的查询操作

##### 19.1 查询操作代码实现

```java
package com.itheima.jdbc.demo8;

import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.ResultSet;

import com.itheima.jdbc.utils.JDBCUtils;

public class JDBCDemo8 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Connection connection = null;
		PreparedStatement pStatement = null;
		ResultSet rSet = null;
		
		try {
			connection = JDBCUtils.getConnection();
			
			String sql = "select * from blog";
			
			pStatement = connection.prepareStatement(sql);
			
			
			rSet = pStatement.executeQuery();
			
			while(rSet.next()) {
				System.out.println(rSet.getInt("id") + " " + rSet.getString("phone"));
			}
			
			
			
 		} catch (Exception e) {
			e.printStackTrace();
		} finally {
			JDBCUtils.release(rSet, pStatement, connection);
		}

	}

}

```

#### JDBC 的批处理

##### 20.1 什么是批处理

之前进行 JDBC 的操作的时候, 都是一条 SQL 语句执行, 现在如果使用批处理, 可以将一批 SQL 一起执行

##### 20.2 批处理基本使用

```java
package com.itheima.jdbc.demo9;

import java.sql.Connection;
import java.sql.Statement;

import com.itheima.jdbc.utils.JDBCUtils;

public class JDBCDemo9 {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		// 批处理的基本操作
		
		Connection connection = null;
		Statement statement = null;
		
		try {
			connection = JDBCUtils.getConnection();
			
			statement = connection.createStatement();
			
			String sql1 = "create database test1";
			String sql2 = "use test1";
			String sql3 = "create table user(id int primary key auto_increment, name varchar(20))";
			String sql4 = "insert into user values(null, 'aaa')";
			String sql5 = "insert into user values(null, 'bbb')";
			String sql6 = "insert into user values(null, 'ccc')";
			String sql7 = "update user set name = 'mmm' where id = 2";
			String sql8 = "delete from user where id = 1";
			
			// 添加到批处理
			statement.addBatch(sql1);
			statement.addBatch(sql2);
			statement.addBatch(sql3);
			statement.addBatch(sql4);
			statement.addBatch(sql5);
			statement.addBatch(sql6);
			statement.addBatch(sql7);
			statement.addBatch(sql8);
			
			// 执行批处理
			statement.executeBatch();

		} catch (Exception e) {
			// TODO: handle exception
			e.printStackTrace();
		} finally {
			JDBCUtils.release(statement, connection);
		}
		
		
	}

}

```

##### 20.3 批量插入 (使用 PreparedStatement)

```java
package com.itheima.jdbc.demo9;

import java.sql.Connection;
import java.sql.PreparedStatement;

import com.itheima.jdbc.utils.JDBCUtils;

public class JDBCDemo9_PreparedStatement {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		// 默认情况下, MySQL 没有开启批处理, 需要在 URL 后拼接一个参数
		// 记录开始时间
		long begin = System.currentTimeMillis();

		Connection connection = null;
		PreparedStatement pStatement = null;
		
		try {
			connection = JDBCUtils.getConnection();
			
			String sqlString = "insert into user values(null, ?)";
			
			pStatement = connection.prepareStatement(sqlString);
			
			for(int i=1; i<=10000; i++) {
				pStatement.setString(1, "name" + i);
				
				// 添加到批处理
				pStatement.addBatch();
				
				// 注意问题
				// 执行批处理
				if(i % 1000 == 0) {
					// 执行批处理
					pStatement.executeBatch();
					// 清除批处理
					pStatement.clearBatch();
					
				}
			}		
		} catch (Exception e) {
			// TODO: handle exception
			e.printStackTrace();
		} finally {
			JDBCUtils.release(pStatement, connection);
		}
		
		// 记录结束时间
		long end = System.currentTimeMillis();
		
		System.out.println((end - begin));
	}

}

```

#### JDBC 的事物环境准备

##### 21.1 事务的概念

事务指的是逻辑上的一组操作, 组成这组操作的各个逻辑单元要么全部成功, 要么全部失败

##### 21.2 事物环境准备

- 创建数据库和表单

```mysql
create database lummer;
use lummer;
create table account (
 	id int primary key auto_increment,
 	name varchar(20),
 	money double
);
insert into account values(null, "aaa", 10000);
insert into account values(null, "bbb", 10000);
insert into account values(null, "ccc", 10000);

```

#### JDBC 的事务管理

##### 22.1 转账案例代码实现

```java
package jdbc_transaction;

import java.sql.Connection;
import java.sql.PreparedStatement;

import org.junit.Test;

import com.itheima.jdbc.utils.JDBCUtils;

public class TransactionDemo1 {

	@Test
	public void demo1() {
		Connection connection = null;
		PreparedStatement pStatement = null;
		try {
			connection = JDBCUtils.getConnection();
			
			String sql = "update blog set password = password + ? where id = ?";
			
			pStatement = connection.prepareStatement(sql);
			
			pStatement.setString(1, "-10000");
			pStatement.setInt(2, 1);
			
			pStatement.setString(1, "10000");
			pStatement.setInt(2, 2);
			
			pStatement.executeUpdate();
			
			System.out.println("转账成功");
		} catch (Exception e) {
			// TODO: handle exception
			e.printStackTrace();
		} finally {
			JDBCUtils.release(pStatement, connection);
		}
	}
}
// 在转账中没有添加事务的管理, 导致 id=1 的帐号的钱被转丢了, 但是 id=2 的帐号的钱没有任何变化. 需要给转账的功能添加事务的管理.
```

##### 22.2 在转账中添加事务管理

- 事务管理的 API
  - setAutoCommit()
  - commit()
  - rollback()

- 在转账中添加事务管理

```java
package jdbc_transaction;

import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.SQLException;

import org.junit.Test;

import com.itheima.jdbc.utils.JDBCUtils;

public class TransactionDemo1 {

	@Test
	public void demo1() throws SQLException {
		Connection connection = null;
		PreparedStatement pStatement = null;
		try {
			connection = JDBCUtils.getConnection();
			connection.setAutoCommit(false);
			
			String sql = "update blog set password = password + ? where id = ?";
			
			pStatement = connection.prepareStatement(sql);
			
			pStatement.setString(1, "-10000");
			pStatement.setInt(2, 1);
			
			pStatement.setString(1, "10000");
			pStatement.setInt(2, 2);
			
			pStatement.executeUpdate();
			
			System.out.println("转账成功");
			connection.commit();
		} catch (Exception e) {
			connection.rollback();
			// TODO: handle exception
			e.printStackTrace();
		} finally {
			JDBCUtils.release(pStatement, connection);
		}
	}
}

```



