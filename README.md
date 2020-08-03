# others

spring.datasource.indicator.cn.url=jdbc:mysql://10.120.15.112:3306/asean_qh?useUnicode=true&allowMultiQueries=true&characterEncoding=utf8&useSSL=true&autoReconnect=true&failOverReadOnly=false
spring.datasource.indicator.cn.username=root
spring.datasource.indicator.cn.password=123456
spring.datasource.indicator.cn.driver-class-name=com.mysql.jdbc.Driver
spring.datasource.indicator.cn.testWhileIdle=true
spring.datasource.indicator.cn.validationQuery=select 1
spring.datasource.indicator.cn.timeBetweenEvictionRunsMillis=30000
spring.datasource.indicator.cn.minEvictableIdleTimeMillis=30000
spring.datasource.indicator.cn.minIdle=5
spring.datasource.indicator.cn.initialSize=5
spring.datasource.indicator.cn.maxActive=30
spring.datasource.indicator.cn.testOnBorrow=true


########################################################SERVER
server.port=33598
server.address = 0.0.0.0
server.context-path: /asean-indicator
#开启mybatis二级缓存
mybatis.configuration.cache-enabled=false


##################################log config#####################
logging.level.root=info
logging.path=/data/xinhua/domain/asean-indicator/logs
logging.level.com.asean.indicator.dao=debug



<?xml version="1.0" encoding="UTF-8"?>
<configuration scan="true" scanPeriod="60 seconds" debug="false">

    <contextName>BillMarket-Data</contextName>

    <property name="logback.appname" value="BillMarket-Data"/>

    <!--输出到控制台-->
    <appender name="console" class="ch.qos.logback.core.ConsoleAppender">
        <encoder>
            <pattern>%d{HH:mm:ss.SSS} %contextName [%thread] %-5level %logger{36} - %msg%n</pattern>
            <charset>UTF-8</charset>
        </encoder>
    </appender>

    <appender name="fileLog" class="ch.qos.logback.core.rolling.RollingFileAppender">
        <File>${LOG_PATH}/${logback.appname}.log</File>
        <rollingPolicy class="ch.qos.logback.core.rolling.TimeBasedRollingPolicy">
            <FileNamePattern>${LOG_PATH}/${logback.appname}.%d{yyyy-MM-dd}.log</FileNamePattern>
            <maxHistory>90</maxHistory>
        </rollingPolicy>
        <!--日志输出编码格式化-->
        <encoder>
            <charset>UTF-8</charset>
            <pattern>%d [%thread] %-5level %logger{36} %line - %msg%n</pattern>
        </encoder>
    </appender>


    <!--指定最基础的日志输出级别-->
    <root level="INFO">
        <appender-ref ref="console"/>
        <appender-ref ref="fileLog"/>
    </root>
</configuration>



<?xml version="1.0" encoding="UTF-8"?>    
<!DOCTYPE configuration    
    PUBLIC "-//mybatis.org//DTD Config 3.0//EN"    
    "http://mybatis.org/dtd/mybatis-3-config.dtd">
    
    
<configuration>


    <!-- 全局参数 -->
    <settings>
        <!-- 使全局的映射器启用或禁用缓存。 -->
        <setting name="cacheEnabled" value="true"/>

        <!-- 全局启用或禁用延迟加载。当禁用时，所有关联对象都会即时加载。 -->
        <setting name="lazyLoadingEnabled" value="true"/>

        <!-- 当启用时，有延迟加载属性的对象在被调用时将会完全加载任意属性。否则，每种属性将会按需要加载。 -->
        <setting name="aggressiveLazyLoading" value="true"/>

        <!-- 是否允许单条sql 返回多个数据集  (取决于驱动的兼容性) default:true -->
        <setting name="multipleResultSetsEnabled" value="true"/>

        <!-- 是否可以使用列的别名 (取决于驱动的兼容性) default:true -->
        <setting name="useColumnLabel" value="true"/>

        <!-- 允许JDBC 生成主键。需要驱动器支持。如果设为了true，这个设置将强制使用被生成的主键，有一些驱动器不兼容不过仍然可以执行。  default:false  -->
        <setting name="useGeneratedKeys" value="false"/>

        <!-- 指定 MyBatis 如何自动映射 数据基表的列 NONE：不隐射　PARTIAL:部分  FULL:全部  -->
        <setting name="autoMappingBehavior" value="PARTIAL"/>

        <!-- 这是默认的执行类型  （SIMPLE: 简单； REUSE: 执行器可能重复使用prepared statements语句；BATCH: 执行器可以重复执行语句和批量更新）  -->
        <setting name="defaultExecutorType" value="SIMPLE"/>

        <!-- 使用驼峰命名法转换字段。 -->
        <setting name="mapUnderscoreToCamelCase" value="true"/>

        <!-- 设置本地缓存范围 session:就会有数据的共享  statement:语句范围 (这样就不会有数据的共享 ) defalut:session -->
        <setting name="localCacheScope" value="SESSION"/>

        <!-- 设置但JDBC类型为空时,某些驱动程序 要指定值,default:OTHER，插入空值时不需要指定类型 -->
        <setting name="jdbcTypeForNull" value="NULL"/>

        <!--
        修正SQL字段为null时，接口不返回对应字段问题
        -->
        <setting name="cacheEnabled" value="true"/>
        <setting name="callSettersOnNulls" value="true"/>

    </settings>

