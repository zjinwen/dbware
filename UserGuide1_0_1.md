新增功能：
1，实现对备库可动态扩容，而不需要重启服务器。
2，实现对日志记录可以动态修改，不需要重启服务器。

备库扩容方法：
1，先在dbServer.xml中配置数据源：如：
> 

&lt;named-config name="slave3"&gt;


> > 

&lt;property name="driverClass"&gt;

com.mysql.jdbc.Driver

&lt;/property&gt;


> > 

&lt;property name="jdbcUrl"&gt;

jdbc:mysql://127.0.0.1:3306/wuxiaodong

&lt;/property&gt;


> > 

&lt;property name="user"&gt;

root

&lt;/property&gt;


> > 

&lt;property name="password"&gt;

123456

&lt;/property&gt;



> 

&lt;/named-config&gt;



2，在dbRule.xml的节点slave中加入该数据源名称slave3，如：

&lt;slave&gt;

slave1\*3,slave2,slave3\*2

&lt;/slave&gt;



这样就完成扩容。一般在5分钟内生效。


日志记录可以动态修改：
只需按您的需要正常修改dbware.xml中节点general\_log，slowSql的值即可生效。