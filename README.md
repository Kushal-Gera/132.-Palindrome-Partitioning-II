# 132.-Palindrome-Partitioning-II
class Solution {
public:
    bool check(string &s, int start, int end)
    {
        while(start<end)
        {
            if(s[start++]!=s[end--])
            {
                return 0;
            }
        }
        return 1;
    }
    int minCut(string s) {
        
        int *arr=new int[s.size()+1];
        for(int i=0;i<=s.size();i++)
        {
            arr[i]=INT_MAX;
        }
        
        arr[s.size()-1]=0;
        arr[s.size()]=0;
        
        for(int i=s.size()-2;i>=0;i--)
        {
            for(int j=i;j<s.size();j++)
            {
                if(check(s,i,j))
                {
                    if(j==s.size()-1)
                    {
                        arr[i]=0;
                        break;
                    }
                    int x = 1 + arr[j+1];
                    if(x<arr[i])
                    {
                        arr[i]=x;
                    }
                }
                
            }
            
        }
        return arr[0];
        
        
    }
};
