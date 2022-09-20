- 👋 Hi, I’m @EduardoRodriguess
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
EduardoRodriguess/EduardoRodriguess is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading;
using System.Threading.Tasks;

namespace ATM_BANK
{
    internal class Program
    {
        String cardNum;
        String firstName;
        String lastName;
        double balance;

        public Program (string cardNum, string firstName, string lastName, double balance)
        {
            this.cardNum = cardNum;
            this.firstName = firstName;
            this.lastName = lastName;
            this.balance = balance;
        }
        public String GetCardNum() { return cardNum; }
        public String GetFirstName() { return firstName; }
        public String GetLastName() { return lastName; }
        public double GetBalance() { return balance; }
        public void SetCardNum(string newCardNum) { cardNum = newCardNum; }
        public void SetFirstName(string newFirstName) { firstName = newFirstName; }
        public void SetLastName(string newLastName) { lastName = newLastName; }
        public void SetBalance(double newBalance) { balance = newBalance; }
        static void Main(string[] args)
        {
            Console.SetCursorPosition(0, 0);
            Console.CursorVisible = false;
            for (int i = 0; i < 10; i++)
            {
                Console.WriteLine(i + "|");
                Thread.Sleep(100);
            }
            Console.SetCursorPosition(0, 0);
            Console.CursorVisible = true;
            Console.Clear();
            Console.ForegroundColor = ConsoleColor.Cyan;
            Console.WriteLine("--- THIS IS A ATM ---\n");
            Console.ForegroundColor = ConsoleColor.White;
            Console.WriteLine("Enter Your CARD NUMBER\n");

            void printOptions()
            {
                Console.ForegroundColor = ConsoleColor.White;
                Console.WriteLine(" 1. DEPOSIT");
                
                Console.WriteLine(" 2. WITHDRAW");
               
                Console.WriteLine(" 3. SHOW BALANCE");
                Console.ForegroundColor = ConsoleColor.Red;
                Console.WriteLine(" 4. EXIT");
                
            }
            void Deposit (Program currentUser)
            {
                Console.ForegroundColor = ConsoleColor.White;
                Console.WriteLine("How much $$ do you wanna DEPOSIT? ");
                int deposit = int.Parse(Console.ReadLine());
                currentUser.SetBalance(currentUser.GetBalance() + deposit);
                Console.WriteLine("Your Current Balance: \n" + currentUser.GetBalance());
                Console.ReadLine();
                Console.Clear();
                printOptions();
            }
            void WithDraw (Program currentUser2)
            {
                Console.ForegroundColor = ConsoleColor.White;
                Console.WriteLine("How much money do you wanna WITHDRAW? ");
                int withDraw = int.Parse(Console.ReadLine());
                currentUser2.SetBalance(currentUser2.GetBalance () - withDraw);
                Console.WriteLine("Your Current Balance: \n" + currentUser2.GetBalance());
               
                Console.ReadLine();
                Console.Clear();
                printOptions();
            }
            void ShowBalance(Program currentUser3)
            {
                Console.ForegroundColor = ConsoleColor.White;
                Console.WriteLine("Your Current Balance: \n" + currentUser3.GetBalance());
                Console.ReadLine();
                Console.Clear();
                printOptions();
            }
            List<Program> list = new List<Program>();
            list.Add(new Program("1234", "Eduardo", "Rodrigues", 8000.50));
            list.Add(new Program("4321", "Roberto", "Silva", 1003.50));
            list.Add(new Program("3242", "Leonardo", "Silva", 2304.50));
            list.Add(new Program("9999", "Ana", "Silva", 841.50));
            list.Add(new Program("1111", "Joao", "Silva", 100.50));

            String cardNumber = "";
            Program currentUser4;

            while (true)
            {
                cardNumber = Console.ReadLine();
                currentUser4 = list.FirstOrDefault(a => a.cardNum == cardNumber);
                if(currentUser4 != null)
                {
                    break;
                    Console.Clear();
                }
                else
                {
                    Console.WriteLine("Invalid Card Number");
                }
            }
            int options = 0;
            

            while (true)
            {
                Console.ForegroundColor = ConsoleColor.Yellow;
                Console.WriteLine("WELCOME " + currentUser4.GetFirstName() + " " + currentUser4.GetLastName());

                printOptions();

                do
                {
                    try
                    {
                        options = int.Parse (Console.ReadLine());
                        Console.Beep();
                        if(options == 1) { Deposit(currentUser4); }
                        else if(options == 2) { WithDraw(currentUser4); }
                        else if(options == 3) { ShowBalance(currentUser4);}
                    }
                    catch { }
                } while (options != 4);
                break;
            }
        }
    }
}
