```java
import java.util.*;  
//TIP To <b>Run</b> code, press <shortcut actionId="Run"/> or  
// click the <icon src="AllIcons.Actions.Execute"/> icon in the gutter.  
public class Main {  
  
    public static void main(String[] args) {  
  
        Scanner scn  = new Scanner(System.in);  
        String s = scn.next();  
        String com = "";  
  
        for( int i = 0 ; i < s.length() - 1 ;  i++ )  
        {  
            if(s.charAt(i) != s.charAt(i+1)){  
                com += s.charAt(i);  
            }  
        }  
  
        com += s.charAt(s.length() - 1 ) ;  
  
        System.out.println(com);  
    }  
}
```
