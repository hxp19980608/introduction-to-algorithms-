This is the function of insertsort

    void insertsort(int* a,int len)
    {
        for (int j = 1;j < len; j ++)
        {
            int key = a[j];
            int i;
            for (i = j-1;i > -1 && a[i] > key;i --)
                a[i+1] = a[i];
            a[i+1] = key;
        }
    }
    void insertsort(int *a,int len)
    {
        if (len > 1)
        {
            insertsort(a,len-1);
            int pos = len-1;
            for (int i = 0;i < len-1;i ++)
            {
                if (a[i] > a[len-1])
                {   
                    pos = i;
                    break;
                }
            }
            int tmp = a[len-1];
            for (int i = len-1;i > pos;i--)
                a[i] = a[i-1];
            a[pos] = tmp;
        }
    } // recursive version
