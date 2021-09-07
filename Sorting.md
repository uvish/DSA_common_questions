**Selection Sort**
```java
public class Main {
    public static void main(String[] args) {
        int temp;
        int[] a={9,2,4,6,-7,10,1};
        for(int i=0;i<a.length-1;i++){
            for(int j=i;j<a.length;j++){
                if(a[j]<a[i]){
                    temp=a[i];
                    a[i]=a[j];
                    a[j]=temp;
                }
            }
        }
        
        for(int i=0;i<a.length-1;i++){
         System.out.println(a[i]);     
            }
    }
}
```

**Bubble Sort**
```java
public class Main {
    public static void main(String[] args) {
        int temp;
        int[] a={9,2,4,6,-7,10,1};
        for(int i=0;i<a.length-1;i++){
            for(int j=0;j<a.length-i-1;j++){
                if(a[j]>a[j+1]){
                    temp=a[j];
                    a[j]=a[j+1];
                    a[j+1]=temp;
                }
            }
        }
        
        for(int i=0;i<a.length;i++){
         System.out.println(a[i]);     
            }
    }
}
```

**Insertion Sort**
```java
void sort(int arr[])
    {
        int n = arr.length;
        for (int i = 1; i < n; ++i) {
            int key = arr[i];
            int j = i - 1;

            while (j >= 0 && arr[j] > key) {
                arr[j + 1] = arr[j];
                j = j - 1;
            }
            arr[j + 1] = key;
        }
    }
```