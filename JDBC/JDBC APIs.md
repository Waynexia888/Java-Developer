### 什么是JDBC？
- Java数据库连接 -> Java DataBase Connectivity
- JDBC可让Java通过程序操作关系型数据库
- JDBC基于驱动程序实现与数据库的连接与操作

### JDBC的优点
- 统一的API，提供一致的开发过程
- 易于学习，容易上手，代码结构稳定
- 功能强大，执行效率高，可处理海量数据

### JDBC开发流程
- 加载并注册JDBC驱动
  - 获取JDBC的MySQL驱动：https://www.mysql.com/products/connector/
  - Class.forName用于加载指定的JDBC驱动类
  - Class.forName本质是通知JDBC注册这个驱动类
  - 驱动由数据库厂商自行开发，连接字符串也不同
  - <img src="https://github.com/Waynexia888/Java-Developer/blob/main/Images/%E5%88%9B%E5%BB%BA%E6%95%B0%E6%8D%AE%E5%BA%93%E8%BF%9E%E6%8E%A5%E4%BB%A3%E7%A0%81.png" width="600" height="400">
  - <img src="https://github.com/Waynexia888/Java-Developer/blob/main/Images/%E6%95%B0%E6%8D%AE%E5%BA%93%E4%B8%8E%E8%BF%9E%E6%8E%A5%E5%AD%97%E7%AC%A6%E4%B8%B2.png" width="800" height="400">
- 创建数据库连接
- 创建Statement对象
- 遍历查询结果
- 关闭连接，释放资源