</configuration>
# Tomcat
server:
    port: 33370
    servlet:
      context-path: /aseanApi

Spring:
    datasource:
      financial-info-network-news:
            url: jdbc:mysql://10.120.15.112:3306/financial_info_network_news?useUnicode=true&characterEncoding=utf8&useSSL=false&allowPublicKeyRetrieval=true&serverTimezone=GMT%2B8
            type: com.alibaba.druid.pool.DruidDataSource
            username: root
            password: 123456
            driver-class-name: com.mysql.cj.jdbc.Driver
            initialSize: 1
            minIdle: 3
            maxActive: 20
            maxWait: 60000
            #配置间隔多久才进行一次检测，检测需要关闭的空闲连接，单位是毫秒
            timeBetweenEvictionRunsMillis: 60000
            #销毁线程中如果检测到当前连接的最后活跃时间和当前时间的差值大于minEvictableIdleTimeMillis，则关闭当前连接。
            minEvictableIdleTimeMillis: 300000
            validationQuery: select 'x'
            testWhileIdle: true
            testOnBorrow: false
            testOnReturn: false
            useGlobalDataSourceStat: true
            removeAbandoned: true
            removeAbandonedTimeout: 1800
            logAbandoned: true
##################################log config#####################
logging:
    level: info
    file:
      path: ./target/logs
    level.com.xinhua.financialnetwork: debug

##################################Constants#####################
constants:
    cat-id-country-map:
      5393: DM_BRU_MAIN,文莱
      5394: DM_KHM_MAIN,柬埔寨
      5395: DM_IDN_MAIN,印度尼西亚
      5396: DM_LA_MAIN,老挝
      5397: DM_MAL_MAIN,马来西亚
      5398: DM_MMR_MAIN,缅甸
      5399: DM_PHL_MAIN,菲律宾
      5400: DM_SG_MAIN,新加坡
      5401: DM_TH_MAIN,泰国
      5402: DM_VNM_MAIN,越南
enable-token-validate: true

asean:
  auth:
    appkey: icmp
    appsecret: 80aaf1d5-12e4-4f56-a03b-92ac4cd4dde9
    
    
    
    package com.xhcj.common;

import org.springframework.beans.BeansException;
import org.springframework.beans.factory.DisposableBean;
import org.springframework.cloud.config.client.ConfigServicePropertySourceLocator;
import org.springframework.context.ApplicationContext;
import org.springframework.context.ApplicationContextAware;
import org.springframework.core.env.Environment;
import org.springframework.stereotype.Component;

import javax.swing.*;

/**
 * @Package com.xinhua.aseanspider.common.entity
 * @ClassName SpringContextHolder
 * @Description TODO
 * @Author JYX
 * @Date 2019/8/20
 * @Version 1.0
 * Created by JYX on 2019/8/20 9:57
 */
@Component
public class SpringContextHolder implements ApplicationContextAware, DisposableBean {

    private static final String PROD_ENVIRONMENT_PROFILE="prod";

    private  static ApplicationContext applicationContext=null;
    @Override
    public void setApplicationContext(ApplicationContext applicationContext) throws BeansException {
        SpringContextHolder.applicationContext=applicationContext;
    }

    @Override
    public void destroy() throws Exception {
        SpringContextHolder.applicationContext=null;
    }

    public static <T> T getBean(String name) {
        return (T) applicationContext.getBean(name);
    }

    public static <T> T getBean(Class<T> requiredType) {
        return applicationContext.getBean(requiredType);
    }

    public static String getSpringBootActiveProfile() {
        return applicationContext.getEnvironment().getActiveProfiles()[0];
    }

    public static String getSpringCloudActiveProfile() {
        String profileKey = "spring.cloud.config.profile";
        Environment environment = applicationContext.getEnvironment();

        if (!environment.containsProperty(profileKey)) {
            return "";
        }
        return environment.getProperty(profileKey);
    }

    /**
     * @Method  getActiveProfile
     * @Description 获取当前环境 profile
     * @Author: JYX
     * @Param []
     * @Return java.lang.String
     * Created by JYX on 2019/4/8 11:21
     */
    public static String getActiveProfile(){
        String cloudProfile = getSpringCloudActiveProfile();
        if(!"".equals(cloudProfile)){
            return cloudProfile;
        }

        return getSpringBootActiveProfile();
    }

    public static boolean isProdEnvironment(){
        if(PROD_ENVIRONMENT_PROFILE.equals(getActiveProfile())){
            return true;
        }
        return false;
    }



}

package com.xhcj.common.config;

