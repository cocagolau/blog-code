# 2018년 상반기 회고

[2017년 회고](https://brunch.co.kr/@jojoldu/19)에서 얘기했었지만, 이제부터는 1년 단위가 아닌 분기 혹은 반기 단위로 회고를 남길 계획이다.  
원래는 분기 단위로 하려고 했었지만, [3월에 개인 사정](https://brunch.co.kr/@jojoldu/27)으로 1분기가 그냥 지나가버리고 4월부터는 신규 프로젝트로 바빠서 어쩔수 없이 상반기로 회고를 하게 됐다.  
  
상반기인데 7월도 아니고 웬 8월에 상반기 회고냐 라고 생각할수도 있다.  
회사 프로젝트가 **7월 말에 최종 오픈하고 8월 초에는 오픈 안정화**를 하다보니 늦어지게 됐다.  
그래도 프로젝트가 잘 끝나서 기분 좋게 회고를 쓴다.

## 회사

회사의 일은 2개로 분리할 수 있을것 같다.

### 1 ~ 2 월 - 정산 시스템 운영

기억이 가물가물해서 Jira 티켓을 보니 1월까지는 신규 SAP 연동 시스템 연동작업을 계속 했었다.  
2017년에 정산 파트의 연동이 있었고, 1월에는 포인트, 세금계산서 등등 정산 외 다른 서비스들의 연동을 진행했었다.  
기존에 정산 연동을 진행할 때부터 플랫폼 형식으로 연동 시스템을 구축했기 때문에 추가로 연동하는 것에 크게 문제가 될 건 없었다.  
  
다만 이 플랫폼 형식이라는게 중요한데, **어설픈 프레임워크 형태로 만드는건 안하니만 못하다**는 생각을 하게 됐다.  
너무 추상화시키고, 재사용성을 강조하다보니 **내가 열어놓은 부분 외에는 추가하기가 정말 어려웠다**.    
잘못된 추상화가 얼마나 부담스러운지 직접 경험하게 되었다.  
  
2월은 대부분이 검증 로직과 자동화 작업, 운영 업무였다.  
엑셀로 검증하던 작업을 플랫폼 내에서 해결한다던지, 각 서비스에서 넘어오는 매출 데이터들에 대한 사전 검증 로직을 좀 더 촘촘하게 추가하는 등의 일을 진행했었다.  
  
어느 회사에서나 하는 운영업무와 개선 작업을 했다고 생각한다.  
이 기간에 확실히 깨닫게 된 것은 **Jenkins + Spring Batch 조합은 환상적**이란 것이다.  
모든걸 Spring MVC + Tomcat (Spring Boot Web) 으로만 해결하려고 했던 나에게 아주 좋은 시간이였다.

### 4 ~ 7월 - 신규 포인트 시스템 구축

기존 포인트 시스템이 회사 초창기에 만들어져 있었다.  
너무 오래된 시스템이다보니 더이상 확장은 어렵고 유지보수하기는 더더욱 어려운 상황에 도달했다.  
뭐 어디든 레거시 시스템이란게 다 이런 형태일꺼라 아마 많은 분들이 이해 하실것 같다.  
  
기존에는 다른 팀이 대신 운영해주었지만, 이제는 더 그럴수 없어 우리 팀이 포인트 시스템을 가져가야하는 시기가 되었고 팀장님은 개편을 결정하셨다.  
  
팀에서 운영하던 결제 시스템과 정산 시스템은 정책상 클라우드 서비스를 못쓰지만 포인트의 경우 클라우드 서비스가 가능하기에 팀에서도 확장성을 고려해서 AWS로 구축을 결정하게 됐다.  
근데 나는 **AWS를 운영 서비스에 써본적이 없었다**.  
물론 그전부터 회사 인프라가 모두 AWS 기반으로 구동되고 있었기에 AWS를 해야한다는 생각이 있었고, 토이 프로젝트로 이것저것 만들어보면서 사용중이였다.  
하지만 **토이는 토이다**.  
대규모 트래픽 맞아보고 네트워크 튀는거 경험하고 제한적 상황에서 구현 하는등 그런 경험이 없다면 경험했다고 할 수는 없다고 생각했다.  
그래서 3월에 쉬면서 본격적으로 AWS 공부를 시작했다.  
덤으로 신규 포인트 도메인을 **나라면 어떻게 구축할까 고민하고** [구현](https://github.com/jojoldu/point)해봤다.  
  
> 근데 실제로 이 도메인, 코드대로는 안갔다.  
회사와서 팀 분들과 논의하고 회사 포인트 도메인을 까보니 고민했던대로는 도저히 안되겠더라.  
그래도 훨씬 더 좋은 아키텍처와 도메인 구조로 가게 됐다.

3월에 이것저것 실컷해보고 4월에 설레는 마음으로 복직했다.  
포인트 시스템 개편 일정이 4월 중순에 시작해서 7월에 오픈하고 인원은 개발자 3명이라고 한다.  
이게 **3명이서 3개월만에 가능한건가** 라고 잠깐 생각을 했었다.  
근데 팀 전체 인원이 6명 (팀장님 빼면 5명)이고 결제, 정산 시스템 운영도 해야하고, 한 분은 출산 휴가도 가셔야 했기 때문에 인원을 더 늘릴수는 없긴 했다.  

> 와 근데 하반기는 더 큰 산이 있을줄이야.. 이건 하반기 회고때...  
  
팀장님의 강력한 믿음(?)으로 열심히 달리고 **일정에 맞춰 오픈**했다.  
순탄하지는 않았다.  
정산쪽에 갑자기 이슈가 많아 그 대응으로 5월에 많은 시간을 보내고, 프로젝트 **오픈 한달전 팀장님과 메인 기획자분이 바뀌기도 했다**.  

> 뭔가 문제가 있어 변경된건 아니고 더 중요한 일이 있어서 변경된 것이니 오해는 금물!
  
팀장님들도 인수인계만으로도 정신이 없으셔서 성능 테스트와 QA, 정책 결정 등은 우리 꼬꼬마 주니어들끼리 진행했다.  
  
그래서 엄청 걱정했다.  
아 진짜 이렇게 하면 오픈되는게 맞나 싶기도 하고, 한달만 더있었으면 좋겠다는 생각도 많이 했었다.  

그래도 일정에 차질 없이, 큰 오류나 버그 없이 잘 오픈 되었고 현재까지 안정적으로 운영중이다.  
  
어찌됐든 A부터 Z까지 다 구축한 경험을 얻었다.  


시스템 전환 노하우도 많이 얻게 되었다.  
이번 신규 포인트 시스템은 오픈하면서 **서비스 다운 없이** 진행했다.  
즉, 서비스가 운영되는 와중에 포인트 시스템이 전면 교체된 것이다.   
(서버, DB, 테이블 구조, 프로젝트 코드 전체가 다)  
  
사용자들은 아마 포인트 시스템 교체 작업이 있었는지 전혀 체감하지 못했을것이다.  
**포인트 적립도, 취소도 전부 돌아가고 있는 상태에서 교체**했으니깐.  
(포인트 사용은 잠깐 막았다.)  
  
이걸 위해서 **서비스 오픈을 3단계로 나눠서 3번 진행**했었다.  
기존 도메인을 도저히 그대로 쓸 수 없던 형태였기 때문에 도메인도 완전히 개편되었고, 이때문에 테이블 역시 새로 구조를 잡았다.  
**도메인 구조까지 완전히 전환되는 개편에서 어떻게 안정적으로 오픈하면 되는지**에 대해서 제대로 익힐 수 있었다.  
  
위 얘기와 별개로 개인적인 소감이지만, 이 프로젝트로 **팀의 파워가 올라갔다**고 생각한다.  
우리팀은 팀 조합이 정말 좋다.  
인프라, 도메인 지식, 어플리케이션 구현 등등 각자 자신의 전문 분야가 확실하고 부족한 부분을 서로가 잘 메꿔주고 있다.  
이건 장점이면서도 확실한 단점인데, **한 사람이 빠지면 구멍이 굉장히 크다**.  
  
가령 우리팀에는 인프라를 정말 잘하시는 분이 계신다.  
그리고 우리 팀은 **사내에서 유일하게 AWS를 쓰지 않고 국내 IDC를 쓰고 서버/DB를 직접 다 관리**하고 있다.  
(이젠 포인트 시스템 때문에 AWS도 쓰고 있는 팀이 됐다.)  
  
관리하는 서버 대수만 수십대이고 (개발/QA 서버 빼고), DB 백업이나 my.cnf 튜닝, 파티션까지 다 직접하고 있었고, 그걸 **그 분 혼자서 다하고 있었다**.  
  
그러다보니 만약 이번 포인트 시스템도 그 분이 인프라를 구축하게 되면 **그 분은 우리팀의 SPOF** (Single point of failure)이 된다.  
  
팀의 입장에서 봤을때 너무 위험한 구조였다.  
그래서 일부러 이번 개편때는 그 분이 **인프라를 못하게 했다**.  
그리고 어플리케이션 구현 위주로 담당하셨다.  
개편을 진행하던 3명이서 **서로 잘하는 분야 절반, 가장 못하는 분야 절반씩을 맡아서 진행**했다. 

> 자신 없는 분야를 100% 맡아 공부하면서 진행하기엔 일정상 무리였다.  
 
같이 진행했던 다른 한분은 **수억건이 넘는 레거시 데이터를 새로운 도메인 모델로 마이그레이션**을 진행해주셨다.  
마찬가지로 **마이그레이션을 위한 인프라 환경 구축과 프로젝트 구성도 그 분이 직접 다** 하셨다.  

> 레거시를 개편해보신 분들은 아시겠지만, **시스템 개편의 성공과 실패는 마이그레이션이 좌지우지**한다.  
예전 데이터를 신규 모델로 마이그레이션 못하면 서비스는 오픈 하지 못한다.  
특히 포인트 같은 경우엔 과거의 데이터가 다 마이그레이션 되야만 했다.  
**2011년 부터 쌓인 모든 데이터를 신규 모델로 완전히 마이그레이션**했다.  
테이블 형태는 그대로 두고 데이터만 복사하는 마이그레이션이 아니다보니 3개월 안에 혼자서 마이그레이션이 가능할까 걱정이 됐다.  
**틀어진 수억건의 데이터를 어떻게든 맞춰서 기간내에 마이그레이션이 끝났기 때문에** 오픈할 수 있었다.

그리고 나는 신규 시스템의 AWS 인프라와 배포환경, 완전히 개편된 신규 도메인 모델의 API 구현과 프로젝트 전체 구조를 잡았다.  


성능 테스트, RDS 페일오버 테스트, 각종 타임아웃 테스트도 직접 진행했다.  


> 3번째 회사까지 오면서 느낀거지만 팀에는 항상 SPOF가 존재한다.  
인프라, 도메인 지식이 특히나 심한데 어플리케이션 구현은 팀의 모든 사람이 하지만, 인프라와 도메인 지식은 특정인들만 다루는 경우가 많다.  
이러면 진짜 위기감을 느끼고 그 일들을 분배시킬 수 있어야 한다.  
도메인 지식에 대해서 과소평가하는 경향이 있는데, 도메인/정책을 모를때 특정인에게 계속 물어보고 있다면 어서 빨리 본인이 도메인 지식을 쌓을려고 노력해야만 한다.  
인프라도 마찬가지.


이게 진짜 이벤트 소싱인지는 모르겠다.  
사실 이벤트 소싱으로 문제를 해결했다 라는 식의 이야기를 하고 싶지는 않다.  
뭔가 거창한게 싫다.  
발표나 글을 볼때 
내가 여기서 이벤트 소싱이란 단어를 쓰게 되면 진짜 그런 사람들이 되는 것 같아서 싫다.

주문하면 무조건 포인트가 적립되기 때문에 


  
그냥 모든 테이블은 수정/삭제가 없다.  
라고만 이야기 하고 싶다.  

## 블로그

2018년 1월 ~ 7월까지 총 72개의 글을 썼다.  
월 평균 10개의 글을 쓴 셈이다.  
  
평균 작성수가 많아진 이유는 아무래도 시리즈물이 많아서 그런것 같다.

* [스프링부트로 웹 서비스 출시하기](http://jojoldu.tistory.com/250) (10부작) 
* [3번째 직장에 오기까지](http://jojoldu.tistory.com/277) (6부작)
* [AWS Code Deploy로 Jenkins & Spring Batch 배포 및 운영하기](http://jojoldu.tistory.com/313) (3부작)
* [텔레그램 & AWS 서비스 연동하기](http://jojoldu.tistory.com/304) (3부작)
* [Jenkins로 Gradle Multi Module 프로젝트 AWS Beanstalk에 배포하기](http://jojoldu.tistory.com/290) (3부작)
* [AWS Beanstalk으로 진행하는 성능 튜닝 시리즈](http://jojoldu.tistory.com/318) (4부작)

아마 올 한해가 끝날때 쯤엔 100개 이상 될 것 같다.  
블로그에 글 쓰는건 여전히 즐겁기 때문에 계속 할 수 있을것 같다.  
  
하지만 브런치에 대해서는 다시 생각중이다.  
다른 것보다 블로그에 글 쓰는 것보다 **브런치에 글 쓰는 것이 어떤 이득이 있는지** 느끼지 못하고 있다.  
브런치가 티스토리보다 좋은 건 분명 몇가지 있다.

* 웹 에디터는 확실히 브런치가 좋다.
* 전용 모바일 앱이 있다.
* 별다른 디자인 없이도 UX가 이쁘게 나온다.
  
하지만 나는 글을 **VSCode와 마크다운으로 작성하다보니 브런치가 더 불편**하다.  
웹 에디터는 단순 텍스트 외에 다른 효과를 주려면 마우스에 손이 갈 수 밖에 없는데, 마크다운은 그럴 필요 없이 키보드로 쭉 치면 되서 사실 브런치 에디터가 훨씬 더 불편하다.  
  
VSCode와 마크다운으로 글 쓰는게 너무 편리하다.  
이건 그 어떤 웹 에디터에서도 못따라갈 것 같다.  
미디움이나 스팀잇, 네이버 블로그등과 같은 대세 플랫폼을 안쓰는 이유도 이것 때문이다.  
더군다나 단축키를 IntelliJ Key Mapping으로 맞춰서 쓰니 **기존에 사용하던 단축키 그대로 사용할 수 있는데** 굳이 웹 에디터를 쓰고 싶지 없다.  

> 브런치에서 티스토리처럼 오픈 API를 제공한다면 고민해볼것 같다.
  
물론 브런치로 책을 낼 수 있다는 장점도 있다.  
하지만 그 조건이 굉장히 까다롭다.  
개발자로서 브런치라는 플랫폼은 티스토리에 비해 크게 메리트가 없다고 느껴진다.  
굳이 익숙한 개발툴과 단축키로 글을 쓸 수 있는 상황에서 브런치를 쓸 이유는 없을것 같다.  
8월이면 티스토리에도 https가 지원되서 더 잘 사용할 것 같다.  

> 뭐 이런 대규모 개편이 한번에 될리 없어서 바로 될지는 모르겠지만..

## 교육

올 상반기에는 하나의 교육을 수강했다.

* [패스트캠퍼스 운영 서버 관리 마스터 워크샵](https://www.fastcampus.co.kr/dev_workshop_opsfse/)

과정은 워크샵이란 타이틀에 맞게 AWS 배포/모니터링 등에 대한 초보자들을 위한 내용이였다.  
하지만 **내가 AWS 초보자였기 때문에 더할나위 없이 좋은 강의**였다.  


## 오픈소스

올해 상반기에는 1개의 오픈소스를 만들었다.  

* [Spring Boot AWS Mock](https://github.com/jojoldu/spring-boot-aws-mock)

AWS의 메세징 큐 서비스인 SQS와 동일한 인터페이스를 가진 [ElasticMQ](https://github.com/adamw/elasticmq)를 Spring Boot에서 임베디드로 사용할 수 있게 랩핑한 라이브러리이다.  
즉, 의존성만 추가하면 H2 사용하듯이 SQS를 사용할 수 있게 해준다.  
  
아직 부족한건 많다.  

> Mock SQS의 종료 라이프 사이클을 리스너보다 후 순위로 둬야하는 등 고칠점이 많다.

그럼에도 이 오픈소스 자랑을 조금 하고 싶다.  
이번 포인트 시스템은 AWS 서비스를 굉장히 하드하게 쓴다.  

SQS는 이번 포인트 시스템의 핵심 서비스이다.  

* DB가 죽어도 포인트 서비스는 유지되어야 한다
* 누락되는 건 없이 언젠가는 요청이 처리된다

라는 2가지 전제조건을 처리하기 위해서 메세지 큐 서비스가 필수였고, 우린 AWS SQS를 선택했다.  
그러다보니 **모든 기능은 SQS를 기반으로 구성**해야만 했다.  
하지만 **격리된 환경에서 사용할 Mock 제품이 없었다**  
다른 서비스는 대체품이 존재했다.

* RDS : H2
* Elastic Cache Redis : [Embedded Redis](https://github.com/ozimov/embedded-redis)

헌데 SQS는 특별히 사용중인게 없었다.  

> 개발용 AWS를 사용해선 안된다.  
공용 저장소를 사용하는 순간 **서로가 서로의 테스트를 침범하게 되어 격리된 테스트 환경 구축을 못하게 된다**.
(Jenkins에서 테스트 하면 로컬 테스트가 깨지는 등등)  

그래서 이런 Mock 제품이 필요하다고 생각을 했고, [ElasticMQ](https://github.com/adamw/elasticmq)가 SQS와 동일한 인터페이스를 제공한다는걸 발견하게 되서 랩핑하였다.  

 **개발하면서 한번도 로컬에서 실행해본적이 없다**.  
  
**모든걸 다 테스트 코드로만 실행하고 검증**했다.  
브라우저로 테스트하는 것은 개발서버에 배포한 뒤에나 했다.  
근데 아무런 문제가 없었다.  
Spring Boot AWS Mock 을 기준으로 구현한 모든 코드들과 테스트 코드들이 AWS 위에서도 의도한대로 잘 작동되었다.  
그래서 좋았다.  

이제는 AWS SQS도 테스트 코드를 작성할 수 있게 되었다.
Jenkins에서, 개발자 개개인의 로컬 PC에서 각자 격리된 환경에서 SQS 관련 테스트 코드를 수행할 수 있게 되었다.  
  
개인적인 가치관이지만, **좋은 프로젝트는 git에서 클론 받으면 바로 로컬에서 실행될 수 있어야 한다**고 생각한다.  
git clone 받은 뒤에 이것도 해야하고 저것도 해야하는 등등의 추가 적인 환경 세팅이 필요하면 그것 역시 비용이라고 생각한다.  

## 발표 및 강의

상반기에 생애 처음으로 개발자 커뮤니티에서 발표를 진행 했다.

* [(2월) KCD 2018 - IntelliJ IDEA만으로 개발하기](https://www.youtube.com/watch?v=wBXSUdT1jX0&t=2121s)
* [(4월) 우아한형제들 테크캠프 밋업](https://gmlwjd9405.github.io/2018/04/27/woowabros-tech-meetup.html)
* [(7월) 인프런 - IntelliJ IDEA 가이드](https://www.inflearn.com/course/intellij-guide/)



## 하반기에는?

일단 2가지 교육을 신청했다.

* 패스트캠퍼스의 [DevOps로 활용하는 클라우드 플랫폼 Workshop](https://www.fastcampus.co.kr/data_camp_cpb/)
* 사내 Java 교육

다양한 언어를 다루는 사람이 되고 싶은 마음은 전혀 없다.  
서비스를 구현하는 언어와 프레임워크는 최대한 1 ~ 2개로 좁혀서 진행하는게 좋다고 생각한다.  
백엔드의 전반적인 기본기를 잘 쌓고 싶다.  
네트워크, 리눅스, RDBMS, 메세징 서비스, DDD, 테스트 코드, 코드/시스템 디자인 등을 더 잘하고 싶다.  
이 중에서 특출나게 잘하는게 없을수도 있지만, 그래도 두루두루 기본은 했으면 좋겠다.  
풀스택 개발자, DevOps 엔지니어와 같은 그런 거창한 단어를 붙이고 싶은게 아니다.  
그냥 백엔드 개발자로서 **어떤 문제가 발생하면 Java 코드만 쳐다보는 개발자가 되고 싶지 않을뿐**이다.  
진짜 탄탄한 개발자가 되고 싶다.  


그리고 개인적으로 부채로 생각만 하고 있는 영어 공부를 시작하려고 한다.  
[조은님의 패스트원 후기](https://blog.naver.com/apes0113/221327173912)를 보고 진짜 시작해야겠다고 생각했다.  
막연하게 영어 공부를 해야겠다고만 생각하면 진행이 잘 안되어서 배운 영어로 단기간에 해낼 수 있는 목표를 세웠다.  
이건 달성하게 되면 그때 공개할 예정이다.  
(안하면 부끄러우니깐)  
느낌은 달성할 수 있을것 같아서 목표 자체는 잘 세운것 같다.  
  
당장은 시작 못한다.  
회사의 중요한 프로젝트에 합류하게 되어 10월까지는 굉장히 바쁠것 같다.  
10월까지는 잘 참아봐야겠다.  
  


