---
description: 객체는 인터페이스를 사용해 참조해라
---

# Item 64

## Intro

- 적합한 인터페이스만 있다면 매개변수뿐 아니라 반환값, 변수, 필드를 전부 인터페이스 타입으로 선언하라
- 인터페이스를 타입으로 사용하는 습관을 길러두면 프로그램이 훨씬 유연해질 것이다.

- 구현 타입을 바꾸려 하는 동기가 뭘까?
	- 각 구현체들의 특수성이 있기 때문이다.
	
- 적합한 인터페이스가 없가면 당연히 클래스로 참조해야 한다.
	- String과 BigInteger
	- 클래스 기반으로 작성된 프레임워크가 제공하는 객체들
	- 인터페이스에는 없는 특별한 메서드를 제공하는 클래스들

- 적합한 인터페이스가 없다면 클래스의 계층구조 중 필요한 기능을 만족하는 가장 덜 구체적인 클래스를 타입으로 사용하는 것이 좋다.