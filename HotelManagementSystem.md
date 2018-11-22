#include<iostream>
#include<fstream>
#include<windows.h>
using namespace std;

void exit();
void staffs1();
void room_service();
void booking();
int hotel();
int staff_no;
void customer_details();
int main();
void login();

class displays{
	public:
		void main_display();
		void staff_display();
	    void roombooking_display();
		void roomservice_display();
		void customercheckout_display();		
};

class person
{
	public:
		person(){};
		person(const person& obj);
		virtual void print_info()=0;
		~person(){};
};

class staff:public person
{
	public:
		staff(const staff&obj);
		staff(){};
		void manager();
		void house_keeping_staff();
		void room_service_staff();
		void reception();
        void staff_s();
        void print_info(){};
		virtual ~staff(){};	
};

class roombooking:public person
{
	public:
		string fname,lname;
		long cnic;
		int schoice;
		int inDay,inMonth,inYear; 
		int dd;
		roombooking(){}
		roombooking(const roombooking& obj);
		void print_info();
		void roomdetails();
		//void form();
		friend istream& operator >>(istream& ,roombooking &obj);
		
};

istream& operator >>(istream& , roombooking &obj)
{
		
			system("CLS");
			ofstream outf("booking.txt", ios::app);
			cout<<"------------ROOM BOOKING FORM-------------"<<endl;
			cout<<"First name: ";
			cin>>obj.fname;
			outf<<obj.fname<<endl;
			cout<<"Last name: ";
			cin>>obj.lname;
			outf<<obj.lname<<endl;
			cout<<"Cnic number: ";
			cin>>obj.cnic;
			outf<<obj.cnic<<endl;
			cout<<"Day : "; 	cin>>obj.inDay;
			cout<<endl<<"Month : ";	cin>>obj.inMonth; 
			cout<<endl<<"Year : "; 	cin>>obj.inYear; 	
			
			cout<<endl<<"Room type selection: "<<endl;
			cout<<"1. Normal room"<<endl;
			cout<<"2. Vip room"<<endl;
			cout<<"3. Suite"<<endl;
			cout<<"Enter the choice of room you want?: ";
			cin>>obj.schoice;
			while (obj.schoice > 3 || obj.schoice < 1)
			{
				cout<<"You entered an invalid option."<<endl;
				cout<<endl<<"Choose your option: ";
				cin>>obj.schoice;
			}
			outf<<obj.schoice<<endl;
			outf<<obj.inDay<<endl;
			outf<<obj.inMonth<<endl;
			outf<<obj.inYear<<endl;
			cout<<endl;
			outf.close();
			
			ofstream file("food.txt", ios::app);
			if(obj.schoice==1)
			{
				int p=2000;
				file<<p<<endl;
			}
			else if (obj.schoice==2)
			{
				int p=5000;
				file<<p<<endl;
			}
			else
			{
				int p = 10000;
				file<<p<<endl;		
			}
			file.close();
}


class service
{	
		
	public:
		service(){}
		//service(const service& obj);
		void menu();
		friend void call(service s1);
};



void displays::main_display()
{
	cout<<"----------------------------------"<<endl;
	cout<<"            WELCOME               "<<endl;
	cout<<"----------------------------------"<<endl;
	cout<<"1. "<<"Staff"<<endl;
	cout<<"2. "<<"Room Booking"<<endl;
	cout<<"3. "<<"Customer Details"<<endl;
	cout<<"4. "<<"Room Service"<<endl;
	cout<<"5. "<<"Customer Checkout"<<endl;
	cout<<"6. "<<"Exit"<<endl;
}

void displays::staff_display()
{
	cout<<"1. Reception:"<<endl;
	cout<<"2.Manager:"<<endl;
	cout<<"3.Room Service Staff:"<<endl;
	cout<<"4.House Keeping Staff:"<<endl;
	cout<<"5. Go back to main menu"<<endl;
}

void displays::roombooking_display()
{
	cout<<"1. Room details"<<endl;
	cout<<"2. Room Booking form"<<endl;
	cout<<"3. Go back to main menu"<<endl;
}

void displays::roomservice_display()
{
	cout<<"1. Order Food"<<endl;
	cout<<"2. Ask personal assistance"<<endl;
	cout<<"3. Go back to main menu"<<endl;
}		

void displays::customercheckout_display()
{
	cout<<"1. Total Bill"<<endl;
	cout<<"2. Go back to main menu"<<endl;
}

void staff::manager()
{
	int count;
	ifstream inf;
	string line;
	inf.open("manager staff.txt", ios::out);
	
	for(count=1;count<=3;count++)
	{
	    inf>>line;
	    cout<<line<<endl;
    }
	inf.close();
}

