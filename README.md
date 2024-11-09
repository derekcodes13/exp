1
#include <iostream>
#include<string>
using namespace std;
class student
{
string name;
int roll_no;
string _class;
char div;
string dob;
string aadhar;
string blood;
string address;
string telephone;
static int count;
int marks[5];
float percentage;
friend void percent(student&);
public:
void studentinfo()
{
cout << "Enter Name: ";
cin >> name;
cout << "Enter Roll No: ";
cin >> roll_no;
cout << "Enter Class: ";
cin >> _class;
cout << "Enter Division: ";
cin >> div;
cout << "Enter Date of Birth: ";
cin >> dob;
cout << "Enter Aadhar Card no.: ";
cin >> aadhar;
cout << "Enter Blood: ";
cin >> blood;
cout << "Enter Address: ";
cin >> address;
cout << "Enter Telephone No.: ";
cin >> telephone;
cout << "Enter Marks: ";
for (int i = 0; i < 5; i++)
{
cout << "Subject " << i + 1 << ": ";
cin >> marks[i];
}
}
static void no_of_students()
{
count = count + 1;
}
static void displaycount()
{
cout << "No. of Students: " << count << endl;
}
void displayinfo()
{
cout << "Name: " << name << endl;
cout << "Roll No: " << roll_no << endl;
cout << "Class: " << _class << endl;
cout << "Division: " << div << endl;
cout << "Date of Birth: " << dob << endl;
cout << "Aadhar Card no.: " << aadhar << endl;
cout << "Blood: " << blood << endl;
cout << "Address: " << address << endl;
cout << "Telephone No.: " << telephone << endl;
cout << "Marks: ";
for (int i = 0; i < 5; i++)
{
cout << "Subject " << i + 1 << ": " << marks[i] << endl;
}
}
};
int student::count = 0;
void percent(student& a)
{
int total = 0;
for (int i = 0; i < 5; i++)
{
total += a.marks[i];
}
a.percentage = static_cast<float>(total) * 100 / 500;
cout << "Percentage received is: " << a.percentage << "%" << endl;
}
int main()
{
student st[5];
for (int i = 0; i < 5; i++)
{
cout << "Student " << i + 1 << endl;
st[i].studentinfo();
cout << endl;
student::no_of_students();
}
for (int i = 0; i < 5; i++)
{
cout << "Student " << i + 1 << endl;
st[i].displayinfo();
cout << endl;
percent(st[i]);
cout << endl;
}
student::displaycount();
return 0;
}

2
#include <iostream>
#include <string>
using namespace std;

class Student 
{
public:
    string name;
    int rno;
    char div;
    string dob;
    long Adhaar;
    string bgroup;
    string address;
    long telno;
    static int ctr;
    int m1, m2, m3;

    // Default constructor
    Student() {
        name = "";
        rno = 0;
        div = 'A';
        dob = "";
        Adhaar = 0;
        bgroup = "";
        address = "";
        telno = 0;
        m1 = m2 = m3 = 0;
    }

    // Parameterized constructor
    Student(string n, int r, char d, string dobirth, long adhaar, string bg, string addr, long tel, int mark1, int mark2, int mark3) {
        name = n;
        rno = r;
        div = d;
        dob = dobirth;
        Adhaar = adhaar;
        bgroup = bg;
        address = addr;
        telno = tel;
        m1 = mark1;
        m2 = mark2;
        m3 = mark3;
    }

    // Copy constructor
    Student(const Student& st) {
        name = st.name;
        rno = st.rno;
        div = st.div;
        dob = st.dob;
        Adhaar = st.Adhaar;
        bgroup = st.bgroup;
        address = st.address;
        telno = st.telno;
        m1 = st.m1;
        m2 = st.m2;
        m3 = st.m3;
    }

    // Destructor
    ~Student() {
        ctr--;
    }

