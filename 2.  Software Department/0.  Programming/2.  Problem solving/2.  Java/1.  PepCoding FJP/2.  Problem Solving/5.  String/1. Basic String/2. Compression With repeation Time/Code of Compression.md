```java 
import java.util.*;  
//TIP To <b>Run</b> code, press <shortcut actionId="Run"/> or  
// click the <icon src="AllIcons.Actions.Execute"/> icon in the gutter.  
public class Main {  
  
    public static void main(String[] args) {  
  
        Scanner scn  = new Scanner(System.in);  
  
        String s = scn.next();  
        scn.nextLine();  
        String com ="";  
        int count = 1 ;  
        int i = 0;  
  
        for( i = 0 ; i < s.length() - 1 ;  i++ )  
        {  
            if( s.charAt(i) == s.charAt(i+1) ){  
                count++;  
            }  
            else{  
                System.out.println(" "+s.charAt(i) + count);  
                com += s.charAt(i);  
                com += count;  
                count = 1 ;  
  
            }  
  
        }  
  
       com+=s.charAt(s.length() - 1 );  
        com+=count;  
  
        System.out.println(com);  
  
  
    }  
}
```