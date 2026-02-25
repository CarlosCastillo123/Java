# Code
``` java
 public static void main(String[] args){
        int i = 10;
        String s = "test";
     
```
# Stack
|Memory address| Content| Var name|
|-|-|-|
|0x100|10|i
|0x200|0xA1|s

# Heap 
|Memory address| Content| Var name|
|-|-|-|
|0xA|t|s[0]
|0xB|s|s[1]
|0xC|e|s[2]
|0xD|t|s[3]
