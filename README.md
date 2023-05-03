Download Link: https://assignmentchef.com/product/solved-cs2211a-lab-no-7-introduction-to-c
<br>
The objective of this lab is to practice:

o Various C data types, arrays, rand function, clock function, and <em>recursion</em> in C o Variables scope o Pointers

If you would like to leave, and at least 30 minutes have passed, raise your hand and wait for the TA.

Show the TA what you did. If, and only if, you did a reasonable effort during the lab, he/she will give you the lab mark.

<strong>==================================================================================== </strong>

<ol>

 <li>Write, compile, and run a program that computers the sum</li>

</ol>

10000

<em>s </em><sup> </sup><em>x</em>       where <em>x</em> = 0.1.

<em>i</em>1

Compute this sum twice:

&#x25aa; One time with <em>s</em> and <em>x</em> variables declared as float  &#x25aa; One time with <em>s</em> and <em>x</em> variables declared as double Calculate the error in each sum (i.e.,<em> 1000.0  – s</em>).

Did you find any difference between the two results? Try to find a reasonable justification.

You may wish to use these declarations:

float  sf = 0.0f, xf = 0.1f; double sd = 0.0, xd = 0.1;

<ol start="2">

 <li>Write, compile, and run the following program. Did you find the result reasonable? How can we fix this program?</li>

</ol>

#include &lt;stdio.h&gt; int main(void)

{ float a = 87654321.0f, b;   b = a + 1;

printf(“a %c= a + 1
”, a == b ? ‘=’ : ‘!’);   return 0; }

<ol start="3">

 <li>Write, compile, and run the following program. Did you find the result reasonable? How can we fix this program?</li>

</ol>

#include &lt;stdio.h&gt; int main(void) { float a;

long int i = 87654321, j;   a = i;   j = a;

printf(“i = %ld, j = %ld, a = %f
”, i, j, a);   return 0; }

<ol start="4">

 <li>Write and compile the following program. Run the program many times. Did you get the same results? How to make rand() function to provide various outputs each time you run it.</li>

</ol>

#include &lt;stdio.h&gt; #include &lt;stdlib.h&gt; int main(void)

{ printf(“%d 
”, rand());   printf(“%d 
”, rand());   printf(“%d 
”, rand());   return 0;

}

<ol start="5">

 <li>Predict the following values:</li>

</ol>

&#x25aa; sizeof(int), sizeof(short), sizeof(long), sizeof(2), and sizeof(87654321)  &#x25aa; sizeof(float), sizeof(double), sizeof(long double), sizeof(2.0f), and sizeof(2.0)

&#x25aa; sizeof(char), and sizeof(‘a’).

Write a program that prints all these values. Compare the printed values with your predictions. If there is any mismatch, you should justify it.

<ol start="6">

 <li>Study the following program:</li>

</ol>

#include &lt;stdio.h&gt;

#define SIZE 10




int main(void)

{

int a[SIZE] = {2, 6, 4, 8, 10, 12, 89, 68, 45, 37};   int pass; // passes counter   size_t i; // comparisons counter

int hold; // temporary location used to swap array elements




printf(“Data items in original order
”);

// output original array   for(i = 0; i &lt; SIZE; ++i)     printf(“%4d”, a[i]);




printf(“
”);




// bubble sort

// loop to control number of passes   for(pass = 1; pass &lt; SIZE; ++pass)

// loop to control number of comparisons per pass      for(i = 0; i &lt; SIZE -1; ++i)         // compare adjacent elements         if(a[i] &gt; a[i+1])         { // swap a[i] and a[i+1]           hold   = a[i];           a[i]   = a[i+1];           a[i+1] = hold;

}




printf(“Data items in ascending order
”);

// output sorted array   for(i = 0; i &lt; SIZE; ++i)     printf(“%4d”, a[i]);




printf(“
”);   return 0; }

<ul>

 <li>After the first pass, the largest number is guaranteed to be in the highest-number element of the array; after the second pass, the two highest numbers are “in place” and so on. Instead of making nine comparisons on every pass, modify the <em>bubble sort</em> to make eight comparisons on the second pass, seven on the third pass and so.</li>

 <li>The data in the array may already be in the proper or near-proper order, so why make nine passes if fewer will suffice? Modify the sort to check at the end of each pass whether any swaps have been made. If none has been made, then the data must already be in the proper order, so the program should terminate. If swaps have been made, then at least one more pass is needed.</li>

</ul>

<ol start="7">

 <li>A recursive function is a function that calls itself. The speed of a recursive program is usually slower than nonrecursive programs because of the stack overheads. The following program recursively calculates one number in the Fibonacci sequence. The <em>first</em> number of the Fibonacci sequence is 0, the <em>second</em> number is 1, and each subsequent number is equal to the sum of the previous two numbers of the sequence, yielding the sequence 0, 1, 1, 2, 3, 5, 8, etc.</li>

</ol>

<ul>

 <li>Type, compile, and run the following program. The program repetitively calculates one number in the Fibonacci sequence for counter At the end, it prints the calculated Fibonacci number and the execution time.</li>

 <li><strong>Read “</strong><strong>man –s 3C clock</strong><strong>” to learn more about the </strong><strong>clock()</strong></li>

 <li>Re-write Fibonacci function in a non-recursive fashion. Re-compile and re-run your program.</li>

 <li>Compare the results and the execution time in the two programs.</li>

 <li>Test your program for Fibonacci(44), Fibonacci(45), Fibonacci(46) and Fibonacci(47).</li>

