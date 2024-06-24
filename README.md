# Module-10-Final-Group-Project---Contractor-Code
This is a GitHub Repository Link for the final group project of COP2360-1 Module 10 on behalf of Carlos Gonzalez, Marcello Gonzalez, Dimitri Finlay, Ottavio Magarelli, and Megan Camiel.

using System;

// Contractor class to represent general contractor information

class Contractor

{

    // Properties to store contractor information

    public string Name { get; set; }

    public int Number { get; set; }

    public DateTime StartDate { get; set; }

    // Constructor to initialize contractor information

    public Contractor(string name, int number, DateTime startDate)

    {

        Name = name;

        Number = number;

        StartDate = startDate;

    }

}

// Subcontractor class derived from Contractor class

class Subcontractor : Contractor

{

    // Properties to store additional subcontractor information

    public int Shift { get; set; }

    public double HrlyRate { get; set; }

    // Constructor to initialize subcontractor information, leveraging base class constructor

    public Subcontractor(string name, int number, DateTime startDate, int shift, double hrlyRate)

        : base(name, number, startDate)

    {

        Shift = shift;

        HrlyRate = hrlyRate;

    }

    // Method to calculate pay with shift differential for night shift

    public float CalcPay()

    {

        // Applying a 3% shift differential for night shift (Shift = 2)

        float shiftDiff = (Shift == 2) ? 0.03f : 0f;

        return (float)(HrlyRate * (1 + shiftDiff));

    }

}

// Program class containing the entry point of the application

class Program

{

    // Main method where the program execution begins

    static void Main()

    {

        Console.Write("Enter number of subcontractors: ");

        int numSubcontractors = int.Parse(Console.ReadLine());; // Number of subcontractors

        for (int i = 1; i <= numSubcontractors; i++)

        {

        // User input to create a subcontractor

        Console.WriteLine("\nEnter subcontractor {0} details:", i);

        Console.Write("Name: ");

        string name = Console.ReadLine();

        Console.Write("Number: ");

        int number = int.Parse(Console.ReadLine());

        Console.Write("Start Date: ");

        DateTime startDate = Convert.ToDateTime(Console.ReadLine());

        Console.Write("Shift (1 for day, 2 for night): ");

        int shift = int.Parse(Console.ReadLine());

        Console.Write("Hourly Pay Rate: ");

        double hourlyRate = double.Parse(Console.ReadLine());

        Console.Write("Hours Worked: ");

        float hoursWorked = float.Parse(Console.ReadLine());

        Console.WriteLine("------------------------------\n");

        // Creating a Subcontractor object

        Subcontractor subcontractor = new Subcontractor(name, number, startDate, shift, hourlyRate);

        // Displaying subcontractor information

        Console.WriteLine("\nSubcontractor {0} Information:", i);

        Console.WriteLine($"Name: {subcontractor.Name}");

        Console.WriteLine($"Number: {subcontractor.Number}");

        Console.WriteLine($"Start Date: {subcontractor.StartDate.ToShortDateString()}");

        Console.WriteLine($"Shift: {subcontractor.Shift}");

        Console.WriteLine($"Hourly Pay Rate: {subcontractor.HrlyRate:C}");

        Console.WriteLine($"Hours worked: {hoursWorked:C}");

        // Calculating and displaying pay

        float pay = subcontractor.CalcPay() * hoursWorked;;

        Console.WriteLine($"Total Pay: {pay:C}");

        Console.WriteLine("------------------------------\n");

        }
    }
}
