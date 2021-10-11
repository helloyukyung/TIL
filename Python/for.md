for
====
for문의 기본구조 
----

```python 
for 반복제어변수 in 반복 가능한(iterable) 객체 [Ex).리스트 튜플, 문자열]:
    수행할 문장1
    수행할 문장2
```
----

index값을 반환하는 for문

```python
N= input() #4
for i in range(N):
    print(i)
## 0 1 2 3

```
list_N의 원소 값을 반환하는 for문

```python
list_N= [3,2,4,7]
for num in list_N :
    print(num)
## 3 2 4 7

```
원소와 index 함께출력 for 문 
```python 
i=0 
for letter in ['A','B','C']:
    print(i, letter)
    i += 1
```
혹은 python 내장함수인 enumerate()함수 사용
```python
for entry in enumerate(['a','b','c']):
    print(entry)
# (0, 'A')
# (1, 'B')
# (2, 'C')
```
인자풀기(unpacking), 인덱스와 원소를 각각 다른 변수에 할당 
```python
for i,letter in enumerate(['a','b','c'],start=1):
    print(i,letter)
# 1 A
# 2 B
# 3 C
```
enumerate() 함수는 함수안에 인자로 들어온 iterable 객체를 순서대로 인덱스와 원소를 반환해주는 함수


_ in iterable객체 for 문
```python
for _ in range(3):
    print("hi")
## hi
## hi
## hi
```
반복만 수행, i(반복제어변수) 에 값을 집어넣지 않음.