    void setname() 
    {
        cout << "Enter name: " << endl;
        cin >> name;
    }
    void setrno() 
    {
        cout << "Enter roll no: " << endl;
        cin >> rno;
    }
    void setdiv() 
    {
        cout << "Enter division: " << endl;
        cin >> div;
    }
    void setdob() 
    {
        cout << "Enter date of birth: " << endl;
        cin >> dob;
    }
    void setadhaar() 
    {
        cout << "Enter Aadhaar no: " << endl;
        cin >> Adhaar;
    }
    void setbgroup() 
    {
        cout << "Enter blood group: " << endl;
        cin >> bgroup;
    }
    void setaddress() 
    {
        cout << "Enter address: " << endl;
        cin >> address;
    }
    void settelno() 
    {
        cout << "Enter telephone no: " << endl;
        cin >> telno;
    }
    void setmarks()
    {
        cout<<"Enter marks of subject 1: "<<endl;
        cin>>m1;
        cout<<"Enter marks of subject 2: "<<endl;
        cin>>m2;
        cout<<"Enter marks of subject 3: "<<endl;
        cin>>m3;
    }
    void displayinfo() 
    {
        cout << "Name: " << name << endl;
        cout << "Roll no: " << rno << endl;
        cout << "Division: " << div << endl;
        cout << "Date of birth: " << dob << endl;
        cout << "Adhaar no: " << Adhaar << endl;
        cout << "Blood group: " << bgroup << endl;
        cout << "Address: " << address << endl;
        cout << "Telephone no: " << telno << endl;
    }
    static void displayCount()
    {
        cout << "Total number of students: " << ctr << endl;
    }
    friend void displaypercentage(const Student&);
};
int Student::ctr = 0;

void displaypercentage(const Student& st)
{
    float per = ((st.m1 + st.m2 + st.m3) / 300.0) * 100;
    cout << "Percentage: " << per << "%" << endl;
}

int main() 
{
    // Using default constructor
    Student st;
        cout << "Student 1: "<<endl;
        st.setname();
        st.setrno();
        st.setdiv();
        st.setdob();
        st.setadhaar();
        st.setbgroup();
        st.setaddress();
        st.settelno();
        st.setmarks();
    cout << "\nDisplaying student information:" << endl;
     cout << "Student 1:" << endl;
        st.displayinfo();
        displaypercentage(st);
        cout << endl;
        Student::ctr++;
    // Using parameterized constructor
    float sample_marks[3] = {85, 90, 88};
    Student student2("Vaansh", 101, 'B', "27-01-2000", 123456789, "O+", "ABC", 98743, 85, 90, 88);
    cout << "Student 2:" << endl;
    student2.displayinfo();
    displaypercentage(student2);
    cout << endl;
    Student::ctr++;

    // Using copy constructor
    Student student3(student2);
    cout << "Student 3:" << endl;
    student3.displayinfo();
    displaypercentage(student3);
    cout << endl;
    Student::ctr++;
    Student::displayCount();
    return 0;
}


3
#include <iostream>

using namespace std;

class Employee
{
protected:
     string ename;
     int eid;

public:
     Employee()
     {
          ename = '\0';
          eid = 0;
     }
     Employee(string name, int id)
     {
          ename = name;
          eid = id;
     }
     virtual void accept(string n, int id)
     {
          ename = n;
          eid = id;
     }
     virtual void display()
     {
          cout << "Name " << ename << " ID " << eid << endl;
     }
     virtual void earnings() = 0;
};

class SalariedEmployee : public Employee
{
private:
     long salary;

public:
     void accept(string n, int id, long s)
     {
          ename = n;
          eid = id;
          salary = s;
     }
     void earnings()
     {
          cout << "Earnings is " << salary << endl;
     }
     void display()
     {
          cout << "Name " << ename << " ID " << eid << endl;
     }
};

class HourlyEmployee : public Employee
{
private:
     int wage;
     int hours;

public:
     void accept(string n, int id, int w, int h)
     {
          ename = n;
          eid = id;
          wage = w;
          hours = h;
     }
     void earnings()
     {
          cout << "Earnings is " << wage * hours << endl;
     }
     void display()
     {
          cout << "Name " << ename << " ID " << eid << endl;
     }
};

class CommisionEmployee : public Employee
{
private:
     int commission;
     int sales;

public:
     void accept(string n, int id, int c, int s)
     {
          ename = n;
          eid = id;
          commission = c;
          sales = s;
     }
     void earnings()
     {
          cout << "Earnings is " << commission * sales << endl;
     }
     void display()
     {
          cout << "Name " << ename << " ID " << eid << endl;
     }
};

