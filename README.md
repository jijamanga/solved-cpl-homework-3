Download Link: https://assignmentchef.com/product/solved-cpl-homework-3
<br>
<ol>

 <li><strong>(note numbers at the start of a problem indicate how many points the problem is worth in grading.)</strong> The C++ template below defines a class for Vectors of any type T.​ Implement the member functions properly and follow the explicit naming conventions shown in the template below. You may copy and paste this template definition into your solution; it is highly suggested that you work from the template. For Vector assignment, reallocate the left Vector to be the same size as the right Vector.  Also, be sure your copy constructor makes a <em>deep copy</em>​ of the vector. Write the entire program in one header file called<strong> vector.h</strong>​   .​</li>

</ol>

<strong> </strong>

<strong>#</strong>ifndef VECTOR_H​

#define VECTOR_H #include &lt;iostream&gt; using namespace std; template

&lt;typename T&gt; // Assume Vector only takes in int or double for T​    class Vector { private:

int sz; // the number of elements in this Vector

T* buf; // the base of the array of Ts, you must allocate it public:

Vector(int n) // Vector v1(10); — create a 10 element Vector​        {

// Implementation Here;

}

Vector(initializer_list&lt;T&gt; L) // Vector v1{T1, T2, T3};​ {

// Implementation Here;

}

~Vector() /* destructor called automatically when a Vector dies​      {

// Implementation Here;

}

Destructor should free memory used. your program should have no leak/lost/still-reachable/errors(suppressed or not), besides 72704 bytes in one still-reachable block (a g++/valgrind bug on some versions). */

Vector(const Vector &amp; v) // Vector v2(v1); deep-copy​

{

// Implementation Here;

} int size() const // v1.size() returns 10 for v1 example above​    {

// Implementation Here;

}

T &amp; operator [] (const int i) /* T x = V[i];​    {

// Implementation Here;

}

Access out-of-bound index should throw an error to be caught in outside scope */

T operator * (const Vector &amp; v) const {

// Implementation Here;

}

// T x = V1 * V2; dot product

// e.g. [1, 2] * [3, 4, 5] = 1 * 3 + 2 * 4 + 0 = 11 // Assume an empty Vector will cause the product to be 0.

Vector operator + (const Vector &amp; v) const

// V3 = V1 + V2; [1, 2, 3] + [4, 5, 6, 7] = [5, 7, 9, 7] {

// Implementation Here;

} const Vector &amp; operator = (const Vector &amp; v) // V1 = V2;​    {

// Implementation Here;

} bool operator == (const Vector &amp; v) const // if (V1 == V2)…​    {

// Implementation Here;

} bool operator != (const Vector &amp; v) const // if (V1 != V2)…​    {

// Implementation Here;

} friend Vector operator * (const int n, const Vector &amp; v) // V1 = 20 * V2; — each element of V1 is element of V2 * 20 {

// Implementation Here;

}

friend Vector operator + (const int n, const Vector &amp; v) // V1 = 20 + V2; — each element of V1 is element of V2 + 20 {

// Implementation Here;

} friend ostream&amp; operator &lt;&lt; (ostream &amp; o, const Vector &amp; v) // cout &lt;&lt; V2; — prints the vector in this format

// (v0, v1, v2, … vn-1);

{

// Implementation Here;

} };

#endif

<strong> </strong>

To test your Vector class works, create a separate file named <strong>test.cpp</strong>​     and write a main()​  function that tests each of the member functions you implemented. Below we have given an example of what you might want to test.




<strong>NOTE:</strong> ​ This is how we will be testing your submission, so ensure that you maintain the names​ of the class and member functions from above.

<strong> </strong>

#include “​ ​vector.h”​ int main() // I’ll start it for you​

{

Vector&lt;int&gt; intVec{1,3,5,7,9};

Vector&lt;double&gt; doubleVec{1.5,2.5,3.5,4.5};

Vector&lt;int&gt; iv(intVec); Vector&lt;double&gt; dv(doubleVec); cout &lt;&lt; “​ ​intVec” ​    ​&lt;&lt; intVec &lt;&lt; endl;

// “​ ​intVec(1, 3, 5, 7, 9)”​  cout &lt;&lt; “​ ​iv”​ ​ &lt;&lt; iv &lt;&lt; endl;  // “​ ​iv(1, 3, 5, 7, 9)”​ cout &lt;&lt; “​ ​doubleVec”​ ​ &lt;&lt; doubleVec &lt;&lt; endl;  // “​ ​doubleVec(1.5, 2.5, 3.5, 4.5)”​  cout &lt;&lt; “​ ​dv”​ ​ &lt;&lt; dv &lt;&lt; endl;

// “​ ​dv(1.5, 2.5, 3.5, 4.5)”​

// add at least one test case for each method defined in Vector return 0;

}

<strong> </strong>

<ol start="2">

 <li>Short answer questions about your program in Problem 1:​

  <ol>

   <li>[5] What is the meaning of const after a member function prototype?</li>

   <li>[5] What happens if you use the default copy constructor for Vector?</li>

   <li>[5] What happens if you use the default assignment operator for Vector?</li>

   <li>[5] Why pass Vector by reference but make it const as with operator *?</li>

   <li>[5] Why are operators *, +, and &lt;&lt; friends and not member functions?</li>

   <li>[5] Why does operator [] return a T &amp; as opposed to a T?</li>

  </ol></li>

</ol>




<ol start="3">

 <li>how the output of the following program (written in a hypothetical Ada-like language)​ executed twice: <strong>1)</strong>​  <strong> assuming static scoping</strong>, and ​     <strong>2)</strong>​      <strong> assuming dynamic scoping</strong>.  Assume​ that appropriate ‘put’ subroutines are defined to print out their arguments in a nice format.  <strong>NOTE:</strong> Be sure you can execute this type of problem with mental tracing and drawing pictures​     of memory because you will do it <u>several more times</u>​  on a quiz and on the final quiz.<u>​   </u></li>

</ol>

<strong> </strong>

<strong>PROCEDURE Simple_Scoping IS m: integer; </strong>

<strong>PROCEDURE P IS </strong>

<strong>BEGIN m := 12; </strong>

<strong>END P; </strong>

<strong>PROCEDURE Q IS m : integer; </strong>

<strong>BEGIN m := 6; P; </strong>

<strong>put(“In Q m = “, m); </strong>

<strong>END Q; </strong>

<strong>BEGIN m := 10; </strong>

<strong>put(“In Simple_Scoping Initially   m = “, m); Q; </strong>

<strong>put(“In Simple_Scoping after Q   m = “, m); P; </strong>

<strong>put(“In Simple_Scoping after P   m = “, m); </strong>

<strong>END Simple_Scoping</strong><strong>;</strong>​

<strong> </strong>