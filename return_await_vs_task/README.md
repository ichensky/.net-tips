.net 5 ex.
```csharp
    class Foo
    {
        public async Task<int> Bar() => await Task.FromResult(1);
    }

    class Program
    {
        static int test() => new Foo().Bar().Result;

        static void Main(string[] args)
        {
            MemoryProfiler.CollectAllocations(true);
            MemoryProfiler.GetSnapshot();

            var r = test();

            MemoryProfiler.GetSnapshot();

            Console.WriteLine(r);
        }
    }
```
![General](General.png)
![Types](Types.png)
![BackTraces](BackTraces.png)
