## Mysql
事务ACID 
### JDBC
1.创建工程导入驱动jar包  
2.注册驱动 Class.forName("com.mysql.jdbc.Driver);  
3.获取连接 Connection conn = DriverManager.getConnection(url, username, password);  

4.获取执行sql对象Statement stmt = conn.createStatement();
5.执行sql 处理返回结果 释放资源
  
  **API**  
1.DriverManager  
一个工具类。
