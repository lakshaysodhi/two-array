# two-array
Copy
#include <bits/stdc++.h>
using namespace std;
#define ll long long
 
 
 
int main()
{
 
    int t;
    cin>>t;
    while(t--){
 
        int n,sum;
        cin>>n>>sum;
        vector<int> A(n);
        unordered_map<int,int> mark;
        unordered_map<int,int> couple;
        for(int i=0;i<n;i++){
            cin>>A[i];
            mark[A[i]]++;
        }
        vector<int> ans(n);
 
        for(int i=0;i<n;i++){
            if(sum-A[i]==A[i]){
                couple[A[i]]=mark[A[i]];
                mark[A[i]]=-2;
            }else if(mark.count(sum-A[i])!=0){
                if(mark[A[i]]>0)
                mark[sum-A[i]]=-1;
            }
        }
        for(int i=0;i<n;i++){
            if(mark[A[i]]>0){
                ans[i]=1;
            }else if(mark[A[i]]==-1){
                ans[i]=0;
            }else if(mark[A[i]]==-2){
                if(couple[A[i]]%2==0){
                    ans[i]=1;
                    couple[A[i]]--;
                }else{
                    ans[i]=0;
                    couple[A[i]]--;
                }
            }
        }
        for(int i=0;i<n;i++){
            cout<<ans[i]<<" ";
        }
        cout<<endl;
    }
    return 0;
}
 
 the above solution is tough easy one down
 
 
 #include <bits/stdc++.h>
using namespace std;
#define ll long long


int main()
{

    int t;
    cin>>t;
    while(t--){

        int n,sum;
        cin>>n>>sum;
        vector<int> A(n);
        vector<int> less;
        vector<int> equal;
        vector<int> greater;
        for(int i=0;i<n;i++){
            cin>>A[i];
            if(sum%2==0){
                if(A[i]<sum/2) less.push_back(i);
                else if(A[i]>sum/2) greater.push_back(i);
                else if(A[i]==sum/2) equal.push_back(i);
            }else{
                if(A[i]<=sum/2) less.push_back(i);
                else if(A[i]>sum/2) greater.push_back(i);
            }
        }
        vector<int> ans(n);
        for(int i=0;i<less.size();i++){
            ans[less[i]]=1;
        }
        for(int i=0;i<greater.size();i++){
            ans[greater[i]]=0;
        }
        for(int i=0;i<equal.size();i++){
            if(i%2==0) ans[equal[i]]=1;
            else ans[equal[i]]=0;
        }
        for(int i=0;i<n;i++){
            cout<<ans[i]<<" ";
        }
        cout<<endl;

    }
    return 0;

}




 
 
 
