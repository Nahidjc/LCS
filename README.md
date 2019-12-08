# LCS
#include<stdio.h>
#include<string.h>
 
int i,j,m,n,c[20][20],s=0;
char x[20],y[20],b[20][20];
 
void display(int i,int j)
{
    if(i==0 || j==0)
        return;
    if(b[i][j]=='P')
    {
        display(i-1,j-1);
        printf("%c",x[i-1]);
       
    }
    else if(b[i][j]=='Q')
        display(i-1,j);
    else
        display(i,j-1);
 
     
}
 
void lcs()
{
    m=strlen(x);
    n=strlen(y);
    for(i=0; i<=m; i++)
        c[i][0]=0;
    for(j=0; j<=n; j++)
        c[0][j]=0;
 
 
    for(i=1; i<=m; i++)
        for(j=1; j<=n; j++)
        {
            if(x[i]==y[j])
            {
                c[i][j]=c[i-1][j-1]+1;
                b[i][j]='P';
            }
            else if(c[i-1][j]>=c[i][j-1])
            {
                c[i][j]=c[i-1][j];
                b[i][j]='Q';
            }
            else
            {
                c[i][j]=c[i][j-1];
                b[i][j]='R';
            }
        }
}
 
int main()
{
    printf("Enter 1st sequence:");
    scanf("%s",x);
    printf("Enter 2nd sequence:");
    scanf("%s",y);
    printf("The Longest Common Subsequence is ");
    lcs();
   display(m,n);
    return 0;
}
