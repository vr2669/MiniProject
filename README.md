# MiniProject
//mini project for student database storage system
#include <math.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
//structure storing student info
struct sinfo {
    char fname[50];
    char lname[50];
    int roll;
    float cgpa;
} st[55];
int i=0; //stores number of students
void welcome()//function to print initial display
{
    printf("*****************");
    printf("\nWelcome to the student database management system");
    printf("\n*******************");
}
void add_student(int j)  //function to add student details
{
    printf("Add the Students Details\n");
    printf("*********\n");
    printf("Enter the first "
           "name of student\n");
    scanf("%s", st[j].fname);
    printf("Enter the last name"
           " of student\n");
    scanf("%s", st[j].lname);
    printf("Enter the Roll Number\n");
    scanf("%d", &st[j].roll);
    printf("Enter the CGPA "
           "you obtained\n");
    scanf("%f", &st[j].cgpa);
 
}
void find_rl() //find student details by roll number
{
    int x;
    printf("Enter the Roll Number"
           " of the student\n");
    scanf("%d", &x);
    for (int j = 1; j <= i; j++) {
        if (x == st[j].roll) {
            printf(
                "The Students Details are\n");
            printf(
                "The First name is %s\n",
                st[j].fname);
            printf(
                "The Last name is %s\n",
                st[j].lname);
            printf(
                "The CGPA is %f\n",
                st[j].cgpa);
            
        break;
    }
}
}
void find_fn() //to find student by first name
{
    char a[50];
    printf("Enter the First Name"
           " of the student\n");
    scanf("%s", a);
    int c = 0;
     for (int j = 0; j < i; j++) {
        if (!strcmp(st[j].fname, a)) {
 
            printf(
                "The Students Details are\n");
            printf(
                "The First name is %s\n",
                st[j].fname);
            printf(
                "The Last name is %s\n",
                st[j].lname);
            printf(
                "The Roll Number is %d\n ",
                st[j].roll);
            printf(
                "The CGPA is %f\n",
                st[j].cgpa);
            c = 1;
        }
        else
            printf(
                "The First Name not Found\n");
    }
}
void del_s() //to delete student details by roll number
{
    int a;
    printf("Enter the Roll Number"
           " which you want "
           "to delete\n");
    scanf("%d", &a);
    for (int j = 1; j <= i; j++) {
        if (a == st[j].roll) {
            for (int k = j; k < 49; k++)
                st[k] = st[k + 1];
            i--;
        }
    }
    printf("The Roll Number"
           " is removed Successfully\n");
}
void up_s() //to update the student details by roll number
{
 
    printf("Enter the roll number"
           " to update the entry : ");
     int x;
    scanf("%d", &x);
    for (int j = 0; j < i; j++) {
        if (st[j].roll == x) {
            printf("1. first name\n"
                   "2. last name\n"
                   "3. roll no.\n"
                   "4. CGPA\n");
            int z;
            scanf("%d", &z);
            switch (z) {
            case 1:
                printf("Enter the new "
                       "first name : \n");
                scanf("%s", st[j].fname);
                break;
            case 2:
                printf("Enter the new "
                       "last name : \n");
                scanf("%s", st[j].lname);
                break;
            case 3:
                printf("Enter the new "
                       "roll number : \n");
                scanf("%d", &st[j].roll);
                break;
            case 4:
                printf("Enter the new CGPA : \n");
                scanf("%f", &st[j].cgpa);
                break;
            
            }
            printf("UPDATED SUCCESSFULLY.\n");
        }
    }
}
int main()
{
    welcome();
    printf("\nEnter number of student details you want to enter");
    int x;
    scanf("%d",&i);
    for(x=0;x<i;x++)
    {
        add_student(x);
    }
    printf("\nSelect which operation you want to do by selecting required number");
    printf("\n 1- Find the student details by Roll number");
    printf("\n 2- Find the student details by First Name");
    printf("\n 3- Delete the student details by Roll Number");
    printf("\n 4- Update the student details by Roll Number");
    printf("\n 5- To perform no operation on the database");
    printf("\nEnter choice");
    int choice;
    scanf("%d",&choice);
    switch(choice)
    {
        case 1:
        {
        find_rl();
        break;
        }
        case 2:
        {
            find_fn();
        break;
        }
        case 3:
        {
         del_s();
        break;
        }
        case 4:
        {
            up_s();
        break;
        }
        case 5:
        {
        exit(0);
        break;
        }
    }
    return 0;
}
