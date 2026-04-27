# Parallel counting using runable
## Code
``` java
import java.util.ArrayList;

class Counter {
    int value = 0;

    synchronized void increment() {
        value++;
    }
}
public class Main {
    public static void main(String[] args) throws Exception {
        Counter counter = new Counter();

        // Runnable task
        Runnable task = () -> {
            for (int i = 1; i <= 5; i++) {
                System.out.println(Thread.currentThread().getName() + " : " + i);
                try {
                    Thread.sleep(500);
                } catch (InterruptedException e) {}
            }
        };
        /* Runnable task = () -> {
            for (int i = 0; i < 1000; i++) {
                counter.increment();   // critical section
            }
        };
            */
        Thread t1 = new Thread(task);
        Thread t2 = new Thread(task);
        Thread t3 = new Thread(task);
        Thread t4 = new Thread(task);
        Thread t5 = new Thread(task);

        t1.start();
        t2.start();
        t3.start();
        t4.start();
        t5.start();

        t1.join();
        t2.join();
        t3.join();
        t4.join();
        t5.join();


        System.out.println("Final Counter: " + counter.value);
    }

```
