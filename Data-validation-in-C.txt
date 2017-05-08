//Program to include data validation in creating new email account
#include <stdio.h>                                                         //preprocessor directives
#include <stdlib.h>
#include <string.h>
void confirm();                                                            //function declarations
void date(char DOB[]);
void mobile_number(void);
void username(void);
void name(void);
void name2(void);
void gen(void);
//main program
main()
{
    char str1[100],str2[100],str3[100],str4[100],str5[100],str6[100],DOB;     //declaring local variables
    printf("**WELCOME**\n");
    printf("CREATE YOUR E-MAIL ACCOUNT\n");
    printf("Personal Details\n");
    name();                                                                   //function calling
    name2();
    username();
    confirm();
    mobile_number();

    gen();
    printf("Enter DOB in the format dd/mm/yyyy: \n");
    scanf("%s",DOB);
    printf("Congratulations!Your account has been created!\n");

}
void confirm()
{
    int n;

    char conf [100],str4[100];
    printf("Create a password: \n");
    scanf("%s",str4);
    n=strlen(str4);
    if(n<=7)
    {
        printf("Weak Password\n");
        confirm();
    }
    else
    {
        printf("Enter your password again: \n");
        scanf("%s",conf);


        if(strcmp(str4,conf)==0)
        {
            printf("Password Confirmed!\n");
        }
        else
        {
            printf("Password doesnot match!\n");
            confirm();
        }
    }
}

void mobile_number(void)                                         //function definition
{
    int n,c=0,i;
    char arr[10];
    printf("Enter your mobile number:");
    scanf("%s",arr);
    n=strlen(arr);
    for(i=0;i<n;i++)
    {
        if(arr[i]>=48&&arr[i]<=57)                               //data validation to check numeric characters and length of string
        {
            c++;
        }
    }
    if(arr[0]!='0')
    {
        if(c!=10||n!=10)
        {
            printf("Enter your valid mobile number!\n");
            mobile_number();
        }
    }
    else
    {
        printf("Enter your valid mobile number not starting with the digit 0!\n");
        mobile_number();
    }

}

void username(void)                                                    //function definition
{
     char str3[100];
     int i,c1=0,c2=0;
     int ch=(int)str3;
     printf("Choose your username: \n");
     scanf("%s",str3);
    for(i=0;str3[i]!='\0';i++)
    {
        if(str3[i]=='@')
            c1++;
        if(str3[i]=='.')
            c2++;
    }

    if(c1!=1||c2!=1)
    {
        printf("Invalid username!\n");
        username();
    }

}
void name(void)                                                   //function definition
{
   char str1[100];
    printf("Enter your first name: \n");
    scanf("%s",str1);

    int i,n,m=0;
    n=strlen(str1);
    for(i=0;str1[i]!='\0';i++)
    {
        if(str1[i]>='a'&&str1[i]<='z'||str1[i]>='A'&&str1[i]<='Z')
        {m++;

        }
    }
    if(m!=n)
    {
        printf("Invalid, try again!\n");
        name();
    }
}
void name2(void)                                                      //defining function
{
   char str2[100];
    printf("Enter your last name: \n");
    scanf("%s",str2);

    int p,q,r=0;
    q=strlen(str2);
    for(p=0;str2[p]!='\0';p++)
    {
        if(str2[p]>='a'&&str2[p]<='z'||str2[p]>='A'&&str2[p]<='Z')
        {r++;

        }
    }
    if(r!=q)
    {
        printf("Invalid, try again!\n");
        name2();
    }
}
void gen(void)                                                 //defining function
{   char g[0];
	int n;
    printf("Enter your gender: M for male or F for female: \n");
    scanf("%s",g);
    if(g[0]!='M'&&g[0]!='F')
    {																					                 //Data validation to check gender
        printf("Invalid,Enter Again!\n");
        gen();
    }

}

