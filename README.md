//# Hospital-management-system
//This a code of hospital management system in C++. It is a console based program that saves patient, doctors and other staff member data.

#include<iostream>
#include<conio.h>
#include<string>
#include<fstream>
using namespace std;
void general_entry();
void patient_entry();
void doctor_entry();
void other_entry();
void read_patient_record();
void read_doctor_record();
void read_other_record();
void delete_record();
void calculate_bill();
void edit_patient_record();
void edit_doctor_list();
void doctor_appointment();
int main()
{
	int x=1;
	int n;
	do
	{
		cout << "Press 1 for general entry. \nPress 2 to access Patients records. \nPress 3 to access doctors records. \nPress 4 to acccess other records." << endl;
		cout << "Press 5 to edit Patients records. \nPress 6 to edit doctors list. \nPress 7 to Doctor Appointment. \nPress 8 to calculate Bill. " << endl;
		cout << "Press 9 to delete patient record. " << endl;
		cin >> n;
		switch (n)
		{
		case 1:
		{
			general_entry();				//From this function we can entry patient, doctor or any other record.
			break;
		}
		case 2:
		{
			read_patient_record();			//This function is to read patient record file from system and display it.
			break;
		}
		case 3:
		{
			read_doctor_record();			//This function is to read doctor record file from system and display it.
			break;
		}
		case 4:
		{
			read_other_record();				//This function is to read other record file from system and display it.
			break;
		}
		case 5:
		{
			edit_patient_record();				//This function is used to add data to patient file later.
			break;
		}
		case 6:
		{
			edit_doctor_list();					//This function is used to add data to doctor file later.
			break;
		}
		case 7:
		{
			doctor_appointment();					//This function is used to get an appointment from doctor for patient.
			break;	
		}
		case 8:
		{
			calculate_bill();					//This function is used to calculate bill of patients.
			break;
		}
		case 9:
		{
			delete_record();					//this function is used to delete a specific record.
		}

		}
		cout << "Press any integer to run agian or Press 0 to quit. " << endl;
		cin >> x;
	} while (x != 0);


	_getch();
	return 0;
}
void general_entry()
{
	int enter;
	cout << "Press 1 to make a entry of a patient. \nPress 2 to make a entry of a doctor. \nPress 3 ro make a entry of other staff member." << endl;
	cin >> enter;
	switch (enter)
	{
	case 1:
	{
		patient_entry();			//this function is used for patient entry
		break;
	}
	case 2:
	{
		doctor_entry();				//this function is used for doctor entry
		break;
	}
	case 3:
	{
		other_entry();					//this function is used for other entry
		break;
	}
	}
}
void patient_entry()
{
	string Patient_name, Patient_ID_cardnum, Patient_gender, Patient_contactnum, Patient_emergencynum, Patient_bloodtype, Patient_problem, Patient_age, Patient_Room_bed;
	fstream write_patient_data;
	string fname;
	cout << "Enter Patient name : " << endl;
	cin.ignore();
	getline(cin, Patient_name);
	cout << "Enter Patient Identity card number :" << endl;
	getline(cin, Patient_ID_cardnum);
	cout << "Enter Patient Identity card number/passport number as file name to create it : " << endl;
	getline(cin, fname);
	write_patient_data.open(fname, ios::out|ios::app);
	if (write_patient_data.is_open())
	{
		cout << "Enter Patient age : " << endl;						//These line will get characterstics of patients and store them in string variable.
		getline(cin, Patient_age);
		cout << "Enter Patient gender : " << endl;
		getline(cin, Patient_gender);
		cout << "Enter Patient contact number : " << endl;
		getline(cin, Patient_contactnum);
		cout << "Enter Patient emergency contact number : " << endl;
		getline(cin, Patient_emergencynum);
		cout << "Enter Patient Blood type : " << endl;
		getline(cin, Patient_bloodtype);
		cout << "Write down the reson of visit, known disease of patient, vital signs of problem : " << endl;
		getline(cin, Patient_problem);
		cout << "Enter Room or Bed for patient : " << endl;
		getline(cin, Patient_Room_bed);


		write_patient_data <<"NAME : " << Patient_name << endl;						//these line will add the characterstics of patient to file.
		write_patient_data <<"Age : " << Patient_age << endl;
		write_patient_data <<"Blood type : " << Patient_bloodtype << endl;
		write_patient_data <<"Gender : " << Patient_gender << endl;
		write_patient_data <<"Identity card / Passport card number : " << Patient_ID_cardnum << endl;
		write_patient_data <<"Contact number : " << Patient_contactnum << endl;
		write_patient_data <<"Emergency Contact number : " << Patient_emergencynum << endl;
		write_patient_data <<"Problem / Disease : " << Patient_problem << endl;
		write_patient_data.close();
	}
	else
	{
		cout << "Error! File is not open. " << endl;
	}
}
void doctor_entry()
{
	string doctor_name, doctor_DOB, doctor_gender, doctor_ID_cardnum, doctor_contactnum, doctor_emergencynum, doctor_spec;
	fstream write_doctor_data;
	string fname;
	cout << "Enter Doctor name : " << endl;
	cin.ignore();
	getline(cin, doctor_name);
	cout << "Enter Doctor Identity card number :" << endl;
	getline(cin, doctor_ID_cardnum);
	cout << "Enter Doctor Identity card number/passport number as file name to create it : " << endl;
	getline(cin, fname);
	write_doctor_data.open(fname, ios::out | ios::app);
	if (write_doctor_data.is_open())
	{														//These line will get characterstics of doctors and store them in string variable.
		cout << "Emter Doctor specilization : " << endl;
		getline(cin, doctor_spec);
		cout << "Enter doctor Date of Birth : " << endl;
		getline(cin, doctor_DOB);
		cout << "Enter doctor gender : " << endl;
		getline(cin, doctor_gender);
		cout << "Enter doctor contact number : " << endl;
		getline(cin, doctor_contactnum);
		cout << "Enter doctor emergency contact number : " << endl;
		getline(cin, doctor_emergencynum);

		write_doctor_data <<"Name : " << doctor_name << endl;							//these line will add the characterstics of doctor to file.
		write_doctor_data <<"Date of Birth : " << doctor_DOB << endl;						
		write_doctor_data <<"Gender : " << doctor_gender << endl;
		write_doctor_data <<"Identity card / Passport number : " << doctor_ID_cardnum << endl;
		write_doctor_data <<"Contact number : " << doctor_contactnum << endl;
		write_doctor_data <<"Emergency Contact number : " << doctor_emergencynum << endl;
		write_doctor_data.close();


		fstream write_doctor_list;											//these line of code will add doctor name and doctor speciality in sepetrate file.
		write_doctor_list.open("Doctors List.txt", ios::out | ios::app);
			if (write_doctor_list.is_open())
			{
				write_doctor_list << doctor_name << " " << doctor_spec;
				write_doctor_list.close();
			}
			else
			{
				cout << "Error! Doctors List File is not open. " << endl;
			}
	}
	else
	{
		cout << "Error! File is not open. " << endl;
	}
}
void other_entry()
{
	string other_roll, other_name, other_DOB, other_gender, other_ID_cardnum, other_contactnum;
	fstream write_other_data;
	string fname;
	cout << "Enter the roll of person : " << endl;
	cin.ignore();
	getline(cin, other_roll);
	cout << "Enter name : " << endl;
	getline(cin, other_name);
	cout << "Enter card number :" << endl;
	getline(cin, other_ID_cardnum);
	cout << "Enter Patient Identity card number/passport number as file name to create it : " << endl;
	getline(cin, fname);
	write_other_data.open(fname, ios::out | ios::app);
	if (write_other_data.is_open())
	{														//These line will get characterstics of other staff-member and store them in string variable.
		cout << "Enter Date of Birth : " << endl;
		getline(cin, other_DOB);
		cout << "Enter gender : " << endl;
		getline(cin, other_gender);
		cout << "Enter contact number : " << endl;
		getline(cin, other_contactnum);;


		write_other_data <<"Name : " << other_name << endl;				//these line will add the characterstics of other staff-member to file.
		write_other_data <<"Date of Birth : " << other_DOB << endl;
		write_other_data <<"Gender : " << other_gender << endl;
		write_other_data <<"Identity card / Passport number : " << other_ID_cardnum << endl;
		write_other_data <<"Contact Number : " << other_contactnum << endl;
		write_other_data.close();
	}
	else
	{
		cout << "Error! File is not open. " << endl;
	}
}
void read_patient_record()
{
	string fname;
	cout << "Enter patient Identity card / Passport number as a file name to access Patient record" << endl;
	cin.ignore();
	getline(cin, fname);
	ifstream read_patient_data(fname);
	if (read_patient_data.is_open())
	{
		string read;
		while (getline(read_patient_data, read))
		{
			cout << read << endl;
			read_patient_data.close();
		}
	}
	else
	{
		cout << "Error! File is not open. " << endl;
	}
}
void read_doctor_record()
{
	string fname;
	cout << "Enter patient Identity card / Passport number as a file name to access doctor record" << endl;
	cin.ignore();
	getline(cin, fname);
	ifstream read_doctor_data(fname);
	if (read_doctor_data.is_open())
	{
		string read;
		while (getline(read_doctor_data, read))
		{
			cout << read << endl;
		}
		read_doctor_data.close();
	}
	else
	{
		cout << "Error! File is not open. " << endl;
	}
}
void read_other_record()
{
	string fname;
	cout << "Enter Identity card number as a file name to access record" << endl;
	cin.ignore();
	getline(cin, fname);
	ifstream read_other_data(fname);
	if (read_other_data.is_open())
	{
		string read;
		while (getline(read_other_data, read))
		{
			cout << read << endl;
		}
		read_other_data.close();
	}
	else
	{
		cout << "Error! File is not open. " << endl;
	}
}
void edit_patient_record()
{
	string fname, text;
	cout << "Enter patient Identity card / Passport number as a file name to access Patient record" << endl;
	cin.ignore();
	getline(cin, fname);
	ofstream edit_patient_data(fname,ios::app);
	if (edit_patient_data.is_open())
	{
		cout << "Enter text to add into patient file : " << endl;
		getline(cin, text);
		edit_patient_data << text << endl;
	}
	else
	{
		cout << "Error! File is not open. " << endl;
	}
}
void edit_doctor_list()
{
	string deleteline, line, out;
	fstream edit_doctor_list;
	edit_doctor_list.open("Doctors List.txt", ios::in);
	cin.ignore();
	while (getline(edit_doctor_list, out))
	{
		cout << out << endl;	
	}
	edit_doctor_list.close();
	edit_doctor_list.open("Doctors List.txt",ios::in);
	ofstream temp;
	temp.open("temp.txt");
	cout << "Which line do you want to remove? ";
	cin >> deleteline;



	while (getline(edit_doctor_list, line))
	{
		if (line != deleteline)
		{
			temp << line << endl;
		}
	}

	temp.close();
	edit_doctor_list.close();
	remove("Doctor Lists.txt");
	rename("temp.txt", "Doctors List.txt");
}
void delete_record()
{
	string line;
	cout << "Enter Identity card number / Passport number as a file name to delete its data" << endl;
	cin.ignore();
	getline(cin, line);
	if (remove(line.c_str())==0)
	{
		cout << "Record has been successfully deleted. " << endl;
	}
	else
	{
		cout << "Error! record is not deleted. " << endl;
	}
}
void calculate_bill()
{
	float days, charges, Med_fee, insurance;
	string id;
	cout << "Enter Identity card number/passport number of patient as file name to calculate Bill." << endl;
	cin.ignore();
	getline(cin,id);
	ifstream read_patient_data(id);
	if (read_patient_data.is_open())
	{
		string read;
		while (getline(read_patient_data, read))
		{
			cout << read << endl;
		}
		read_patient_data.close();
	}
	else
	{
		cout << "Error! File is not open. " << endl;
	}
	cout << "Enter the number of days patient spent : " << endl;
	cin >> days;
	cout << "Enter charges per day of a room or a bed : " << endl;
	cin >> charges;
	cout << "Enter the doctor and medial fee : " << endl;
	cin >> Med_fee;
	cout << "Enter the amount covered by insurance : " << endl;
	cin >> insurance;
	cout << "Total Bill = " << (days * charges) + Med_fee - insurance << " Rupees." << endl;
}
void doctor_appointment()
{
	string patient_ID;
	fstream view_doctor_list;
	view_doctor_list.open("Doctors List.txt", ios::in);
		if (view_doctor_list.is_open())
		{
			string read;
			cin.ignore();
			while (getline(view_doctor_list, read))
			{
				cout << read << endl;
			}
			view_doctor_list.close();
		}
		else
		{
			cout<<"Error! File is not open." << endl;
		}
		cout << "Enter Identity card number of patient as file name for appointment : "<<endl;
		getline(cin, patient_ID);
		fstream patient_file;
		patient_file.open(patient_ID);
		if (patient_file.is_open())
		{
			string doc_name, time;
			cout << "Enter name of doctor for appointment : " << endl;
			getline(cin, doc_name);
			cout << "Enter time for appointment : " << endl;
			getline(cin, time);
			patient_file << doc_name << endl;
			patient_file << time << endl;
			patient_file.close();
		}
		else
		{
			cout<< "Error! File is not open." << endl;
		}

}
