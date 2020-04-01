# N-queen-problem-code
CODE OF N-QUEEN PROBLEM IN C++
////////////////////////////////



































#include<bits/stdc++.h>
using namespace std;
bool issafe(int a[][10],int i,int j,int n)
{
	//check column
	for(int r=0;r<i;r++)
	{
		if(a[r][j]==1)
		{
			return false;
		}
	}
	//check left diagonal
	int x=i,y=j;
	while(x>=0&&y>=0)
	{
		if(a[x][y]==1)
		return false;
		x--;
		y--;
	}
	int h=i,k=j;
	while(h>=0&&k<n)
	{
		if(a[h][k]==1)
		return false;
		h--;
		k++;
	}
	return true;
}
bool print(int a[][10],int i,int n)
{
	if(i==n)
	{
		for(int i=0;i<n;i++)
		{
			for(int j=0;j<n;j++)
			{
				if(a[i][j]==1)
				{
					cout<<"Q ";
				}
				else
				{
					cout<<"- ";
				}
			}
			cout<<endl;
		}
		
		return true;
	}
	for(int j=0;j<n;j++)
	{
			if(issafe(a,i,j,n))
			{
				a[i][j]=1;
				bool nextqn=print(a,i+1,n);
			if(nextqn)
			{
				return true;
			}
				//assumption wrong	
				a[i][j]=0;
			
			}
	}
	return false;

}
int main()
{
	int a[10][10]={0};
	print(a,0,4);
}
