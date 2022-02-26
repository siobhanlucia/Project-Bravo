//Project-Bravo

using System;
using System.Collections.Generic;
using Project_Bravo;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.IO;

namespace Project_Bravo
{
    internal class List
    {
        static List<string> employees = new List<string>();
        static void Main(string[] args)
        {
            int Option;
            Console.WriteLine("==========Employee Information==========");
            //Landing page
            do
            {
                Console.WriteLine("Please enter a number for one of the following options:");

                Console.WriteLine("1. Add Information");
                Console.WriteLine("2. Insert Information");
                Console.WriteLine("3. Update Information");
                Console.WriteLine("4. Delete Information");
                Console.WriteLine("5. Search Information");
                Console.WriteLine("6. Display Information");
                Console.WriteLine("7. Search Information using Index Number");
                Console.WriteLine("8. Write File of Information Gathered"); //added option to display file information gathered
                Console.WriteLine("0. to end this program ");
                Option = Convert.ToInt32(Console.ReadLine()); //Converted from string to int for case numbers

                switch (Option)
                {
                    case 1:
                        Console.WriteLine("You have selected option 1 to Add data into file. Please enter how many records you want to add: ");
                        int recordnumber = Convert.ToInt32(Console.ReadLine()); // added input for number of records to assist with location input for case 2 and list clarity
                        for (int i = 0; i < recordnumber; i++)
                        {
                            AddName(); //function
                        }
                        break;
                    case 2:
                        Console.WriteLine("You have selected option 2 to insert information in the file");
                        InsertName();
                        break;
                    case 3:
                        Console.WriteLine("You have selected option 3 to update information in the file");
                        UpdateName();
                        break;
                    case 4:
                        Console.WriteLine("You have selected option 4 to delete data from file");
                        DeleteName();
                        break;
                    case 5:
                        Console.WriteLine("You have selected option 5 to search data from file");
                        SearchName();
                        break;
                    case 6:
                        Console.WriteLine("You have selected option 6 to display information from file");
                        DisplayData();
                        break;
                    case 7:
                        Console.WriteLine("You have selected option 7 to search data from file using index number");
                        SearchLoc();
                        break;
                    case 8:
                        Console.WriteLine("You have selected option 8 to write a file dictacting all information gathered");
                        FileWrite();
                        break;
                    case 0:
                        Console.WriteLine("Thanks for using this project");
                        Console.ReadLine();
                        break;
                    default:
                        Console.WriteLine("Not in the list, Please select the correct option");
                        break;
                }
                foreach (string str in employees)
                {
                    Console.WriteLine(str); //added output display of list to confirm the list function is working correctly
                }
            } while (Option != 0);
        }

