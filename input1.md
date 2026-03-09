# Input Output
```java
import java.io.FileInputStream;
import java.util.Scanner;
import java.io.IOException;
public class Main {

    public static void main(String[] args) throws IOException {
        FileInputStream fileInputStream = null;
        Scanner inFS = null;
        String file1;
        String path = "ParkPhotos1.txt";
        String target = "_photo.jpg";
        String replace = "_info.txt";
        fileInputStream = new FileInputStream(path);
        inFS = new Scanner(fileInputStream);
        String newString;
        System.out.println("Reading and printing file");

        while (inFS.hasNext()) {
            file1 = inFS.nextLine();
            newString = file1.replace(target, replace);
            System.out.println(newString);
        }
        inFS.close();

    }
}
```
<img width="826" height="413" alt="Screenshot 2026-03-08 222243" src="https://github.com/user-attachments/assets/cf357f3b-3886-4c72-84c8-19bec29072db" />

