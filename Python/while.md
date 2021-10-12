while
====
while문의 기본구조
----

```python
while <조건문>:
    <수행할 문장1>
    <수행할 문장2>
    <수행할 문장3>
```

예외처리 try except
----

```python
try:
    실행할 코드 
except 예외이름:
    예외가 발생했을 때 처리하는 코드

```
에러메세지 받아오기
```python
try:
    실행할 코드 
except 예외이름 as 변수(보통 e,(exception)):
    print("예외가 발생",e)
```

- try의 코드가 에러없이 잘 실행되면 except의 코드는 실행되지 않고 그냥 넘어간다. 
- try의 코드에서 에러가 발생햇을 때만 except의 코드가 실행됨 

while문 예외처리
```python
while True:
    try:
        a, b = map(int, input().split())
        print(a+b)
    except :
        break
```