void staff::house_keeping_staff()
{
	int count;
	ifstream inf;
	string line;
	inf.open("house keeping.txt", ios::out);
	for(count=1;count<=16;count++)
	{
	    inf>>line;
	    cout<<line<<endl;
    }
	inf.close();
}

void staff::room_service_staff()
{
	int count;
	ifstream inf;
	string line;
	inf.open("room service.txt", ios::out);
	for(count=1;count<=24;count++)
	{
	    inf>>line;
	    cout<<line<<endl;
    }
	inf.close();
}

void staff::reception()
{
	int count;
	ifstream inf;
	string line;
	inf.open("reception.txt", ios::out);
	for(count=0;count<=15;count++)
	{	
	    inf>>line;
	    cout<<line<<endl;
    }
	inf.close();
}

void staff_s()
{
	system("CLS");
	int choice;
	int key;
	displays p;
	p.staff_display();
	staff s1s1;
	cout<<endl<<"Choose your option: ";
	cin>>choice;
	int schoice;
	int staff_no;
	
	while(1)
	{
		if(choice==1)
		{
			system("CLS");
			
		   s1s1.reception();
			
			cout<<endl<<"Do you want to go back or exit? (0 for exit or any number for going back): "<<endl;
			cin>>schoice;
			
			if(schoice==0)
			{
				exit();
			}
			else
			{
				staff_s();
			}
			break;
		}
		else if(choice==2)
		{
			system("CLS");
		    cout<<"enter the key to view manager details"<<endl;
            cin>>key;
            if (key==5678)
			{		
				s1s1.manager();
			}
			else
			{
				cout<<"you entered the wrong key. cannot display details."<<endl;
			}
			cout<<endl<<"Do you want to go back or exit? (0 for exit or any number for going back): "<<endl;
			cin>>schoice;
			
			if(schoice==0)
			{
				exit();
			}
			else
			{
				staff_s();
			}
			break;
		}
		else if(choice==3)
		{
			system("CLS");
			
		    s1s1.room_service_staff();
			
			cout<<endl<<"Do you want to go back or exit? (0 for exit or any number for going back): "<<endl;
			cin>>schoice;
			
			if(schoice==0)
			{
				exit();
			}
			else
			{
				staff_s();
			}
			break;
		}
		else if(choice==4)
		{
			system("CLS");
			
		    s1s1.house_keeping_staff();
			
			cout<<endl<<"Do you want to go back or exit? (0 for exit or any number for going back): "<<endl;
			cin>>schoice;
			
			if(schoice==0)
			{
				exit();
			}
			else
			{
				staff_s();
			}
			break;
		}
		else if(choice==5)
		{	
			system("CLS");
			hotel();
			break;				
		}
		else
		{
			cout<<"You entered an invalid option."<<endl;
			cout<<endl<<"Choose your option: ";
			cin>>choice;
		}		
	}	
}

void roombooking::print_info()
{
	customer_details();
}
		
void roombooking::roomdetails()
{
    system("CLS");
	cout<<"----------- ROOM RATES---------------"<<endl;
	cout<<"1. Normal Room                      2000/="<<endl;
	cout<<"2. VIP Room                         5000/="<<endl;
	cout<<"3. Suite                            10000/="<<endl;
}

/*void roombooking::form()
{
	system("CLS");
	ofstream outf("booking.txt", ios::app);
	cout<<"------------ROOM BOOKING FORM-------------"<<endl;
	cout<<"First name: ";
	cin>>fname;
	outf<<fname<<endl;
	cout<<"Last name: ";
	cin>>lname;
	outf<<lname<<endl;
	cout<<"Cnic number: ";
	cin>>cnic;
	outf<<cnic<<endl;
	cout<<"Day: "; 	
	cin>>inDay;
	cout<<endl<<"Month: ";
	cin>>inMonth; 
	cout<<endl<<"Year: "; 	
	cin>>inYear; 	

	cout<<endl<<"Room type selection: "<<endl;
	cout<<"1. Normal room"<<endl;
	cout<<"2. Vip room"<<endl;
	cout<<"3. Suite"<<endl;
	cout<<"Enter the choice of room you want?: ";
	cin>>schoice;
	while (schoice > 3 || schoice < 1)
	{
		cout<<"You entered an invalid option."<<endl;
		cout<<endl<<"Choose your option: ";
		cin>>schoice;
	}
	outf<<schoice<<endl;
	outf<<inDay<<endl;
	outf<<inMonth<<endl;
	outf<<inYear<<endl;
	cout<<endl;		
	outf.close();
			
	ofstream file("food.txt", ios::app);
	if(schoice==1)
	{
		int p=2000;
		file<<p<<endl;
	}
	else if (schoice==2)
	{
		int p=5000;
		file<<p<<endl;
	}
	else
	{
		int p = 10000;
		file<<p<<endl;		
	}
	file.close();
}*/

