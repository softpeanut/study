# QueryDsl

### JPQL이란?

JPQL이란, jpa에서 자동으로 만들어주는 SQL을 말한다.

JPQL은 테이블에 대해 알지 못하며, 오직 객체와 객체간의 관계를 통해 쿼리를 만든다.

JPQL은 엔티티 객체를 대상으로 쿼리를 작성한다.

> SQL은 테이블을 대상으로 쿼리를 작성한다.

jpa에서 @Query 어노테이션을 붙이면 JPQL을 직접 작성할 수 있다.

> nativeQuery=true인 경우에는 그냥 SQL문 이다.

### JPQL의 문제점

1. JPQL은 그저 문자열일 뿐이기 때문에, Type을 체크해줄 수 없다.
2. 또한, 실제 실행 전에는 쿼리에 문제가 있는지 확인이 불가능 하다.

### QueryDsl이란?

QueryDsl이란 SQL, JPQL 문을 코드로 작성할 수 있게 도와주는 오픈소스 라이브러리 이다.

- QueryDsl의 장점

  1. JPQL을 문자열이 아닌 코드로 작성할 수 있다.

  2. JPQL을 실행하기 전에, 즉 컴파일 중에 오류를 발견할 수 있다.

  3. 자동완성이 간편하다(IDE)

  4. 단순하다. 실제 JPQL과 매우 유사하다.

  5. 동적 쿼리를 작성할 수 있다.

     > 쿼리 안의 값이 변화하는 쿼리

- QueryDsl의 단점
  
  1. 세팅이 힘들다.

QueryDsl은 JPA에서 하기 힘든 복잡한 쿼리를 간편하게 만들 수 있기 때문에, 큰 단위의 프로젝트에서 주로 복잡한 쿼리를 만드는데 사용된다.

또한, QueryDsl은 쿼리 내부에 메소드 또한 올 수 있기 때문에 코드를 재사용할 수 있다.