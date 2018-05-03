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