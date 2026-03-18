# Collections
``` java
import java.util.*;

void main(String[] args) {
    boolean isPalindrome = true;
    Deque<String> dequePalindrome = new LinkedList<>();
    Scanner input = new Scanner(System.in);
    System.out.println("Enter String palindrome");
    String word = input.nextLine();
    String[] array = word.split("");
    for (int i = 0;i < array.length; i++){
        dequePalindrome.addLast(array[i]);
    }
    System.out.println(dequePalindrome);
   
    while(dequePalindrome.size()>1){
        String first = dequePalindrome.removeFirst();
        String last = dequePalindrome.removeLast();
       if(!first.equals(last)){
            isPalindrome= false;
            break;
        }
    }

    if(dequePalindrome.size()==1 ||isPalindrome){
        System.out.println("Palindrome detected, "+word+ " is a palindrome");
    }else {
        System.out.println("No palindrome detected, "+ word +" is not a palindrome");
    }

}
```
## Output for civic
<img width="569" height="170" alt="Screenshot 2026-03-18 165116" src="https://github.com/user-attachments/assets/849650d8-b85e-48ae-8b84-d1338e5e5de2" />
## Output for rotostor
<img width="557" height="179" alt="Screenshot 2026-03-18 165058" src="https://github.com/user-attachments/assets/0ae82bdc-12ff-4a3d-a3f2-54c8c3c0d461" />
