# Lab-7_202001020

# **Section A**

## **We can determine the following equivalence classes based on the provided ranges:** <br>

1. Valid dates: The input triple (day, month, year) that represents a Gregorian calendar valid date, such as (3, 4, 1995).
2. Invalid dates: An invalid date is represented by an input triple (day, month, year), such as (31, 2, 2022) or (29, 2, 1900).
3. Dates that are beyond the allowable ranges, such as (0, 5, 2010) or (15, 13, 2005), are considered out of range. 

We may build the following test scenarios based on these equivalence classes:

**Tester Action and Input Data Expected Outcome**<br>

**Valid dates:**<br>
1) Calculate previous date for (14, 9, 2021) 13, 9, 2021
2) Calculate previous date for (1, 1, 2011) 31, 12, 2010
3) Calculate previous date for (21, 12, 2009) 20, 12, 2009

**Invalid dates:**<br>
1) Calculate previous date for (31, 6, 2014) Invalid date
2) Calculate previous date for (29, 2, 2018) Invalid date
3) Calculate previous date for (30, 2, 2001) Invalid date

**Out of range dates:**<br>
1) Calculate previous date for (0, 23, 2090) Invalid date
2) Calculate previous date for (35, 14, 2004) Invalid date
3) Calculate previous date for (67, 45, 0001) Invalid date

## **Boundary Value Analysis:**<br>
We may find the following border test scenarios using boundary value analysis:
1) The 1st possible date: (1, 1, 1900)
2) The last possible date: (31, 12, 2015)
3) One day before 1st possible date: (31, 12, 1899)
4) One day after last possible date: (1, 1, 2016)
5) Leap year day: (29, 2, 2000)
6) Invalid leap year day: (29, 2, 1900)
7) The 1st day of each month: (1, 1, 2000), (1, 2, 2000), (1, 3, 2000),..., (1, 12, 2000)
8) The last day of each month: (31, 1, 2000), (28, 2, 2000), (31, 3, 2000),..., (31, 12, 2000)<br>


We may find the following border test scenarios using boundary value analysis:<br>
Expected Outcome of Tester Action and Input Data<br>

**Boundary Test Cases:**<br>
1) Calculate previous date for (1, 1, 1900) Invalid date
2) Calculate previous date for (29, 2, 1900) Invalid date
3) Calculate previous date for (31, 1, 2000) 30, 1, 2000
4) Calculate previous date for (29, 2, 2000) 28, 2, 2000
5) Calculate previous date for (1, 1, 2000) 31, 12, 1999
6) Calculate previous date for (31, 12, 2015) 30, 12, 2015
<br>

## Program 1:
The function linearSearch searches for a value v in an array of integers a. <br>
If v appears in the array a, then the function returns the first index i, such that a[i] == v; otherwise, -1 is returned.<br>
int linearSearch(int v, int a[])<br>
{
int i = 0;<br>
while (i < a.length)<br>
{<br>
if (a[i] == v)<br>
return(i);<br>
i++;<br>
}<br>
return (-1);<br>
}

**Equivalence Partitioning:**
 
| Tester Action and Input Data     | Expected Outcome      |
| ------------- | :---: |
| v is not present in a         | -1         |
| v is present in a        | Index of v         |

**Boundary Value Analysis:**

| Tester Action and Input Data     | Expected Outcome      |
| ------------- | :---: |
| v is present at the last index of a length of a        | -1         |
| v is present at the first index of a         | 0         |
| v is not present in a         | -1         |
| Empty array a        | -1         |




<br>

## Program 2:
The function countItem returns the number of times a value v appears in an array of integers a.<br>
int countItem(int v, int a[])<br>

{<br>
int count = 0;<br>
for (int i = 0; i < a.length; i++)<br>
{<br>
if (a[i] == v)<br>
count++;<br>

}<br>
return (count);<br>
}

**Equivalence Partitioning:**

| Tester Action and Input Data     | Expected Outcome      |
| ------------- | :---: |
| v is not present in a         | 0         |
| v is present in a        | Number of times v appears in a         |


**Boundary Value Analysis:**

| Tester Action and Input Data     | Expected Outcome      |
| ------------- | :---: |
| v is not present in a         | 0        |
| v is present at the first index of a         | 1         |
| v is present at the last index of a        | 1        |
| v is present multiple times in a        | Number of times v appears in a         |
| v is present once in a         | 1         |
| Empty array a        | 0         |

<br>

