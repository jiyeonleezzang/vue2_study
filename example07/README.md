# 강좌7
## 요약
- watch 속성 구현


# computed vs watch
https://negabaro.github.io/archive/vuejs-computed__watch__methods
변경이 일어날때 무언가를 실행한다라는 의미로는 watch와도 비교된다.

watch와의 공통점과 차이점에 대해 알아보자.

# 공통점
둘다 옵저버 패턴으로 동작한다.

값이 변하면 무언가 실행된다.

# 차이1 template 기술부분
computed는 template에 기술함

watch 메소드는 template에 기술하는 개념이 없음

# 차이2 캐싱
computed는 캐싱의 개념이 있다.

message = "test"상태에서

this.message = "test"하면 값의 변경이 없으므로 computed안의 메소드를 실행하지 않고 캐싱된 값을 리턴해준다.

# 차이3 computed는 return이 필수이다.
computed는 return이 필수이다.

watch는 return이 있어도 동작안할거 같은데?(테스트는 안해봄)

# 차이4 역할이 다름
computed는 변경이 있고, 그 변경으로 인한 결과가 필요할 때 사용( property라는 느낌이 강함)

watch는 트리거의 역할로 사용된다.(값의 변경이 있고 그 변경의 결과에 따라 다른 메소드 등을 호출할 때 사용)

computed의 사용예
data의 값을 대문자로 보여주고 싶을때

a data와 b data를 결합해서 보여주고 싶을때

# watch의 사용예
특정 값이 변경되었을때 axios같은 비동기 통신이나 복잡한 처리를 넣고 싶을때 주로사용

다른 data의 값을 변경할때(this.xx = 'yy',push)