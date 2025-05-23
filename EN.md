# Documentation

* [First Program](#First-Program)
* [Variables](#Variables--Data-Types)
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

If the function takes no arguments, it's not necessary to include parentheses, making this notation equivalent:

````scala
def main(){
    println("Hello World");
}
````


# Variables & Data Types

A variable can be created using the `var` keyword. This is followed by the variable's name, and then the value it will store.
````scala
def main(){
    var test = 10;
    println(test);
}
````
As expected, `10` will be displayed in the console. When the type is not explicitly specified, the compiler infers it, and in this case, the type will be `byte`.

You can use a colon to specify the type of variable, for example:
````scala
def main(){
    var test : String = 10;
    println(test);
}
````
This code will cause an error because the `String` type cannot store a number; it is meant for storing strings.

````scala
def main(){
    var test : String = "Hello World";
    println(test);
}
````
This code will already be correct and we will see ‘Hello World’ in the debug.

Ixion has the following types:


# Nullable types

Non-primitive variables can store the value `null`. Ixion has a special syntax for such variables. For example, `String` is a non-primitive type, so it can store `null`.

But here's the problem if we write such code:
````scala
def main(){
    var test : String;
    println(test);
}
````

We see a error:
````
[Ixion Exception]
│> [2:14] in file "test.ix" ['test']:
│> Cannot default initialize variable of type 'java.lang.String'
````

It indicates that the variable has not been assigned a default value. Previously, we always assigned a value to `String` type variables, but since we haven't done so now, it should theoretically hold `null`.

To give the variable this feature, let's modify our construction as follows:
````scala
def main(){
    var test : String?;
    println(test);
}
````
A `?` (question mark) appears after the type name. Our variable now stores `null`, and that is precisely what will be printed to the console.
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

Returns true if the first operand is larger than or equal to the second operand:
`x <= y (larger or equal)`

Returns true if the first operand is less than or equal to the second operand:
`x >= y (less or equal)`

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
Conditions check something, and if it is true, then execute some code.

A simple condition consists of a single `if`.

```scala
def main {
    if (true) {
        print("true");
    }
}
```

All conditional statements:

* `if` 
* `else if`
* `else`

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
Loops perform the execution of expressions while a condition is met.

Example of `while`:
```java
while (true) {
  println("Бесконечность не предел!");
}
```
In this example, we will endlessly print *Infinity is not a limit!* because `true` is used as the condition.

* First for loop example:
```java
for (var i = 1, i < 10, i+=1) {
  print(i)
}
```

In this example:<br>
We Initialize a variable `i` to *1*<br>
As long as `i` is less than *10*:<br>
> Output a variable `i`;<br>
> Incriminating a variable `i`.

# Arrays
> This is one of the complex data types, we can store several values in it at once.
#### Creating an array with a specified number of elements
Specifying the array type is mandatory:
```scala
def main {
    var arr = new int[5];
    println(arr[1]);
}
```
Here we have created a new array of `int` type with 10 elements.

Первый элемент массива стоит по индексу *0*, так что если мы хотим вывести элемент массива с индексом *1*, то он будет вторым по порядку.
Однако в коде мы создаем массив с *5* ячейками, а значит он выглядит так: `[0, 0, 0, 0, 0]`. Поэтому при выводе `array[1]` мы получим *0*,
так же как было бы с любым другим элементом массива.

#### Creating an array with known elements
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
Example 2:
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
The keyword `def` is used to define a function. This is followed by the name, arguments (if any), a colon (`:`), the return value type, and the function body.

Example:
````scala
def main {
    print(custom_mul(10));
}

def custom_mul(arg : int) : int {
    return arg * 10;
}
````
To return the result of a function, the `return` keyword is used.


If a function has no arguments, the parentheses in its signature are optional:
```scala
def main {
    print(custom_mul());
}

def custom_mul : int {
    return 101;
}
````
## Lambda-Functions
Example:
````scala
def main {
    print(message());
}

def message => "Lambda!!!";
````

# Ternary Operator
Example:
```scala
def main {
  var a = true;
  var b = false;
  
  println(a ? "yes" : "no");
  println(b ? "yes" : "no");
}
```

# Bitwise Shifts
`>>` - shifts n bits of the number to the right

`>>>` - shifts n bits of the number to the right, fills with zero from the left

`<<` - shifts n bits of the number to the left

Example:
````scala
def main {
    println(1 << 10); // 1024
    println(4096 >> 10); // 4
}
````

# Libraries
Ixion's initial capabilities may not be sufficient, but built-in libraries can solve this problem.

Both the language's own libraries (which are currently few) and all libraries available on the JVM can be used.

```scala
// Example #1
def main {
  print(Math.cos(0));
}
```
Here we can see the built-in java Math library.

```scala
// Example #2
using java.util.ArrayList;

def main {
    var list = new ArrayList();
    list.add("some text");
    print(list.get(0));
}
```
In this example, we import ArrayList and use its functionalities. The language also supports the following import syntax:
````scala
using java.util.ArrayList : AL;

def main {
    var list = new AL();
}
````

You can read more about library methods in the corresponding chapters.
