# FatMouse-Trade

FatMouse' Trade

Problem Description

FatMouse prepared M pounds of cat food, ready to trade with the cats guarding the warehouse containing his favorite food, JavaBean.
The warehouse has N rooms. The i-th room contains J[i] pounds of JavaBeans and requires F[i] pounds of cat food. FatMouse does not have to trade for all the JavaBeans in the room, instead, he may get J[i]* a% pounds of JavaBeans if he pays F[i]* a% pounds of cat food. Here a is a real number. Now he is assigning this homework to you: tell him the maximum amount of JavaBeans he can obtain.


Input

The input consists of multiple test cases. Each test case begins with a line containing two non-negative integers M and N. Then N lines follow, each contains two non-negative integers J[i] and F[i] respectively. The last test case is followed by two -1's. All integers are not greater than 1000.


Output

For each test case, print in a single line a real number accurate up to 3 decimal places, which is the maximum amount of JavaBeans that FatMouse can obtain.


Sample Input

5 3 7 2 4 3 5 2 20 3 25 18 24 15 15 10 -1 -1


Sample Output

13.333 31.500

代码：

#include<stdio.h>

#include<string.h>

#define MAX 1000

int main()

{

    int i,j,m,n,temp;
    
    int J[MAX],F[MAX];
    
    double P[MAX];
    
    double sum,temp1;
    
    scanf("%d%d",&m,&n);
    
    while(m!=-1&&n!=-1)
    
    {
   
        sum=0;
        
        memset(J,0,MAX*sizeof(int));
        
        memset(F,0,MAX*sizeof(int));
        
        memset(P,0,MAX*sizeof(double));
        
        for(i=0;i<n;i++){ scanf("%d%d",&J[i],&F[i]);   P[i]=J[i]*1.0/((double)F[i]); }    
        
        for(i=0;i<n;i++)        
        
        {
        
            for(j=i+1;j<n;j++)
            
            {
            
                if(P[i]<P[j])
                
                {
                
                    temp1=P[i];  P[i]=P[j];   P[j]=temp1;
                    
                    temp=J[i];   J[i]=J[j];    J[j]=temp;
                    
                    temp=F[i];   F[i]=F[j];   F[j]=temp;
                    
                }
                
            }
            
        }
        
        for(i=0;i<n;i++)
        
        {
        
            if(m<F[i]){   sum+=m/((double)F[i])*J[i];    break;    }
            
            else     {   sum+=J[i];                  m-=F[i];   }
                       
        }
        
        printf("%.3lf\n",sum);   scanf("%d%d",&m,&n);    
        
    }
    
    return 0;
    
}
