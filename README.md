# -Interpolation-Polynomial-Approximation-In-C
this code is written in C language.


Source: Covid-19 Turkey Daily Data from Ministry of Health of Turkey https://covid19bilgi.saglik.gov.tr/tr/gunluk-vaka.html

Using only the case numbers of days March 12, March 16, March 20, March 23, March 26, March 29, April 3, April 8, April 13, April 18, April 20 and April 21:

1-> the number of cases on April 15 using Direct Method Interpolation. 2-> the number of cases on April 15 using Lagrange Interpolation Polynomial. 3-> the number of cases on April 15 using Newton’s Divided Difference Interpolation.


---------------------------------------------------------------------------------------







//DirectMethodInterpolationsCode
#include<stdio.h>
#include<conio.h>

int main()
{
 float x0,y0,x1,y1,xp,yp;

 

 /* Inputs */
 printf("Enter first point (x0,y0):\n");
 scanf("%f%f",&x0,&y0);
 printf("Enter second point (x1,y1):\n");
 scanf("%f%f",&x1,&y1);
 printf("Enter interpolation point: ");
 scanf("%f", &xp);

 /* Calculation */
 yp = y0 + ((y1-y0)/(x1-x0)) * (xp - x0);
 printf("Interpolated value at %0.3f is %0.3f", xp, yp);
 getch();
 return 0;
}

 ---------------------------------------------------------------------------------------
 // Lagrange Interpolation Polynomial In C code.
 #include<stdio.h>
#include<conio.h>

void main()
{
	 float x[100], y[100], xp, yp=0, p;
	 int i,j,n;
	
	 /* Input Section */
	 printf("Enter number of data: ");
	 scanf("%d", &n);
	 printf("Enter data:\n");
	 for(i=1;i<=n;i++)
	 {
		  printf("x[%d] = ", i);
		  scanf("%f", &x[i]);
		  printf("y[%d] = ", i);
		  scanf("%f", &y[i]);
	 }
	 printf("Enter interpolation point: ");
	 scanf("%f", &xp);
	 /* Implementing Lagrange Interpolation */
	 for(i=1;i<=n;i++)
	 {
		  p=1;
		  for(j=1;j<=n;j++)
		  {
			   if(i!=j)
			   {
			    	p = p* (xp - x[j])/(x[i] - x[j]);
			   }
		  }
		  yp = yp + p * y[i];
	 }
	 printf("Interpolated value at %.3f is %.3f.", xp, yp);
	 getch();
}


--------------------------------------------------------------------------------

//Newton’s Divided Difference Interpolation In C Code.
#include<stdio.h>
#include<conio.h>
 
void main()
{
    int x[10], y[10], p[10];
    int k,f,n,i,j=1,f1=1,f2=0;
    printf("\nEnter the number of observations:\n");
    scanf("%d", &n);
 
    printf("\nEnter the different values of x:\n");
    for (i=1;i<=n;i++)
        scanf("%d", &x[i]);
 
    printf("\nThe corresponding values of y are:\n");
    for (i=1;i<=n;i++)
        scanf("%d", &y[i]);
 
    f=y[1];
    printf("\nEnter the value of 'k' in f(k) you want to evaluate:\n");
    scanf("%d", &k);
 
    do
    {
        for (i=1;i<=n-1;i++)
        {
            p[i] = ((y[i+1]-y[i])/(x[i+j]-x[i]));
            y[i]=p[i];
        }
        f1=1;
        for(i=1;i<=j;i++)
            {
                f1*=(k-x[i]);
            }
        f2+=(y[1]*f1);
        n--;
        j++;
    }
 
    while(n!=1);
    f+=f2;
    printf("\nf(%d) = %d", k , f);
    getch();
}