import com.github.pagehelper.PageInterceptor;
import org.apache.ibatis.annotations.Mapper;
import org.apache.ibatis.plugin.Interceptor;
import org.apache.ibatis.session.SqlSessionFactory;
import org.mybatis.spring.SqlSessionFactoryBean;
import org.mybatis.spring.SqlSessionTemplate;
import org.mybatis.spring.annotation.MapperScan;
import org.springframework.beans.factory.annotation.Qualifier;
import org.springframework.boot.context.properties.ConfigurationProperties;
import org.springframework.boot.jdbc.DataSourceBuilder;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.context.annotation.Primary;
import org.springframework.core.io.support.PathMatchingResourcePatternResolver;
import org.springframework.jdbc.datasource.DataSourceTransactionManager;

import javax.sql.DataSource;
import java.util.Properties;

/**
 * @author zhb
 * @description
 * @time 2019-11-27 10:48
 */

@Configuration
@MapperScan(basePackages = "com.xhcj.dao" , sqlSessionTemplateRef = "sqlSessionTemplate")
public class DataSourceConfig {

    @Bean(name = "dataSource")
    @ConfigurationProperties(prefix = "spring.datasource")
    public DataSource dataSource() {
        return DataSourceBuilder.create().build();
    }

    @Bean(name = "sqlSessionFactory")
    @Primary
    public SqlSessionFactory testSqlSessionFactory(@Qualifier("dataSource") DataSource dataSource) throws Exception {
        SqlSessionFactoryBean bean = new SqlSessionFactoryBean();
        bean.setDataSource(dataSource);
        bean.setMapperLocations(new PathMatchingResourcePatternResolver().getResources("classpath:mybatis/mapper/*.xml"));
        bean.setPlugins(new Interceptor[]{getPageHelper()});
        return bean.getObject();
    }

    @Bean(name = "sqlSessionTemplate")
    @Primary
    public SqlSessionTemplate sqlSessionTemplate(@Qualifier("sqlSessionFactory") SqlSessionFactory sqlSessionFactory) throws Exception {
        return new SqlSessionTemplate(sqlSessionFactory);
    }

    @Bean(name = "transactionManager")
    @Primary
    public DataSourceTransactionManager transactionManager(@Qualifier("dataSource") DataSource dataSource) {
        return new DataSourceTransactionManager(dataSource);
    }

    public PageInterceptor getPageHelper() {
        PageInterceptor interceptor = new PageInterceptor();
        Properties properties = new Properties();
        properties.setProperty("helperDialect", "mysql");
        properties.setProperty("reasonable", "true");
        properties.setProperty("supportMethodsArguments", "true");
        properties.setProperty("returnPageInfo", "check");
        properties.setProperty("params", "count=countSql");
        interceptor.setProperties(properties);
        return interceptor;
    }
}


package com.xhcj.common.dao;

import com.github.pagehelper.PageHelper;
import com.github.pagehelper.PageInfo;
import com.google.common.collect.Lists;
import com.xhcj.common.SpringContextHolder;
import com.xhcj.common.utils.StringUtil;
import lombok.extern.slf4j.Slf4j;
import org.apache.ibatis.cursor.Cursor;
import org.apache.ibatis.session.ExecutorType;
import org.apache.ibatis.session.SqlSession;
import org.mybatis.spring.SqlSessionTemplate;
import org.springframework.transaction.TransactionStatus;

import java.util.Collection;
import java.util.List;
import java.util.Map;
import java.util.Objects;

/**
 * @Package com.xinhua.aseanspider.common.service
 * @ClassName MyBatisBaseDao
 * @Description TODO
 * @Author JYX
 * @Date 2019/8/20
 * @Version 1.0
 * Created by JYX on 2019/8/20 11:25
 */
@Slf4j
public class MyBatisBaseDao {

    private static SqlSessionTemplate sqlSessionTemplate=null ;

    public static SqlSessionTemplate getSqlSessionTemplate() {
        if (sqlSessionTemplate == null) {
            sqlSessionTemplate = SpringContextHolder.getBean("sqlSessionTemplate");
    }
        return sqlSessionTemplate ;
    }

    /**
     * mapKey需与数据库字段名完全匹配
     *
     * @param statement
     * @param params
     * @param mapKey 字段名
     * @return
     */
    public static Map<String,Map> selectMap(String statement, Map params,String mapKey) {
        return getSqlSessionTemplate().selectMap(statement,params,mapKey);
    }

    /**
     * 大数量使用游标进行分批处理
     *
     * Cursor<Map> cursor = selectCursor(statement,params);
     * Iterator<Map> iter = cursor.iterator();
     *
     * List<Map> fetchGroup = new ArrayList(10);
     * while (iter.hasNext()) {
     *     // Fetch next 10 records
     *     for(int i = 0; i<10 && iter.hasNext(); i++) {
     *         fetchGroup.add(iter.next());
     *     }
     *     doSomething(fetchGroup);
     *     fetchGroup.clear();
     * }
     *
     * @param statement
     * @param params
     * @return
     */
    public static Cursor<Map> selectCursor(String statement, Map params){
         return getSqlSessionTemplate().selectCursor(statement,params);
    }

    /**
     * 获取list最上面一个值 ,结果集超过一个，抛出异常
     * @Method  selectMapAsItem0
     * @Description
     * @Author: JYX
     * @Params [statement, params]
     * @Return java.util.Map
     * Created by JYX on 2019/4/12 15:51
     */
    public static Map selectOne(String statement, Map params) {
        return getSqlSessionTemplate().selectOne(statement,params);
    }

