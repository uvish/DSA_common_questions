**Maximum Product Triplet**

_maximum possible product between 3 number_
```java
// Java program to find a maximum product of a
// triplet in array of integers

import java.util.Arrays;

class GFG {

	/* Function to find a maximum product of a triplet
in array of integers of size n */
	static int maxProduct(int arr[], int n) {
		// if size is less than 3, no triplet exists
		if (n < 3) {
			return -1;
		}

		// Sort the array in ascending order
		Arrays.sort(arr);  // nlogn QuickSort

		// Return the maximum of product of last three
		// elements and product of first two elements
		// and last element
		return Math.max(arr[0] * arr[1] * arr[n - 1],
				arr[n - 1] * arr[n - 2] * arr[n - 3]);
	}

// Driver program to test above functions
	public static void main(String[] args) {
		int arr[] = {-10, -3, 5, 6, -20};
		int n = arr.length;

		int max = maxProduct(arr, n);

		if (max == -1) {
			System.out.println("No Triplet Exists");
		} else {
			System.out.println("Maximum product is " + max);
		}

	}
}

```

**Longest Common Substring**
```java
class GFG {
	static int LCSubStr(char X[], char Y[],
						int m, int n)
	{
		int LCStuff[][] = new int[m + 1][n + 1];
		int result = 0;
		for (int i = 0; i <= m; i++)
		{
			for (int j = 0; j <= n; j++)
			{
				if (i == 0 || j == 0)
					LCStuff[i][j] = 0;
				else if (X[i - 1] == Y[j - 1])
				{
					LCStuff[i][j]= LCStuff[i - 1][j - 1] + 1;
					result = Integer.max(result,LCStuff[i][j]);
				}
				else
					LCStuff[i][j] = 0;
			}
		}
		return result;
	}

	public static void main(String[] args)
	{
		String X = "OldSite:GeeksforGeeks.org";
		String Y = "NewSite:GeeksQuiz.com";
		int m = X.length();
		int n = Y.length();
		System.out.println(LCSubStr(X.toCharArray(),Y.toCharArray(), m,n));
	}
}
```

**Longest Common Subsequence**
```java
public class LongestCommonSubsequence
{

int lcs( char[] X, char[] Y, int m, int n )
{
	int L[][] = new int[m+1][n+1];
	for (int i=0; i<=m; i++)
	{
	for (int j=0; j<=n; j++)
	{
		if (i == 0 || j == 0)
			L[i][j] = 0;
		else if (X[i-1] == Y[j-1])
			L[i][j] = L[i-1][j-1] + 1;
		else
			L[i][j] = max(L[i-1][j], L[i][j-1]);
	}
	}
return L[m][n];
}

int max(int a, int b)
{
	return (a > b)? a : b;
}

public static void main(String[] args)
{
	LongestCommonSubsequence lcs = new LongestCommonSubsequence();
	String s1 = "AGGTAB";
	String s2 = "GXTXAYB";

	char[] X=s1.toCharArray();
	char[] Y=s2.toCharArray();
	int m = X.length;
	int n = Y.length;

	System.out.println("Length of LCS is" + " " +
								lcs.lcs( X, Y, m, n ) );
}

}
```