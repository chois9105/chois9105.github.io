---

layout: post
title:  "Setting up mybatis-generator on intellij."
subtitle: 'This is for web developer who want to know how to set mybatis generator'
date:   2018-01-03
categories: spring
tags: mybatis generator intellij
---

# intellij에서 mybatis generator 사용하기

mybatis gereator란 이름에서 알수있듯이 DTO, Mapper class, Mapper xml 등 mybatis를 사용하면서 꼭 만들어야 되는 파일들을 쉽게 생성하게 도와주는 플러그인 이다. 뿐만 아니라 간단한 CRUD 예제까지 만들어낸다.
일단 제일 먼저 플러그인을 설치해 보자. 여기서는 스프링 부트에 maven을 이용해서 plugin을 추가했다.

# Using mybatis generator in intellij

As the name implie, i'm sure you will understand what it is.  
It is plugin for generating boilerplate code like DTO, Mapper Class, Mapper xml easily. Besides it makes exmples using CRUD operations.  
First of all, let's add a plugin. In my case, I used maven with spring boot.

```xml
<build>
...  
<plugin>  
    <groupId>org.mybatis.generator</groupId>  
    <artifactId>mybatis-generator-maven-plugin</artifactId>  
    <version>1.3.6</version>  
    <configuration>  
	<verbose>true</verbose>  
	<overwrite>true</overwrite>  
    </configuration>  
</plugin>  
...  
</build>
```

pom.xml에 플러그인을 추가한 후 메이븐에 새로운 플러그인이 나오는지 확인해야된다.
만약 이 화면이 안 나온다면 View -> Tool Windows -> Maven proejcts를 선택한다.

You have to make sure maven plugin was added on the maven projects view after adding plugin on pom.xml.  
If you don't know how to open a view, you should follow it.

![Maven View]({{site.url}}/assets/post/20180103/mavenview.png)

이제 src/main/resources 폴더 안에 generatorConfig.xml 파일을 만들고 아래 내용을 복사한다.

You have to make generatorConfig.xml file in src/main/resources folder and wrtie it below.

```xml

<!DOCTYPE generatorConfiguration PUBLIC
        "-//mybatis.org//DTD MyBatis Generator Configuration 1.0//EN"
        "http://mybatis.org/dtd/mybatis-generator-config_1_0.dtd"
        >
<generatorConfiguration>

    <classPathEntry location="C:\Users\<USER_NAME>\.m2\repository\mysql\mysql-connector-java\5.1.6\mysql-connector-java-5.1.6.jar" />
    
    <context id="db1">

        <commentGenerator>
            <property name="suppressAllComments" value="true" />
            <property name="suppressDate" value="true" />
        </commentGenerator>

        <jdbcConnection driverClass="com.mysql.jdbc.Driver"
                        connectionURL="jdbc:mysql://<DB_IP>:<DB_PORT>/<DB_NAME>?useUnicode=true&amp;characterEncoding=utf8&amp;verifyServerCertificate=false&amp;useSSL=true"
                        userId="<DB_ID>"
                        password="<DB_PW>">
        </jdbcConnection>


        <javaTypeResolver >
            <property name="forceBigDecimals" value="false" />
        </javaTypeResolver>

        <javaModelGenerator targetPackage="com.test.boot.domain" targetProject="src/main/java">
            <property name="enableSubPackages" value="true" />
            <property name="trimStrings" value="true" />
        </javaModelGenerator>

        <sqlMapGenerator targetPackage="mappers" targetProject="src/main/resources">
            <property name="enableSubPackages" value="true" />
        </sqlMapGenerator>

        <javaClientGenerator type="XMLMAPPER" targetPackage="com.test.boot.mapper"  targetProject="src/main/java">
            <property name="enableSubPackages" value="false" />
        </javaClientGenerator>

        <table tableName="<TABLE_NAME>" domainObjectName="<OBJECT_NAME>"  />

    </context>
</generatorConfiguration>
```

1. classPathEntry  
2. DB connection info (DB_IP, DB_PORT, DB_NAME, DB_ID, DB_PW)  
3. Table info (TABLE_NAME, OBJECT_NAME)  

xml파일에 위 정보를 확인한 후 mybatis-generator:generator를 실행해 보자.  
지정한 위치에 각각 mapper와 domain이 생긴걸 확인할 수 있다. 만약 mysql을 사용하는게 아니라면 자신의 DB에 맞는 설정값을 넣어줘야 된다.

After make sure information above on xml, you have to run maven using: Mybatis-generator:generator.  
You can see making classes at the target locations. If you are not using mysql, you must change properties for your DB.

자세한 내용은 [공식 문서](http://www.mybatis.org/generator/index.html)를 확인하자.

See the [official document](http://www.mybatis.org/generator/index.html) for details.