    public static List<Map> selectList(String statement, Map params) {
        return getSqlSessionTemplate().selectList(statement,params);
    }

    public static int  insert(String statement, Map params) {
        return getSqlSessionTemplate().insert(statement,params);
    }

    /**
     * sql 中使用 foreach
     *
     * @param statement
     * @param params
     * @return
     */
    public static int  insertBatch(String statement, Map params) {
        return getSqlSessionTemplate().insert(statement,params);
    }

    public static void insertBatch(String statement, Collection<Map> params) throws Exception {
        Objects.requireNonNull(params);

        SqlSession sqlSession = null;
        TransactionStatus tx = null;
        try {
            tx = TransactionUtil.newTransaction();
            //创建一个不自动commit的sqlsession
            sqlSession = getSqlSessionTemplate().getSqlSessionFactory().openSession(ExecutorType.BATCH,false);

            for(Map record : params){
                sqlSession.insert(statement,record);
            }
            sqlSession.commit();
            TransactionUtil.commit(tx);
        } catch (Exception e) {
            TransactionUtil.rollback(tx);
            throw e;
        } finally {
            if(sqlSession != null){
                sqlSession.close();
            }
        }
    }

    public static int  update(String statement, Map params) {
        return getSqlSessionTemplate().update(statement,params);
    }
    public static int  delete(String statement, Map params) {
        return getSqlSessionTemplate().delete(statement,params);
    }

    public static Page<List<Map>> selectPage(String statement, Map params) throws Exception {
        String pageNumber = StringUtil.getParamOrDefault(params,"pageNo");
        String pageSize = StringUtil.getParamOrDefault(params,"pageSize");

        return selectPage(statement,params,pageNumber,pageSize);
    }

    public static Page<List<Map>> selectPage(String statement, Map params, String pageNo, String pageSize){
        return selectPage(statement,params,pageNo,pageSize,"");
    }

    public static Page<List<Map>> selectPage(String statement, Map params, String pageNo, String pageSize, String orderBy){
        if( pageNo == null || "".equals(pageNo)) {
            pageNo = "1";
        }
        if( pageSize == null || "".equals(pageSize)) {
            pageSize = Page.PAGE_SIZE+"";
        }
        return selectPage(statement,params, Integer.valueOf(pageNo), Integer.valueOf(pageSize),orderBy);
    }

    public static Page<List<Map>> selectPage(String statement, Map params, int  pageNo, int pageSize, String orderBy){
        PageHelper.startPage(pageNo, pageSize,orderBy);

        List<Map> rs =getSqlSessionTemplate().selectList(statement,params);
        if(rs==null){
            return Page.<List<Map>>builder().data(Lists.newArrayList()).pageCount(1).pageNum(pageNo).pageSize(pageSize).totalCount(0L).build();
        }
        PageInfo p = ((com.github.pagehelper.Page)rs).toPageInfo();
        return Page.<List<Map>>builder().data(rs).pageCount(p.getPages()).pageNum(p.getPageNum()).pageSize(p.getPageSize()).totalCount(p.getTotal()).build();
    }
}



package com.xhcj.common.dao;

import lombok.AllArgsConstructor;
import lombok.Builder;
import lombok.Data;
import lombok.NoArgsConstructor;
import lombok.extern.slf4j.Slf4j;

import java.util.List;
import java.util.Map;

/**
 *  分页实体类
 * @Package com.jyx.ps.service.mybatis.entity
 * @ClassName Page
 * @Description TODO
 * @Author JYX
 * @Date 2019/4/12
 * @Version 1.0
 * Created by JYX on 2019/4/12 16:06
 */
@Data
@Builder
@Slf4j
@AllArgsConstructor
@NoArgsConstructor
public class Page<T> {

    public static final int PAGE_SIZE=10;

    private Integer pageSize;

    private Integer pageNum;

    private Integer pageCount;

    private Long totalCount;

    private T data;

    public static Page instanceNullPage(int pageNum, int pageSize){
        return  Page.builder()
                .pageCount(1)
                .pageNum(pageNum)
                .pageSize(pageSize)
                .totalCount(0L)
                .data(null).build();
    }


    public static Page pageList(List<Map> result, int pageNum, int pageSize){
        //分页
        //计算总页数
        int pageCount=result.size()/pageSize;
        if(result.size()%pageSize > 0){
            pageCount++;
        }
        //如果小于第一页返回第一页 ，如果大于最后一页，返回最后一页
        if(pageNum<1){
            pageNum=1;
        }
        if(pageNum>pageCount){
            pageNum=pageCount;
        }
        //计算当前页码索引
        int startIndex=(pageNum-1)*pageSize;
        int endIndex=startIndex+pageSize;
        if(endIndex>result.size()){
            endIndex=result.size();
        }

        if(pageCount != 0){
            result= result.subList(startIndex,endIndex);
        }

        int pageIndex=(pageNum-1)*pageSize+1;
        for(Map record : result){
            record.put("pageIndex",pageIndex);
            pageIndex++;
        }

        return  Page.builder()
                .pageCount(pageCount)
                .pageNum(pageNum)
                .pageSize(pageSize)
                .totalCount((long)result.size())
                .data(result).build();
    }
}