int main()
{
     Employee *a;
     SalariedEmployee b;
     a = &b;
     a->accept("Adam", 1);
     a->display();
     a->earnings();
}

4
#include <iostream>
using namespace std;
class Complex
{
int real;
float img;
public:
Complex()
{
real = 0;
img = 0;
}
Complex(int r, float i)
{
real = r;
img = i;
}
Complex operator+(Complex comp)
{
Complex C;
C.real = real + comp.real;
C.img = img + comp.img;
return (C);
}
Complex operator*(Complex comp)
{
Complex C;
C.real = (real * comp.real) - (img * comp.img);
C.img = (real * comp.img) + (img * comp.real);
return (C);
}
friend Complex operator-(Complex comp1, Complex comp2);
friend Complex operator/(Complex comp1, Complex comp2);
void display(void);
};
// Friend function for subtraction
Complex operator-(Complex comp1, Complex comp2)
{
Complex C;
C.real = comp1.real - comp2.real;
C.img = comp1.img - comp2.img;
return (C);
}
// Friend function for division
Complex operator/(Complex comp1, Complex comp2)
{
Complex C;
C.real = ((comp1.real * comp2.real) + (comp1.img * comp2.img)) / ((comp2.real *
comp2.real) + (comp2.img * comp2.img));
C.img = ((comp1.img * comp2.real) - (comp1.real * comp2.img)) / ((comp2.real *
comp2.real) + (comp2.img * comp2.img));
return (C);
}
void Complex ::display(void)
{
cout << real << "+" << img << "i" << endl;
}
int main()
{
Complex c1, c2, c3, c4, c5, c6;
c1 = Complex(1, 5);
c2 = Complex(4, 6);
c3 = c1 + c2;
c4 = c1 * c2;
c5 = c1 - c2;
c6 = c1 / c2;
cout << "Enter complex no 1 : " << endl;
c1.display();
cout << "Enter complex no 2 : " << endl;
c2.display();
cout << "Addition of the 2 numbers is : " << endl;
c3.display();
cout << "Multiplication of the 2 numbers is : " << endl;
c4.display();
cout << "Subtraction of the 2 numbers is : " << endl;
c5.display();
cout << "Division of the 2 numbers is : " << endl;
c6.display();
return 0;
}

5
#include <iostream>
#include <string.h>
using namespace std;
class hotel{
private:
string cust_name;
int cust_id;
int income;
int age;
string city;
string room_type;
public:
hotel(){
cust_name = "";
cust_id = 0;
income=0;
city="";
room_type ="";
}
void accept(){
cout<<"Welcome to KH Mahal!"<<endl;
cout<<"Enter name : ";
cin>>cust_name;
cout<<endl;
cout<<"Enter age : ";
cin>>age;
cout<<endl;
cout<<"Enter customer id : ";
cin>>cust_id;
cout<<endl;
cout<<"Enter income : ";
cin>>income;
cout<<endl;
cout<<"Enter city : ";
cin>>city;
cout<<endl;
cout<<"Enter room type ";
cin>>room_type;
cout<<endl;
cout<<"Thankyou for your response"<<endl;
}
void display(){
cout<<"\nCustomer information : ";
cout<<"\nName : "<<cust_name;
cout<<"\nAge : "<<age;
cout<<"\nIncome : "<<income;
cout<<"\nCity : "<<city;
cout<<"\nRoom type : "<<room_type;
}
void get_age(){
try{
if (age<18 || age>55){
throw(age);
}
}
catch(int i){
cout<<"Entered age is invalid.";
}
}
void getincome(){
try{
if (income<50000 || income>100000){
throw(income);
}
}
catch(int i){
cout<<"\nEntered income is invalid.";
}
}
void getcity(){
try{
if(city != "Pune" || city!="Mumbai"){
throw(city);
}
}
catch(string i){
cout<<"\nInvalid city";
}
}
void get_room_type(){
try{
if(room_type != "Duplex" || room_type !="Super Dulex"){
throw(room_type);
}
}
catch(string i){
cout<<"\nInvalid room type entered."<<endl;
}
}
};
int main(){
hotel h;
h.accept();
h.get_age();
h.getincome();
h.getcity();
h.display();
}
