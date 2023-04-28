# Constructor 

``` cs
using System.Drawing;

namespace ConstructorExample
{
    class Cat
    { 
        // Properties
        public DateTime BirthTime { get; set; }
        public Color CatColor { get; set; }

        // Constructor
        public Cat() 
        {
            BirthTime = DateTime.Now;
            CatColor = Color.Transparent;
        }
    }
    internal class Program
    {
        static void Main(string[] args)
        {
            var c1 = new Cat();
            Console.WriteLine($"Cat birth time = {c1.BirthTime}");
            Console.WriteLine($"Cat color = {c1.CatColor.Name}");
        }
    }
}
```


# Constructor overloading

```cs
using System.Drawing;
namespace ConstructorExample
{
    class Cat
    { 
        // Properties
        public DateTime BirthTime { get; set; }
        public Color CatColor { get; set; }
        
        // Default constructor
        public Cat() 
        {
            BirthTime = DateTime.Now;
            CatColor = Color.Transparent;
        }
        // Parameterized constructor
        public Cat(Color catColor)
        {
             BirthTime = DateTime.Now;
             CatColor = catColor;
        }
    }
    internal class Program
    {
        static void Main(string[] args)
        {
            var c1 = new Cat();
            Console.WriteLine($"Cat birth time = {c1.BirthTime}");
            Console.WriteLine($"Cat color = {c1.CatColor.Name}");
        }
    }
}
```


## การใช้ this() เพื่อเรียก constructor

```cs
using System.Drawing;
namespace ConstructorExample
{
    class Cat
    {
        // Properties
        public DateTime BirthTime { get; set; }
        public Color CatColor { get; set; }

        // Default constructor
        public Cat()
        {
            BirthTime = DateTime.Now;
            CatColor = Color.Transparent;
        }
        // Parameterized constructor
        public Cat(Color catColor)  : this()
        {
            CatColor = catColor;
        }
    }
    internal class Program
    {
        static void Main(string[] args)
        {
            var c1 = new Cat(Color.AntiqueWhite);
            Console.WriteLine($"Cat birth time = {c1.BirthTime}");
            Console.WriteLine($"Cat color = {c1.CatColor.Name}");
        }
    }
}
```

## Static constructor

```cs
using System.Drawing;
namespace ConstructorExample
{
    class Cat
    {
        // Properties
        public DateTime BirthTime { get; set; }
        public Color CatColor { get; set; }

        public static readonly DateTime globalStartTime;

        // Default constructor
        public Cat()
        {
            BirthTime = DateTime.Now;
            CatColor = Color.Transparent;
        }

        // Static constructor
        static Cat()  
        {
            globalStartTime = DateTime.Now;
        }


        // Parameterized constructor
        public Cat(Color catColor)  : this()
        {
            CatColor = catColor;
        }
        public Cat(Color catColor, DateTime born) : this(catColor)
        {
            BirthTime = born;
        }
    }
    internal class Program
    {
        static void Main(string[] args)
        {
            var c1 = new Cat(Color.AntiqueWhite);
            Console.WriteLine($"Cat 1 birth time = {c1.BirthTime}");
            Console.WriteLine($"Cat 1 color = {c1.CatColor.Name}");
            Console.WriteLine($"Cat 1 age = {Cat.globalStartTime - c1.BirthTime}"); 

            var c2 = new Cat(Color.Brown, new DateTime(2023, 04, 13));
            Console.WriteLine($"Cat 2 birth time = {c2.BirthTime}");
            Console.WriteLine($"Cat 2 color = {c2.CatColor.Name}");
            Console.WriteLine($"Cat 1 age = {Cat.globalStartTime - c2.BirthTime}");

            var c3 = new Cat() { CatColor = Color.Orange, BirthTime = new DateTime(2022, 05, 01) };
            Console.WriteLine($"Cat 3 birth time = {c3.BirthTime}");
            Console.WriteLine($"Cat 3 color = {c3.CatColor.Name}");
            Console.WriteLine($"Cat 1 age = { Cat.globalStartTime - c3.BirthTime}");
        }
    }
}
```

## Object initializer
```cs
using System.Drawing;

namespace ConstructorExample
{
    class Cat
    { 
        public DateTime BirthTime { get; set; }
        public Color CatColor { get; set; }
        public static int catID;
        public Cat() 
        {
            BirthTime = DateTime.Now;
            CatColor = Color.Transparent;
            catID++;
        }
        public Cat(Color catColor) :this()     
        {
            CatColor = catColor;
        }
    }
    internal class Program
    {
        static void Main(string[] args)
        {
            var c3 = new Cat() { CatColor = Color.Orange, BirthTime = new DateTime(2023, 05, 01) };
            Console.WriteLine($"Cat 3 birth time = {c3.BirthTime}");
            Console.WriteLine($"Cat 3 color = {c3.CatColor.Name}");
        }
    }
}

```
