using System;

namespace ParkingSystem {
    class Program {
        static void Main(string[] args) {
            while (true) {
                try {
                    string plateNum;
                    string type; 
                    string brand;
                    
                    Console.Write("Plate No.    : ");
                    plateNum = Console.ReadLine();
                
                    Console.Write("Vehicle Type : ");
                    type = Console.ReadLine();
                    
                    // Ensure the vehicle type is in uppercase for consistency
                    type = type.ToUpper();
                    
                    Console.Write("Vehicle Brand: ");
                    brand = Console.ReadLine();
                    
                    DateTime parkIn = DateTime.Now;
                    Console.WriteLine("\nParking In(Date/Time) : {0}", parkIn.ToString("MM/dd/yyyy hh:mm:ss tt"));
                    
                    Console.Write("Parking Out(Time)     : ");
                    
                    string timeInput = Console.ReadLine();
                    
                    DateTime parkOut = DateTime.Parse($"{parkIn.ToString("MM/dd/yyyy")} {timeInput}");
                    
                    Vehicle v = new Vehicle(plateNum, type, brand, parkIn, parkOut);
                    
                    v.MainSystemOutput();
                    
                    Console.WriteLine("\nType 'quit' to exit or press any key to continue.");
                    string input = Console.ReadLine();
                    if (input.ToLower() == "quit") {
                        break;
                    }
                }
                catch (Exception e) {
                    Console.WriteLine($"Error: {e.Message}");
                }
            }
        }
    }
    
    class Vehicle {
        public string vehicleType;
        public string vehicleBrand;
        public string vehiclePlate;
        public DateTime parkIn;
        public DateTime parkOut;
        
        public Vehicle(string vehiclePlate, string vehicleType, string vehicleBrand, DateTime parkIn, DateTime parkOut) {
            this.vehiclePlate = vehiclePlate;
            this.vehicleType  = vehicleType;
            this.vehicleBrand = vehicleBrand;
            this.parkIn       = parkIn;
            this.parkOut      = parkOut;
        }

        public void MainSystemOutput() {
            double flagDown    = 0;
            double addAmount   = 0; 
            double totalAmount = 0;
            
            TimeSpan parkingTime = parkOut - parkIn;
            
            switch(vehicleType) {
                case "MOTORBIKE":
                    flagDown  = 20.00;
                    addAmount = 5.00;
                    break;
                case "SUV":
                case "VAN":
                    flagDown  = 40.00;
                    addAmount = 20.00;
                    break;
                case "SEDAN":
                    flagDown  = 30.00;
                    addAmount = 15.00;
                    break;
                default:
                    Console.WriteLine("Invalid Vehicle Type.");
                    return;
            }
            
            
            totalAmount = flagDown + addAmount * Math.Ceiling(parkingTime.TotalHours);
            
            
            Console.WriteLine("\nOutput:\nDate/Time In: " + parkIn.ToString("MM/dd/yyyy hh:mm:ss tt"));
            Console.WriteLine("         Out: " + parkOut.ToString("MM/dd/yyyy hh:mm:ss tt"));
            Console.WriteLine("Parking Time: " + Math.Ceiling(parkingTime.TotalHours) + " hrs");
            Console.WriteLine("Amount      : " + totalAmount.ToString("F2"));
        }
    }
}
