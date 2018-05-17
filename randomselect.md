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

    int randomizedselect(int *a,int p,int r,int i)
    {
        if (p == r)
            return a[p];
        int q = partitionrandom(a,p,r);
        int k = q-p+1;
        if (i == k)
            return a[q];
        else if(i < k)
            return randomizedselect(a,p,q-1,i);
        else 
            return randomizedselect(a,q+1,r,i-k);
    }