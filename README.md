## EX 5 : TWO DIMENSIONALTRANSFORMATION 

NAME: VIJAYAKUMAR S

REG NO: 212224040359

**AIM**

To write a c program to implement 2D transformation of image.


**ALGORITHM**

Step 1:Start the program.

Step 2:Draw the image with default parameters.

Step 3 : Get the choice from the user.

Step 4: Get the parameters for transformation.

Step 5 : Perform the transformation.

Step 6 : Draw the image.

Step 7 : Stop the program.


**Program :**
```
#include<graphics.h>
#include<stdio.h>
#include<conio.h>
#include<math.h>
int main()
{
int gd=DETECT,gm,i,j,k,ch;
float tx,ty,x,y,ang,n,temp;
float  a[5][3],si,co,b[5][3],c[5][3];
initgraph(&gd,&gm,"c:\\turboc3\\bgi");
n=4;
a[0][0]=0;    a[0][1]=0;   a[1][0]=100;  a[1][1]=0;
a[2][0]=100;  a[2][1]=100; a[3][0]=0;    a[3][1]=100;
a[4][0]=0;    a[4][1]=0;
while(1)
{
cleardevice();
gotoxy(1,8);
printf("\n\t******** Program to perform 2-D Transformations ********");
printf("\n\t\t\t 1. Accept the polygon");
printf("\n\t\t\t 2. Perform translation");
printf("\n\t\t\t 3. Perform scaling");
printf("\n\t\t\t 4. Perform rotation");
printf("\n\t\t\t 5. Perform reflection");
printf("\n\t\t\t 6. Perform shearing");
printf("\n\t\t\t 7. Exit");
printf("\n\t\t\t Enter your choice::");
scanf("%d",&ch);
switch(ch)
{
case 1:
cleardevice();
gotoxy(1,1);
printf("\n\tEnter no of points.:");
scanf("%f",&n);

    for(i=0;i<n;i++)
 {
   printf("\n\t Enter x,y co-ordinates for %d::",i+1);
   scanf("%f %f",&a[i][0],&a[i][1]);
  }
       a[i][0]=a[0][0];
       a[i][1]=a[0][1];
      cleardevice();
      for(i=0;i<n;i++)
      line(320+a[i][0],240-a[i][1],320+a[i+1][0],240-a[i+1][1]);
      line(0,240,639,240);
      line(320,0,320,479);
      getch();
      break;

    case 2:
      cleardevice();
      for(i=0;i<n;i++)
      line(320+a[i][0],240-a[i][1],320+a[i+1][0],240-a[i+1][1]);
      line(0,240,639,240);
      line(320,0,320,479);
       gotoxy(1,1);
       printf("Enter translation vectors tx and ty\n\t");
       scanf("%f %f",&x,&y);
       cleardevice();
  for(i=0;i<n;i++)
  line(320+a[i][0]+x,240-(a[i][1]+y),320+a[i+1][0]+x,240-(a[i+1][1]+y));
  line(0,240,639,240);
  line(320,0,320,479);
  getch();
       break;

    case 3:
	   cleardevice();
      for(i=0;i<n;i++)
      line(320+a[i][0],240-a[i][1],320+a[i+1][0],240-a[i+1][1]);
      line(0,240,639,240);
      line(320,0,320,479);
     gotoxy(1,1);
     printf("Enter scaling vectors tx and ty\n\t");
     scanf("%f %f",&x,&y);
     if(x==0)
     x=1;
     if(y==0)


       y=1;
       cleardevice();
  for(i=0;i<n;i++)
  line(320+(a[i][0]*x),240-(a[i][1]*y),320+(a[i+1][0]*x),240-(a[i+1][1]*y));
  line(0,240,639,240);
  line(320,0,320,479);
  getch();
  break;

  case 4:
      cleardevice();
      for(i=0;i<n;i++)
      line(320+a[i][0],240-a[i][1],320+a[i+1][0],240-a[i+1][1]);
      line(0,240,639,240);
      line(320,0,320,479);
     gotoxy(1,1);
     printf("Enter the angle of rotation\n\t");
     scanf("%f",&ang);
     ang=ang*0.01745;
     gotoxy(1,3);
     printf("Enter point of rotation\n\t");
     scanf("%f %f",&x,&y);
     gotoxy(1,5);
     printf("1.clockwise  2.anticlockwise\n\t");
     scanf("%d",&k);
     si=sin(ang);
     co=cos(ang);
     for(i=0;i<n+1;i++)
 {
   c[i][0]=a[i][0];
   c[i][1]=a[i][1];
   c[i][2]=1;
 }
	   b[0][0]=co;
      b[0][1]=si;
      b[0][2]=0;
      b[1][0]=(-si);
      b[1][1]=co;
      b[1][2]=0;
      b[2][0]=(-x*co)+(y*si)+x;
      b[2][1]=(-x*si)-(y*co)+y;
      b[2][2]=1;



      if(k==1)
      {
 b[0][1]=(-si);
 b[1][0]=(si);
 b[2][0]=(-x*co)-(y*si)+x;
 b[2][1]=(-x*si)+(y*co)+y;
      }

     for(i=0;i<n+1;i++)
    {
       for(j=0;j<3;j++)
   {
     a[i][j] = 0 ;
     for(k=0;k<3;k++)
     a[i][j] = a[i][j] + c[i][k] * b[k][j] ;
   }
     }

     cleardevice();
     for(i=0;i<n;i++)
       line(320+a[i][0],240-a[i][1],320+a[i+1][0],240-a[i+1][1]);
       line(0,240,639,240);
       line(320,0,320,479);
       getch();
       break;

    case 5:
      cleardevice();
      for(i=0;i<n;i++)
      line(320+a[i][0],240-a[i][1],320+a[i+1][0],240-a[i+1][1]);
      line(0,240,639,240);
      line(320,0,320,479);
      gotoxy(1,1);
      printf("\n1.Reflection about Y-axis");
      printf("\n2.Reflection about X-axis");
      printf("\n3.Reflection about origin");
      printf("\n4.Reflection about line y=x");
      printf("\n5.Reflection about line y=-x");
      printf("\nEnter your choice:");
      scanf("%d",&ch);






  switch(ch)
      {
  case 1:
      for(i=0;i<n+1;i++)
	a[i][0]=a[i][0]*(-1);
       /* Plot the polygon */
       cleardevice();
       for(i=0;i<n;i++)
       line(320+a[i][0],240-a[i][1],320+a[i+1][0],240-a[i+1][1]);
       line(0,240,639,240);
       line(320,0,320,479);
       getch();
       break;

   case 2:
       for(i=0;i<n+1;i++)
	a[i][1]=a[i][1]*(-1);
	cleardevice();
       for(i=0;i<n;i++)
       line(320+a[i][0],240-a[i][1],320+a[i+1][0],240-a[i+1][1]);
       line(0,240,639,240);
       line(320,0,320,479);
       getch();
    break;

  case 3:
      for(i=0;i<n+1;i++)
      {
	a[i][1]=a[i][1]*(-1);
	a[i][0]=a[i][0]*(-1);
      }
	cleardevice();
       for(i=0;i<n;i++)
       line(320+a[i][0],240-a[i][1],320+a[i+1][0],240-a[i+1][1]);
       line(0,240,639,240);
       line(320,0,320,479);
       getch();
    break;

   case 4:
      for(i=0;i<n+1;i++)
      {
       temp=a[i][0];
       a[i][0]=a[i][1];
       a[i][1]=temp;
      }
       cleardevice();
       for(i=0;i<n;i++)
       line(320+a[i][0],240-a[i][1],320+a[i+1][0],240-a[i+1][1]);
       line(0,240,639,240);
       line(320,0,320,479);
       line(0,479,639,0);
       getch();
    break;

   case 5:
      for(i=0;i<n+1;i++)
      {
       temp=a[i][0];
       a[i][0]=a[i][1];
       a[i][1]=temp;
      }

	      for(i=0;i<n+1;i++)
      {
	a[i][1]=a[i][1]*(-1);
	a[i][0]=a[i][0]*(-1);
      }
	      cleardevice();
       for(i=0;i<n;i++)
       line(320+a[i][0],240-a[i][1],320+a[i+1][0],240-a[i+1][1]);
       line(0,240,639,240);
       line(320,0,320,479);
       line(0,0,639,479);
       getch();
    break;
  default:
    break;
      }
      break;

    case 6:
       cleardevice();
      for(i=0;i<n;i++)
      line(320+a[i][0],240-a[i][1],320+a[i+1][0],240-a[i+1][1]);
      line(0,240,639,240);
      line(320,0,320,479);
      gotoxy(1,1);
      printf("\n1.X shear with y reference line");
      printf("\n2.Y shear with x reference line");


      printf("\nEnter your choice:");
      scanf("%d",&ch);
      switch(ch)
      {

       case 1:
   printf("\nEnter the x-shear parameter value:");
   scanf("%f",&temp);
   printf("\nEnter the yref line");
   scanf("%f",&ty);
       b[0][0]=1;
      b[0][1]=0;
      b[0][2]=0;
      b[1][0]=temp;
      b[1][1]=1;
      b[1][2]=0;
      b[2][0]=(-temp)*(ty);
      b[2][1]=0;
      b[2][2]=1;

     for(i=0;i<n+1;i++)
     a[i][2]=1;

  for(i=0;i<n+1;i++)
    {
       for(j=0;j<3;j++)
   {
     c[i][j] = 0 ;
     for(k=0;k<3;k++)
     c[i][j] = c[i][j] + a[i][k] * b[k][j] ;
   }
     }

     cleardevice();
     for(i=0;i<n;i++)
       line(320+c[i][0],240-c[i][1],320+c[i+1][0],240-c[i+1][1]);
       line(0,240,639,240);
       line(320,0,320,479);
       getch();
 break;

       case 2:
   printf("\nEnter the y-shear parameter value:");
   scanf("%f",&temp);
	      printf("\nEnter the xref line");
   scanf("%f",&tx);
		 b[0][0]=1;
      b[0][1]=temp;
      b[0][2]=0;
      b[1][0]=0;
      b[1][1]=1;
      b[1][2]=0;
      b[2][0]=0;
      b[2][1]=(-temp)*(tx);
      b[2][2]=0;
     for(i=0;i<n+1;i++)
     a[i][2]=1;

  for(i=0;i<n+1;i++)
    {
       for(j=0;j<3;j++)
   {
     c[i][j] = 0 ;
     for(k=0;k<3;k++)
     c[i][j] = c[i][j] + a[i][k] * b[k][j] ;
   }
     }

	  cleardevice();
     for(i=0;i<n;i++)
       line(320+c[i][0],240-c[i][1],320+c[i+1][0],240-c[i+1][1]);
       line(0,240,639,240);
       line(320,0,320,479);
       getch();
 break;

case 7:
    exit(1);
    closegraph();
    restorecrtmode();
    break;
    default: break;
    }

  }}}
```


