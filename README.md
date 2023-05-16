# Assignment
#include <iostream>

using namespace std;

#include <iostream>
 #include <vector>


using namespace std;

class maxvalue
{
   public:
   int Rank(int n,vector<vector<int>> cable )// max degree b/w n array n*n
   {
       int links[100][100]={0};//link b/w same lab rank 0
       int deg[100] = {0};
       for (auto r : cable)
       {
           links[r[0]][r[1]]=1;// bidirectional link b/w two nodes 
           links[r[0]][r[0]]=1;
           deg[r[0]]++;// when it conned to different lab rank will increase
           deg[r[1]]++;
       }
       int res = 0; // intialy consider rank 0
       for(int i=0;i<100;i++) //arry[i]th elemets
       {
           for(int j=0;j<100;j++)// array[j]th elemets 
           {
               if(i != 0)// a != b
               {
                   int value = deg[i]+deg[j];
                   if(links[i][j])//a = b
                   value--;
                   res = max(res, value);// max rank
               }
           }
       }
       cout<<"res"<<res<<ends;
      
       return 0;
       
   }
};