package com.xhcj.common.dao;


import com.xhcj.common.SpringContextHolder;
import org.springframework.jdbc.datasource.DataSourceTransactionManager;
import org.springframework.transaction.TransactionDefinition;
import org.springframework.transaction.TransactionStatus;
import org.springframework.transaction.support.DefaultTransactionDefinition;

/**
 * @Package com.jyx.ps.util
 * @ClassName TransactionUtil
 * @Description TODO
 * @Author JYX
 * @Date 2019/4/15
 * @Version 1.0
 * Created by JYX on 2019/4/15 16:38
 */
public class TransactionUtil {

    public static DataSourceTransactionManager getTxManager(){
        DataSourceTransactionManager transactionManager = SpringContextHolder.getBean("transactionManager");
        return transactionManager;
    }

    public static TransactionStatus newTransaction(){
        DefaultTransactionDefinition def = new DefaultTransactionDefinition();
        // 事物隔离级别，开启新事务，这样会比较安全些
        def.setPropagationBehavior(TransactionDefinition.PROPAGATION_REQUIRES_NEW);
        // 获得事务状态
        TransactionStatus status = getTxManager().getTransaction(def);
        return status ;
    }

    public static void commit(TransactionStatus status) {
        if ( status != null) {
            getTxManager().commit(status);
        }

    }



    public static void rollback(TransactionStatus status) {
        if( status != null) {
            getTxManager().rollback(status);
        }

    }
}

package com.xhcj.common.exception;

import com.xhcj.common.SpringContextHolder;
import com.xhcj.common.utils.ExceptionUtil;
import com.xhcj.common.web.ComResponse;
import com.xhcj.common.web.ResponseCode;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.web.bind.annotation.ControllerAdvice;
import org.springframework.web.bind.annotation.ExceptionHandler;
import org.springframework.web.bind.annotation.ResponseBody;

/**
 * @Package com.xinhua.aseanspider.common.exception
 * @ClassName GlobalExceptionHandler
 * @Description TODO
 * @Author JYX
 * @Date 2019/8/20
 * @Version 1.0
 * Created by JYX on 2019/8/20 9:57
 */
@ControllerAdvice
public class GlobalExceptionHandler {
    private Logger logger = LoggerFactory.getLogger(GlobalExceptionHandler.class);
    @ResponseBody
    @ExceptionHandler(value = Exception.class)
    public ComResponse exceptionHandler(Exception ex) {
        logger.error("",ex);
        if(!SpringContextHolder.isProdEnvironment()){
            return ComResponse.builder()
                    .status(ResponseCode.SYSTEM_ERROR.getCode())
                    .msg(ExceptionUtil.toString(ex).replaceAll("\r\n\tat","</br>").replaceAll("\r\n","</br>"))
                    .build();
        }
        return ComResponse.error();
    }
}


package com.xhcj.common.exception;

import lombok.Getter;

/**
 * @Package com.xinhua.aseanspider.common.exception
 * @ClassName ServiceException
 * @Description TODO
 * @Author JYX
 * @Date 2019/8/20
 * @Version 1.0
 * Created by JYX on 2019/8/20 9:57
 */
@Getter
public class ServiceException extends RuntimeException {

  private String code;
  private String errorMessage;

  public ServiceException(String code) {
    this.code = code;
  }

  public ServiceException(String code, String errorMessage) {
    this.code = code;
    this.errorMessage = errorMessage;
  }
}


package com.xhcj.common.web;

import lombok.Builder;
import lombok.Data;

@Data
@Builder
public class ComResponse<T> {
    public static <T> ComResponse success(T data) {
        return ComResponse.builder()
                .status(ResponseCode.SUCCESS.getCode())
                .msg(ResponseCode.SUCCESS.getMessage())
                .data(data).build();
    }

    public static <T> ComResponse error() {
        return ComResponse.builder()
                .status(ResponseCode.SYSTEM_ERROR.getCode())
                .msg(ResponseCode.SYSTEM_ERROR.getMessage())
                .build();
    }

    public static <T> ComResponse invalid(String message) {
        return ComResponse.builder()
                .status(ResponseCode.BAD_REQUEST.getCode())
                .msg(message)
                .build();
    }

    public static <T> ComResponse invalid() {
        return invalid(ResponseCode.BAD_REQUEST.getMessage());
    }

    private Integer status;

    private String msg;

    private T data;

    public ComResponse(Integer status, String msg, T data) {
        this.status = status;
        this.msg = msg;
        this.data = data;
    }
}


package com.xhcj.common.web;

import lombok.AllArgsConstructor;
import lombok.Builder;
import lombok.Data;
import lombok.NoArgsConstructor;
import lombok.extern.slf4j.Slf4j;

import java.io.Serializable;
import java.util.List;

/**
 * @author zhb 2019-03-20
 */
