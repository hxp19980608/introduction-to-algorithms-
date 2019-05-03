This is the code of mergesort
    
    void merge(int *a,int p,int q,int r)
    {
        for (int i = q+1;i <= r;i ++)
        {
            int key = a[i];
            int pos = p-1;
            int j;
            for (j = i-1;j > pos && a[j] > key;j --)
                a[j+1] = a[j];
            pos = j+1;
            a[j+1] = key;
        }
    }   // put two sorted subarray together
  
    void mergesort(int *a,int p,int r)
    {
        if (p < r)
        {
            int q = (p+r)/2;
            mergesort(a,p,q);
            mergesort(a,q+1,r);
            merge(a,p,q,r);
        }
    }
