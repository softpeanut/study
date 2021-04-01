# 챕터5 연관 관계 매핑

> 페러다임 불일치를 설명할 때 말했듯이, 객체와 테이블은 연관 관계의 매핑을 할 때 다른 점이 있다.
>
> 이번 챕터는 객체의 참조와 테이블의 외래 키를 매핑하는 것이 목적이다.

### 단방향 연관관계

테이블의 구조

- 회원과 팀 테이블이 있다.

- 회원은 하나의 팀에만 속할 수 있다.

- 하나의 팀에는 여러 회원들이 올 수 있다.

  > 일대다 관계

![mapping_basic](.\images\mapping_basic.png)

- 객체 연관관계

  회원 객체는 Member의 team 필드로 팀 객체와 관계를 갖는다.

  회원 객체와 팀 객체는 **단방향 관계**다.

  즉, Member가 있으면 Team을 알 수 있지만 Team이 있다고 해서 Member를 알 수 없다.

- 테이블 연관관계

  회원 테이블은 MEMBER의 TEAM_ID를 통해 관계를 갖는다.

  회원 테이블과 팀 테이블은 **양방향 관계**이다.

  > 테이블은 기본적으로 양방향 관계를 갖는다.

  즉, TEAM_ID가 있으면 MEMBER들과 TEAM 모두 찾을 수 있다.

이러한 차이로 인해서 우리는 **객체를 양방향 관계로 만들어 준다.**