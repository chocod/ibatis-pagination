# ibatis-pagination
ibatis的分页实现



#配置引入 configLocation文件#
	<bean id="sqlSessionFactory" class="org.mybatis.spring.SqlSessionFactoryBean">
		<property name="dataSource" ref="dataSource" />
		<!--configLocation属性指定mybatis的核心配置文件 -->
		<property name="configLocation" value="classpath:mybatis-config.xml" />
		   <!-- 所有配置的mapper文件 -->
	     <property name="mapperLocations" value="classpath*:mapper/*.xml" />
	</bean>

	<bean class="org.mybatis.spring.mapper.MapperScannerConfigurer">
		<property name="basePackage" value="com.chocod.summarize.dao.mapper" />
	</bean>
	
#configLocation文件#
	<?xml version="1.0" encoding="UTF-8"?>
	<!DOCTYPE configuration PUBLIC "-//mybatis.org//DTD Config 3.0//EN" 	"http://mybatis.org/dtd/mybatis-3-config.dtd">

<configuration>

	<plugins>
		<plugin interceptor="com.chocod.pagination.paginator.PageInterceptor">
			<property name="dialectClass" value="com.chocod.pagination.paginator.dialect.MySQLDialect" />
		</plugin>
	</plugins>
	
</configuration>