```java 
import java.util.*;  
 
public class Main {  
    public static void main(String[] args) {  
        Scanner scn = new Scanner(System.in);  
        int n = scn.nextInt();  
        int[] arr = new int[n];  
  
        for (int i = 0; i < n; i++) {  
            arr[i] = scn.nextInt();  
        }  
  
        int k = scn.nextInt();  
                                ///4 5 6 3 2 k=3  
        k = k % n ;  
		if(k<0) k+= n;
		
        if(k > 0 ){  
            rotate(arr , 0 , (n-k)-1 );  
            rotate(arr,  (n-k) , n-1) ;  
            rotate(arr,0 , n-1);  
        }  
  
        for(int j = 0 ; j<n ;j++ )  
            System.out.print(arr[j]+" ");  
  
        System.out.println();  
    }  
  
    public static void rotate(int[] arr , int str , int lst) {  
        while (str < lst) {  
            int temp = arr[str];  
            arr[str] = arr[lst];  
            arr[lst] = temp;  
            str++;  
            lst--;  
        }  
  
    }  
  
}
```

