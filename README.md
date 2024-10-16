# java-calculator-precourse

## 구현할 기능 목록

- [x] 입력받은 문자열 `계산식` 객체 만들기
- [ ] 문자열을 입력받기
- [x] 입력받은 `계산식`이 정상적인 형태가 아니면 예외 발생하기
- [x] 입력받은 `계산식`에 커스텀 구분자가 있으면 분리하기
- [x] 입력받은 `계산식`에서 모든 구분자로 숫자 부분을 분리하기
- [ ] `계산식`의 숫자 부분을 덧셈 연산하기
- [ ] 더한 결과를 출력하기


## 주의사항
잊기 쉬운 제한사항과 얼핏 헷갈리지만 문서에 명확한 근거가 있어 해결되는 점을 기록한다.  
```markdown
- (주의할 내용)
    - (근거가 되는 문구)
```
의 형태로 기록한다.  

- 콘솔 입력은 반드시 주어진 라이브러리를 사용한다
  - 사용자가 입력하는 값은`camp.nextstep.edu.missionutils.Console`을 활용한다.
- 음수는 예외처리 해야 한다.
  - 구분자와 *양수*로 구성된 문자열
- 커스텀 구분자에 기본 구분자를 입력해도 동작해야 한다.
  - 따로 표현되어 있지 않으나, 기본 구분자의 커스텀 구분자 입력에 대한 제한 사항이 없음.
- 커스텀 '문자'는 하나다.
  - 커스텀 구분자는 문자열 앞부분의 "//"와 "\n" 사이에 위치하는 *문자*를 커스텀 구분자로 사용한다.
  - 문서에서 문자열과 문자를 구분하여 표현하고 있으므로, 위의 경우 하나의 문자로 해석함.

## 애매한 동작에 대한 정의
동작의 근거가 명확히 정의되지 않은 문제에 대해, 어떻게 동작할 지 소신껏 규칙을 정하여 기록한다.  
```markdown
- (문제가 되는 내용)
    - (스스로 정한 동작 규칙 또는 그렇게 생각한 이유1)
    - (스스로 정한 동작 규칙 또는 그렇게 생각한 이유2)
      ...
    - (스스로 정한 동작 규칙 또는 그렇게 생각한 이유n)
```
의 형태로 기록한다.

- 엄청나게 큰 숫자가 엄청나게 많이 들어와서 연산 시 오버플로우가 발생하 수 있음.
  - 표현 범위에 제한이 없는 `BigDecimal` 타입을 사용한다. (`BigInteger`가 아닌 이유는 다음 항목 참고)
- 양의 소수(decimal number)도 양수에 해당하는데, `.` 또한 구분자로 사용될 수 있음.
  - `.`가 커스텀 구분자로 입력되는 경우, 크게 문제 되지 않으므로 그대로 구분자로 사용한다.
  - `.`가 구분자가 아닌 경우, 계산 결과가 양의 정수라는 표현은 없기 때문에 소수도 연산 대상으로 판별하여 계산한다. 
  - 대신, 출력 시 소수점 이하가 0인 경우에는 연산 결과로 정수부만을 출력한다.
- "//"와 "\n" 사이에 숫자문자("0" ~ "9")가 주어진다면, 해당 숫자문자를 커스텀 구분자로 판별할 것인가?
  - 정말, 해도 안해도 무방할 것 같다. 구분자 종류의 제한은 제안되지 않았기 때문이다.
  - 특별히 동작을 제한하지 않았다면, 그리고 그 동작의 개연이 떨어지지 않는다면, 일단 그렇게 동작해야 할 것 같다.
  - 즉, 구분자로 판별하여 동작하는 것으로 한다.