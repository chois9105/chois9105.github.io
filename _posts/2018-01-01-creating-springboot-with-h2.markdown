---

layout: post
title:  "Creating spring boot project with H2 DB"
subtitle: 'If you want to create spring project with h2 db, this post help you make it.'
date:   2018-01-01
categories: spring
cover: 
tags: spring h2
---

#### Spring boot project 만들기.
spring boot로 프로젝트를 만들면 h2 db와 연결하기 매우 쉽다.  
스크린샷을 보고 spring boot 프로젝트를 만들어 보자. 화면은 intellij이지만 eclipse도 비슷하다.


#### Creating spring boot project.  
If you are creating spring boot project, It will be very easy to setting h2 db with spring boot.  
Let's follow screenshots below. that is intellij but eclipse much similar to it.

![1]({{site.url}}/assets/post/20180101/1.PNG)
![2]({{site.url}}/assets/post/20180101/2.PNG)
![3]({{site.url}}/assets/post/20180101/3.PNG)


h2 db와 관련된 dependency 추가 및 yaml에 h2관련 정보 설정.  
Adding gradle dependencies for h2 database.


```gradle
dependencies {
    ...
    runtime('com.h2database:h2')
    ...
}
```


yaml에 db정보 설정.  
Setting database properties in yaml.


```yaml
spring:
  h2:
    console:
      enabled: true
      path: /h2-console
```


![4]({{site.url}}/assets/post/20180101/4.PNG)

spring boot 프로젝트를 실행시켜 동작이 제대로 되는지 확인해보자.  
Let's run spring boot project if it does well or not.

![5]({{site.url}}/assets/post/20180101/5.PNG)
![6]({{site.url}}/assets/post/20180101/6.PNG)

이로써 spring boot 프로젝트에 h2 db를 연결하는 부분을 모두 끝냈다.  
github에 방금 구성한 설정들을 올려 놓았으니 잘 모르겠으면 프로젝트를 받아서 사용하면 된다.

Finally, you finish the project settings which is configuring spring boot with h2 db.
I push the project on my github. if you are not easy to understand it, you should get it.

[Github](//github.com/chois9105/springboot-with-h2)