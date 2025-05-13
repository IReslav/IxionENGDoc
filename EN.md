# Documentation

* [First Program](#First-Program)
* [Variables](#Variables-Data-Types)
* [Nullable types](#Nullable-types)
* [Comparison Operators](#Comparison-Operators)
* [Conditional Statements](#Conditional-Statements)
* [Loops](#Loops)
* [Arrays](#Arrays)
* [Functions](#Functions)
  * [Functions](#Functions)
  * [Lambda-Functions](##Lambda-Functions)
* [Ternary Operator](#Ternary-Operator)
* [Bitwise Shifts](#Bitwise-Shifts)
* [Libraries](#Libraries)
* [OOP](#OOP)
  * [Classes](#Classes)
  * [Enums](#Enums)
  * [Interfaces](#Interfaces)
  * [Inheritance](#Inheritance)

# First Program
The entry point of the program is `main` function. Everything inside it will be executed when program starts.

Сперва давайте поздороваемся с миром 
при помощи функции `print` или
`println`.

````scala
def main {
    println("Hello World");
}
````

Если функция не принимает аргументов,
то скобки писать необязательно, 
поэтому такая запись эквивалентна:

````scala
def main(){
    println("Hello World");
}
````


# Variables & Data Types

Создать переменную можно при помощи
ключевого слова `var`. 
После этого указывается имя переменной,
а после равно значение, которая она будет
хранить.
````scala
def main(){
    var test = 10;
    println(test);
}
````
Ожидаемо, что в консоли мы увидим `10`.
Когда тип явно не указывается, компилятор
его определяет сам, и в данном случае
тип будет `byte`.

Через двоеточие можно указывать тип
переменной, например:
````scala
def main(){
    var test : String = 10;
    println(test);
}
````
Данный код вызовет ошибку, так как тип 
String не может хранить число, он нужен
для хранения строк.

````scala
def main(){
    var test : String = "Hello World";
    println(test);
}
````
Данный код уже будет валидным, и в 
консоли мы увидим Hello World.

В ixion'e есть следующие типы:


# Nullable types

Переменные, которые не являются 
примитивными могут хранить значение
`null`. В Ixion'e есть специальный 
синтаксис для таких переменных.
Например `String` - это не примитивный тип,
а значит хранить `null` он может.

Но вот проблема, если мы напишем такой
код:
````scala
def main(){
    var test : String;
    println(test);
}
````

То мы увидим ошибку:
````
[Ixion Exception]
│> [2:14] in file "test.ix" ['test']:
│> Cannot default initialize variable of type 'java.lang.String'
````

Она говорит о том, что переменной
не было присвоено дефолтное значение.
До этого мы всегда присваивали значение
переменной с типом String, но сейчас
мы этого не сделали, а значит в теории
она должна хранить `null`.

Чтобы дать переменной эту возможность,
изменим нашу конструкцию следующим
образом:
````scala
def main(){
    var test : String?;
    println(test);
}
````
После названия типа появился знак `?`,
теперь наша переменная хранит `null`, 
а значит именно это она и выведет в консоль.

# Comparison Operators

When comparing, the return value is of type `boolean`.

Returns true if operands are equal:
`x == y (equal)`

Returns true if operands are not equal:
`x != y (not equal)`

Returns true if the first operand is larger than the second operand:
`x > y (larger)`

Returns true if the first operand is less than the second operand:
`x < y (less)`

Возвращает true, если первый операнд больше или равен второму:
`x <= y (больше или равно)`

Возвращает true, если первый операнд меньше или равен второму:
`x >= y (меньше или равно)`

Example:
````scala
def main {
    var x = 2;
    var y = 3;
    println(x == y);
}
````
In debug we see `false`, since 2 doesn't equal 3.


# Conditional Statements
Условия проверяют что-либо, и если это верно, то выполняют какой-либо код.

Простое условие состоит из одного `if`.

```scala
def main {
    if (true) {
        print("true");
    }
}
```

Все условные операторы:

* `if` - *если...*
* `else if` - *в другом случае, если...*
* `else` - *если ни одно из прошлых условий не выполнилось...*

```scala
def main {
    var x = 10;
    if (false) {
        print(1);
    
    } else if (x == 1) {
        print(2);
    
    } else if (x == 10) {
        print(3);
    
    } else {
        print(4);
    }
}
```

Вышеуказанный код выведет 3.
Первое условие не выполниться, потому-что оно false.
Второе условие не выполниться, так как x не равен 1.
Третье условие *выполнится*, так как x равен 10.
else не выполниться, так как было выполнено третье условие.


# Loops
Циклы производят выполнение выражений при выполнении условия.

Пример цикла `while`:
```java
while (true) {
  println("Бесконечность не предел!");
}
```
В данном примере мы будем бесконечно выводить *Бесконечность не предел!*, т.к. вместо условия стоит `true`.

* Первый пример цикла `for`:
```java
for (var i = 1, i < 10, i+=1) {
  print(i)
}
```

В данном примере:<br>
Определяем переменную `i` равную *1*<br>
Пока `i` будет меньше *10*:<br>
> Выводим переменную `i`;<br>
> Инкриминируем переменную `i`.

# Arrays
> Это один из сложных типов данных, в нём мы можем хранить сразу несколько значений.
#### Создание массива с указанием количества элементов
Указывать тип массива обязательно:
```scala
def main {
    var arr = new int[5];
    println(arr[1]);
}
```
Тут мы создали новый массив с типом int, в котором будет 10 элементов.

Первый элемент массива стоит по индексу *0*, так что если мы хотим вывести элемент массива с индексом *1*, то он будет вторым по порядку.
Однако в коде мы создаем массив с *5* ячейками, а значит он выглядит так: `[0, 0, 0, 0, 0]`. Поэтому при выводе `array[1]` мы получим *0*,
так же как было бы с любым другим элементом массива.

#### Создание массива с заранее известными элементами
```scala
def main(){

    var names = new String[] {
            "Artyom",
            "Alexandr",
            "Danya"
    };

}
```
```scala
def main(){

    var names = new String[] {
            "Artyom",
            "Alexandr",
            "Danya"
    };

}
```
Пример 2:
````scala
def main {
    var ages = new int[]{
        14,
        16,
        18
    };
    println(ages[1]);
}
````
Так как индексация в массивах начинается с нуля, то в консоли мы увидим: "16", так как 
обратившись к элементу массива с индексом 1 мы получили именно его.

# Functions
Для определения функции используется ключевое слово `def`. 
Затем идёт имя, аргументы (если они есть), через `:` тип возвращаемого значения 
и тело функции. 

Пример:
````scala
def main {
    print(custom_mul(10));
}

def custom_mul(arg : int) : int {
    return arg * 10;
}
````
Чтобы вернуть результат функции используется ключевое слово `return`.

Если функция не имеет аргументов, то скобки, 
в которые они заключены, в сигнатуре писать необязательно:
````
def main {
    print(custom_mul());
}

def custom_mul : int {
    return 101;
}
````
## Lambda-Functions
Пример:
````scala
def main {
    print(message());
}

def message => "Lambda!!!";
````

# Ternary Operator
Пример использования:
```scala
def main {
  var a = true;
  var b = false;
  
  println(a ? "yes" : "no");
  println(b ? "yes" : "no");
}
```

# Bitwise Shifts
`>>` - сдвигает n бит числа вправо

`>>>` - сдвигает n бит числа вправо, переносит последний бит в начало

`<<` - сдвигает n бит числа влево

Примеры битового сдвига:
````scala
def main {
    println(1 << 10); // 1024
    println(4096 >> 10); // 4
}
````

# Libraries
Изначальных возможностей Ixion может быть недостаточно,
однако эту проблему могут решить встроенные библиотеки.

Импорт библиотек, 
поставляемых вместе с Ixion происходит с помощью ключевого слова `using`.
Могут использоваться как библиотеки самого языка (которых сейчас не так много),
так и все библиотеки, которые есть под jvm.

```scala
// Пример #1
def main {
  print(Math.cos(0));
}
```
Тут можно наблюдать встроенную библиотеку java Math.

```scala
// Пример #2
using java.util.ArrayList;

def main {
    var list = new ArrayList();
    list.add("some text");
    print(list.get(0));
}
```
А в данном примере мы импортируем ArrayList и используем его возможности.
В языке так же имеется возможность использовать такой синтаксис для импорта:
````scala
using java.util.ArrayList : AL;

def main {
    var list = new AL();
}
````

Более подробно о методах библиотек можно почитать в соответствующих главах.
