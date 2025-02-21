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
            for( int j = i ; j < s.length() ; j++ )  
            {  
                String com ="";  
                for(int k = i ; k <= j ; k++ )  
                {  
                    com += s.charAt(k);  
                }  
  
                System.out.println(com);  
            }  
            System.out.println();  
        }  
  
  
  
  
    }  
}
```