@Data
@Builder
@Slf4j
@AllArgsConstructor
@NoArgsConstructor
public class Pager<T> implements Serializable {

  private Integer pageSize;

  private Integer pageNum;

  private Integer pageCount;

  private Long totalCount;

  private T data;

  public static Pager pageList(List result, int pageNum, int pageSize){
    //分页
    //计算总页数
      int pageCount = result.size()/pageSize;

      if(result.size() % pageSize > 0){
          pageCount++;
      }

      //如果小于第一页返回第一页 ，如果大于最后一页，返回最后一页
      if(pageNum  < 1){
          pageNum = 1;
      }

      if(pageNum  > pageCount){
          pageNum = pageCount;
      }

      //计算当前页码索引
      int startIndex = (pageNum-1) * pageSize;
      int endIndex = startIndex+pageSize;

      if(endIndex > result.size()){
        endIndex = result.size();
      }

      if(pageCount != 0){
        result = result.subList(startIndex,endIndex);
      }

      return  Pager.builder()
              .pageCount(pageCount)
              .pageNum(pageNum)
              .pageSize(pageSize)
              .totalCount((long)result.size())
              .data(result).build();
  }
}


package com.xhcj.common.web;

public enum ResponseCode {
    /**
     * 返回编码
     *
     */
    SUCCESS(0,"请求成功"),
    BAD_REQUEST(400,"参数错误"),
    SYSTEM_ERROR(500,"系统错误");

    ResponseCode(Integer code, String message) {
        this.code = code;
        this.message = message;
    }

    Integer code;
    String message;

    public Integer getCode() {
        return code;
    }

    public void setCode(Integer code) {
        this.code = code;
    }

    public String getMessage() {
        return message;
    }

    public void setMessage(String message) {
        this.message = message;
    }
}


package com.xhcj.common.utils;

import java.io.PrintWriter;
import java.io.StringWriter;
import java.util.Map;

/**
 * @Package com.jyx.ps.util
 * @ClassName ExceptionUtil
 * @Description TODO
 * @Author JYX
 * @Date 2019/4/12
 * @Version 1.0
 * Created by JYX on 2019/4/12 15:40
 */
public class ExceptionUtil {

    /**
     * @Method  newInstance
     * @Description  捕获下层异常时创建新异常抛出
     * @Author: JYX
     * @Param [msg, e]
     * @Return java.lang.Exception
     * Created by JYX on 2019/4/9 9:11
     */
    public static Exception newInstance(String msg, Exception e){
        Exception ex=new Exception(msg+ "\r\n"+e.getClass().toString().replace("class","").trim()+": "+e.getMessage());
        ex.setStackTrace(e.getStackTrace());

        return ex;
    }
    
    public static String toString(Exception e) {

        try {
            StringWriter sw = new StringWriter();
            PrintWriter pw = new PrintWriter(sw);
            e.printStackTrace(pw);
            return  sw.toString()  ;
        } catch (Exception e2) {
            return "get exception string fail,"+e2.getMessage();
        }
    }

    public static String toString(Map params, Exception e) {

        try {
            StringWriter sw = new StringWriter();
            PrintWriter pw = new PrintWriter(sw);
            e.printStackTrace(pw);
            return  "\nparams="+params.toString()+"\nexception="+sw.toString()  ;
        } catch (Exception e2) {
            return "get exception string fail,"+e2.getMessage();
        }
    }

    public static String toString(String params, Exception e) {

        try {
            StringWriter sw = new StringWriter();
            PrintWriter pw = new PrintWriter(sw);
            e.printStackTrace(pw);
            return  "params="+params +"exception="+sw.toString()  ;
        } catch (Exception e2) {
            return "get exception string fail,"+e2.getMessage();
        }
    }
}


package com.xhcj.common.utils;

import lombok.extern.slf4j.Slf4j;
import org.apache.http.util.Asserts;

import java.math.BigDecimal;
import java.util.*;
import java.util.regex.Matcher;
import java.util.regex.Pattern;

/**
 * @Package com.xinhua.statisticalAnalysis.common.utils
 * @ClassName StringUtil
 * @Description TODO
 * @Author JYX
 * @Date 2019/9/24
 * @Version 1.0
 * Created by JYX on 2019/9/24 14:57
 */
@Slf4j
public class StringUtil {

    private static final String CHARSET_NAME = "UTF-8";
    private static final String NULL_STR = "null";

    /**
     *
     * @param subtrahend 被减数
     * @param minuend 减数
     * @return
     */
    public static String substact(String subtrahend,String minuend){
        Asserts.check(!isEmpty(subtrahend),"subtrahend被减数不能为空");
        Asserts.check(!isEmpty(minuend),"minuend减数不能为空");

        return operate(subtrahend,minuend,"-");
    }

    /**
     *
     * @param dividend 被减数
     * @param divisor 减数
     * @return
     */
    public static String division(String dividend,String divisor){
        Asserts.check(!isEmpty(dividend),"dividend被除数不能为空");
        Asserts.check(!isEmpty(divisor),"divisor除数不能为空r");

        return operate(dividend,divisor,"/");
    }

