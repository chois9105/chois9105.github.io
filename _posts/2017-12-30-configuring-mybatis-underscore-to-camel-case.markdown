---

layout: post
title:  "configuring mybatis-underscore to camel case"
subtitle: 'This is a post description for setting up Mybatis. After reading this post, you are able to configure to return map object as a camel case on mybatis.'
date:   2017-12-31
categories: spring
cover: 
tags: spring mybatis underscore camelcase
---

### mybatis에서 map으로 return 받을 때 Camel Case로 사용해보자. 
Spring boot 혹은 Spring MVC 환경에서 Mybatis와 연동할 경우 xml 파일 안에 result type을 Map으로 받는경우가 많다.
DB 컬럼명이 myName, myPassword, emailAddress 처럼 되어있는 경우 상관이 없지만 my_name, my_password, email_address 같은 경우에 내가 사용하기 편한 카멜케이스로 이용할수 있는 방법이 없는지 해서 찾아보았다.


### Using map object from underscore to camel-case when returning on mybatis
There are a lot of cases to receive map type object on spring framework with mybatis.
If column names in a database are myName, myPassword and emaillAdress, It will be very simple. But sometimes, it was made underscore. Even though, I want to use camel case not underscore. So I was found out the way to convert underscroe to camel case on mybatis.

#### VO를 이용하는 경우 매우 간단하다. 
mybatis 설정파일에 값을 추가해보자.  

#### If you are using VO, It's very simple
You have to define it on your mybatis-configure file.

* xml파일 이용 (Using XML file).

```xml 
<settings>
	<setting name="mapUnderscoreToCamelCase" value="false"/>
</settings>
```


* properties 파일 이용 (Using properties file).

```properties
mybatis.configuration.map-underscore-to-camel-case=true
```

* yaml 파일 이용 (Using YAML file).

```yaml
mybatis:
    configuration:
        map-underscore-to-camel-case: true
```


#### Map을 이용해서 return 받는 경우
현재 Mybatis 측에서 공식적으로 지원하지 않는다고 알고 있어서 나의 경우 return 받는 객체 에서 처리했다.  

#### Using map object while returning values.
I assumed it is not support on mybatis officially. So in my case, I managed a java class while binding data.

* Map을 상속받는 클래스 만들기(CamelListMap).
예제에서는 ListOrderedMap을 상속 받았다.  
Making a java class extends Map. It extends ListOrderedMap in my example.

```java

    import org.apache.commons.collections4.map.ListOrderedMap;

    public class CamelListMap extends ListOrderedMap {

    private String toProperCase(String s, boolean isCapital) {

        String rtnValue = "";

        if(isCapital){
            rtnValue = s.substring(0, 1).toUpperCase() +
                    s.substring(1).toLowerCase();
        }else{
            rtnValue = s.toLowerCase();
        }
        return rtnValue;
    }

    private String toCamelCase(String s){
        String[] parts = s.split("_");
        StringBuilder camelCaseString = new StringBuilder();

        for (int i = 0; i < parts.length ; i++) {
            String part = parts[i];
            camelCaseString.append(toProperCase(part, (i != 0 ? true : false))) ;
        }

        return camelCaseString.toString();
    }

    @Override
    public Object put(Object key, Object value) {
        return super.put(toCamelCase((String)key), value.toString());

    }

}

```

* xml에 resultType을 방금 만든 객체로 지정  
Adding a result type to java class on mapper xml

```xml

<select id="sampleList" parameterType="java.util.Map" resultType="CamelListMap">
    SELECT       
          *  
    FROM USER
</select>

```


* 제대로 작동이 되는지 확인.  
Check if it is pass or not.

```java
CamelListMap map = sampleMapper.sampleList(paramsMap);

for (Object key : map.keyList()){
    System.out.println(key);
}
```

![테스트결과(test result)]({{site.url}}/assets/post/camelcase.PNG)