void booking()
{
		system("CLS");
		int choice;
		displays d;
		d.roombooking_display();
		
		cout<<endl<<"Choose your option: ";
		cin>>choice;
		int schoice;
		roombooking b;
		while(1)
		{
			if(choice ==1)
			{
				b.roomdetails();
				cout<<endl<<"Do you want to go back or exit? (0 for exit or any number for going back): "<<endl;
				cin>>schoice;
					
				if(schoice==0)
				{
					exit();
				}
				else
				{
					booking();
				}
				break;
			}
		if(choice == 2)
		{		
			
			//b.form();
			cin>>b;
			cout<<endl<<"Room booked succesfully!"<<endl;
			
			cout<<endl<<"Do you want to go back or exit? (0 for exit or any number for going back): "<<endl;
			cin>>schoice;
				
			if(schoice==0)
			{
				exit();
			}
			else
			{
				booking();
			}
			break;
		}
		
		else if(choice == 3)
		{
			system("CLS");
			hotel();
			break;
		}
		
		else
		{
			cout<<"You entered an invalid option."<<endl;
			cout<<endl<<"Choose your option: ";
			cin>>choice;
		}	
	}
}

void customer_details()
{
		system("CLS");
		string fname,lname;
		long cnic;
		int schoice;
		ifstream inf("booking.txt");
		int i=1;
		int inDay,inMonth,inYear;
		
		while(true)
		{
			if(inf.fail())
			{
				cout<<"Nothing in file";
				break;
			}
			else
			{	
					cout<<"Customer "<<i<<": "<<endl;
					inf>>fname;
					if( inf.eof() ) break;
					cout<<"First name: "<<fname<<endl;
					inf>>lname;
					if( inf.eof() ) break;
					cout<<"Last name: "<<lname<<endl;
					inf>>cnic;
					if( inf.eof() ) break;
					cout<<"cnic: "<<cnic<<endl;
					inf>>schoice;
					if( inf.eof() ) break;
				    inf>>inDay;	
					if( inf.eof() ) break;
					inf>>inMonth;	
					if( inf.eof() ) break;
					inf>>inYear;	
					if( inf.eof() ) break;
					
					if(schoice==1)
					{
						cout<<"Normal Room"<<endl;
					}
					else if(schoice==2)
					{
						cout<<"VIP room"<<endl;
					}
					else
					{
						cout<<"Suite"<<endl;
					}
					cout<<"Check in date : "<<inDay<<"/";
					cout<<inMonth<<"/";
					cout<<inYear<<endl;
					cout<<endl;
					i++;
			}
		}
		inf.close();
				
		cout<<endl<<"Do you want to go back or exit? (0 for exit or any number for going back): "<<endl;
		cin>>schoice;
				
		if(schoice==0)
		{
			exit();
		}
		else
		{
			hotel();
		}		
}

void service::menu()
{
	system("CLS");
	cout<<"---------------FOOD MENU----------------"<<endl<<endl;
	cout<<"1. Soup                             100/="<<endl;
	cout<<"2. Pizza                            700/="<<endl;
	cout<<"3. Biryani                          200/="<<endl;
	cout<<"4. Tea                              50/="<<endl;
}

void call(service s1)
{
	system("CLS");
	cout<<"Someone will be ccoming to your room shortly"<<endl;
}

void room_service()
{
	system("CLS");
	//const static float tax=0.03;
	int choice,schoice;
	displays d;
	d.roomservice_display();
	cout<<endl<<"Choose your option: ";
	cin>>choice;
	int quantity;
	service s1;
	int c=1;
	int price;
	while(1)
	{
		if(choice==1)
		{
			s1.menu();
			
			while(c==1)
			{
				cout<<endl<<"Enter your choice: ";
				cin>>schoice;
				while(schoice > 4 || schoice < 1)
				{
					cout<<"You entered an invalid option."<<endl;
					cout<<endl<<"Choose your option: ";
					cin>>schoice;
				}
				cout<<"Enter quantity: ";
				cin>> quantity;
				ofstream outf;
				outf.open("food.txt", ios::app);
				if(schoice==1)
				{
					price=quantity*100;
					outf<<price<<endl;
				}
				else if(schoice==2)
				{
					price=quantity*700;
					outf<<price<<endl;
				}
				else if(schoice==3)
				{
					price=quantity*200;
					outf<<price<<endl;
				}
				else if(schoice==4)
				{
					price=quantity*50;
					outf<<price<<endl;
				}
				outf.eof();
				outf.close();
				
				cout<<"Do you want to enter another item? (press 1 for yes or any number for no";
				cin>>c;
			}
			
			cout<<endl<<"Do you want to go back or exit? (0 for exit or any number for going back): "<<endl;
			cin>>choice;
			
			if(choice==0)
			{
				exit();
			}
			else
			{
				room_service();
			}
			break;
		}
		else if(choice ==2)
		{
			service s1;
			call(s1);
			cout<<endl<<"Do you want to go back or exit? (0 for exit or any number for going back): "<<endl;
			cin>>choice;
			
			if(choice==0)
			{
				exit();
			}
			else
			{
				room_service();
			}
			break;	
		}
		else if(choice == 3)
		{
			system("CLS");
			hotel();
			break;
		}
		else
		{
			cout<<"You entered an invalid option."<<endl;
			cout<<endl<<"Choose your option: ";
			cin>>choice;
		}		
	}
}

