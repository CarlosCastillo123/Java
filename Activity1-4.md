# Word Count
![Word-count](https://github.com/user-attachments/assets/7fe5f43e-9319-4e97-b334-d9aa4dfb403b)
 
## Code
``` java
import java.util.HashMap;
import java.util.Map;


public class Main {
    public static void main(String[] args) {
        String text = "java is easy and java is powerful";

        Map<String, Integer> wordCount = new HashMap<>();

        String[] words = text.split(" ");
        for (String word : words) {
            if (wordCount.containsKey(word)) {
                wordCount.put(word, wordCount.get(word) + 1);
            } else {
                wordCount.put(word, 1);
            }
        }

        for(String word: wordCount.keySet()){
            System.out.println(word + ":" + wordCount.get(word));
        }
    }
}
```
