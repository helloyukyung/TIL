function 
====
함수란 
----
함수는 어떤 일을 수행한 다음에 그 결과물을 내어놓는다.<br> 

 함수는 믹서기와 같다. 그리고 믹서기에 넣는 과일은 "입력", 과일주스는 "출력(결과값)"이 될 것이다. 


function 기본구조
----
```python 
def 함수명(매개변수):
    <수행할 문장1>
    <수행할 문장2>
    ...
```
<br>

------
<br>



1.return, 매개변수, 인수
----

```python 
def add(a, b): #a, b는 매개변수
    return a + b

print(add(3,4)) #3, 4는 인수 
```
함수의 이름은 add이고 입력으로 2개의 값을 받으며 결과값은 2개의 입력값을 더한 값.

<b>매개변수</b>는 함수에 입력으로 전달된 값을 받는 변수를 의미(a,b)

<b>인수</b>는 함수를 호출할 때 전달하는 입력값을 의미(3,4)

<br>

2.입력값이 없는 함수 
----

```python 
def food():
    retrun 'tomato'
```
매개변수가 비어있는 것을 확인할 수 있음<br> 
입력값이 없는 함수  함수는 다음과 같이 사용<br>
(결괏값을 받을 변수 = 함수이름())

```python 
a= tomato()
print(a)
#tomato
```

3.결과값이 없는 함수
----

```python 
def add(a, b): 
    print(f"{a}, {b}의 합은 {a+b}입니다.")
```

결과값은 오직 return 명령어로만 돌려받을 수 있음 (print()는 결과값이 아님)
```python
a = add(3, 4)
print(a)
#None
```
결과값이 없는 함수  함수는 다음과 같이 사용<br>
(함수이름(입력인수1, 입력인수2, ...))


```python 
add(3, 4)
#3, 4의 합은 7입니다.
```

4.입력값도 결괏값도 없는 함수 
----
```python
def food()
    print('tomato')
```
입력 인수를 받는 매개변수도 없고 return 문도 없으므로 입력값도 결과값도 없는 함수임
이러한 함수는 다음과 같이 사용<br>
(함수이름())

```python
food()
#tomato
```


5.입력값이 몇 개가 될지 모를 때
----
<br>
기본구조는 다음과 같음

```python
def 함수이름(*매개변수): 
    <수행할 문장>
    ...
```
여러개의 입력값을 받는 함수 만들어보자<br>
예를 들어 add_many(1, 2)이면 3을, add_many(1,2,3)이면 6을 돌려줌 


```python
def add_many(*args):
    result = 0 
    for i in args:
        result =result +i 
        return result
```
위에서 만든 add_many함수는 입력값이 몇개든 상관없음.

매개변수 이름 앞에 *를 붙이면 입력값을 전부 모아서 튜플로 만들어줌 

```python 
result = add_many(1,2,3)
print(result)
#6
``` 
