Download Link: https://assignmentchef.com/product/solved-math-551-lab-6
<br>
<strong>Goal: </strong>In this assignment you will learn basic Matlab commands dealing with LU factorization, learn to find LU factorizations of matrices, and learn to find inverses and solve linear systems using the LU factorization. During the lab session, your lab instructor will teach you the necessary MATLAB commands to complete the assignment.

<strong>What you have to submit: </strong>An M-file whose contents are described in the task list below.

<h1>Reminders About the Grading Software</h1>

Remember, the labs are graded with the help of software tools. If you do not follow the instructions, you will lose points. If the instructions ask you to assign a value to a variable, you must <strong>use the variable name given in the instructions</strong>. If the instructions ask you to make a variable named x1 and instead you make a variable named x or X or X1 or any name other than x1, the grading software will not find your variable and you <em>will </em>lose points. Required variables are listed in the lab instructions in a gray box like this:

<h2>Variables: x1, A, q</h2>

At times you will also be asked to answer questions in a comment in your M-file. You must <strong>format your text answers correctly</strong>. Questions that you must answer are shown in gray boxes in the lab. For example, if you see the instruction

Q7: What does the Matlab command lu do? your file must contain a line similar to the following somewhere

% Q7: It computes the LU decomposition of a matrix.

The important points about the formatting are

<ul>

 <li>The answer is on a single line.</li>

 <li>The first characters on the line is the comment character %.</li>

 <li>The answer is labeled in the form Q<em>n</em>:, where <em>n </em>stands for the question number from the gray box.</li>

</ul>

If you do not format your answers correctly, the grading software will not find them and you <em>will </em>lose points.

<h1>Tasks</h1>

Create an M-file named m551lab06.m in which you will complete the following tasks. 1. Start your M-file by defining the variable A to hold the matrix

<strong>A </strong><em> .</em>

<h2>Variables: A</h2>

<ol start="2">

 <li>Add the command</li>

</ol>

[LA,UA]=lu(A);

<h2>Variables: LA, UA</h2>

Execute the M-file and examine the contents of the matrices LA and UA. Observe that UA is upper triangular.

Q1: Is LA lower triangular? Why?

Hint: Type doc lu and look at the difference between the commands

[L,U] = lu(A)                                  and                                    [L,U,P] = lu(A)

<ol start="3">

 <li>Now add the command</li>

</ol>

[L,U,P]=lu(A);

<h2>Variables: L, U, P</h2>

Execute the M-file again and look at the matrices L, U and P.

Q2: Is L lower triangular?

<ol start="4">

 <li>In the Matlab command window, type the commands</li>

</ol>

&gt;&gt; P’*P

&gt;&gt; P*P’

Q3: What do the results tell you about the relationship between <strong>P </strong>and <strong>P</strong><em><sup>T</sup></em>?

<ol start="5">

 <li>In the Matlab command window, type</li>

</ol>

<table>

 <tbody>

  <tr>

   <td width="127"></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

  </tr>

 </tbody>

</table>

&gt;&gt; A-P’*L*U

and examine the result. It should be consistent with what you saw in the lu documentation. (Round-off errors may prevent you from seeing exactly what you expect, but it should be close.)

<ol start="6">

 <li>From the previous step we saw that <strong>A </strong>= <strong>P<sup>T</sup>LU</strong>. For your own edification, you should check that this means that <strong>A</strong><sup>−1 </sup>= <strong>U</strong><sup>−1</sup><strong>L</strong><sup>−1</sup><strong>P</strong>. One way to compute the matrix on the right-hand side is to use the backslash operator: U(LP). Add a variable named inv LU to your M-file, storing the inverse of A computed in this way.</li>

</ol>

Variables: inv LU

<ol start="7">

 <li>Add a command to compute the inverse by applying the inv function to A. Name the result inv A.</li>

</ol>

<h2>Variables: inv A</h2>

<ol start="8">

 <li>Define a variable called inv err holding the difference between inv LU and inv A. Variables: inv err</li>

</ol>

Q4: Is inv err the zero matrix? Why not?

<ol start="9">

 <li>Create a variable b holding the the column vector</li>

</ol>

<strong>b </strong><em> .</em>

Variables: b

<ol start="10">

 <li>Now we’re going to solve the linear system</li>

</ol>

<h1>Ax = b</h1>

using the LU decomposition. This can be done efficiently in Matlab by observing that

<strong>Ax </strong>= <strong>b        </strong>⇐⇒         <strong>P</strong><em><sup>T</sup></em><strong>LUx </strong>= <strong>b         </strong>⇐⇒        <strong>x </strong><em>.</em>

We’ll work our way from the innermost parentheses outward and use the backslash operator instead of explicitly computing inverses. As we proceed, notice that we <em>never </em>use the expensive operations of inv or matrix-matrix multiplication.

Now, add the line

Pb = P*b; beneath the definition of b in your M-file. Variables: Pb

Run the M-file and compare b and Pb in command window.

Q5: How are the two vectors related?

<table>

 <tbody>

  <tr>

   <td width="127"></td>

  </tr>

  <tr>

   <td></td>

   <td></td>

  </tr>

 </tbody>

</table>

<ol start="11">

 <li>Add two more lines to your M-file, one computing LPb and storing it in the variable y, and the next finishing the computation by computing Uy and storing it in x.</li>

</ol>

<h2>Variables: x, y</h2>

Run your M-file, and examine the variable x. If you have completed all steps correctly, x should be the solution to the linear system.

&gt;&gt; x x =

1.0000

2.0000

3.0000

If the above isn’t what you see, go back and check your work.

<ol start="12">

 <li>Now define a new variable z in your M-file and assign it the value Ab and define xz err to be the difference between x from the previous steps and z.</li>

</ol>

<h2>Variables: z, xz err</h2>

In the command window, examine the value of xz err. This time you should get <em>exactly </em>the zero vector. The reason is that the steps you took in finding x are exactly the same steps that Matlab took in finding z.