</ul>

Explain why the Fibonacci(47)results is not consistence with the sequence.




#include &lt;stdio.h&gt;

#include &lt;time.h&gt;




long fibonacci(long n) {  if (n == 0 || n == 1)       return n;    else

return fibonacci(n – 1) + fibonacci(n – 2); }




int main()

{  long result, number;    long counter;    clock_t start, end;




printf(“Enter an integer number: “);    scanf( “%ld”, &amp;number );




printf(“Enter repeatitions: “);    scanf( “%ld”, &amp;counter );




start = clock();




while(counter– &gt; 0)      result = fibonacci(number);




end = clock();




printf(“Fibonacci(%ld) = %ld
”, number, result);    printf(“Calculation time %f
”, ((double) (end – start))                                    / CLOCKS_PER_SEC);




return 0;

}




<ol start="8">

 <li>Trace the execution of the following function by hand.</li>

</ol>

What does the function do?

Write a program that calls the function, passing it a number entered by the user.




void pb(int n)

{

if (n != 0)    { pb(n / 2);

putchar(‘0’ + n%2);

} }

<ol start="9">

 <li>What is the output of the following program? <strong><em><u>Hint: You should consider the scope of each variable first.</u> You should decide on the correct responses before running the code to test the real result.</em></strong></li>

</ol>




#include &lt;stdio.h&gt;




/*———————————*/ void print_variable(int i);




void print_variable_2(void);




int f1(int i);




void f2(void);

/*———————————*/




int i = 0;




/*———————————*/




int main(void)

{

print_variable_2();

f2();    i=f1(i);   i=f1(50);




print_variable(i);




return 0;

}




/*———————————*/




void print_variable(int i)

{

printf(“%d
”, i++);

}




/*———————————*/




void print_variable_2(void)

{

printf(“%d
”, i++);

}




/*———————————*/




int f1(int i)

{

printf(“Begining of f1
”);   print_variable_2();

{     int i = 100;     print_variable(i);

}

print_variable(i);




printf(“Ending of f1

”);




return ++i;

}




/*———————————*/




void f2(void)

{

printf(“Begining of f2
”);   print_variable_2();

{

int i = 200;     print_variable(i);

}

print_variable(i);




printf(“Ending of f2

”);

}

/*———————————*/ <strong> </strong>

<strong><em>In the following questions, you should decide on the correct responses before running the code to test the real result.</em></strong>

<table width="542">

 <tbody>

  <tr>

   <td width="240"><strong>10.</strong> int a, *p; a = 2; p = &amp;a; a = a + 1; printf(“%d
”, *p);</td>

   <td width="144"> </td>

   <td width="158"> </td>

  </tr>

  <tr>

   <td width="240">        <strong>a) 2         b) 3   </strong><strong>11.</strong> int a, *p; a = 2; p = a; a = a + 2; printf(“%d
”, *p);</td>

   <td width="144"><strong>c) Won’t Run </strong></td>

   <td width="158"><strong>d) Random Garbage </strong></td>

  </tr>

  <tr>

   <td width="240">        <strong>a) 2         b) 4   </strong></td>

   <td width="144"><strong>c) Won’t Run </strong></td>

   <td width="158"><strong>d) Random Garbage </strong></td>

  </tr>

 </tbody>

</table>

<ol start="12">

 <li>int a, b, *p; p = &amp;a; *p = 4; p = &amp;b; *p = 3;</li>

</ol>

printf(“%d %d
”, a, b);

<ol>

 <li><strong>4 3      b) 3 3  c) Won’t Run d) Random Garbage </strong></li>

</ol>

<ol start="13">

 <li>int a, b, *p, *q; a = 3; p = &amp;a; q = p; *q = *q + 5;</li>

</ol>

printf(“%d
”, *p);

<ol>

 <li><strong>8 b) 3       c) Won’t Run    d) Random Garbage </strong></li>

</ol>

<ol start="14">

 <li>int a; int *p; a = 4; p = &amp;a;</li>

</ol>

printf(“%d
”, (*p)/a);

<ol>

 <li><strong>1 b) 4       c) Won’t Run    d) Random Garbage </strong></li>

</ol>

<ol start="15">

 <li>void f1(int *p) {(*p) = (*p) * 2;} int main() { int a = 5; f1(&amp;a); printf(“%d
”, a);</li>

</ol>

}

<ol>

 <li><strong>5 b) 10      c) Won’t Run    d) Random Garbage </strong></li>

</ol>

<ol start="16">

 <li>int a = 3, b = 4; int *p, *q; p = &amp;a; q = p; *q = b;</li>

</ol>

printf(“%d %d
”, *p, a);

<ol>

 <li><strong>4 3      b) 3 4  c) 4 4 d) 3 3 </strong></li>

</ol>

<ol start="17">

 <li>int a = 4, *p; p = &amp;a; printf(“%d
”, *p+1);

  <ol>

   <li><strong>4 b) 5       c) Won’t Run    d) Random Garbage </strong></li>

  </ol></li>

 <li>int a = 4, *p; p = &amp;a; printf(“%d
”, *(p+1));

  <ol>

   <li><strong>4 b) 5       c) Won’t Run    d) Random Garbage </strong></li>

  </ol></li>

</ol>


