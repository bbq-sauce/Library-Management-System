#include<iostream.h>
#include<conio.h>
#include<stdio.h>
#include<fstream.h>
#include<string.h>

class library
{
char bno[20];
char bname[20];
char aname[20];
char admno[20];
char token;
char stbno[20];
char sname[20];

public:void bcreate()
      { gets(bno);
gets(bname);
gets(aname);
      }
      void bshow()
      {cout<<bno<<'\t'<<bname<<'\t'<<aname;}

      void setstbno(char a[20])
      {strcpy(stbno,a);}

      void resettoken()
      {token='0';}

      void settoken()
      {token='1';}

      char rettoken()
      {return token;}

      library()
      {token='0';
      strcpy(stbno,"0");
      }

      char* retstbno()
      {return stbno;}

      void screate()
      {gets(admno);
       gets(sname);
      }

      void sshow()
      {cout<<admno<<'\t'<<sname<<'\t'<<stbno;}

      char*  retbno()
      {return bno;}

      char*  retadmno()
      {return admno;}

  }l;

  void main()
  {
   clrscr();
   int opt;
   char ch;
   ofstream f1("lib",ios::binary);
   cout<<"Enter details of books[Booknumber,Bookname,Authorname]:\n";
   for(int i=0;i<3;i++)
   {l.bcreate();
    f1.write((char*)&l,sizeof(l));
   }
   f1.close();
   ofstream f2("stud",ios::binary);
   cout<<"Enter details of students[Admission number,Name of student]:\n";
   for(i=0;i<3;i++)
   {l.screate();
    f2.write((char*)&l,sizeof(l));
   }
   f2.close();
   void issue();
   void deposit();
   void bdisplay();
   void sdisplay();
   do
   {cout<<"Welcome to school library:\n1.Issue book\n2.Deposit book\n3.Display book details\n4.Display student details\n";
    cin>>opt;
    switch(opt)
   {case 1:issue();
  break;
    case 2:deposit();
  break;
    case 3:bdisplay();
  break;
    case 5:sdisplay();
  break;
   }
   cout<<"\nDo you want menu again?[If yes[y or Y] and if no[n or N]]:";
   cin>>ch;
   }while(ch=='y'||ch=='Y');
   }

   void issue()
   {
   char n[20],a[20];
   cout<<"Enter Admission number:";
   gets(n);
   ofstream f2("temp",ios::binary);
   ifstream f1("stud",ios::binary);
   while(f1.read((char*)&l,sizeof(l)))
   {if(strcmp(l.retadmno(),n)==0)
    {if(l.rettoken()=='0')
    {cout<<"Enter Booknumber:";
     gets(a);
     l.setstbno(a);
     l.settoken();
    }
     else
     cout<<"\nReturn previous book";
     f2.write((char*)&l,sizeof(l));
    }
   else
   f2.write((char*)&l,sizeof(l));
    }
  f1.close();
  f2.close();
  remove("stud");
  rename("temp","stud");
  }

  void deposit()
  {
  char n[20],a[20];
  cout<<"Enter Admission number:";
  gets(a);
  cout<<"Enter Book number:";
  gets(n);
  ofstream f2("temp",ios::binary);
  ifstream f1("stud",ios::binary);
  while(f1.read((char*)&l,sizeof(l)))
  {
  if(strcmp(l.retadmno(),a)==0)
  {if(strcmp(l.retstbno(),n)==0)
  {
  l.resettoken();
  l.setstbno("0");
  }
  else
  cout<<"Wrong book number entered";
  f2.write((char*)&l,sizeof(l));
  }
  else
  f2.write((char*)&l,sizeof(l));
  }
  f1.close();
  f2.close();
  remove("stud");
  rename("temp","stud");
  }

 void bdisplay()
 {
 char n[20];
 cout<<"enter Book number you want:";
 gets(n);
 ifstream f2("lib",ios::binary);
 while(f2.read((char*)&l,sizeof(l)))
 {if(strcmp(l.retbno(),n)==0)
  l.bshow();
 }
  f2.close();
 }

  void sdisplay()
 {
 char n[20];
 cout<<"Enter  admission number of student you want:";
 gets(n);
 ifstream f2("stud",ios::binary);
 while(f2.read((char*)&l,sizeof(l)))
 {
 if(strcmp(l.retadmno(),n)==0)
 l.sshow();
 }
 f2.close();
 }
