> # Nullable Type (C# programming)
Nullable types are instances of the `System.Nullable<T>` struct.A nullable type can represent the correct range of values for its underlying value type plus additional `null`.for Example a `Nullable<int32>` is called the `Nullable of Int32` can be assigned any value.
A  `Nullable of bool` can be assigned the following values.
<li>true</li>
<li>false</li>
<li>null</li>

> # What is the Importance of Nullable
The ability to assign `null` to numeric and boolean types is especiallly usefull when dealing with databases and other types that contains elements that may nor be assigned a value.For Example a boolean field in a database can either be the values `true`,`false` and `null`(undefined).

```Csharp
static void Main(string[] args){
    int? num=null;
    //is the HasValue Property true
    if(num.HasValue)
        Console.WriteLine($"num = "+ num.HasValue);
    else
        Console.WriteLine("num = null");
    
    //y is set to Zero
    int y=num.GetValueOrDefault();
    try{
        y=num.Value;
    }catch(InvalidOperationException e){
        
        Console.WriteLine(e.Message);

    }
    Console.WriteLine("Hello World!");

    Console.ReadKey();
}
```
> # Nullable Types Overview
Nullable types have the following characteristics.
<li>NUllalable types represent value types variables that can be assigned the value of null value</li>
<li>The syntax T? is shorthand for Nullable<T> , where T is a value type.The two forms are interchangeble</li>
<li>Assign a value to a nullable type just as you would for an ordinary value type,for Example int? x=10 or double? d=4.100. A nullable type can also be assigned the value null: int? x = null</li>
<li>Use the Nullable<T>GetValueOrDefault method to return either the assigned value or the default value for the underlying type if the value is null for example int j=x.GetValueOrDefault():</li>
<li>Use the HasValue and Value readonly properties to test for null and retrieve the value as shown int the following </li>
 
The `HasValue` and `Value` readonly properties return true if the variable contains a value,of `false` if it is `null`.

The `value` property returns `true` if the variable contains a value or `false` it its null.

The value property returns a value if one is assigned.Otherwise a System.InvalidOperationExeption is thrown.

The `default` value for `HasValue` is `false`.the `Value` property has no default value.

Use the `??` operator to assign a default value that will be applied when a nullable type whose current value is null is assigned to a non-nullable type,for example `int? x=null ; int y=x??-1`;

`Nested` nullable types are not allowed .The following line will not compile `Nullable<Nullable<int>> n`

> # Using Nullable Types
Nullable types can be represent all the value of an underlying type and an addition null value.Nullable types are declared in two ways
```csharp
System.Nullable<T> variable

      or 
T? variable
```
T is the underlying type of the nullable type T can be any value including `struct` but is cannot be a reffence type.For example of when you might use a nullable type consider how an ordinary Boolean variable can have two values;`true of false` .There is no value that signifies  `Undefined` .In many orogramming application most notable database interactions ,variables can occur in an undefined state.For exampe, a field in a database may contain the value true or false but it may also contain no value at all.Similary,referenc types can be set to null to idicate that they are not initialised.

This disparity can create extra proramming work with additional variables used to store information,the use of special values and so on.The nullable types modifiers enables c# to create value-type can be set to indicate and udefined value.

> # Example of Nullablel Types
Any value type may be the basic for Nullable.For example
```Csharp
int? i=10;
double? di=3.14;
bool? flag=null;
char? letter='a';
int?[] arr=new int?[10];
```
> # The Members of Nullable Types
Each instance of nullable type has two public read-only propertis
<li>HasValue is of type bool.It is set to true when the variable contains a non-null value</li>
<li>Value</li>
`Value` is of the same type as the undelying type .if HasValue is `true` Value contains a meannigful value.If `HasValue` is false,accesing Value will throw a `InvalidOperationException`

In this example, the `HasValue` member is used to test whether the variable contains a value before it tries to displat it.

>  # Explicit Conversions
A nullable type can be cast to a reqular type either explicitly with a cast of using the value Property.example
```Csharp
int? n=null;// will not compile 
int m2=(int)n; //compiles, but will create an exception if n is null
int m3=n.Value;//compile, but will not create an exeption when n is null
```

> # Impicit conversion
A variable of nullable types can be set to null with the null data type keyword

