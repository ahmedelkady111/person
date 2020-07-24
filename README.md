// my test.cpp : This file contains the 'main' functio
//#include "pch.h"
#include <iostream>
using namespace std;
//abstract class
class person {
protected:
	char name[40];
public:
	void get_name() {
		cout << "enter the name: "; cin >> name;
	}
	virtual void get_data() = 0;  // to get the data of student and the proffesor;
	virtual bool isoutstanding() = 0; // the good person
};
class student :public person
{
private:
	int degre;
public:
	void get_data() {
		person::get_name();
		cout << "enter the degre: "; cin >> degre;
	}
	bool isoutstanding() {
		return(degre > 90 ? true : false);
	}
	
};
class professor :public person
{
private:
	int numpubs;
public:
	void get_data() {
		person::get_name();
		cout << "Enter number of professor’s publications: "; cin >> numpubs;
	}
	bool isoutstanding() {
		return(numpubs > 100 ? true : false);
	}

};

int main()
{
	person* ptr[100];
	char choice;
	int n = 0;
	do {
		cout << "enter the student or professor(s/p)"; cin >> choice;
		if (choice == 's')ptr[n] = new student;
		if (choice == 'p')ptr[n] = new professor;
		ptr[n++]->get_data();
		cout << "if you want to continue enter y else enter no(y/n)"; cin >> choice;
	} while (choice == 'y');
	for (int i = 0; i < n; i++) {
		if (ptr[i]->isoutstanding())
			cout << "This person is outstanding\n";
	}
	return 0;
}

// Run program: Ctrl + F5 or Debug > Start Without Debugging menu
// Debug program: F5 or Debug > Start Debugging menu

// Tips for Getting Started: 
//   1. Use the Solution Explorer window to add/manage files
//   2. Use the Team Explorer window to connect to source control
//   3. Use the Output window to see build output and other messages
//   4. Use the Error List window to view errors
//   5. Go to Project > Add New Item to create new code files, or Project > Add Existing Item to add existing code files to the project
//   6. In the future, to open this project again, go to File > Open > Project and select the .sln file
