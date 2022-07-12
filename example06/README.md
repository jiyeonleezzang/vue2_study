# 강좌6
## 요약
- computed와 method차이 설명



# computed vs methods
- https://negabaro.github.io/archive/vuejs-computed__watch__methods
템플릿에서 data를 직관적으로 표현하기 위해 사용 한다면 methods와의 차이는 무엇일까?

# 공통점1
data값이 변경되었을때 양쪽 다 재호출이 일어난다.

# 공통점2
데이터 변동이 없는 상태라면 양쪽 다 재호출이 일어나지 않았다.(아마도 캐쉬하는듯)

vue.js computed와 methods의 차이라는 블로그에서

데이터 변동이 없는 상태에서 computed는 이전의 계산된 값을 캐시해 두었다가 함수 호출시 다시 쓰게 된다. 반면 methods는 사용될 때마다 함수의 계산을 다시 하게 된다.

이런 문구가 있는데 필자의 테스트 결과 methods,computed양쪽 다 캐쉬하는듯하다.

# 차이1 호출방법이 틀림.
methods의 경우 함수를 의미하는 ()붙여서 호출해야한다.

testMessage()

computed의 경우 ()를 붙일 필요가 없이 기존 data와 같은 방식이다.

testMessage

# 차이2 computed에서는 인자를 넘길 수 없음
차이1에서 설명했듯이 computed는 함수형태로 호출하는 방식이 아니므로 인자를 가질 수 없다.

methods는 인자를 가질 수 있다.

# 차이3 computed에서는 반드시 return값이 있어야 한다.
template안에서 쓰는거라면 method도 return값이 있어야 하는건 마찬가지겠지만 강제성은 computed가 강한것 같다.

# 차이4 update life cycle hook발생시 template에 정의한 method들은 무조건 실행됨

 
update hook이 발생하면 template에 있는 method들은 반드시 실행된다. 헷갈리는 부분인데 method가 종속성이 높다라는 이해로 받아들이면 좋을거 같다.

update hook은 데이터가 변경되어 가상돔을 재랜더링할때 발생한다.

이렇게되면 해당 method와 관련없는 어떤 액션에 의해 method가 실행되버리므로 의도치 않는 버그가 발생할 가능성이 있다.

그래서 특별한 이유가 없는 한 computed를 사용하는것을 권장한다.(인자를 반드시 넘겨주고 싶다거나 하는 이유)