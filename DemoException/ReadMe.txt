Demo Exception
======================
Copy code to Program.cs and run it.



Demo IndexOutOfRangeException
=========================
using System;

class Program
{
    static void Main()
    {
        int[] numbers = { 36, 34, 39, 41 };

        for (int i = 1; i <= 4; i = i + 1)
        {
            Console.WriteLine(numbers[i]);
        }
    }
}

proper solution
------------
using System;

class Program
{
    static void Main()
    {
        int[] numbers = { 36, 34, 39, 41 };

		// two changes made in next line
        for (int i = 0; i < 4; i = i + 1)
        {
            Console.WriteLine(numbers[i]);
        }
    }
}

solution with try catch - do NOT use
----------------------------

using System;

class Program
{
    static void Main()
    {
        int[] numbers = { 36, 34, 39, 41 };

        for (int i = 1; i <= 4; i = i + 1)
        {
            try
            {
                Console.WriteLine(numbers[i]);
            }
            catch (IndexOutOfRangeException e)
            {
                Console.WriteLine("index i = " + i + " not in use");
				Console.WriteLine(e.Message);
            } 
        }
    }
}


Demo NullReferenceException
============================
using System;

class Program
{
    static void Main(string[] args)
    {
        string[] shoppingList = new string[3];

        shoppingList[0] = "milk";
        shoppingList[2] = "butter";

        // search for eggs
        foreach(string item in shoppingList)
        {
            if (item.Equals("eggs"))
            {
                Console.WriteLine("found egg"); 
            }
        }
    }
}


proper solution
-----------------------
using System;

class Program
{
    static void Main(string[] args)
    {
        string[] shoppingList = new string[3];

        shoppingList[0] = "milk";
        shoppingList[2] = "butter";

        // search for eggs
        foreach(string item in shoppingList)
        {
            if (item.Equals("eggs"))
            {
                if (item != null)
                {
                    Console.WriteLine("found egg");
                }  
            }
        }
    }
}

solution with try catch - do NOT use
----------------------------

using System;

class Program
{
    static void Main(string[] args)
    {
        string[] shoppingList = new string[3];

        shoppingList[0] = "milk";
        shoppingList[2] = "butter";

        // search for eggs
        foreach(string item in shoppingList)
        {
            try
            {
                if (item.Equals("eggs"))
                {
                    Console.WriteLine("found egg");
                }
            }
            catch (NullReferenceException)
            {
                // empty place in list
            }

        }
    }
}