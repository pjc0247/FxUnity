FxUnity
====

SuperPowerUnity

````c#
IEnumerator BeginTurn() {
  Fx( countdown -Fx.To(10.0)> 10);

  /* .... */

  yield return Fx( countdown |Fx.Trap(5) );
  anduin.Message("���� �����ؾ� �ϴµ�!");
  batzul.Burn();
}
````

Extensions
----
__Fx.To__
```c#
number -Fx.To(duration)> target_value1 > target_value2 > ...

// ������ 1�� �������� ����-�������� �ݺ��Ѵ�.
opacity -Fx.To(1.0)> 0 > 255 > 0 > 255
```

__Fx.Blink__
```c#
number -Fx.Blink(duration)> target_value1 > target_value2 > ...

// ������ 0.1�� �������� ���������Ѵ�.
opacity -Fx.Blink(0.1)> 0 > 255 > 0 > 255
```

__Fx.Trap__
```c#
number |Fx.Trap(target_value)| timeout

// hp�� 10���� ������ �� ���� ���� �ڵ� ������ �����.
hp |Fx.Trap(10)
```
* timeout : optional

__Fx.Watch__
```c#
dst_number <Fx.Watch()- src_number - delta

// ��Ƽ ���2�� 1�� 10�ȼ� �������� ����ٴϰ� �Ѵ�. 
member2.x <Fx.Watch()- member1.x - 10
```
* delta : optional

__Fx.Stop__
```c#
number <Fx.Stop()> target_value

// ��� �̺�Ʈ�� ������ ������ 255�� ����
opacity <Fx.Stop()> 255;
```
number�� ���� �������� ��� Fx �̺�Ʈ�� �����ϰ� `target_value`�� ���� �����Ѵ�.

AAAA
----
Blink �� �ڿ� Blink�� �ٽ� ȣ���Ͽ� �ֱ⸦ ������ �� �ִ�.
```c#
opacity -Fx.Blink(0.1)> 0 > 255 > Fx.Blink(1.0) > 0 > 255
```
Blink �� �ڿ� To�� ȣ���Ͽ� ȿ���� ������ �� �ִ�. (���� ����)
```c#
opacity -Fx.Blink(0.1)> 0 > 255 > Fx.To(1.0) > 0 > 255
```