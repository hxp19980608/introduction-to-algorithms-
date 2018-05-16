    #include <iostream>
    #define ll long long
    #define For(i,a,b) for(int (i)=(a);(i) < (b); ++(i))
    #define roF(i,a,b) for(int (i)=(a);(i) > (b); --(i))
    using namespace std;

    int a[100010];
    int b[100010];
    void countsort(int *a,int len,int *b,int k)
    {
        int c[100010];
        For(i,0,k+1)
            c[i] = 0;
        For(j,1,len+1)
            c[a[j]] ++;
        For(i,1,k+1)
            c[i] = c[i] + c[i-1];
        roF(j,len,0)
        {
            b[c[a[j]]] = a[j];
            c[a[j]] --;
        }
    }