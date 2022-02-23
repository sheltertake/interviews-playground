# Intro

SW vs ST (funny question)

## Past project experience
 - What did you personally work on?
 - What was the most interesting work you ever did?

## Design patterns
 - What are they good for? -> communication
 - Which design patterns did you use and why?

# .NET 

## MSIL / JIT
	
```
C# (and in general all CLI programming languages) is compiled in Microsoft Intermediate Language a sort of assembly format. 
IL code is hardware independent, so we can reuse the same binary file on different platforms
MSIL is compiled just in time (JIT) by Common Language Runtime.
The generated code can be optimized. 
```	
	
	
## GC

```
In the common language runtime (CLR), the garbage collector (GC) serves as an automatic memory manager.
.NET's garbage collector manages the allocation and release of memory
the garbage collector is triggered by allocations.
In .NET there are two types of heaps (SOH/LOH).
Objects are moved by the collector in 3 SOH Generations based on their age (G0/G1/G2).
```

## IDisposable Pattern

```
Provides a mechanism for releasing unmanaged resources. 
The IDisposable interface is defined as
public interface IDisposable
{
   void Dispose();
}
Performs application-defined tasks associated with freeing, releasing, or resetting unmanaged resources.
C# provides a special "using" statement to call Dispose method explicitly.
In using statement, we instantiate an object in the statement. 
At the end of using statement block, it automatically calls the Dispose method.
```

## Linq
		

```
LINQ, or Language Integrated Query, is a set of language and framework features
for writing structured type-safe queries over local object collections and remote data
sources. 
LINQ was introduced in C# 3.0 and Framework 3.5.

LINQ enables you to query any collection implementing IEnumerable<T>, whether
an array, list, or XML DOM, as well as remote data sources, such as tables in a SQL
Server database. LINQ offers the benefits of both compile-time type checking and
dynamic query composition. 

There are 2 syntax: fluent syntax and query expression (from where select)
```
### LINQ - delayed execution

```
An important feature of most query operators is that they execute not when constructed, but when enumerated (ToList | ToArray)
```

## Generic types
```
C# has two separate mechanisms for writing code that is reusable across different types: inheritance and generics. 
Whereas inheritance expresses reusability with a base type, generics express reusability with a "template" that contains "placeholder" types.
Generics, when compared to inheritance, can increase type safety and reduce casting and boxing.

You should use generics when you want only the same functionality applied to various types (Add, Remove, Count) and it will be implemented the same way. 
Inheritance is when you need the same functionality (GetResponse) but want it to be implemented different ways.
```

### Static member on generic type

```
In the vast majority of cases, having a static field or auto-property in a generic type is a sign of an error. The reason for this is that a static member in a generic type will not be shared among instances of different close constructed types.
```

## Multithreading

```
Every process/application runs by default with a single thread.
Multithreaded applications introduced the capability to process the independent code concurrently in more than one thread.
```		
### Threads

```
A thread is an execution path that can proceed independently of others.

A thread is a low-level tool for creating concurrency.

While it's easy to pass data into a thread that you start, there's no easy way to get a "return value" back from a thread that you Join. You have to set up some kind of shared field

hundreds or thousands of concurrent I/O-bound operations, a thread-based approach consumes hundreds or thousands of MB of memory purely in thread overhead.
```
### Tasks
```
Task is higher-level abstraction, it represents a concurrent operation that may or may not be backed by a thread.
The Task types were introduced in Framework 4.0 as part of the parallel programming library.
From Framework 4.5, the easiest way to start a Task backed by a thread is with the static method Task.Run

Task.Run (() => Console.WriteLine ("Foo"));

Tasks use pooled threads by default, which are background threads.

Task.Run returns a Task object that we can use to monitor its progress.
```

###  async
```
C# 5.0 introduced the async and await keywords.
The await keyword simplifies the attaching of continuations.

var awaiter = expression.GetAwaiter();
awaiter.OnCompleted (() => ...
```

### Parallel Linq

```
PLINQ automatically parallelizes local LINQ queries
To use PLINQ, simply call AsParallel() on the input sequence and then continue
the LINQ query as usual. The following query calculates the prime numbers
between 3 and 100,000—making full use of all cores on the target machine:
```


```csharp
// Calculate prime numbers using a simple (unoptimized) algorithm.
IEnumerable<int> numbers = Enumerable.Range (3, 100000-3);
var parallelQuery = 
	from n in numbers.AsParallel()
	where Enumerable.Range (2, (int) Math.Sqrt (n)).All (i => n % i > 0)
	select n;

int[] primes = parallelQuery.ToArray();
```

### what thread synchronizaytion objects do you know

```
```

	Collections
		- when would you NOT use Dictionary<TKey, TValue>

SQL
	Report logins by hour
	Compare with NoSQL

MongoDB
	How to do Upsert
	Compare/Exchange

Source Control
	Experience with Git?
	Development workflow in git? (branching vs forking)

CI
	What is CI?
	What should be part of CI and what should not?
	What CI/CD technologies did you use? (Balboo, Jenkins, ...?)

AWS / Azure
	Auto scaling groups, how does that work?
	Service health checks, what should be in them, how do they work?

Find Errors

Algoritmization

His questions for me