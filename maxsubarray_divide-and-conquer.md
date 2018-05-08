    void findmaxcrossarray(int *a,int beg,int mid,int end,int& start,int& stop,int& maxsum)
    {
        int leftsum = INT_MIN;
        int sum = 0;
        for (int i = mid;i >= beg;i --)
        {
            sum += a[i];
            if (sum > leftsum)
            {
                start = i;
                leftsum = sum;
            }
        }
        sum = 0;
        int rightsum = INT_MIN;
        for (int i = mid+1;i <= end;i ++)
        {
            sum += a[i];
            if (sum > rightsum)
            {
                stop = i;
                rightsum = sum;
            }
        }
        maxsum = rightsum + leftsum;
    } // function to find the cross maxsubarray


    void findmaxsubarray(int *a,int beg,int end,int& start,int& stop,int &maxsum)
    {
        if (beg == end)
        {
            start = beg;
            stop = beg;
            maxsum = a[beg];
        }
        else
        {
            int mid = (beg+end)/2;
            int left_start,left_end,left_sum;
            findmaxsubarray(a,beg,mid,left_start,left_end,left_sum);
            int right_start,right_end,right_sum;
            findmaxsubarray(a,mid+1,end,right_start,right_end,right_sum);
            int cross_start,cross_end,cross_sum;
            findmaxcrossarray(a,beg,mid,end,cross_start,cross_end,cross_sum);
            if (left_sum >= right_sum && left_sum >= cross_sum)
            {
                start = left_start;
                stop = left_end;
                maxsum = left_sum;
            }
            else if(right_sum >= left_sum && right_sum >= cross_sum)
            {
                start = right_start;
                stop = right_end;
                maxsum = right_sum;
            }
            else if(cross_sum >= left_sum && cross_sum >= right_sum)
            {
                start = cross_start;
                stop = cross_end;
                maxsum = cross_sum;
            }
        }
    }// function to find the maxsubarray 