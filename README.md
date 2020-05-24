# some-code
#include<iostream>
#include<math.h>
#include<cstdlib>
using namespace std;


class studentdetails
	{
		string name;
		int sid;
		string branch;
		public:
		static int n;
		void getsid() {cout<<"Enter sid:";cin>>sid;cout<<endl;}
		int putsid(){return sid;}
		void getname() {cout<<"Enter name:";cin>>name;cout<<endl;}
	    void getbranch() {cout<<"Enter branch:";cin>>branch;cout<<endl;}
		studentdetails()
		{
			n++;
			sid=0;
			name="null";
			branch="null";
		}
		static int showcount()
		{
			return n;
		}
	};
	int studentdetails::n=0;

	class abc{
	int year,daynumber,monthnumber,monthday;
	public:
	void setval()
	{
		cout<<endl<<"Enter year:";cin>>year;
		cout<<endl<<"Enter day number:";cin>>daynumber;
		cout<<endl<<"Enter month number:";cin>>monthnumber;

		if(monthnumber==4||monthnumber==6||monthnumber==9||monthnumber==11) monthday=30;
		if(monthnumber==2){
			monthday=28;
			if(year%4==0) monthday=29;
		}
		else monthday=31;
	}
	abc()
	{
		year=daynumber=monthnumber=monthday=0;
	}
	int operator-(abc a)
	{
		int l,s,t,diff=0;
		if(a.year==year)
		{
			if(monthnumber==a.monthnumber) {
				t=daynumber-a.daynumber;
				t=abs(t);
				diff+=t;
			}

			else{
				s=a.monthnumber>monthnumber?daynumber:a.daynumber;
				t=(a.monthnumber>monthnumber?monthday:a.monthday)-s;
				diff+=t;
				t=(a.monthnumber<monthnumber?daynumber:a.daynumber);
				diff+=t;
				s=a.monthnumber>monthnumber?monthnumber:a.monthnumber;
				l=a.monthnumber<monthnumber?monthnumber:a.monthnumber;
				for(int i=s+1;i<l;i++)
				{
					if(i==4||i==6||i==9||i==11) t=30;
		if(i==2){
			t=28;
		}
		else t=31;
		diff+=t;
				}
			}
		}

			else{
				int s1,l1,l0,s0;
				l=a.year>year?a.year:year;
				s=a.year<year?a.year:year;
				for(int i=s+1;i<l;i++)
				{
					if(i%4==0) diff+=366;
					else diff+=365;
				}
				l1=a.year>year?a.daynumber:daynumber;
				s1=a.year<year?a.daynumber:daynumber;
				l=a.year>year?a.monthday:monthday;
				s=a.year<year?a.monthday:monthday;
				l0=a.year>year?a.monthnumber:monthnumber;
				s0=a.year<year?a.monthnumber:monthnumber;
				t=s-s1;
				diff+=t;
				for(int i=s0+1;i<=12;i++)
					{
					if(i==4||i==6||i==9||i==11) t=30;
		if(i==2){
			t=28;
		}
		else t=31;
		diff+=t;
				}
				for(int i=1;i<l0;i++)
				{
					if(i==4||i==6||i==9||i==11) t=30;
		if(i==2){
			t=28;
		}
		else t=31;
		diff+=t;
				}
			diff+=l1;
			diff-=4;
			}
			return diff;
	}

	void operator++()
	{
		if(monthday==daynumber)
		{
			if(monthnumber==12)
			{
				year++;
				monthnumber=1;
				daynumber=1;
			}
			else{
				monthnumber++;
				daynumber=1;
			}
		}
		else{
			daynumber++;
		}
	}

	void getval()
	{
		cout<<"Date:"<<daynumber<<endl<<"Month:"<<monthnumber<<endl<<"year:"<<year<<endl;
	}

	int mnum()
	{
		return monthday;
	}
};

int main()
{
	int a1;
	char ch1='y';
	while(ch1=='y'||ch1=='Y')
	{
	cout<<"Enter question number(1/2/3/4):";
	cin>>a1;
	switch(a1)
	{
		case 1:{
			string name;
    float height,weight;
        cout<<"Enter your name"<< endl;
            cin>>name;
        cout << "Enter your height(in inches)" << endl;
            cin>>height;
        cout<< "Enter your weight (in pounds)" <<endl;
            cin>>weight;

    float a = height*height;
    float b= weight*703;
    float BMI = b/a;
        cout<<"BMI of "<<name<< " is "<<BMI<<endl;
    if (BMI<19)
    {
        cout<<"You are Underweight"<<endl;
		}
    else if (BMI <25)
    {
        cout<<"Your BMI is Normal"<<endl;
		}
    else if (BMI <29)
    {
        cout<<"You are Overweight"<<endl;
		}
    else
    {
        cout<<"You are Obese"<<endl;
		}
}
break;
case 2:{
	double a;
	cout<<"Enter age(in days):";
	cin>>a;
char x;
cout<<"Enter A for physical, intellectual and emotional indces or B for biorhythm index"<<endl;
cin>>x;
switch(x)
{case 'A' :

	double e,p,i;
	e=sin(a*3.14/14);
	p=sin(a*2*3.14/23);
	i=sin(a*2*3.14/33);
	cout<<"Emotional index:"<<e<<endl<<"Physical index:"<<p<<endl<<"Intellectual index:"<<i<<endl;
break;
case 'B' :


	double a,d,c,b;
	a=sin(a*3.14/14);
	d=sin(a*2*3.14/23);
	c=sin(a*2*3.14/33);
	b=a+d+c;
	cout<<"Biorhythm index:"<<b<<endl;
break;

default :
cout<< "Invalid input"<<endl;


}
break;
case 3:{

	int no, s;
char c= 'y';
	cout<<"Enter number of students in class:";
	cin>>no;
	studentdetails *p,*p2;
	cout<<"Enter SID as 0 for empty details"<<endl;
	p=new studentdetails[no];
	p2=p;
	for(int j=0;j<no;j++)
	{
		p2->getsid();
		if(!p2->putsid())goto end;
		p2->getname();
		p2->getbranch();
		end:
		p2++;
	}
	cout<<endl<<"Number of objects created:"<<studentdetails::showcount();
	delete p;
}
break;

case 4:{
	int d,z;
	char ch1,ch='y';
	while(ch=='y'||ch=='Y')
	{
	abc a[2];
	for(int i=0;i<2;i++)
	{
		a[i].setval();
		po1:
		cout<<endl<<"What to do?...1.INCREMENT DATE or 2.SEE MONTH DAYS or 3.SUBTRACT or 4.SEE ENTERED VALUES...(1/2/3/4)....";
		cin>>z;
		switch(z)
		{
			case 1:cout<<++a[i];
			break;
			case 2:cout<<endl<<"Month days:"<<a[i].mnum()<<endl;
			break;
			case 3:goto po;
			break;
			case 4:a[i].getval();
			break;
			default:{cout<<endl<<"Wrong input!!!!!";
			goto po1;
			}
		}
			cout<<"Want to do more then type y or type c to continue?...";
			cin>>ch1;
			if(ch1=='y'||ch1=='Y') goto po1;
			po:;
		}
		d=a[0]-a[1];
	cout<<endl<<"Difference:"<<d;
cout<<endl<<"enter more dates?(y/n)...";cin>>ch;
	}

}
break;

default:cout<<endl<<"Wrong question number!";

	}
	cout<<endl<<"Do more questions?(y/n)....";
	cin>>ch1;}

return 0;}}