**Output :**


![image](https://github.com/user-attachments/assets/39dd11d0-162a-40fe-8849-c01aef0d2af2)

![image](https://github.com/user-attachments/assets/5fb91fc3-d9a3-4243-b156-4c706737e632)

![image](https://github.com/user-attachments/assets/bb6f7560-9d2d-4f6a-aea6-15d69ad9f858)

![image](https://github.com/user-attachments/assets/7f00cb3f-c443-477d-9f1f-139d07bdb207)

![image](https://github.com/user-attachments/assets/b0b07033-6fc5-4e63-91e7-d5a5771c1976)

![image](https://github.com/user-attachments/assets/4d3d3020-b7b7-47a2-afb3-265575e54461)

![image](https://github.com/user-attachments/assets/81011d10-3dae-4d46-b459-a5a408997a18)

![image](https://github.com/user-attachments/assets/6ab016a3-8463-43e2-b5cf-670b5c9be2cb)

![image](https://github.com/user-attachments/assets/dac0610e-6822-423e-b842-5fd996da93a7)

![image](https://github.com/user-attachments/assets/4d3500d7-18c1-493a-ba59-a71bc0978d18)

![image](https://github.com/user-attachments/assets/3dbecd0c-9150-4f48-9f5d-64034d6e9982)

![image](https://github.com/user-attachments/assets/c3511783-bc8a-46b2-a4cb-91a027fef8f3)

![image](https://github.com/user-attachments/assets/d59d4766-ef67-462b-aaa3-171f03691ec4)

![image](https://github.com/user-attachments/assets/1f7f8730-db2d-424a-8027-2deb4c6907d1)

![image](https://github.com/user-attachments/assets/f2acb528-56bf-447f-a19e-878c13d73e46)




**Result :**

Thus 2D transformation of image is implemented using c coding.
