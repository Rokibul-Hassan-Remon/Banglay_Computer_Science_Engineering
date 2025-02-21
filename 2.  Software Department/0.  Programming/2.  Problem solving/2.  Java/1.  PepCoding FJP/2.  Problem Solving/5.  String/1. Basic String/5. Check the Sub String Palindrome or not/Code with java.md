```java
import java.util.*;  
//TIP To <b>Run</b> code, press <shortcut actionId="Run"/> or  
// click the <icon src="AllIcons.Actions.Execute"/> icon in the gutter.  
public class Main {  
  
    public static void main(String[] args) {  
  
        Scanner scn  = new Scanner(System.in);  
        String s = scn.nextLine();  
        String com = "";  
  
        for(int i = 0 ; i < s.length() ; i++ ){  
            for(int j = i ; j < s.length()  ; j++ )  
            {  
                com = "";  
                /// making the sub-string  
                for(int k = i ; k <= j ; k++ ){  
                    com += s.charAt(k) ;  
                }  
  
                ///checking sub-string is palindrome or not  
                boolean flag_palindrome = true;  
                int l = 0 , r = com.length() - 1 ;  
                while( l < r ){  
                    if( com.charAt(l) != com.charAt(r) ){  
                        flag_palindrome = false;  
                        break;  
                    }  
  
                    l++;  
                    r--;  
                }  
                if(flag_palindrome)  
                    System.out.println(com);  
  
            }  
        }  
  
  
  
    }  
}
```

