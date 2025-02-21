```java
import java.util.*;  
//TIP To <b>Run</b> code, press <shortcut actionId="Run"/> or  
// click the <icon src="AllIcons.Actions.Execute"/> icon in the gutter.  
public class Main {  
  
    public static void main(String[] args) {  
  
        Scanner scn  = new Scanner(System.in);  
  
        String s = scn.next();  
  
  
  
        for( int i = 0 ; i < s.length()  ;  i++ )  
        {  
            for( int j = (i+1) ; j <= s.length() ; j++ )  
            {  
                String com = s.substring(i , j);  
                System.out.println(com);  
            }  
            System.out.println();  
        }  
  
  
  
  
    }  
}
```

