#include<stdio.h>
#include<stdlib.h>
// To heapify a subtree rooted with node i which is
// an index in arr[]. n is size of heap
void maxheapify(int a[], int n, int i)
{
	int largest = i; // Initialize largest as root
	int l = 2*i + 1; // left = 2*i + 1
	int r = 2*i + 2; // right = 2*i + 2

	// If left child is larger than root
	if (l < n && a[l] > a[largest])
		largest = l;

	// If right child is larger than largest so far
	if (r < n && a[r] > a[largest])
		largest = r;

	// If largest is not root
	if (largest != i)
	{
	  int t=a[i];
	  a[i]=a[largest];
	  a[largest]=t;
		// Recursively heapify the affected sub-tree
		maxheapify(a, n, largest);
	}
}

// main function to do heap sort
	// Build heap (rearrange array)
    void 	buildmaxheap(int a[],int n){
	for (int i = n / 2 - 1; i >= 0; i--)
		maxheapify(a, n, i);
	}
	void heapsort(int a[], int n){
    buildmaxheap(a,n);
	// One by one extract an element from heap
	for (int i=n-1; i>=0; i--)
	{
		// Move current root to end
		int t=a[0];
		a[0]=a[i];
		a[i]=t;
		// call max heapify on the reduced heap
		maxheapify(a, i, 0);
	}
}

/* A utility function to print array of size n */
// Driver program
int main()
{
	int a[100];
	int i;
	int n;
	scanf("%d",&n);
	for(i=0;i<n;i++)
	scanf("%d",&a[i]);
	heapsort(a, n);
	for(i=0;i<n;i++)
	printf("%d ",a[i]);
	return 0;
}