    private static String operate(String val1,String val2,String type){
        Double val1Double = Double.parseDouble(val1);
        Double val2Double = Double.parseDouble(val2);

        BigDecimal val1BigDecimal = BigDecimal.valueOf(val1Double);
        BigDecimal val2BigDecimal = BigDecimal.valueOf(val2Double);

        String rs;
        switch (type) {
            case "+" :
                rs= val1BigDecimal.add(val2BigDecimal).doubleValue()+"";
                break;
            case "-":
                rs= val1BigDecimal.subtract(val2BigDecimal).doubleValue()+"";
                break;
            case "*":
                rs= val1BigDecimal.multiply(val2BigDecimal).doubleValue()+"";
                break;
            case "/":
                Asserts.check(val2BigDecimal.compareTo(BigDecimal.ZERO) !=0 ,"被除数不能为0");
                rs= val1BigDecimal.divide(val2BigDecimal,BigDecimal.ROUND_HALF_UP).doubleValue()+"";
                break;
            default:
                throw new RuntimeException(String.format("%s 目前不支持，目前支持【+,-,*,/】"));
        }

        return rs;
    }

    /**
     * 转换为Double类型
     */
    public static Double toDouble(Object val){
        Objects.requireNonNull(val);
        return Double.valueOf(val.toString().trim());
    }

    /**
     * 转换为Float类型
     */
    public static Float toFloat(Object val){
        return toDouble(val).floatValue();
    }


    /**
     * 转换为Long类型
     */
    public static Long toLong(Object val){
        return toDouble(val).longValue();
    }

    /**
     * 转换为Integer类型
     */
    public static Integer toInteger(Object val){
        return toLong(val).intValue();
    }


    public static byte[] getBytes(String str) throws Exception {
        Objects.requireNonNull(str);
        return str.getBytes(CHARSET_NAME);
    }

    public static String toString(byte[] bytes) throws Exception {
        Objects.requireNonNull(bytes);
        return new String(bytes, CHARSET_NAME);
    }

    /**
     *  转换为字符串
     * @param obj
     * @return String
     */
    public static String toStr(Object obj){
        if (obj == null){
            return "";
        }
        if (NULL_STR.equals(obj.toString().trim())){
            return "";
        }

        if (obj instanceof BigDecimal) {
            BigDecimal bigObj = (BigDecimal) obj;
            return bigObj.toString();
        }

        return String.valueOf(obj);
    }

    /**
     * @Method  isEmpty
     * @Description 
     * @Author: JYX
     * @Params [obj]
     * @Return boolean
     * Created by JYX on 2019/4/12 14:28
     */
    public static boolean isEmpty(Object obj) {
        if(obj == null) {
            return true;
        }else if(obj instanceof String) {
            return isEmpty((String)obj);
        }else if(obj instanceof Map) {
            return isEmpty((Map)obj);
        }else if(obj instanceof List) {
            return isEmpty((List)obj);
        }else {
            return false;
        }
    }

    /**
     * Map是否为空
     * @param map 对象
     * @return boolean
     */
    public static boolean isEmpty(Map map){
        if(map == null){
            return true;
        }
        if(map.isEmpty()){
            return true;
        }
        if(map.size() == 0){
            return true;
        }
        return false;
    }
    /**
     * 对象是否为空
     * @param obj
     * @return boolean
     */
    public static boolean isNull(Object obj){
        if(obj == null) return true;
        return false;
    }

    /**
     * 字符串是否为空
     * @param str
     * @return boolean
     */
    public static boolean isEmpty(String str){
        if(str == null){
            return true;
        }
        if("".equals(str.trim())){
            return true;
        }
        if(NULL_STR.equals(str.trim())){
            return true;
        }
        return false;
    }

    /**
     * List是否为空
     * @param array 列表
     * @return boolean
     */
    public static boolean isEmpty( List array){
        if(array == null){
            return true;
        }
        if(array.isEmpty()){
            return true;
        }
        if(array.size() == 0){
            return true;
        }
        return false;
    }

    /**
     * 校验入参是否缺少，是否为空
     * @param keys 入参名称，字符串数组
     * @param paramsMap	传入的参数
     * @return
     */
    public static String isParamsEmpty(String[] keys, Map<String, Object> paramsMap) throws Exception {
        for (String key : keys) {
            if (isNull(paramsMap.get(key))) {
                return key;
            }
            if (isEmpty(toStr(paramsMap.get(key)))) {
                return key;
            }
        }
        return null;
    }

    /**
     * 检验是否为纯数字的字符串
     * @param str
     * @return
     */
    public static final Pattern ONLY_NUM_STR_PATTERN= Pattern.compile("^([0-9]+)|((-?\\d+)(\\.\\d+)?)$");
    public static boolean onlyNumStr(String str){
        if(isEmpty(str)){
            return false;
        }
        Matcher m = ONLY_NUM_STR_PATTERN.matcher(str);
        return m.matches();
    }

    /**
     * 是否是数字
     * @param str
     * @param length
     * @return
     */
    public static boolean isNum(String str, int length){
        boolean flag  = length < 1 ;
        String module = flag ? "^([\\d])$" : "^([\\d]{"+length+"})$" ;
        Pattern p = Pattern.compile(module);
        Matcher m = p.matcher(str);
        return m.matches();
    }


