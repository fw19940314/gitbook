### equals 和 ==

####  == 比较时

> 1.对于基本类型来说，根据基本数据的值判断是否相等，两端的数据类型可以不同。
>
> 2.引用数据类型比较时，比较引用类型变量的地址值是否相等。

#### equals 比较时

> 1.只能处理引用类型变量；
>
> 2.equals底层任然比较的是两个引用变量的地址值；

```java
String str1 = new String("aa");

String str2 = new String("aa");

System.out.println(str1==str2)//false(==比较对象时，比较的是地址值)

System.out.println(str1.equals(str2))//true

String类重写了equals（）方法

源码解析

public boolean equals(Object anObject) {

if (this == anObject) {

return true;

}

if (anObject instanceof String) {

String anotherString = (String)anObject;

int n = value.length;

if (n == anotherString.value.length) {

char v1[] = value;

char v2[] = anotherString.value;

int i = 0;

while (n-- != 0) {

if (v1[i] != v2[i])

return false;

i++;

}

return true;

}

}

return false;

}
```

> 像String、File、Date..这些类重写了Object类的equals方法，比较的是两个对象的“实体内容”是否完全相同
