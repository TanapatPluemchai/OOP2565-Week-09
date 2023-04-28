# Indexer

```cs
namespace IndexerExample
{
    class Person
    {
        static public int size = 10;
        private string[] namelist = new string[size];
         public Person()
        {
            for (int i = 0; i < size; i++)
                namelist[i] = "Nobody here...";
        }
        public string this[int index]
        {
            get
            {
                string tmp;

                if (index >= 0 && index <= size - 1)
                {
                    tmp = namelist[index];
                }
                else
                {
                    tmp = "";
                }

                return (tmp);
            }
            set
            {
                if (index >= 0 && index <= size - 1)
                {
                    namelist[index] = value;
                }
            }
        }
    }
        internal class Program
    {
        static void Main(string[] args)
        {
            Person p = new Person();
            p[0] = "Wichai";
            p[1] = "Wichit";
            p[2] = "Wichien";
            p[3] = "Winai";
            p[4] = "Wipa";
            p[5] = "Wipoo";
            p[6] = "Wirat";

            for (int i = 0; i < Person.size; i++)
            {
                Console.WriteLine($"Person no {i+1,2} is {p[i]}");
            }
        }
    }
}
```


``` cs
namespace IndexerExample
{
    class DayOfWeek
    {
        string[] DayName = new string[7];
        
        // Constructor
        public DayOfWeek()  
        {
            DayName[0] = "Sunday";
            DayName[1] = "Monday";
            DayName[2] = "Tuesday";
            DayName[3] = "Wednesday";
            DayName[4] = "Thursday";
            DayName[5] = "Friday";
            DayName[6] = "Saturday";
        }

        // Indexer
        public  string this[int index]
        {
            get { return  DayName[index]; }
        }
    }

    internal class Program
    {
        static void Main(string[] args)
        {
            var dow = new DayOfWeek();
            for (int i = 0; i < 7; i++)
                Console.WriteLine($"{i + 1}. {dow[i]}");
        }
    }
}
```
## Indexer return tuple 

```cs
namespace IndexerExample
{
    class DayOfWeek
    {
        string[] DayName = new string[7];
        string[] DayColor = new string[7];
        public DayOfWeek()  // Constructor
        {
            DayName[0] = "Sunday";
            DayName[1] = "Monday";
            DayName[2] = "Tuesday";
            DayName[3] = "Wednesday";
            DayName[4] = "Thursday";
            DayName[5] = "Friday";
            DayName[6] = "Saturday";

            DayColor[0] = "Red";
            DayColor[1] = "Yellow";
            DayColor[2] = "Pink";
            DayColor[3] = "Green";
            DayColor[4] = "Orange";
            DayColor[5] = "Sky blue";
            DayColor[6] = "Purple";
        }

        // Indexer
        public (string, string) this[int index]
        {
            get { return (DayName[index], DayColor[index]); }
        }
    }

    internal class Program
    {
        static void Main(string[] args)
        {
            var dow = new DayOfWeek();
            for (int i = 0; i < 7; i++)
                Console.WriteLine($"{i + 1}. {dow[i].Item1, -10} Color {dow[i].Item2} ");
        }
    }
}
```

# indexer string

```cs
using System.Drawing;

namespace IndexerExample
{
    class DayOfWeek
    {
        const int size = 7;
        string[] DayName = new string[size];
        string[] DayColor = new string[size];
        public DayOfWeek()  // Constructor
        {
            DayName[0] = "Sunday";
            DayName[1] = "Monday";
            DayName[2] = "Tuesday";
            DayName[3] = "Wednesday";
            DayName[4] = "Thursday";
            DayName[5] = "Friday";
            DayName[6] = "Saturday";

            DayColor[0] = "Red";
            DayColor[1] = "Yellow";
            DayColor[2] = "Pink";
            DayColor[3] = "Green";
            DayColor[4] = "Orange";
            DayColor[5] = "Sky blue";
            DayColor[6] = "Purple";
        }

        // Indexer
        public (string, string) this[int index]
        {
            get { return (DayName[index], DayColor[index]); }
        }

        public string this[string name]
        {
            get
            {
                int index = 0;

                while (index < size)
                {
                    if (DayName[index] == name)
                    {
                        return  DayColor[index];
                    }
                    index++;
                }
                return DayColor[index];
            }
        }
    }

    internal class Program
    {
        static void Main(string[] args)
        {
            var dow = new DayOfWeek();
            Console.WriteLine($"Input = Sunday    ==> color = {dow["Sunday"]}");
            Console.WriteLine($"Input = Monday    ==> color = {dow["Monday"]}");
            Console.WriteLine($"Input = Tuesday   ==> color = {dow["Tuesday"]}");
            Console.WriteLine($"Input = Wednesday ==> color = {dow["Wednesday"]}");
            Console.WriteLine($"Input = Thursday  ==> color = {dow["Thursday"]}");
            Console.WriteLine($"Input = Friday    ==> color = {dow["Friday"]}");
            Console.WriteLine($"Input = Saturday  ==> color = {dow["Saturday"]}");
        }
    }
}
```

# แบบฝึกหัด
