# *텍스트 RPG게임*



#### 🎯 *실행 화면*


![Sep-26-2021 03-17-12](https://user-images.githubusercontent.com/86669143/134781972-37ae435a-5417-4b94-8dbb-4da41d6aec04.gif)





---
#### 🧩 *배운 내용 정리하기*

    1. window
    => window 객체는 브라우저를 가리키는 객체로 , 브라우저가 제공하는 기본 객체와 함수들은 대부분 window 객체 안에 들어있다.
       document 객체나 console 객체도 실제로는 window.documnet,window.console 인데, window를 생략하고 
       document와 console만 적는다.

    2. this
    => this는 상황에 따라 다른 값을 가진다. 기본적으로 this는 window 객체를 가리키므로 어떤 때에 어떤 값을 가지는지 외우면 된다.

    1) 객체를 통해 this를 사용할 때는 this가 해당 객체를 가리키게 된다.

    2) 특정 메서드는 콜백 함수의 this를 바꾼다. addEventListener가 대표적이다.

    3) this가 바뀌는 것을 원치 않는다면 함수 선언문 대신 화살표 함수를 사용한다.

    3. 참조, 깊은 복사, 얕은복사
    => 복사는 어떤 값을 다른 변수에 대입할 때 기존 값과 참조 관계가 끊기는 것을 의미한다. 객체가 아닌 값은 애초부터 참조 관계가
       없으므로 그냥 복사된다.
       객체를 복사할 때는 얕은 복사와 깊은 복사가 있는데, 
       얕은 복사는 중첩된 객체가 있을 때 가장 바깥 객체만 복사되고 내부 객체는 참조 관계를 유지하는 복사를 의미한다.
       깊은 복사는 내부 객체까지 참조 관계가 끊겨서 복사된는 것을 의미한다.

    ex) const array = [{ j: 'k'}, {l:'m}];
        const reference = array; // 참조
        const shallowCopy = [...array]; // 얕은 복사
        const deepCopy = JSON.parse(JSON.stringify(array)); // 깊은 복사
        console.log(array === reference); // true
        console.log(array[0] === reference[0]); // true
        console.log(array === shallowCopy); // false
        console.log(array[0] === shallowCopy[0]); // true
        console.log(array === deepCopy); // false
        console.log(array[0] === deepCopy[0]); // false
    - JSON.parse(JSON.stringify(값))으로 간단하게 깊은 복사를 할 수 있다.
    - 얕은 복사를 할때는 ...연산자를 사용한다.
      ...연산자를 스프레드(spread) 문법이라고 하는데 스프레드 문법은 기존 객체의 속성을 새 객체에 할당할 때 사용한다.
      배열이라면 [...배열]
      객체라면 {...객체} 해주면 된다.

    4. 클래스
    => 객체를 생성하는 템플릿 문법이다. class 예약어로 클래스를 선언하고 constructor 메서드 안에 기존 코드를 넣는다.
       new를 붙여 호출하면 constructor 함수가 실행되고 객체가 반환된다. this는 생성된 객체 자신을 가리키게 된다.

    5. 클래스 상속
    => 클래스 끼리 extends 예약어로 상속할 수 있다. 상속하는 클래스는 부모 클래스가 되고, 상속받는 클래스는 자식 클래스가 된다.
       공통되는 속성이나 메서드는 부모 클래스로부터 상속받는다.

    ex) class Hero extends Unit {
          constructor(game, name) {
              super(game, name, 100, 10, 0); // 부모 클래스의 생성자 호출
              this.lev = 1; 
          }
          attack(target) {
            super.attack(target) // 부모 클래스의 attack
            //자식 클래스만의 동작
          }
        }
    - 자식 클래스에서 super 함수는 부모 클래스를 의미하며 부모 클래스의 생성자에 인수를 전달한다.
      공통되는 속성은 부모 클래스의 것을 사용하고 , 공통되지 않는 속성은 자식 클래스에 따로 선언한다.
    
    - 메서드에서도 super를 사용할 수 있다. 자식 클래스에서 super.메서드를 호출하는 것은 부모 클래스의
      메서드를 호출하는 것과 같다. 부모 클래스의 메서드를 호출한 후 다른 작업을 할 수 있다.
      자식 클래스에 메서드를 생성하지 않은 경우에도 부모 클래스에 메서드가 존재한다면 호출할 수 있다.
