# 7.1 Exceptions
## Code with stepsToMiles method
``` java
import java.util.Scanner;

public class Main {
    public static double stepsToMiles(Scanner scnr) throws Exception {
        int input = scnr.nextInt();
        double result = (double) input / 2000;
        if (input < 0) {
            throw new Exception("Exception: Negative step count entered.");
        }
        return result;
    }

    public static void main(String[] args) {
        int steps;
        double result = 0.0;
        Scanner input = new Scanner(System.in);
        System.out.println("Please enter the number of steps you took today");
        try {
            result = stepsToMiles(input);
            System.out.printf("You walked %.2f miles today!",result);
            System.out.flush();
        } catch (Exception expt) {
            System.out.println(expt.getMessage());
        }
    }
}
```
## Input/Output with negative number
<img width="501" height="167" alt="Screenshot 2026-03-11 145641" src="https://github.com/user-attachments/assets/3694f4d9-b529-4c7c-8626-8a508c4550c1" />

## Input/Output with positive number
<img width="487" height="138" alt="Screenshot 2026-03-11 145617" src="https://github.com/user-attachments/assets/174c81ba-52d9-442c-b247-6fc11c9decb9" />
