# Lab: Understanding and Using Wrapper Classes in Java

## Objectives

By the end of this lab, students will: - Understand Java Wrapper
Classes - Perform boxing and unboxing - Use wrapper utility methods -
Store wrapper objects inside ArrayList - Apply Character class utility
methods

------------------------------------------------------------------------

## Background

Java primitive types: `int`, `double`, `char`, `boolean`

Wrapper classes: `Integer`, `Double`, `Character`, `Boolean`

Collections like `ArrayList` require objects --- not primitives.

------------------------------------------------------------------------

# Part 1 --- Boxing and Unboxing

### Task 1.1 --- Manual Boxing

1.  Create an `int` variable.
2.  Convert it to an `Integer` using `Integer.valueOf()`.
3.  Print both values.

```java
int a = 0;
        Integer b = Integer.valueOf(a);
        System.out.println(a +" "+ b);
```

```txt
0 0
```


### Task 1.2 --- Auto Boxing and Unboxing

1.  Assign an int directly to an Integer.
2.  Assign an Integer back to an int.
3.  Print both values.
   ``` java
   Integer i = Integer.valueOf(10);
        int num = i;
        System.out.print(i+" "+num);

```
``` txt
10 10
```

### Reflection Questions

1.  What is the difference between primitive and wrapper types?
   Primitave data types have no funtions. Wrapper types have classes and funtions.
3.  When does auto-boxing occur?
Auto-boxing occurs at run time
 ------------------------------------------------------------------------

# Part 2 --- Wrapper Utility Methods

### Task 2.1 --- Convert String to Integer

1.  Create a string `"123"`.
2.  Convert it using `Integer.parseInt()`.
3.  Add 10 and print result.
``` java
String s = "123";
 System.out.println(Integer.parseInt(s)+10);
```
``` txt
133
```
### Task 2.2 --- Print Limits

Print: - `Integer.MAX_VALUE` - `Integer.MIN_VALUE`
```txt
-1
```

### Reflection

Why are these constants useful in programming?
Constants eliminate bugs from changing values in the future.
------------------------------------------------------------------------

# Part 3 --- Wrapper Classes with ArrayList

1.  Create an `ArrayList<Integer>`.
2.  Add at least 3 numbers.
3.  Compute and print their sum.
   ``` java

        ArrayList<Integer> list = new ArrayList<>();
        list.add(10);
        list.add(10);
        list.add(10);
        int total = 0;
        for(int l : list){
             total+=l;
        };
        System.out.println(total);
```
```txt
30
```
    

### Question

Why can't we use `ArrayList<int>`?
You cant make an array list of a prative datatype

------------------------------------------------------------------------

# Part 4 --- Character Wrapper

1.  Declare a character.
2.  Use:
    -   `Character.isUpperCase()`
    -   `Character.isDigit()`
    -   `Character.isLetter()`
3.  Print results.
   ``` java
 char character = 'c';
        System.out.println(Character.isUpperCase(character));
        System.out.println(Character.isLowerCase(character));
        System.out.println(Character.isLetter(character));
```
```txt
false
true
true
```

------------------------------------------------------------------------

# Bonus Challenge

1.  Ask user for 5 numbers (as strings).
2.  Convert them to Integer objects.
3.  Store in ArrayList.
4.  Compute:
    -   Sum
    -   Average
    -   Maximum (without using Collections.max)
      ```java
        Scanner input = new Scanner(System.in);
        System.out.println("Enter 5 numbers");
        ArrayList<Integer> list2 = new ArrayList<>();
        for (int e = 0; e <= 4; e++) {
           String number = input.nextLine();
            list2.add(Integer.parseInt(number));
        }
        int total2 = 0;
        int average = 0;
        int max = 0;
        for (int f : list2) {
            total2 += f;
            if (max < f) {
                max = f;
            }
        }
        average = total2 / 5;
        System.out.println("Total: " + total2 + " Average: " + average
                + " Maximum value: " + max);
      ```
 ```txt
55
99
77
66
11
Total: 308 Average: 61 Maximum value: 99

```

------------------------------------------------------------------------

# Submission

Submit: - All in github. Reflection answers, clean formatting and proper comments
