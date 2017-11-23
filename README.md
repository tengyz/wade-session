wade-session
======================
-------------

#简介#

##分布式session框架##

默认使用redis做session储存，支持redis集群
使用filter方式实现无缝切换，兼容老项目，无需修改任何代码



##使用方式##
#1.classpath下建立config.properties文件#

cookie.domain=www.wade.com   非必须 默认为空
cookie.path=/xxx  非必须  默认为"/"  
cookie.name=XXXXXX  非必须 默认为WADE_SESSIONID  
cookie.maxAge=1029  非必须 默认为-1  
session.timeout=3600（秒） 非必须 默认为1800  
session.storage=com.wade.framework.storage.redis.RedisStorage 非必须  默认为RedisStorage  自定义储存请实现Storage接口

redis.address=127.0.0.1:6379  单机  
redis.address=127.0.0.1:7001,127.0.0.1:7002,127.0.0.1:7003,127.0.0.1:7004,127.0.0.1:7005,127.0.0.1:7006  集群  
redis.timeout=3000  
redis.database=3    
redis.maxIdle=3000  
redis.maxWait=6000  
redis.minEvictableIdleTimeMillis=864000000  
redis.minIdle=1000  
redis.numTestsPerEvictionRun=10  
redis.softMinEvictableIdleTimeMillis=10  
redis.timeBetweenEvictionRunsMillis=300000  
 
#2.web.xml文件中添加filter
	
	<filter>
		<filter-name>WadeSessionFilter</filter-name>
		<filter-class>com.wade.session.WadeSessionFilter</filter-class>
	</filter>
	<filter-mapping>
		<filter-name>WadeSessionFilter</filter-name>
		<url-pattern>/*</url-pattern>
	</filter-mapping>

OK.至此，分布式session搞定
