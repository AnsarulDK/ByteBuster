using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.IO;

namespace ByteBuster
{
    class Program
    {
        static void Main(string[] args)
        {
            Initialisering();

            int decVærdi, hit = 0, miss = 0, count = 0, x = 0, y = 0;
            List<string> lines;
            string filePath;
            string valg = "";

            try
            {
                Fil_håndetering();

                //LOOP:do
                do
                {
                    //Console.Clear();
                    Random randBin = new Random();
                    int nummer = randBin.Next(128);
                    string binVærdi = Convert.ToString(nummer, 2);
                    Console.SetCursorPosition(x + 8, y + 8);
                    Console.WriteLine("\n  \n");
                    Console.Write("\n Gæt værdien af dette binære tal      > " + binVærdi + " <  ");
                    decVærdi = Convert.ToInt32(Console.ReadLine());

                    if (nummer == decVærdi)
                    {
                        Console.Write("           Korrekt");
                        count++;
                        Forsøg(count);
                        hit++;
                        Resultat(hit, miss);
                        if (hit == 3)
                        {
                            Console.SetCursorPosition(x, y + 28);
                            Console.Write("Du har vandt denne runde - Tillykke");
                            //Skrivning på fil
                            Console.WriteLine("\n Indtast dit navn: ");
                            string input = Console.ReadLine();
                            lines.Add(input);
                            File.WriteAllLines(filePath, lines);
                            break;
                        }
                    }
                    else
                    {
                        Console.Write("           Forkert");
                        count++;
                        Forsøg(count);
                        miss++;
                        Resultat(hit, miss);
                        if (miss == 3)
                        {
                            Console.SetCursorPosition(x, y + 24);
                            Console.Write("Du har tabt denne runde - Desværre ");

                            Console.Write("Vil du prøve igen (y/n): ");
                            valg = Console.ReadLine();
                            if (valg == "y")
                            {
                                count = 0; hit = 0; miss = 0; x = 0; y = 0;
                                Console.Clear();
                                Console.SetCursorPosition(x + 6, y + 6);
                                Initialisering();
                                Fil_håndetering();
                                continue;
                            }
                            else
                                break;
                        }
                    }
                    x = x + 2;
                    y = y + 2;
                } while (hit != 3 || miss != 3);
                void Resultat(int w, int z)
                {
                    Console.SetCursorPosition(1, 22);
                    Console.WriteLine("\n Hit: {0}  Miss:{1}", w, z);
                }
                void Forsøg(int r)
                {
                    Console.SetCursorPosition(1, 20);
                    Console.WriteLine("Forsøg # " + r);
                }
                void Fil_håndetering()
                {
                    //Læsning på file
                    filePath = @"C:\Users\mdans\OneDrive\Desktop\Vinderliste.txt";
                    lines = new List<string>();
                    lines = File.ReadAllLines(filePath).ToList();
                    foreach (String line in lines)
                    {
                        Console.WriteLine(line);
                    }
                }
                Console.ReadLine();
            }
            catch
            {
                Console.WriteLine("Du skal indtaste kun hel tal/nummer");
                Console.WriteLine("Sluk vinduet og prøv igen");
            }
            void Initialisering()
            {
                Console.BackgroundColor = ConsoleColor.Blue;
                Console.ForegroundColor = ConsoleColor.White;
                Console.Clear();
                Console.WriteLine("      ....    BYTEBUSTER version 2.0 Demo");
                Console.WriteLine("\n  \n");
            }
        }
    }
}
