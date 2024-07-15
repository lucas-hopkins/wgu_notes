
## General

Compiler turns cpp files into obj files
Linker then runs by  reading the obj files and makes sure they are values
Next the linker ensures all cross 

### Initialization 

```C++
int a;         // no initializer (default initialization)
int b = 5;     // initial value after equals sign (copy initialization)
int c( 6 );    // initial value in parenthesis (direct initialization)

// List initialization methods (C++11) (preferred)
int d { 7 };   // initial value in braces (direct list initialization)
int e = { 8 }; // initial value in braces after equals sign (copy list initialization)
int f {};      // initializer is empty braces (value initialization)

```

- **Copy initialization** - When initial value ios provided after the equal sigh 
	- Whenever values are implicitly copied or converted, such as when passing arguments to a function by value, returning from a function by value or catching exceptions by value
- **Direct initialization** - When initial value is provided in parentheses
	- Largely fallen out of favor but is useful in certain cases
	- Also used when values are explicitly cast to another type
- **List initialization** - Initializing inside curly braces
	- Has benefit of "narrowing conversions" in list initializations are ill-formed. Meaning if you try to brace initialize a variable using a value that the variable can not safely hold, the compiler is required to produce a diagnostic (usually an error).
- 