        static string AddName() //function
        {
            string name;
            Console.WriteLine("Please enter the employee's first name: ");
            string firstName = Console.ReadLine();
            Console.WriteLine("Please enter the employee's last name: ");
            string lastName = Console.ReadLine();
            Console.WriteLine("Please enter employee's email id: ");
            string emailid = Console.ReadLine(); //added email 
            Console.WriteLine("Please enter employee's mobile phone number: ");
            string mobilephone = Console.ReadLine(); // added mobile phone
            Console.WriteLine("Please enter employee's adress: ");
            string address = Console.ReadLine(); //added address
            employees.Add(firstName + " " + lastName + ", " + emailid + ", " + mobilephone + ", " + address); //adding first records to list function
            return name = firstName + " " + lastName + ", " + emailid + ", " + mobilephone + ", " + address;


            Console.ReadKey();
        }
        static void InsertName()
        {
            Console.WriteLine("Please enter the first name: ");
            string firstName = Console.ReadLine();
            Console.WriteLine("Please enter the last name: ");
            string lastName = Console.ReadLine();
            Console.WriteLine("Please enter employee's email id: ");
            string emailid = Console.ReadLine();  //added email 
            Console.WriteLine("Please enter employee's mobile phone number: ");
            string mobilephone = Console.ReadLine();  //added mobile phone
            Console.WriteLine("Please enter employee's adress: ");
            string address = Console.ReadLine(); //added address
            Console.WriteLine("Please enter the location you'd like to insert this record: (with the first entry as 0, second = 1,etc)");
            int loc = Convert.ToInt32(Console.ReadLine()); //convert to number to indicate place in list
            if (loc > employees.Count) //if location number is outside of the number of listed information recorded then this will be communicated
            {
                Console.WriteLine("Location out of range");
            }
            else
            {
                employees.Insert(loc, firstName + ", " + lastName + ", " + emailid + ", " + mobilephone + ", " + address);
            }
            Console.ReadKey();
        }
        static void UpdateName()
        {
            Console.WriteLine("Please enter the number of the existing employee name you would like to replace: (with the first entry as 0, second = 1,etc)");
            foreach (string str in employees)
            {
                Console.WriteLine(str);
            }
            int loc = Convert.ToInt32(Console.ReadLine());
            Console.WriteLine("Existing employee: " + employees[loc]);
            Console.WriteLine("Please enter the name you wish to replace the existing employee: ");
            Console.WriteLine("Please enter first name: ");
            string firstName = Console.ReadLine();
            Console.WriteLine("Please enter last name: ");
            string lastName = Console.ReadLine();
            Console.WriteLine("Please enter employee's email id: ");
            string emailid = Console.ReadLine();
            Console.WriteLine("Please enter employee's mobile phone number: ");
            string mobilephone = Console.ReadLine();
            Console.WriteLine("Please enter employee's adress: ");
            string address = Console.ReadLine();
            employees[loc] = (firstName + ", " + lastName + ", " + emailid + ", " + mobilephone + ", " + address);
            Console.WriteLine("The updated information for " + loc + " is " + firstName + " " + lastName + ", " + emailid + ", " + mobilephone + ", " + address);
            Console.ReadKey();

        }

        static void DeleteName() //function
        {
            Console.WriteLine("Please enter the number of the existing employee name you would like to delete: (with the first entry as 0, second = 1,etc)");
            foreach (string str in employees)
            {
                Console.WriteLine(str);
            }
            int loc = Convert.ToInt32(Console.ReadLine()); //convertins string to int for specified index
            Console.WriteLine("Existing employee: " + employees[loc]);
            employees.RemoveAt(loc); //removing chosen employee
            Console.WriteLine("The updated employees records are: ");
            foreach (string str in employees)
            {
                Console.WriteLine(str); //new list with record deleted
            }
            Console.ReadKey();
        }
        static void SearchName() //function
        {
            Console.WriteLine("Please enter the first name of the existing employee name you would like to confirm is in the system:");
            string SearchRecord = Console.ReadLine();
            string employeesData; //employees full name

            for (int iCount = 0; iCount < employees.Count; iCount++) //iCount int variable
            {

                if (employees[iCount].Contains(SearchRecord)) //Contains the first name that user has input
                {
                    employeesData = employees[iCount]; //accessing employee full name from user input
                    Console.WriteLine(employeesData); //outputting user full name
                }
            }
            Console.ReadKey();

        }
        static void DisplayData() //function
        {
            Console.WriteLine(string.Join(", ", employees)); //string.Join() method concatenates the list elements with a seperator in between
            Console.ReadKey();

        }
        static void SearchLoc() //function
        {
            Console.WriteLine("Please enter the index number of the existing employee name you would like to confirm is in the system:");
            int loc = Convert.ToInt32(Console.ReadLine());
            Console.WriteLine("Existing employee: " + employees[loc]);

            Console.ReadKey();
        }
        static void FileWrite() //function
        {
            string folder = "Employee Information"; //Folder where file is created
            string fileName = "EmployeeInformation.txt"; // Filename
            string fullPath = folder + fileName; // Fullpath
            string[] employee = { string.Join(", ", employees) }; //List from display
            File.WriteAllLines(fullPath, employee);
            using (StreamWriter writer = new StreamWriter(fullPath)) //write file using SreamWriter
            {
                Console.WriteLine(string.Join(", ", employees));
            }
            Console.ReadKey();
            
            
            // Read  file  
           string readfile = File.ReadAllText(fullPath);
            Console.WriteLine(readfile);

            Console.ReadKey();
        }

    }
}


