# C-Program-to-find-Second-smallest-element-in-an-array

Find Second Smallest Element in an Array in C
Today we learn how to Find the Second smallest element in an array with help of the C Programming concept.

second smallest element
Different methods covered in this post
Method 1: Uses two loops find 2nd smallest
Method 2: Uses a single loop to find 2nd smallest
Let’s look at both the methods one by one

second smallest element in array in c
Method 1
Working
We assign min = arr[0]
In loop 1, we find the smallest element in the array
We assign sec_smallest = INT_MAX
In loop 2, we try to find the element with the given condition
(arr[i] != smallest && arr[i] < sec_smallest)
Method Code in C
Run
Run
 
#include <stdio.h>
#include <limits.h>

int secSmallest(int arr[], int n)
{
    // assigning first element as smallest temporarily
    int smallest = arr[0];
    
    // we find the smallest element here
    for (int i=0; i < n; i++){
        if(arr[i] < smallest)
            smallest = arr[i];
    }
    
    // temporarily assinging largest max value
    int sec_smallest = INT_MAX;
    
    // finding second smallest here
    for (int i=0; i < n; i++){
        if(arr[i] != smallest && arr[i] < sec_smallest)
            sec_smallest = arr[i];
    }

    return sec_smallest;
    
}
int main()
{
    int arr[] = {70, 40, 30, 20, 10, 90};
    
    // get the length of the array
    int len = sizeof(arr)/sizeof(arr[0]);    
    
    printf("The 2nd smallest : %d",secSmallest(arr, len));
}
Output
The 2nd smallest : 20
While loop in C
Related Pages
Find Smallest Element in an Array
 
Find the Smallest and largest element in an array

Calculate the sum of elements in an array 

Reverse an Array

Sort first half in ascending order and second half in descending 

Method 2
We try to find smallest and 2nd smallest with variable first and second respectively

Working
first = second = INT_MAX
If the current element being read is the smallest i.e. if (arr[i] < first)
Do second = first, first = arr[i];
else if you’re reading an element that lies between first and second
Do second = arr[i]
Second smallest element in an array in C
Run
Run
#include <stdio.h>
#include <limits.h>

void get2ndSmallest(int arr[], int n)
{
    int i, first, second;
 
    /* The array must have 2 or more items */
    if (n < 2)
    {
        printf(" Array has lesser than 2 items");
        return;
    }
 
    first = second = INT_MAX;
    for (i = 0; i < n ; i ++)
    {
        /* If the current array element is smaller than the first
        then update both first and second */
        if (arr[i] < first)
        {
            second = first;
            first = arr[i];
        }
 
        /* If arr[i] lies between first and second
        then update second */
        else if (arr[i] < second && arr[i] != first)
            second = arr[i];
    }
    if (second == INT_MAX)
        printf("We don't have 2nd smallest item in array\n");
    else
        printf("The 2nd smallest : %d",second);
}
 
int main()
{
    int arr[] = {70, 40, 30, 20, 10, 90};
    int len = sizeof(arr)/sizeof(arr[0]);

    get2ndSmallest(arr, len);

    return 0;
}
Output
The 2nd smallest : 20
