```java
import java.util.*;  
//TIP To <b>Run</b> code, press <shortcut actionId="Run"/> or  
// click the <icon src="AllIcons.Actions.Execute"/> icon in the gutter.  
public class Main {  
  
    public static void main(String[] args) {  
        Scanner scn = new Scanner(System.in);  
  
        System.out.println("Input the No. of Row = ");  
        int n = scn.nextInt();  
        System.out.println("\nInput the No of Col = ");  
        int m = scn.nextInt();  
        System.out.println();  
  
        /// initialize the array  
        int[][] a= new int[n][m];  
        System.out.println("Input the Array Element :");  
        for(int i = 0 ; i < n ; i++ )  
        {  
            for(int j = 0 ; j < m ; j++ )  
            {  
                a[i][j] = scn.nextInt();  
            }  
        }  
  
        int s = scn.nextInt();  
        int r = scn.nextInt();  
  
        TwoD_to_OneD_arra(a , s , r);  
  
        Display(a);  
  
    }  
  
    public static void TwoD_to_OneD_arra(int[][] a ,int s ,int r){  
  
        int min_row = s - 1 ;  
        int min_col = s - 1 ;  
        int max_row = a.length - 1 - min_row ;  
        int max_col = a[0].length - 1 - min_col ;  
  
        /// count down start  
        int ele = count(a,min_row , min_col) ;  
       ////System.out.println("Element  =  " + ele);  
  
        int[] one_array = new int[ele] ;  
  
        /// one_array filled with specific shell  
        One_D_filling_from_Two_D(a , one_array , min_row , min_col);  
  
  
  
        ///now rotation  
        if(r>one_array.length)  
         r =  r % one_array.length ;  
  
        if(r<0)  
            r+= one_array.length ;  
  
        int k = one_array.length - 1 - r;  
        reverse( one_array , 0   ,  k);  
        reverse(one_array  , k+1 , one_array.length - 1);  
        reverse(one_array  ,0    ,one_array.length-1);  
  
  
  
        ///after rotation filling specific shell of the Two Dimension Array(a) with this one Dimension array (one_array)  
        One_D_put_data_into_Two_D( a , one_array , min_row , min_col );  
  
    }  
  
    public static void One_D_put_data_into_Two_D( int[][] a , int[] one_d , int min_row , int min_col )  
    {  
        int element = 0 ;  
        int i = one_d.length  ;  
        int max_row = a.length - 1 - min_row ;  
        int max_col = a.length - 1 - min_col;  
        int k = 0 ;  
  
        /// left Wall  
        if( element < i )  
            for (int j = min_row; j <= max_row; j++) {  
                  a[j][min_col] = one_d[k++] ;  
                ++element;  
            }  
  
  
  
        /// Bottom Wall  
        if( element < i )  
            for (int j = min_col + 1; j <= max_col; j++) {  
                  a[max_row][j]=one_d[k++] ;  
                ++element;  
            }  
  
  
  
        /// Right Wall  
        if( element < i )  
            for (int j = max_row - 1; j >= min_row; j--) {  
                 a[j][max_col]=one_d[k++] ;  
                ++element;  
            }  
  
  
        /// Top Wall  
        if( element < i )  
            for (int j = max_col - 1; j >= min_col + 1; j--) {  
  
                a[min_row][j]= one_d[k++]  ;  
                ++element;  
            }  
    }  
  
    public static void reverse(int[] a ,int left , int right){  
        while( left < right )  
        {  
            int temp = a[left];  
            a[left] = a[right] ;  
            a[right] = temp ;  
  
            left++;  
            right--;  
        }  
    }  
  
    public static void One_D_filling_from_Two_D(int[][] a , int[] one_d , int min_row ,int min_col)  
    {  
        int element = 0 ;  
        int i = one_d.length  ;  
        int max_row = a.length - 1 - min_row ;  
        int max_col = a.length - 1 - min_col;  
        int k = 0 ;  
        /// left Wall  
        if( element < i ) {  
            for (int j = min_row; j <= max_row; j++) {  
               one_d[k++] = a[j][min_col] ;  
                ++element;  
            }  
  
        }  
  
        /// Bottom Wall  
        if( element < i ) {  
            for (int j = min_col + 1; j <= max_col; j++) {  
                one_d[k++] = a[max_row][j] ;  
                ++element;  
            }  
  
        }  
  
        /// Right Wall  
        if( element < i ) {  
            for (int j = max_row - 1; j >= min_row; j--) {  
                one_d[k++] = a[j][max_col] ;  
                ++element;  
            }  
  
        }  
  
        /// Top Wall  
        if( element < i ) {  
            for (int j = max_col - 1; j >= min_col + 1; j--) {  
  
                one_d[k++] = a[min_row][j] ;  
                ++element;  
            }  
  
        }  
  
    }  
  
    public static int count(int[][] a , int min_row , int min_col)  
    {  
        int max_row = a.length - 1 - min_row;  
        int max_col = a[0].length - 1 - min_col;  
        int ele  ;  
  
        if(max_row == min_row ){  
            ele = max_col - min_col + 1 ;  
  
        }  
        else if(max_col == min_col ){  
            ele = max_row - min_row + 1 ;  
  
        }  
        else {  
            ele = 2*( max_row - min_row +1 ) + 2*( max_col - min_col - 1 );  
        }  
  
        return ele ;  
    }  
  
    public static void Display(int[][] a){  
  
        int max_row = a.length - 1;  
        int max_col = a[0].length - 1 ;  
  
        int min_row = 0 ;  
        int min_col = 0 ;  
  
        int i = ( max_row + 1 ) * ( max_col + 1 );  
        int element = 0 ;  
        while ( element < i ){  
  
            /// left Wall  
            if( element < i ) {  
                for (int j = min_row; j <= max_row; j++) {  
                    System.out.print(a[j][min_col] + " ");  
                    ++element;  
                }  
                System.out.println();  
            }  
  
            /// Bottom Wall  
            if( element < i ) {  
                for (int j = min_col + 1; j <= max_col; j++) {  
                    System.out.print(a[max_row][j] + " ");  
                    ++element;  
                }  
                System.out.println();  
            }  
  
            /// Right Wall  
            if( element < i ) {  
                for (int j = max_row - 1; j >= min_row; j--) {  
                    System.out.print(a[j][max_col] + " ");  
                    ++element;  
                }  
                System.out.println();  
            }  
  
            /// Top Wall  
            if( element < i ) {  
                for (int j = max_col - 1; j >= min_col + 1; j--) {  
  
                    System.out.print(a[min_row][j] + " ");  
                    ++element;  
                }  
                System.out.println();  
            }  
  
            min_row++;  
            max_row--;  
            min_col++;  
            max_col--;  
  
        }  
  
    }  
  
}
```