    /**
     * 转换对象为字符串类型
     * @param obj
     * @return
     */
    public static String valueOf(Object obj) {
        if (obj == null) {
            return "";
        }
        if (obj instanceof String) {
            String strObj = obj.toString().trim();
            if (NULL_STR.equalsIgnoreCase(strObj)) {
                return "";
            }
            return strObj;
        }
        if ( obj instanceof BigDecimal) {
            BigDecimal bigObj = (BigDecimal)obj;
            return bigObj.toString();
        }

        return obj.toString().trim();
    }

    /**
     * 判断字符串为整数(int)
     * @param str
     * @return
     */
    public static final Pattern IS_INTEGER_PATTERN= Pattern.compile("^[-\\+]?[\\d]*$");
    public static boolean isInteger(String str) {
        if (null == str || "".equals(str)) {
            return false;
        }
        return IS_INTEGER_PATTERN.matcher(str).matches();
    }

    /**
     * 判断字符串为浮点数(double和float)
     * @param str
     * @return
     */
    public static final Pattern IS_DOUBLE_PATTERN= Pattern.compile("^[-\\+]?[.\\d]*$");
    public static boolean isDouble(String str) {
        if (null == str || "".equals(str)) {
            return false;
        }
        return IS_DOUBLE_PATTERN.matcher(str).matches();
    }

    /**
     * @Method  getParamOrDefault
     * @Description 
     * @Author: JYX
     * @Params [params, key]
     * @Return java.lang.String
     * Created by JYX on 2019/4/12 14:12
     */
    public static String getParamOrDefault(Map params, String key){
        if(key == null || "".equals(key.trim())){
            throw new NullPointerException("can't get key from map,because of key is null or \"\"");
        }
        Object val=params.get(key);
        if(val == null){
            return "";
        }else if(val instanceof String){
            return (String)val;
        }else if(val instanceof Long){
            return val.toString();
        }else if(val instanceof Double){
            return val.toString();
        }  else if(val instanceof Integer){
            return val.toString();
        }else if(val instanceof BigDecimal){
            BigDecimal bigObj = (BigDecimal)val;
            return bigObj.toString();
        }else if( val instanceof Boolean){
             return val.toString();
        }else{
            throw new ClassCastException("can't convert the key's value to String : "+key);
        }
    }

    /**
     * 移除入参中为空串的 param
     *
     * @Method  mapRemoveEmptyValue
     * @Description
     * @Author: JYX
     * @Params [paramsMap]
     * @Return java.util.Map
     * Created by JYX on 2019/4/12 14:30
     */
    public Map mapRemoveEmptyValue(Map paramsMap) throws Exception {
        Map<String, Object> newMap = new HashMap<>(16);
        newMap.putAll(paramsMap);

        for(Object key : paramsMap.keySet()){
            Object val=paramsMap.get(key);
            if(isEmpty(val)){
                newMap.remove(key);
            }
        }
        return newMap;
    }

    /**
     * 检查map中是否含有某几个字符串元素
     * @param map
     * @param args
     * @throws Exception
     */
    public static void checkMapNull(Map map, String...args) throws Exception {
        String[] inputs = args;

        List<String> newList = new ArrayList<String>();
        for (String input : inputs) {
            if (input == null || "".equals(input.trim())) {
                continue;
            }
            newList.add(input);
        }
        inputs = newList.toArray(new String[newList.size()]);

        if (inputs != null && inputs.length > 0) {
            StringBuffer checkedResult = null;
            for (String input : inputs) {
                Object value = map.get(input);
                if (value == null) {
                    if (checkedResult == null) {
                        checkedResult = new StringBuffer();
                    }
                    checkedResult.append(" [").append(input).append("] ");
                }else if(value instanceof String){
                    if("".equals(((String)value).trim())){
                        if (checkedResult == null) {
                            checkedResult = new StringBuffer();
                        }
                        checkedResult.append(" [").append(input).append("] ");
                    }
                }
            }
            if (checkedResult != null) {
                throw new NullPointerException(String.format("入参 %s 不能为空", checkedResult.toString()));
            }
        }
    }

    /**
     * 循环向map中添加key，value
     * @param strs
     * @return
     */
    public static final Integer STEP = 2;
    public static Map<String, Object> map(Object...strs){
        LinkedHashMap map = new LinkedHashMap(16);
        for(int i = 0 ; i < strs.length ; i = i + STEP){
            map.put(strs[i].toString(),strs[i+1]);
        }
        return map;
    }

    public static <T> List<T> list(T ...strs){
        List<T> list= new ArrayList();
        for(T str : strs){
            list.add(str);
        }
        return list;
    }

    public static List<Object> listObject(Object...strs){
        List<Object> list= new ArrayList();
        for(Object str : strs){
            list.add(str);
        }
        return list;
    }

    public static  String[] listToArray(List<String> list){
        if(list == null || list.size() < 1){
            return new String[0];
        }
        String[] array =new String[list.size()];
        array=list.toArray(array);
        return array;
    }


}