## Program 3:
The function binarySearch searches for a value v in an ordered array of integers a. <br>
If v appears in the array a, then the function returns an index i, such that a[i] == v; otherwise, -1 is returned.<br>
Assumption: the elements in the array a are sorted in non-decreasing order.<br>
int binarySearch(int v, int a[])<br>
{<br>
int lo,mid,hi;<br>
lo = 0;<br>
hi = a.length-1;<br>
while (lo <= hi)<br>
{<br>
mid = (lo+hi)/2;<br>
if (v == a[mid])<br>
return (mid);<br>
else if (v < a[mid])<br>
hi = mid-1;<br>
else<br>
lo = mid+1;<br>
}<br>
return(-1);<br>
}


**Equivalence Partitioning:**

| Tester Action and Input Data     | Expected Outcome      |
| ------------- | :---: |
| v is not present in a         | -1         |
| v is present in a        | Index of v         |

**Boundary Value Analysis:**

| Tester Action and Input Data     | Expected Outcome      |
| ------------- | :---: |
| v is not present in a         | -1         |
| v is present at the first index of a         | 0         |
| v is present at the last index of a length of a        | -1         |
| Empty array a        | -1         |

<br>

## Program 4:
P4. The following problem has been adapted from The Art of Software Testing, by G. Myers (1979). <br>
The function triangle takes three integer parameters that are interpreted as the lengths of the sides of a triangle. <br>
It returns whether the triangle is equilateral (three lengths equal), isosceles (two lengths equal), scalene (no lengths equal), or invalid (impossible lengths).<br>

final int EQUILATERAL = 0;<br>
final int ISOSCELES = 1;<br>
final int SCALENE = 2;<br>
final int INVALID = 3;<br>
int triangle(int a, int b, int c)<br>
{<br>
if (a >= b+c || b >= a+c || c >= a+b)<br>
return(INVALID);<br>
if (a == b && b == c)<br>
return(EQUILATERAL);<br>
if (a == b || a == c || b == c)<br>
return(ISOSCELES);<br>
return(SCALENE);<br>
}


**Equivalence Partitioning:**

| Tester Action and Input Data     | Expected Outcome      |
| ------------- | :---: |
| Invalid tri. (a+b<=c)        | INVALID         |
| Valid equilateral tri. (a=b=c)         | EQUILATERAL         |
| Valid isosceles tri. (a=b<c)        | ISOSCELES         |
| Valid scalene tri. (a<b<c)         | SCALENE         |

**Boundary Value Analysis:**

| Tester Action and Input Data     | Expected Outcome      |
| ------------- | :---: |
| Invalid tri. (a+b<=c)        | INVALID         |
| Invalid tri. (a+c<b)         | INVALID         |
| Invalid tri. (b+c<a)        | INVALID         |
| Valid equilateral tri. (a=b=c)         | EQUILATERAL         |
| Valid isosceles tri. (a=b<c)        | ISOSCELES         |
| Valid isosceles tri. (a=c<b)        | ISOSCELES         |
| Valid isosceles tri. (b=c<a)        | ISOSCELES         |
| Valid scalene tri. (a<b<c)         | SCALENE         |

<br>

## Program 5:
The function prefix (String s1, String s2) returns whether or not the string s1 is a prefix of string s2 (you may assume that neither s1 nor s2 is null).<br>
public static boolean prefix(String s1, String s2)<br>
{<br>
if (s1.length() > s2.length())<br>
{<br>
return false;<br>
}<br>
for (int i = 0; i < s1.length(); i++)<br>
{<br>
if (s1.charAt(i) != s2.charAt(i))<br>
{<br>
return false;<br>
}<br>
}<br>
return true;<br>
}

**Equivalence Partitioning:**

| Tester Action and Input Data     | Expected Outcome      |
| ------------- | :---: |
| both strings s1 and s2 are empty        | True         |
| string s1 is empty and s2 is non-empty        | True         |
| Non-empty s1 is longer than s2         | False         |
| Non-empty s1 is not a prefix of s2         | False         |
| Non-empty s1 is a prefix of non-empty s2        | True         |


**Boundary Value Analysis:**

| Tester Action and Input Data     | Expected Outcome      |
| ------------- | :---: |
| both strings s1 and s2 are empty        | True         |
| string s1 is empty and s2 is non-empty         | True         |
| Non-empty s1 is not a prefix of s2         | False         |
| Non-empty s1 is longer than s2         | False         |
<br>

## Program 6:
Consider again the triangle classification program (P4) with a slightly different specification: <br>
The program reads floating values from the standard input. The three values A, B, and C are interpreted as representing the lengths of the sides of a triangle. <br>
The program then prints a message to the standard output that states whether the triangle, if it can be formed, is scalene, isosceles, equilateral, or right angled.<br>
Determine the following for the above program:<br>
<br>

