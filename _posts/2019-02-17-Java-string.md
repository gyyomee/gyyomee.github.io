---
*layout: post
title: Java - indexOf, lastIndexOf, substring
tags:
- Java
- indexOf
- lastIndexOf
- substring



---



**indexOf**

- 메서드에 문자열을 입력하면 왼쪽에서 부터 일치하는 문자의 index 값을 반환한다.

```java
public static void main(String[] args){
    String s = "hello";
    System.out.println(s.indexOf('h')); // 0
}
```





**lastIndexOf**

- 메서드에 문자열을 입력하면 오른쪽에서 부터 일치하는 문자의 index 값을 반환한다.

```java
public static void main(String[] args){
    String s = "hello";
    System.out.println(s.indexOf('l')); // 3
}
```





**substring**

- 인자가 한개일 경우는 index위치부터 그 이후의 모든 문자열을 return
- 인자가 두개일 경우는 [index, index) 의 문자열을 return

```java
public static void main(String[] args){
    String s = "hello";
    System.out.println(s.subtring(1)); //ello
    System.out.println(s.substring(1,3)); //el
}
```



