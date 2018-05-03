This is the code of mergesort
    
    int L[100010];
    int R[100010];

    void merge(int *a,int p,int q,int r)
    {
        int n1 = q-p+1,n2 = r-q;    
        for (int i = 1;i <= n1;i ++)
            L[i] = a[p+i-1];
        for (int i = 1;i <= n2;i ++)
            R[i] = a[q+i];
        int i = 1,j = 1;
        for (int k = p;k <= r;k ++)
        {
            if(i > n1 || j > n2)
            {
                if (i > n1)
                    a[k] = R[j++];
                else if (j > n2)
                    a[k] = L[i++];
            }   
            else
            {
                if (L[i] <= R[j])
                    a[k] = L[i++];
                else
                    a[k] = R[j++];
            }
        }
    }     // merge two sorted subarray 

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
