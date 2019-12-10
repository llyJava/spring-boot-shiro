1.下载或者克隆项目
   把项目添加到IDE下，用maven插件下载依赖，一般maven都是自动下载依赖的，若有问题，自行解决maven相关问题。

2.初始数据
     目前用的是mysql数据库，在resources/sql目录下找到mysql的sql文件到mysql数据库执行
     若是pg库，找到pg的sql文件到pg数据库执行

3.配置文件修改，根据指定的环境修改指定的yml文件
  3.1数据源修改
     3.1.1druib密码加密的问题：
     不加密：spring.datasource.connectionProperties属性值去掉config.decrypt=true和config.decrypt.key，然后spring.datasource.password=明文密码
     加密：默认是加密的，我们需要获得config.decrypt.key值和passwoord加密值，步骤1：到maven仓库找到druib jar包，在该目录下打开命令行，执行
        java -cp .\druid-xxx.jar com.alibaba.druid.filter.config.ConfigTools password(你的明文密码) ，产生的publicKey就是config.decrypt.key，password就是加密后的密码
        参考：https://blog.csdn.net/feifuzeng/article/details/80798934

      3.1.2 相关的数据库的ip，port和库名要与数据库信息一致
  3.2 redis配置
    redis必须设置密码，关于redis的下载，安装和配置详解：https://blog.csdn.net/Rudolf__/article/details/103476111