void checkout()
{
	system("CLS");
	const static float tax=0.04;
	static int amount;
	int price;
	int outDay,outMonth,outYear; 
	int inDay,inMonth,inYear;
	string fname,lname;
	int cnic,sschoice,dd=0;

	displays d;
	d.customercheckout_display();
	int choice,schoice;
	cout<<endl<<"Choose your option: ";
	cin>>choice;
		
	cout<<"Day : "; 	
	cin>>outDay;
	cout<<endl<<"Month : ";	cin>>outMonth;
	cout<<endl<<"Year : "; 	cin>>outYear; cout<<endl;
	ifstream inf("booking.txt");
	while(true)
	{
		inf>>fname;
		if( inf.eof() ) break;
		inf>>lname;
		if( inf.eof() ) break;
		inf>>cnic;
		if( inf.eof() ) break;
		inf>>sschoice;
		if( inf.eof() ) break;
		inf>>inDay;	
		if( inf.eof() ) break;
		inf>>inMonth;	
		if( inf.eof() ) break;
		inf>>inYear;	
		if( inf.eof() ) break;
	}
	inf.close();	
	if(outYear>inYear || outMonth!=inMonth || outDay<inDay)
	{ 	
		dd = outDay-inDay;
		dd+=30;
	}
	else
	{ 	
	    dd=outDay-inDay;
	}
		
	while(1)
	{
		if(choice == 1)
		{
			system("CLS");
			ifstream inf("food.txt");
			while(!inf.fail())				
			{
					inf>>price;
					amount =amount+price;				
			}
			amount=amount-price;
			float temp=(amount*tax);
			amount=amount+temp;
            amount*=dd;
            cout<<"Check-in date : "<<inDay<<"/"<<inMonth<<"/"<<inYear<<endl;
			cout<<"Check-Out date : "<<outDay<<"/"<<outMonth<<"/"<<outYear<<endl;
			cout<<"You stayed for "<<dd<<" days"<<endl<<endl;
			cout<<"Bill is: "<<amount<<endl;
			cout<<endl<<"Do you want to go back or exit? (0 for exit or any number for going back): "<<endl;
			cin>>schoice;
				
			if(schoice==0)
			{
				exit();
			}
			else
				{
					checkout();
				}
				break;
			}
			else if (choice == 2)
			{
				hotel();
				break;
			}
			
			else
			{
				cout<<"You entered an invalid option."<<endl;
				cout<<endl<<"Choose your option: ";
				cin>>choice;
			}		
		}	
}

void exit()
{
	system("CLS");
	cout<<"THANKYOU FOR USING OUR MANAGEMENT SYSTEM"<<endl;
}

int hotel()
{
	system("CLS");
	displays m;
	m.main_display();
	int choice,n;
	cout<<endl<<"Choose your option: ";
	cin>>choice;
	string password,username,pass,user;
	while(1)
	{
		if(choice==1)
		{
			system("CLS");
			staff_s();
			break;			
		}
		else if(choice==2)
		{
			booking();
			break;
		}
		else if(choice==3)
		{
			customer_details();
			break;
		}
		else if(choice==4)
		{
			room_service();
			break;
		}
		else if(choice == 5)
		{
			system("CLS");
			checkout();
			break;
		}
		else if(choice == 6)
		{
			exit();
			break;
		}
		else
		{
			cout<<"You entered an invalid option."<<endl;
			cout<<endl<<"Choose your option: ";
			cin>>choice;
		}
	}		
}

int main()
{
	int count=0;
	system("COLOR 8B");
			cout<<"\t\t\t----------------------------------"<<endl;
			cout<<"\t\t\t----------------------------------"<<endl<<endl;
			cout<<"\t\t\t     HOTEL MANAGEMENT SYSTEM      "<<endl<<endl;
			cout<<"\t\t\t----------------------------------"<<endl;
			cout<<"\t\t\t----------------------------------"<<endl;
			
			cout<<endl<<"\t\t\tSystem is loading"<<endl;
			cout<<"\t\t\t";
			while(count<10)
			{
				cout<<"=";
				count++;
				Sleep(0700);
			}
	hotel();					
}
