    #include <iostream>
    #include <ctime>
    #define ll long long
    #define For(i,a,b) for(int (i)=(a);(i) < (b); ++(i))
    #define roF(i,a,b) for(int (i)=(a);(i) > (b); --(i))    
    #define random(a,b) (rand()%(b-a+1)+a)
    using namespace std;

        void swap(int &a,int &b)
    {
        int tmp = a;
        a = b;
        b = tmp;
    }

    int partition(int *a,int l,int r)
    {
        int x = a[r];
        int i = l - 1;
        For(j,l,r)
        {
            if (a[j] <= x)
            {
                i++;
                swap(a[i],a[j]);
            }
        }
    swap(a[i+1],a[r]);
    return i+1;
    }     //original version partition

    void quicksort(int *a,int l,int r)
    {
        if (l < r)
        {
            int q = partition(a,l,r);
            quicksort(a,l,q-1);
            quicksort(a,q+1,r);
        }
    }  //original version quicksort



    int partitionrandom(int *a,int l,int r)
    {
        int m = random(l,r);
        swap(a[r],a[m]);
        int x = a[r];
        int i = l - 1;
        For(j,l,r)
        {
            if (a[j] <= x)
            {
                i++;
                swap(a[i],a[j]);
            }
        }
    swap(a[i+1],a[r]);
    return i+1;
    }
    void quicksortrandom(int *a,int l,int r)
    {
        if (l < r)
        {
            int q = partitionrandom(a,l,r);
            quicksortrandom(a,l,q-1);
            quicksortrandom(a,q+1,r);
        }
    } // random version      