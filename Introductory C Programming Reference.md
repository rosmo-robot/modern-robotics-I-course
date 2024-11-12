

# **![][image1]**

# **Introductory C Programming Reference**

January 2024

**Introductory C Programming Reference**

Version 1.2, January 2024

Introductory C Programming Reference © 2024 by [mirobo.tech](https://mirobo.tech/) is licensed under [CC BY 4.0](http://creativecommons.org/licenses/by/4.0/?ref=chooser-v1). To view a copy of this license, visit [http://creativecommons.org/licenses/by/4.0/](http://creativecommons.org/licenses/by/4.0/)

This reference is designed to be a concise resource as an adjunct to classroom instruction for students beginning to learn Arduino or PICmicro C programming. Its purpose is not to be a comprehensive C guide or tutorial, but simply a reference for common C expressions, structures, and idioms seen in typical microcontroller programs. **Permission is hereby freely granted for anyone to share, adapt, copy, and redistribute any or all parts of this work, in any format, as long as credit is provided to mirobo.tech.** We hope you will find it useful.

This work is provided ‘as-is’, for educational purposes only. No warranty is provided or implied relating to the accuracy of this work or its suitability for any purpose.

Please help us to improve this reference by reporting errors and suggestions to: [https://mirobo.tech/contact](https://mirobo.tech/contact)

# **Introductory C Programming Reference**

Table of Contents:

[**Numbers, constants, and variables**](#numbers,-constants,-and-variables)

[Numeric types](#numeric-types)

[Constants](#constants)

[Declaring constants](#declaring-constants)

[Variables](#variables)

[Declaring variables](#declaring-variables)

[**C language expressions and statements**](#c-language-expressions-and-statements)

[Expressions](#expressions)

[Mathematical operators](#mathematical-operators)

[Logical operators](#logical-operators)

[Statements](#statements)

[**Functions**](#functions)

[main( ) function](#main\(-\)-function-in-mplab)

[Declaring functions](#declaring-functions)

[Example functions](#example-picmicro-c-functions)

[Example function calls](#example-function-calls)

[Function benefits](#function-benefits)

[**C language structures**](#c-language-structures)

[Decision structures](#decision-structures)

[if...else if...else](#if...else-if...else)

[Conditional comparison operators](#conditional-comparison-operators)

[Logical operators](#logical-operators-1)

[Example if condition](#example-if-condition)

[Example if...else condition](#example-if...else-condition)

[Example if...else if...else condition](#example-if...else-if...else-condition)

[Loop structures](#loop-structures)

[Main while( ) loop](#picmicro-c-main-while\(-\)-loop)

[While loops](#while-loops)

[Example non-counted while loop](#example-non-counted-while-loop)

[Example counted while loop](#example-counted-while-loop)

[For loop](#for-loop)

[Example for loop](#example-for-loop)

[Accumulator operations](#compound-operators)

[Accumulator operators](#accumulator-operators)

# **Numbers, constants, and variables** {#numbers,-constants,-and-variables}

## **Numeric types** {#numeric-types}

All [numbers used in](https://docs.google.com/document/d/1OYUOmz8skNLGm7sRO4qbaR25OmM6TEB0k5FXBWDWjB8/edit?usp=sharing) computer programs have to be defined using a known ‘type’. This is necessary to ensure that the computer can both understand and properly encode the number. The type defines the number of bits used to represent the number, and whether the number can represent only positive values, or both negative and positive values. In C language programs, the numeric type has to be declared before a number can be used as a constant or variable.

Each type, except for bool and nybble, can be *unsigned* or *signed*. Unsigned types represent only positive numbers, while signed types represent mixed positive and negative numbers. The following chart compares the most common numeric types:

| Type | \# of bits | Smallest value | Largest value | Typical uses: |
| :---- | :---- | :---- | :---- | :---- |
| bool | 1 | 0 (false) | 1 (true) | Logic, inputs, outputs |
| nybble | 4 | 0 | 15 | 1 Hex digit, 1 BCD digit |
| unsigned char | 8 | 0 | 255 | Small positive integers |
| char (signed char) | 8 | \-128 | 127 | Small positive and negative integers |
| unsigned int | 16 | 0 | 65 535 | Large positive integers |
| int (signed int) | 16 | \-32 768 | 32 767 | Large positive and negative integers |
| unsigned long | 32 | 0 | 4 294 967 295 | Very large positive integers, variables |
| long (signed long) | 32 | \-2 147 483 648 | 2 147 483 647 | Very large positive and negative integers |
| float | 32 | \-3.4028235E+38 | 3.4028235E+38 | Very large positive and negative decimals |

In many simple PICmicro programs the primary data type is the 8-bit unsigned char.  
In most Arduino programs the primary data type is the 16-bit signed int. 

The most commonly used numeric types in simple Arduino programs are:

* **bool** (Boolean) \- 1-bit number, either 0 or 1 (or false or true)  
* **int** (integer) \- 16-bit (2 Byte) numbers representing \-32768 to \+32767  
* **unsigned long** \- 32-bit (4 Byte) numbers representing 0 to 4294967295

The most commonly used numeric types in simple PICmicro programs are:

* **bool** (Boolean) \- 1-bit number, either 0 or 1 (or false or true)

* **char** (character) \- 8-bit (1 Byte) number representing 0 to 255, or Latin letters (ASCII)

* **int** (integer) \- 16-bit (2 Byte) numbers representing \-32768 to \+32767

For both simplicity and to allow the compiler to generate the smallest and fastest code, programmers should strive to use whole number integers (character or integer types), and avoid decimal numbers (float types) and complex decimal calculations whenever possible.

### **Constants** {#constants}

Constants are named values used in a program that don’t change – that is to say, they remain constant. Constants are most often used to define hardware features and program values that are set during program creation and used repeatedly during a program’s operation.

#### **Declaring constants** {#declaring-constants}

Constants are declared using the ***const*** keyword, the numeric ***type***, the constant’s ***name***, and the constant’s ***value***, for example:

const unsigned char maxNum \= 12;

const int LED3 \= 5;

The first example assigns the constant named **maxNum** the value of **12**, and the compiler represents **maxNum** as an 8-bit character. Any time that the word **maxNum** is used in a program containing this declaration, the program will interpret the value of **maxNum** as **12**.

The second example assigns the constant **LED3** the value of **5**. In this case the compiler represents **LED3** as a 16-bit integer.

One advantage of declaring a constant at the beginning of a program is that it makes it much easier to change the value of every instance of the constant after the program is written, since changing the constant declaration changes every statement using the named constant. Another advantage of assigning constants is that the constant’s name can be created to be much more meaningful than the simple value it replaces.

### **Variables** {#variables}

Variables are named values used in a program that can change, or vary. Variables are most often used to keep track of temporary data, user input, program output, and loop iterations. Similar to constants, variables are declared when a program is created, and can be assigned a value either when they are created, or while the program runs.

#### **Declaring variables** {#declaring-variables}

Variables are declared using the numeric ***type***, the variable ***name***, and an optional ***value***:

bool isPressed \= false;

unsigned char button;

char hello\[\] \= “Hello, world\!”;

int tempC \= \-20;

In the first example, the variable **isPressed** is given the value **false**, or **0** (**true** has the value **1**).

In the second example, the variable **button** has been created, but assigned no value. It is important to assign the button variable a value before any code tries to use it, as uninitialized variables may not be within a range that the program expects.

In the third example, the array variable named **hello** holds all of the individual ASCII character codes that make up the character string “**Hello, world\!**”.

In the fourth example, the signed integer variable **tempC** has been created and assigned the negative numeric value **\-20**.

# **C language expressions and statements** {#c-language-expressions-and-statements}

Program expressions and statements in the C language represent a single program action and are terminated with ‘**;**’ (semicolon) – similar to how we use a period to terminate every written sentence. Expressions and statements usually fit on a single line of code, but they can wrap to the next line if necessary because the semicolon will explicitly end the statement.

## **Expressions** {#expressions}

Expressions contain a single equal sign ‘**\=**’ and are used to declare constants and variables, or assign values to variables.

button \= getKey();

metres \= cm / 100;

In the first example, the **button** variable is assigned a value by the **getKey( )** function. Functions will be explored in the next topic area.

In the second example, a mathematical expression, the variable **metres** is assigned the value of the variable **cm** divided by **100** using the **/** division operator. Spaces in expressions do not matter and can aid in readability. Typical math rules of order (BEDMAS) apply to mathematical expressions, and the common math and logical operators used in expressions are listed below:

### **Mathematical operators** {#mathematical-operators}

The list shows the most common mathematical operators used in expressions:

  \+ 	Addition

  \- 	Subtraction

  \* 	Multiplication

  / 	Division

  % 	Modulus (remainder)

  \*\* 	Exponent

### **Logical operators** {#logical-operators}

This list shows common bit-wise logical operators, which perform the selected operation on each of the representative binary bits of constants and variables.

  &	bit-wise AND

  |	bit-wise OR

  ^	bit-wise XOR

 \<\< n	bit-shift left n digits

 \>\> n	bit-shift right n digits

## **Statements** {#statements}

Statements include function calls, return operations, program control instructions, or other program directives that perform operations other than assigning values.

delay(10);

return;

The first example calls the **delay( )** function with the value **10**.

The second example causes code execution to **return** from a function or subroutine.

# **Functions** {#functions}

Functions are named blocks of code designed to accomplish a specific purpose, or perform a specific function. Most PICmicro functions must be created by programmers, although some pre-made functions exist in the MPLAB X and MPLAB Xpress IDEs used for creating PICmicro programs. Many Arduino commands are actually functions, and can be identified as being functions in the [Arduino Language Reference documentation](https://www.arduino.cc/reference/en/) by ending with brackets ( ).

Functions may contain any mix of typical C expressions, statements, and code structures. The program code inside a function is grouped within curly braces { } and indented from the left margin to aid in identification and program readability.

Functions are typically *called* (a term for invoking the function) from within the main program code. Calling a function temporarily diverts the microcontroller to processing to the code inside the function before returning processing to the originally running program code.

## **main( ) function in MPLAB** {#main(-)-function-in-mplab}

A single main( ) function is required to be present in every MPLAB C language project:

int main(void)

The main( ) function identifies the starting, or entry point of the program – where the microcontroller begins to run the program. The entire main part of the program is contained within the main( ) function, and additional functions are also typically a part of Microchip C programs.

## **Arduino setup( ) and loop( ) functions**

Every Arduino program requires the presence of both the setup( ) and loop( ) functions, as declared by the statements:

void setup()

void loop()

The Arduino setup( ) function is the starting point of the program and contains program instructions that will run once, at start-up.

The loop( ) function begins running once the setup( ) function has finished, and contains the main program loop consisting of the program code that will repeat while continuously running the program. Additional functions can also be included in Arduino programs.

## **Declaring functions** {#declaring-functions}

Functions are declared by a statement including a ***return type***, function ***name***, and zero or more optional **parameters**. A function declaration statement takes the form:

return-type function-name(optional parameter1, optional parameter2, …)

The return-type is the numeric type of any data that is returned by the function to the code that called it. If no data is to be returned, the return type is identified as **void**.

The function-name is self descriptive – it is the name the function is called by. Using names that describe the actions or the results of a function can help to make program code more logical and readable.

Parameters are optional variable declarations for data transferred to the function code by the calling code, and create variables whose values are local (only available to) the function.

The code that makes up the function follows the function declaration and is contained within curly braces **{ }**. 

## **Example PICmicro C functions** {#example-picmicro-c-functions}

int main(void)

The **main( )** function is unusual in that it is declared with an *int* return type, though there is no code for it to return to. The **void** parameter placeholder indicates that no parameters are accepted into the function, which makes sense since this function represents the start of the program and contains the very first code to run. Every MPLAB C program must contain one, single main( ) function that contains the code that starts the program.

The **OSC\_config( )** function (oscillator configuration) is an example of a self-contained function. It can be called from the main program using a function call statement, like this: ***OSC\_config( );***

void OSC\_config(void)

{

    OSCCON \= 0xFC;              // Set 16MHz HFINTOSC with 3x PLL enabled

    ACTCON \= 0x90;              // Enable active clock tuning from USB clock

    while(\!PLLRDY);             // Wait for PLL lock (disable for simulation)

}

This **OSC\_config** function declaration in the first line shows that this function accepts no parameters, and returns no data. When it is called, the statements inside the curly braces are run in turn. When all three statements have finished, program execution continues from the next line of the code after the original function call statement in the program.

## **Example Arduino C functions**

void setup()

The **setup( )** function is declared with a void return type, meaning it can return no data. Since the setup( ) function is automatically invoked in every Arduino program, there is no calling statement for the function to return a value to. The brackets following the function name are empty, showing that no parameters are expected to be received by this function (also equivalent to void).

## **Example C functions**

The imaginary **readButton( )** function, below, represents an example function designed to read physical key switches and return a key code representing a currently active switch. (The actual code required to read a button depends on your circuit and is not shown.)

unsigned char readButton(void)

{

    …

    return(key);

}

This **readButton** function’s return type indicates that the data returned by the function will be in the form of an *unsigned character*. The returned data comes from the key variable used by the return( ) statement inside the function, and the value returned will need to be received by another variable in the calling program. The **void** parameter indicates no data is received by this function to do its task. So, an example function call expression to read a button using this function in a program might look like this:

button \= readButton();

The function declaration for **lightLED**, below, represents a function that might light a selected LED in a group of LEDs or a programmable lighting strip.

void lightLED(int num)

The **int num** parameter instructs the function to expect to receive a single piece of data, formatted as an integer numeric type, and to store this value in the *num* variable inside the function. The **void** return type indicates that no data is returned by this function.

### **Example function calls** {#example-function-calls}

As long as the numeric types match (or the data can be cast from one type to another), a calling program could easily call functions like these sequentially, storing the variable returned by one function and then passing it to the next function as a parameter:

button \= readButton();

lightLED(button);

This same sequence of functions can be nested and combined on one line, although doing so risks making the nested operations less obvious to new programmers:

lightLED(readButton());

## **Function benefits** {#function-benefits}

* Functions allow code to be re-used if the same action is required in multiple parts of a program, making programs smaller and easier to maintain,  
* functions simplify the main code by moving large blocks of code out of the main line of code execution, and  
* logically-named functions aid code readability by replacing complex blocks of code with shorter, and potentially more descriptive function calls

# **C language structures** {#c-language-structures}

Structures are parts of programming languages that typically control program flow using decisions, or repeat blocks of code using loops. 

## **Decision structures** {#decision-structures}

Decision structures decide which blocks of code to run. The most common decision structure is the *if...else if...else* structure which selects one block of code out of multiple possible blocks to run. The related *switch...case* structure can select one or more than one block of code to run.

### **if...else if...else** {#if...else-if...else}

If structures are commonly used to choose a block of code to run if a condition is true, and reject a block of code if the condition is false. A binary conditional comparison follows the if or else if statement (inside brackets), and determines if the condition is true or false. Multiple conditional comparisons can be combined using logical operators. The common conditional and logical operators are listed, below:

#### **Conditional comparison operators** {#conditional-comparison-operators}

\==	(is equal to)

\!= 	(is not equal to)

\> 	(is greater than)

\>= 	(is greater or equal)

\< 	(is less than)

\<= 	(is less or equal)

#### **Logical operators** {#logical-operators-1}

&& 	(logical AND)

|| 	(logical OR)

\! 	(logical NOT)

### **Example if condition** {#example-if-condition}

if (count \== 10\)

{

    moveTray();

}

In this example, the code inside the curly braces **{ }** will run only if the **count** variable is equal to the value **10**. If count is not 10, the code inside the braces will be skipped.

### **Example if...else condition** {#example-if...else-condition}

if (count \== 10\)

{

  moveTray();

}

else

{

  setBrake();

}

This if structure contains an optional else condition which will be true whenever the if condition is false. The **moveTray( )** function will be called only if the **count** is equal to **10**, and the **setBrake( )** function will be called for all other values of **count**.

### **Example if...else if...else condition** {#example-if...else-if...else-condition}

if (count \== 10\) {

  moveTray();

}

else if (count \> 10\) {

  reportJam();

}

else {

  setBrake();

}

This structure contains multiple conditions and an optional else condition. Only the code within the first true conditional block will run, excluding all of the other code blocks in the if structure.

This means that the **moveTray( )** function will run only if the value of count is **equal** to **10**, the **reportJam( )** function will run if the value of count is any number **greater** than **10** (11 or higher), and the **setBrake( )** function will run for all other values of **count**, essentially 0 through 9\.

This structure also illustrates an alternate method of grouping a code block using curly braces in which the opening brace **{** is at the end of the line containing the conditional statement. This method results in more compact code than starting the opening brace on the next line, but at the expense of visually mis-aligning the braces for the beginning and ending of the code block, making debugging potential more difficult for beginners.

## **Loop structures** {#loop-structures}

Loop structures repeat blocks of code while a condition is true. The conditional check is often based on the value of a loop variable that counts the number of loop repetitions, but other conditional checks are also valid for structures such as while loops.

### **PICmicro C main while( ) loop** {#picmicro-c-main-while(-)-loop}

Most microcontroller programs don’t start and stop like computer apps. Instead, they run forever, repeating their program code. The code structure that repeats the main part of PIC microcontroller programs and mimics Arduino’s loop( ) function is a while loop structure, which is typically coded into the main function like this:

int main(void)

{

    // put code meant to run once here

    while(1)

    {

        // all of the program code in the while loop repeats forever

    }

}

The **while** structure normally contains a conditional expression inside its bracket. In this case, the conditional expression is replaced by the constant **1**, which is the the boolean equivalent of ‘true’, and forces the loop to always repeat.

### **While loops** {#while-loops}

While loops repeat a block of code while a condition is true. An advantage of while loops is their ability to repeat code even when the number of repetitions is not known ahead of time.

#### **Example non-counted while loop** {#example-non-counted-while-loop}

while (key \== 0\)

{

  key \= getKey();

  delay(50);

}

The code within this while loop will continue to run if the value of the **key** variable **equals** **zero**. Another way to think of this is that the contents of the loop will run until the value of the key variable is not equal to zero.

The total number of times this loop will run is not known ahead of time, illustrating a unique capability of the while loop structure. While loops can also be used when the number of loops to be executed is known, and for loop structures can do the same using more compact code.

#### **Example counted while loop** {#example-counted-while-loop}

bottles \= 0;

while (bottles \< 10\)

{

  fillBottle();

  bottles \= bottles \+ 1;

}

The **bottles** variable is initialized to 0 before the **while** structure starts the loop. The code within this while loop runs **while** the value of the **bottles** variable is **less** than **10**. If the value of the bottles variable is 10 or more, the code inside the while loop structure is skipped. Inside the loop code block (within the curly braces **{ }** ), the bottles variable is incremented every cycle of the loop in order to count the number of iterations of the loop.

### **For loop** {#for-loop}

For loops repeat blocks of code while a condition is true, and include the code to initialize, modify, and test the value of the loop iteration variable in the loop statement itself. For this reason, for loops are more compact than equivalent (counted) while loops, but they can only be used if the number of loop iterations is known before the loop is initialized.

#### **Example for loop** {#example-for-loop}

for (int bottles \= 0; bottles \< 10; bottles \++)

{

  fillBottle();

}

In the initialization statement for this for loop, the **bottles** variable is declared as an **int** number type and initialized to **zero**. The condition is next and will run the content within the braces { } if the **bottles** variable is **less** than **10**. The loop statement ends with an accumulator instruction that modifies the **bottles** variable each time through the loop. In comparison to the counted while loop structure, which only includes the condition as part of the while structure itself and has separate expressions to initialize and to modify the loop variable, for loops combine all three of these actions on one line.

### **Compound operators** {#compound-operators}

Compound operators are simplified methods used to modify the contents of a variable instead of a long-form operation. Using compound operators, the expression:

counter \= counter \+ 1;

could be shortened to:

counter++;

The following compound operators can be used after a variable name in many program expressions:

#### **Accumulator operators** {#accumulator-operators}

\++	(increment, or add 1\)

\+=1	(increment, or add 1\)

\+=n	(increment by, or add n to the variable)

\--	(decrement, or subtract 1\)

\-=1	(decrement, or subtract 1\)

\-=n	(decrement by, or subtract n from the variable)

[image1]: <data:image/png;base64,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>