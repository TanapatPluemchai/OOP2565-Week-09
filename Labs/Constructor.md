# Constructor 

``` cs
using System.Drawing;

namespace ConstructorExample
{
    class Cat
    { 
        public DateTime BirthTime { get; set; }
        public Color CatColor { get; set; }
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


```cs
using System.Drawing;
namespace ConstructorExample
{
    class Cat
    { 
        public DateTime BirthTime { get; set; }
        public Color CatColor { get; set; }
        public Cat() 
        {
            BirthTime = DateTime.Now;
            CatColor = Color.Transparent;
        }
        public Cat(Color catColor)
        {
            BirthTime = DateTime.Now;
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



