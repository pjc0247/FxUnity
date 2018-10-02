FxUnity
====

SuperPowerUnity

````c#
// A virtual scenario that simulates HearthStone.
IEnumerator BeginTurn() {
  Fx( countdown -Fx.To(10.0)> 10 );

  /* .... */

  yield return Fx( countdown |Fx.Trap(5) );
  anduin.Message("I must choose quickly!");
  rope.Burn();
}
````

Extensions
----
__Fx.To__
```c#
number -Fx.To(duration)> target_value1 > target_value2 > ...

// 투명도를 1초 간격으로 투명-반투명을 반복한다.
opacity -Fx.To(1.0)> 0 > 255 > 0 > 255
```

__Fx.Blink__
```c#
number -Fx.Blink(duration)> target_value1 > target_value2 > ...

// 투명도를 0.1초 간격으로 깜빡깜빡한다.
opacity -Fx.Blink(0.1)> 0 > 255 > 0 > 255
```

__Fx.Trap__
```c#
number |Fx.Trap(target_value)| timeout

// hp가 10으로 떨어질 때 까지 다음 코드 실행을 멈춘다.
hp |Fx.Trap(10)
```
* timeout : optional

__Fx.Watch__
```c#
dst_number <Fx.Watch()- src_number - delta

// 파티 멤버2를 1에 10픽셀 떨어져서 따라다니게 한다. 
member2.x <Fx.Watch()- member1.x - 10
```
* delta : optional

__Fx.Stop__
```c#
number <Fx.Stop()> target_value

// Stop all events and set opacity to 255.
opacity <Fx.Stop()> 255;
```
`number` 에 대해 진행중인 모든 Fx 이벤트를 제거하고 `target_value`로 값을 설정한다.

AAAA
----
Blink 식 뒤에 Blink를 다시 호출하여 주기를 변경할 수 있다.
```c#
opacity -Fx.Blink(0.1)> 0 > 255 > Fx.Blink(1.0) > 0 > 255
```
Blink 식 뒤에 To를 호출하여 효과를 변경할 수 있다. (역도 가능)
```c#
opacity -Fx.Blink(0.1)> 0 > 255 > Fx.To(1.0) > 0 > 255
```

Issusssss
-----
* `Fx()`로 안감싸면 에러남
  * C# 문법상 `a -Fx.To()> 10`이 단순 식으로 판단되서 실행 안시켜줌
