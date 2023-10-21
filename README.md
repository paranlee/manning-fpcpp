# Functional programming in C++

![Book cover](https://gitlab.com/manning-fpcpp-book/code-examples/raw/master/.resources/fpcpp-cover.png)

## Code examples

C++ 함수형 프로그래밍은 각 장이 이전 장에서 배운 개념을 기반으로 하기 때문에 순차적으로 읽기 권함
각 장마다 개념이 어려워져서 처음 읽은 후 이해가 안 되는 부분이 있다면 계속 진행하기보다는 다시 읽기
유일한 예외는 8장인데, 영구 데이터 구조가 구현되는 방식에 관심이 없다면 건너뛸 수 있음
이 책은 두 부분으로 나뉨.

첫 번째 파트에서는 함수형 프로그래밍 관용어와 이를 C++에 적용하는 방법을 다룸

- 1장에서는 함수형 프로그래밍에 대한 간략한 소개와 함수형 프로그래밍이 C++ 세계에 가져다주는 이점을 설명합니다.
- 2장에서는 고차 함수, 즉 다른 함수를 인수로 받거나 새로운 함수를 반환하는 함수를 다룹니다. C++ 프로그래밍 언어의 표준 라이브러리에서 찾을 수 있는 몇 가지 유용한 고차 함수를 통해 이 개념을 설명합니다.
- 3장에서는 일반 C 함수부터 함수 객체와 람다에 이르기까지 C++에서 함수 또는 함수와 유사한 것으로 간주하는 모든 다양한 사물에 대해 설명합니다.
- 4장에서는 기존 함수에서 새로운 함수를 만드는 다양한 방법을 설명합니다. std::바인드와 람다를 사용해 부분 함수를 적용하는 방법을 설명하고, 커링이라는 함수를 바라보는 또 다른 방법을 보여줍니다.
- 5장에서는 절대 변하지 않는 데이터, 즉 불변 데이터의 중요성에 대해 이야기합니다. 변경 가능한 상태를 가질 때 발생하는 문제와 변수 값을 변경하지 않고 프로그램을 구현하는 방법을 설명합니다.
- 6장에서는 지연 평가에 대해 자세히 살펴봅니다. 문자열 연결과 같은 간단한 작업부터 동적 프로그래밍을 사용한 알고리즘 최적화까지, 지연 평가를 최적화에 어떻게 사용할 수 있는지 보여줍니다.
- 7장에서는 사용성과 성능을 개선하기 위한 표준 라이브러리 알고리즘을 현대적으로 재해석한 범위(range)에 대해 설명합니다.
- 8장에서는 불변 데이터 구조, 즉 데이터 구조가 수정될 때마다 이전 버전을 유지하는 데이터 구조에 대해 설명합니다.

책의 두 번째 부분에서는 주로 함수형 소프트웨어 설계와 관련된 고급 개념을 다룸

- 9장에서는 프로그램에서 유효하지 않은 상태를 제거하기 위해 합계형을 사용하는 방법을 보여줍니다. 9장에서는 상속과 std::variant를 사용하여 합계형을 구현하는 방법과 오버로드된 함수 객체를 생성하여 처리하는 방법을 보여 줍니다.
- 10장에서는 일반 유형을 더 쉽게 처리하고 벡터, 옵션, 퓨처와 같은 일반 유형과 함께 작동하는 함수를 작성할 수 있게 해주는 추상화인 함수와 모나드에 대해 설명합니다.
- 11장에서는 C++ 프로그래밍 언어에서 FP에 유용한 템플릿 메타프로그래밍 기법을 설명합니다. 정적 인트로스펙션 기법, 콜러블 객체, C++에서 템플릿 메타프로그래밍을 사용해 도메인별 언어를 만드는 방법을 다룹니다.
- 12장에서는 이 책에서 배운 모든 내용을 결합하여 동시 소프트웨어 시스템 설계에 대한 기능적 접근 방식을 보여 줍니다. 이 장에서는 연속 모나드를 사용해 리액티브 소프트웨어 시스템을 구축하는 방법을 설명합니다.
- 13장에서는 프로그램 테스트와 디버깅에 대한 함수형 접근법을 소개합니다.


### 챕터별 예제

- `01-..` - Introduction to functional programming
- `02-..` - Getting started with functional programming
- `03-..` - Functional objects
- `04-..` - Creating new functions from the old ones

`common` 디렉토리 안의 `<person.h>` 헤더 파일에 정의한 `person_t` 클래스는 사용하는 챕터 2, 3, 4 예제에서 사용함.

`3rd-party` 디렉토리는 챕터 10, 12, 13 예제에서 사용하는 특정 free/libre open source 3rd party 라이브러리를 포함함.

### Running the examples

- 주로 C++14와 C++17에 초점(함수형 프로그래밍 패러다임을 본격 도입한)을 맞춘 내용
- 두 언어의 최신 버전은 우리가 사용할 모든 C++17 기능을 지원함
- 모든 예제는 GCC 7.2와 Clang 5.0으로 테스트함
- [cppreference](https://en.cppreference.com/w/cpp ) 와 같이 보기

```C++
// ranges example
// - https://en.cppreference.com/w/cpp/ranges

#include <iostream>
#include <ranges>
 
int main()
{
    auto const ints = {0, 1, 2, 3, 4, 5};
    auto even = [](int i) { return 0 == i % 2; };
    auto square = [](int i) { return i * i; };
 
    // the "pipe" syntax of composing the views:
    for (int i : ints | std::views::filter(even) | std::views::transform(square))
        std::cout << i << ' ';
 
    std::cout << '\n';
 
    // a traditional "functional" composing syntax:
    for (int i : std::views::transform(std::views::filter(ints, even), square))
        std::cout << i << ' ';
}
```