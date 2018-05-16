    #include <iostream>
    #define ll long long
    #define For(i,a,b) for(int (i)=(a);(i) < (b); ++(i))
    #define roF(i,a,b) for(int (i)=(a);(i) > (b); --(i))
    using namespace std;
    int a[100010];
        
    int parent(int i)
    {
    return i/2;
    } 

    int left(int i)
    {
    return 2*i;
    }

    int right(int i)
    {
        return 2*i+1;
    }

    void swap(int &a,int &b)
    {
    int tmp = a;
    a = b;
    b = tmp;
    }

    void maxheapify(int *a,int i,int heapsize)
    {
        int l = left(i),r = right(i);
        int largest = i;
        if (l <= heapsize && a[l] > a[i])
            largest = l;
        if(r <= heapsize && a[r] > a[largest])
            largest = r;
        if (largest != i)
        {
            swap(a[i],a[largest]);
            maxheapify(a,largest,heapsize);
        }
    }
            
    void buildmaxheap(int *a,int n,int heapsize)
    {
        roF(i,n/2,0)
            maxheapify(a,i,heapsize);
    }

    void heapsort(int *a,int n)
    {
        int heapsize = n;
        buildmaxheap(a,n,heapsize);
        For(i,1,n+1)
            cout << a[i] << " ";
        cout << endl;
        roF(i,n,1)
        {
            swap(a[1],a[i]);
            heapsize --;
            maxheapify(a,1,heapsize);
        }
    }                               