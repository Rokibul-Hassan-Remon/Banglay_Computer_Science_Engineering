
##  


```java
import java.util.*;  
//TIP To <b>Run</b> code, press <shortcut actionId="Run"/> or  
// click the <icon src="AllIcons.Actions.Execute"/> icon in the gutter.  
public class Main {  
  
    public static void main(String[] args) {  
  
        Scanner scn  = new Scanner(System.in);  
        String s = scn.next();  
        String com = "";  
        int l = 0 , r = s.length() - 1 ;  
        boolean flag = true;  
        while( l < r ){  
            if( s.charAt(l) != s.charAt(r) ){  
                flag = false;  
                break;  
            }  
  
            l++;  
            r--;  
        }  
  
        if(flag == false )  
            System.out.println("It is not palindrome");  
        else  
            System.out.println("It is palindrome ");  
  
        System.out.println(com);  
          
    }  
}
```