`int? n1 =null;`
> # Operators
The predefined `unary` and `binary` operators and any user-defined operators that exist for value type may also be used by nullable types.These Operators produce a null value if the operand are null; otherwise,the operators uses the contained value to calculate the result.For example
```Csharp
int? a=10;
int? b=null;
a++; //now increments by 1, now a is 11
a=a*10;  //Multiply by 10, now a is 110
a=a+b;//Add b now a is null
```
When you perform comparisons with nullable types, if the value of one of the nullable types is `null` and the `other is not`, all comparisons evaluate to `false` except for `!= (not equal)`. It is important not to assume that because a
particular comparison returns false , the opposite case returns `true `. In the following example, 10 is `not greater than`, `less than`, `nor equal` to `null`. Only `num1 != num2` evaluates to true .

```Csharp
int? num1 = 10;
int? num2 = null;
if (num1 >= num2)
{
Console.WriteLine("num1 is greater than or equal to num2");
}
else
{
// This clause is selected, but num1 is not less than num2.
Console.WriteLine("num1 >= num2 returned false (but num1 < num2 also is false)");
}
if (num1 < num2)
{
Console.WriteLine("num1 is less than num2");
}
else
{
// The else clause is selected again, but num1 is not greater than
// or equal to num2.
Console.WriteLine("num1 < num2 returned false (but num1 >= num2 also is false)");
}
if (num1 != num2)
{
// This comparison is true, num1 and num2 are not equal.
Console.WriteLine("Finally, num1 != num2 returns true!");
}
// Change the value of num1, so that both num1 and num2 are null.
num1 = null;
if (num1 == num2)
{
// The equality comparison returns true when both operands are null.
Console.WriteLine("num1 == num2 returns true when the value of each is null");
}
```
> # The ?? Operator
The ?? operators defines a default value that is retured when a nullable type is assigned to a nullable type.
```csharp
int? c =null;
int d=c ?? -1;
```
This Operators can also be used with multiple nullabe types.For Example

int? e=null;
int? f=null;

//g=e or f , unless e and f are both null,in which case g=-1

> # The bool? type
The bool? nullable type can contain three diffrent value;True false and null.

Nullable Booleans are like the Boolean variable type is used in sql .To ensure that the result produced by the $ and ! operators are consistent with the three Boolean type in Sql;the following predifined operators are provided.

`bool? operator&(bool? x ,bool? y)`
`bool? operator|(bool? x ,bool? y)`

> # Boxing Nullable Types
objects based on nullable types are only boxed if the object is non-null.If `HasValue` is false,the object is assigned to null istead of boxing .ie
```csharp
bool? b=null;
object o=b;
//Now o is null
```
if the object is non-null .if the `HasValue` is true --then boxing occurs, but only the underlying type that the nullable object is based on is boxed.Boxing a non-null type itself not the System.Nullable<T> that wraps the value type.ie,
```Csharp
bool? b = false;
int? i = 44;
object bBoxed = b; // bBoxed contains a boxed bool.
object iBoxed = i; // iBoxed contains a boxed int.
```
The two boxed objects are identical to those created by boxing non-nullable types.And, just like non-nullable boxed types,they can be unboxed into nullable type in the following example.

```Csharp
bool? b2 = (bool?)bBoxed;
int? i2 = (int?)iBoxed;
```
The two boxed objects are identica to those created by boxing non-nullable types and just like non-nullable boxed types they can unbox into nullabl types as in the following example.

```Csharp
bool? b2=(bool?)bBoxed;
int? i2=(int?)iBoxed;
```
> # Remarks
The behaviour of nullable type when boxed provides two advantages:

<li>Nullable objects and their boxs couterpart can be tested for null</li>

```Csharp
bool? b=null;
object boxedb=b;
if(b==null){
    true
}
if(boxedb==null){
    //also True
}
```
<li>Boxed nullable types fully support the fuctionality of the undelying type</li>

```Csharp
double? d = 44.4;
object iBoxed = d;
// Access IConvertible interface implemented by double.
IConvertible ic = (IConvertible)iBoxed;
int i = ic.ToInt32(null);
string str = ic.ToString();
```
> # Safely Cast from bool? to bool
The `bool?` nullable type can contain three different values: `true , false , and null` . Therefore, the` bool?` type
cannot be used in conditionals such as with `if , for , or while` . For example, the following code causes a `compiler error`.first check its `HasValue` property to ensure that its value is `not null` , and then cast it to `bool` .
```Csharp
bool? test = null;
// Other code that may or may not
// give a value to test.
if(!test.HasValue) //check for a value
{
// Assume that IsInitialized
// returns either true or false.
test = IsInitialized();
}
if((bool)test) //now this cast is safe
{
// Do something.
}
```

