# Java Basics

``` java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        int first = 1;
        int second = 2;
        double third = 3.44;
        char c = 'c';
        boolean basic = true;
        System.out.println(
                first + "\n" + second + "\n" + third + "\n" + c + "\n" + basic);
        Scanner input = new Scanner(System.in);

        int sum = first + second;
        int product = first * second;
        int diff = first - second;
        double quotient = first / second;
        int remainder = first % second;
        System.out.println("Sum =" + sum);
        System.out.println("Product =" + product);
        System.out.println("Difference =" + diff);
        System.out.println("Quotient =" + quotient);
        System.out.println("Remainder =" + remainder);


        System.out.println("What is your name");
        String name = input.nextLine();
        System.out.println("What is your age");
        int age = input.nextInt();
        System.out.println("Hello " + name + "," + "You will be " + (age + 1) + " next year");

        System.out.println("Enter your first number");
        int f = input.nextInt();
        System.out.println("Enter your second number");
        int s = input.nextInt();

        System.out.println("The larger number is " + (f > s ? f : s));
       /* if (f>s) {
            System.out.println(f);
        }
        else System.out.println(s); */

        System.out.println("Enter Number");
        int number = input.nextInt();
        if (number > 0) {
            System.out.println("Positive");
        } else if (number < 0) {
            System.out.println("Negative");
        } else {
            System.out.println("Zero");
        }

        System.out.println("Enter a number between 1 and 7");
        int entry = input.nextInt();
        switch (entry) {
            case 1:
                System.out.println("Monday");
                break;
            case 2:
                System.out.println("Tuesday");
                break;
            case 3:
                System.out.println("Wednesday");
                break;
            case 4:
                System.out.println("Thursday");
                break;
            case 5:
                System.out.println("Friday");
                break;
            case 6:
                System.out.println("Saturday");
                break;
            case 7:
                System.out.println("Sunday");
                break;
        }
        for (int i = 1; i <= 20; i++) {
            System.out.print(i + " ");
        }
        ;
        System.out.println();
        // System.out.println("Enter a number until your enter -1");
        int num = 0;
        int total = 0;
        //num = input.nextInt();
        while (num != -1) {
            System.out.println("Enter a number until your enter -1");
            num = input.nextInt();
            total += num;

        }
        System.out.println("The sum of the numbers is " + total);

        for (int i = 0; i <= 5; i++) {
            for (int j = 1; j <= i; j++) {
                System.out.print("*");
            }
            System.out.println();
        }

        int array[] = new int[5];
        System.out.println("Enter 5 numbers");
        int sum3 = 0;
        double average = 0;
        for (int i = 0; i <= 4; i++) {
            array[i] = input.nextInt();
            sum3 += array[i];
        }
        average = (double) sum3 / 5;
        System.out.println("The sum of the numbers is " + sum3);
        System.out.println("The average of the numbers is " + average);
        int max = array[0];
        int min = array[0];
        for (int i = 0; i <= 4; i++) {
            if (array[i] < min) {
                min = array[i];
            }
            if (array[i] > max) {
                max = array[i];

            }

        }
        System.out.println("The max value is " + max);
        System.out.println("The min value is " + min);

        System.out.println("How many students are in the class?");
        int classSize = input.nextInt();
        int array2[] = new int[classSize];
        System.out.println("Enter scores");
        int count = 0;
        for (int i = 0; i < classSize; i++) {
            array2[i] = input.nextInt();
            if (array2[i] >= 60) {
                count++;
            }
        }
        double average2;
        int sum2 = 0;
        int highest = array2[0];
        for (int i = 0; i < classSize - 1; i++) {
            sum2 += array2[i];
            if (highest < array2[i]) {
                highest = array2[i];
            }
        }
        average2 = (double) sum2 / classSize;
        System.out.println("The average score is " + average2);
        System.out.println("The highest score is " + highest);
        System.out.println("The number of students who passed is " + count);
    }

}
```