**a) Identify the equivalence classes for the system<br>**

Equivalence Classes:<br>
EC1: All sides are positive, real numbers.<br>
EC2: One or more sides are 0 or negative.<br>
EC3: The length of any two sides added together is less than or equal to the length of the remaining side (impossible lengths).<br>
EC4: The sum of any two sides' lengths is larger than the length of the remaining side (possible lengths).<br>

<br>


**b) Identify test cases to cover the identified equivalence classes. Also, explicitly mention which test case would cover which equivalence class.<br>**

Test cases:<br>
TC1 (EC2): A=0, B=4, C=5 (invalid input)<br>
TC2 (EC2): A=-2, B=4, C=5 (invalid input)<br>
TC3 (EC1): A=5, B=6, C=7 (scalene triangle)<br>
TC4 (EC1): A=5, B=5, C=7 (isosceles triangle)<br>
TC5 (EC1): A=3, B=4, C=5 (right-angled triangle)<br>
TC6 (EC1): A=5, B=5, C=5 (equilateral triangle)<br>

<br>


**c) For the boundary condition A + B > C case (scalene triangle), identify test cases to verify the boundary.<br>**

Test cases for the boundary condition A + B > C:<br>
TC7 (EC4): A=2, B=3, C=5 (sum of A and B is equal to C)<br>

<br>


**d) For the boundary condition A = C case (isosceles triangle), identify test cases to verify the boundary.<br>**

Test cases for the boundary condition A = C:<br>
TC8 (EC4): A=5, B=6, C=5 (A equals to C)<br>

<br>

**e) For the boundary condition A = B = C case (equilateral triangle), identify test cases to verify the boundary.<br>**

Test cases for the boundary condition A = B = C:<br>
TC9 (EC4): A=3, B=3, C=3 (all sides are equal)<br>

<br>

**f) For the boundary condition A^2 + B^2 = C^2 case (right-angle triangle), identify test cases to verify the boundary.<br>**

Test cases for the boundary condition A^2 + B^2 = C^2:<br>
TC10 (EC4): A=6, B=8, C=10 (right-angled triangle)<br>

<br>

**g) For the non-triangle case, identify test cases to explore the boundary.<br>**

Test cases for the non-triangle case:<br>
TC11 (EC3): A=2, B=2, C=4 (sum of A and B is less than C)<br>

<br>

**h) For non-positive input, identify test points.<br>**

Test points for non-positive input:<br>
TP1 (EC2): A=-2, B=4, C=5 (invalid input)<br>
TP2 (EC2): A=0, B=4, C=5 (invalid input)<br>
Note: Test cases TC1 to TC10 covers all identified equivalence classes.<br>

<br>

# **Section B**
1. **Control flow diagram:**<br>
![CFG lab7 drawio](https://user-images.githubusercontent.com/77296298/231450621-84663712-6803-49b5-8fa5-ff44ac2ac74a.png)


2. **Test sets:**<br>

**a) Statement coverage test sets:** To achieve statement coverage, each statement in the code must be performed at least once.
<br>
* Test 1: p = A vector with three or more points with the same y component
* Test 2: p = A vector with three or more points with different y components
* Test 3: p = A vector with one point
* Test 4: p = A vector with two points with the same y component
* Test 5: p = A vector with two points with different y components
* Test 6: p = empty vector



<br>

**b) Branch coverage test sets:** We must ensure that each possible branch in the code is taken at least once in order to achieve branch coverage.
<br>
* Test 1: p = A vector having three or more points that all have the same y component and the same x component.
* Test 2: p = A vector consisting of three or more points with distinct y components, none of which have the same x component
* Test 3: p = A vector consisting of three or more points with the same y component and some with the same x component
* Test 4: p = A vector with one point
* Test 5: p = A vector with two points with the same y component
* Test 6: p = A vector with two points with different y components
* Test 7: p = empty vector

<br>

**c) Basic condition coverage test sets:** To achieve basic condition coverage, we need to make sure that every basic condition in the code (i.e., every Boolean subexpression) is evaluated as both true and false at least once
<br>
* Test 1: p = A vector having three or more points that all have the same y component and the same x component.
* Test 2: p = A vector consisting of three or more points with distinct y components, none of which have the same x component
* Test 3: p = A vector consisting of three or more points with the same y component and some with the same x component
* Test 4: p = A vector with one point
* Test 5: p = A vector with two points with different y components
* Test 6: p = A vector containing two points that have the same y component, with the first point having a smaller x component.
* Test 7: p = A A vector containing two points that have the same y component, with the second point having a smaller x component.
* Test 8: p = empty vector


