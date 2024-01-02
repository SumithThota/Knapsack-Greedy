# Knapsack-Greedy
Greedy methods are used to solve optimization problems such an example is a knapsack
```
#include <stdio.h>
#include<stdlib.h>
int cap=20,profit=0;;

void swap(int a[],int i,int j)
{
    int t=a[i];
    a[i]=a[j];
    a[j]=t;
}
void swap1(double a[],int i,int j)
{
    float t=a[i];
    a[i]=a[j];
    a[j]=t;
}
void sort(double ip[],int p[],int w[],int size)
{
int i,j;
for(i=0;i<size;i++)
    for(j=i+1;j<size;j++)
        if(ip[i]<ip[j])
        {
            swap1(ip,i,j);
            swap(p,i,j);
            swap(w,i,j);
        }

}

void display(double ip[],int p[],int w[],int size)
{
int i;
    for(i=0;i<size;i++)
        printf("%f\t",ip[i]); 
    printf("\n");
    for(i=0;i<size;i++)
        printf("%d\t",p[i]);
    printf("\n");
    for(i=0;i<size;i++)
        printf("%d\t",w[i]);
    printf("\n%d\t",profit);
}


void knapsack(int p[],int w[],int n)
{
    int i;
    double ip[n];
    for(i=0;i<n;i++)
    {
        ip[i]=p[i]/w[i];
    }
    sort(ip,p,w,n);
    for(i=0;i<n;i++)
    {
        if(w[i]>cap)
        {
            break;
        }
        else
        {
            cap=cap-w[i];
            profit=profit+p[i];
        }
    }
    
    if(i<n)
    {    printf("%d\n",i);
        profit=profit+(ip[i]*cap);
        
    }
    display(ip,p,w,n);
}
int main() 
{
int p[]={54,60,100},w[]={18,15,10};
int size= sizeof(p)/sizeof(p[0]);
knapsack(p,w,size);
    return 0;
}





/*

#include<stdio.h>
int main()
{
     float weight[50],profit[50],ratio[50],Totalvalue,temp,capacity,amount;
     int n,i,j;
     printf("Enter the number of items :");
     scanf("%d",&n);   
    for (i = 0; i < n; i++)
    {
        printf("Enter Weight and Profit for item[%d] :\n",i);
        scanf("%f %f", &weight[i], &profit[i]);
    } 
    printf("Enter the capacity of knapsack :\n");
    scanf("%f",&capacity);
     
     for(i=0;i<n;i++)
         ratio[i]=profit[i]/weight[i];
         
    for (i = 0; i < n; i++) 
      for (j = i + 1; j < n; j++) 
         if (ratio[i] < ratio[j]) 
        {
            temp = ratio[j];
            ratio[j] = ratio[i];
            ratio[i] = temp;
 
            temp = weight[j];
            weight[j] = weight[i];
            weight[i] = temp;
 
            temp = profit[j];
            profit[j] = profit[i];
            profit[i] = temp;
         }
    
     printf("Knapsack problems using Greedy Algorithm:\n");
     for (i = 0; i < n; i++) 
     {
      if (weight[i] > capacity)
          break;
       else 
      {
          Totalvalue = Totalvalue + profit[i];
          capacity = capacity - weight[i];
       }
     } 
       if (i < n)
       Totalvalue = Totalvalue + (ratio[i]*capacity);
     printf("\nThe maximum value is :%f\n",Totalvalue);     
     return 0;
}*/
```
