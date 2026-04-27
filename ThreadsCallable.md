# Callable Threads
## Code 
``` java
import java.util.concurrent.*;
import java.util.*;
import java.util.Arrays;
import java.util.List;


public class Main {
    public static void main(String[] args) throws Exception {

        ExecutorService executor = Executors.newFixedThreadPool(3);

        List<Callable<Integer>> tasks = List.of(
                () -> {
                    Thread.sleep(3000);
                    return 10;
                },
                () -> {
                    Thread.sleep(1000);
                    return 20;
                },
                () -> {
                    Thread.sleep(2000);
                    return 30;
                }


        );
        // Display the fastest result
        int fastestResult = executor.invokeAny(tasks);
        System.out.println("Fastest Result: " + fastestResult);

        List<Future<Integer>> results = executor.invokeAll(tasks);
        // Calculate sum of results
        int sum = 0;
        for (Future<Integer> f : results) {
            sum += f.get();
        }

        System.out.println("Sum of all results: " + sum);
        // Completion Order
        CompletionService<Integer> service =
                new ExecutorCompletionService<>(executor);

        for (Callable<Integer> task : tasks) {
            service.submit(task);
        }

        System.out.println("Results in completion order:");

        for (int i = 0; i < tasks.size(); i++) {
            Future<Integer> result = service.take();
            System.out.println(result.get());
        }
        // Performance Experiment
        long start = System.currentTimeMillis();

        // run tasks

        long end = System.currentTimeMillis();
        System.out.println("Time: " + (end - start));
        // Db task
        Callable<String> dbTask = () -> {
            Thread.sleep(3000);
            return "Database Query";
        };
        //Cache lookup
        Callable<String> cacheTask = () -> {
            Thread.sleep(1000);
            return "Cache Lookup";
        };
        Callable<String> apiTask = () -> {
            Thread.sleep(2000);
            return "API Call";
        };
        List<Callable<String>> tasks3 = Arrays.asList(dbTask, cacheTask, apiTask);

        List<Future<String>> futures = executor.invokeAll(tasks3);
        for (Future<String> future : futures) {
            System.out.println(future.get());
        }


    }
}


```
