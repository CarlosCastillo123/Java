# Statistical_Data_Analysis
``` java
import java.util.Scanner;

public class Main {
    static void sorting(double[] arr) {
        double temp;
        for (int i = 0; i < arr.length; i++) {
            for (int j = i + 1; j < arr.length; j++) {
                if (arr[i] > arr[j]) {
                    temp = arr[i];
                    arr[i] = arr[j];
                    arr[j] = temp;
                }
            }
        }
    }

    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        System.out.println("How many days of temperature data will be entered");
        int days = input.nextInt();
        double arr[] = new double[days];
        System.out.println("Enter the temperatures individually");
        for (int i = 0; i < arr.length; i++) {
            arr[i] = input.nextDouble();
        }
        double sum = 0;
        for (double v : arr) {
            sum += v;
        }
        double mean = sum / days;
        System.out.println("The mean value for the temperatures is " + mean);
        sorting(arr);
        for (double v : arr) {
            System.out.println(v);
        }
        if (arr.length % 2 == 0) {
            int middleValue = arr.length / 2;
            double average = (arr[middleValue] + arr[middleValue - 1]) / 2;
            System.out.println("The median temp is " + average);
        } else {
            int middleValue = arr.length / 2;
            System.out.println("The median temp is " + arr[middleValue]);
        }
        double max = arr[0];
        double min = arr[0];
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] > max) {
                max = arr[i];
            } else if (arr[i] < min) {
                min = arr[i];
            }
        }
        double range = max - min;
        System.out.println("The range is " + range);
        double variance = 0;
        double total = 0;
        for (int i = 0; i < arr.length; i++) {
            total += ((arr[i] - mean) * (arr[i] - mean));
        }
        variance = total / arr.length;
        System.out.println("The variance is " + variance);

        double standardDeviation = Math.sqrt(variance);

        System.out.println("The standard deviation is " + standardDeviation);

        if (standardDeviation < 2) {
            System.out.println("Temperatures are consistent");
        } else if (standardDeviation < 5) {
            System.out.println("Temperatures show moderate Variation");
        } else {
            System.out.println("Temperatures vary significantly");
        }

    }

}
```
