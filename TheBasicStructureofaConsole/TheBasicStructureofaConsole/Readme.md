﻿## The anatomy of a Simple C# Program
A console application starts from the Main method.The main method is the entry point of a console 
application.C# is a case sensitive therefore the keyword Main, (M) is always capitalized.
## The Main Method 
Every executable files
written in c# must contain a Main method that is used to signify the entry point of the application.The main method has 
static keyword.In addition to the static method ,this Main() Method has a single parameters ,which happens to be an array of string().
Beign array means that the Method can contain a number incoming command-line arguments of strings.

finally , this Main method has been set up using the void keyword,meaning you do not explicity define the return value using the return 
value before exiting the program.The logic of the application is within the main method.Here we Make use of the console class which is defined 
within the System namespace.
## The output Method
Among its memeber is the static WriteLine() which take in string and the sends it to the output stream.

## Variation of the Main Method
By default visual studio will generate a Main() method that has a void return valur and an array of string
type as the single input parameter.The main method can have many singnatures

```Csharp
// int return type, array of strings as the parameter.
static int Main(string[] args)
{
// Must return a value before exiting!
return 0;
}
// No return type, no parameters.
static void Main()
{
}
// int return type, no parameters.
static int Main()
{
// Must return a value before exiting!
return 0;
}
````