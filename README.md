using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Задание_2
{
    internal class Program
    {
        static string ReverseString(string str)
        {
            char[] chars = str.ToCharArray();
            Array.Reverse(chars);
            return new string(chars);
        }
        static void PrintRepeatFrequency(string str)
        {
            var repeat = new Dictionary<char, int>();
            foreach (char c in str)
            {
                if (repeat.ContainsKey(c))
                {
                    repeat[c]++;
                }
                else
                {
                    repeat[c] = 1;
                }
            }
            foreach (var kvp in repeat)
            {
                Console.WriteLine($"{kvp.Key}: {kvp.Value}");
            }
        }
        static void Main(string[] args)
        {
            string a = Console.ReadLine();
            string result; 
            int k = 0;
            Console.WriteLine(a);

            List<char> invalid = new List<char>();
            foreach (char c in a)
            {
                if (c != 'a' && c != 'e' && c != 'i' && c != 'o' && c != 'u' && c != 'y')
                {
                    invalid.Add(c);
                }
            }

            if (invalid.Count > 0)
            {
                Console.WriteLine("Ошибка: введены неподходящие символы: " + string.Join(", ", invalid));
                Console.ReadKey();

            }

            if (a.Length % 2 == 0) {
                k = a.Length / 2;
                string first = a.Substring(0, k);
                string second = a.Substring(k);
                result = ReverseString(first) + ReverseString(second);
            }
            else {
                result = ReverseString(a) + a;
            }

            Console.WriteLine("Обработанная строка: " + result);
            PrintRepeatFrequency(result);


            Console.ReadKey();


        }

    }
}
