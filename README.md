Block swap algorithm for array rotation
Here in this program we will be learning about Block swap algorithm. It is one of the most efficient algorithms used for array rotation. Now, let’s discuss about block swap algorithm and a program to rotate an array using the same algorithm.

Block swap algorithm in Java
Method Discussed :
Method 1 : Recursive Way
Method 2 : Iterative Way
Method 1 :
Declare two arrays A and B,
Copy all the elements from index 0 to (d-1) to A[] and from index d to n-1 to B[].
Run a loop till size of array A is equal to size of B[].
If A is longer, divide A into Al and Ar such that Al is of same length as B Swap Al and B to change AlArB into BArAl.
Now B is at its final place, so recur on pieces of A. 
Finally when A and B are of equal size, block swap them.
Method 1 : Code in Java
//Write a program for block swap algorithm in Java
import java.util.*;
 
class Main
{

    public static void leftRotate(int arr[], int d, int n)
    {
        leftRotateRec(arr, 0, d, n);
    }
 
    public static void leftRotateRec(int arr[], int i, int d, int n)
    {

        if(d == 0 || d == n)
            return;
         
        if(n - d == d){
            swap(arr, i, n - d + i, d);
            return;
        }
        
        if(d < n - d){
            swap(arr, i, n - d + i, d);
            leftRotateRec(arr, i, d, n - d);    
        }
        else{
            swap(arr, i, d, n - d);
            leftRotateRec(arr, n - d + i, 2 * d - n, d);
        }
    }
 
    public static void swap(int arr[], int fi, int si, int d){
        int i, temp;
        
        for(i = 0; i < d; i++){
            temp = arr[fi + i];
            arr[fi + i] = arr[si + i];
            arr[si + i] = temp;
        }
    }
 
    public static void main (String[] args){
        int arr[] = {10, 20, 30, 40, 50, 60, 70};
        leftRotate(arr, 2, 7);
    
        for( int i = 0; i < 7; i++)
            System.out.print(arr[i] + " ");
    }
}
Output
30 40 50 60 70 10 20
Method 2 :
In this method we implement the iterative approach for the algorithm discussed in method 1.

Method 2 : Code in Java
//Write a program for block swap algorithm in Java
import java.util.*;
 
class Main
{

    public static void leftRotate(int arr[], int d, int n)
    {
        leftRotateRec(arr, 0, d, n);
    }
 
    public static void leftRotate(int arr[], int d, int n){
        int i, j;
        if(d == 0 || d == n)
            return;

        if(d > n)
            d = d % n;
        i = d;
        j = n - d;
    
        while (i != j){
            if(i < j){
                swap(arr, d-i, d+j-i, i);
                j -= i;
            }
            else{
                swap(arr, d-i, d, j);
                i -= j;
            }
   
        }
        swap(arr, d-i, d, i);
    }
 
    public static void swap(int arr[], int fi, int si, int d){
        int i, temp;
        
        for(i = 0; i < d; i++){
            temp = arr[fi + i];
            arr[fi + i] = arr[si + i];
            arr[si + i] = temp;
        }
    }
 
    public static void main (String[] args){
        int arr[] = {10, 20, 30, 40, 50, 60, 70};
        leftRotate(arr, 2, 7);
    
        for( int i = 0; i < 7; i++)
            System.out.print(arr[i] + " ");
    }
}
Output
30 40 50 60 70 10 20
