Download Link: https://assignmentchef.com/product/solved-cs224-lab-3-floating-point-numbers-recursion-linked-lists
<br>
Linked lists are important dynamic data structures, useful to a variety of algorithms because of their ability to grow and shrink.  Utilities / libraries for linked lists are therefore useful, so that common functions can be available to users, pre-written, tested and ready to go. In this lab, you will write the utility functions defined only in this assignment for linked lists, in MIPS assembly language.  Your utilities will be combined with other utility programs such as create_list and display_list, and called by a main program. [Any code other than the you are asked to write in this lab will be provided (see the Unilica folder)—you don’t need to write it].

In memory, the linked lists your utilities will work with are implemented as follows: each element consists of 2 parts: pointerToNext, and value. Each part is a 32-bit MIPS word in memory. The two parts are located in successive word addresses, with the pointerToNext being first.  For example, if the byte address of the pointerToNext is 100, then the byte address of the value will be 104.  Remember, MIPS memory is byte addressable.

In the last element of the linked list, the pointerToNext has value 0, in other words it is the null pointer. This means that there is not any next element. The last element still has a value.

Write only the linked list utility routines as defined in Part 1 and Part 2. Follow MIPS programming conventions in terms of using the stack and registers. Ignore the other methods not implemented.  Modify the menu to support the new subprograms.

<strong><u>In both parts when needed you have to follow the conventions of professional MIPS programmers and use stack when needed.</u></strong>

<strong><u>For the linked list parts only upload the utilities that you have implemented do not upload the parts provided to you.</u></strong>

<strong>Part 1. Preliminary Work / Preliminary Design Report </strong>

You have to provide a neat presentation prepared by <u>Word or a word processor with similar output quality such as Latex as you were asked in Lab 1</u>. At the top of the paper on left provide the following information and staple all papers. In this part provide the program listings with proper identification (please make sure that this info is there for proper grading of your work, otherwise some points will be taken off).

Section No.: Enter your section no. here

Lab No.

Your Full Name/Bilkent ID

<ol>

 <li><strong>1</strong>. <strong>Floating Point Numbers Problem Solving</strong>:For each show your work briefly as suggested below.</li>

 <li><strong>a</strong>. Convert the number – 77.125 (do not miss the minus sign) to IEEE 754 standard. Show how you obtain mantissa and exponent. Give the final answer in hex.Single precision representation:Double precision representation:</li>

 <li><strong>b</strong>. Convert – 77.125 to a hypothetical floating point representation. Give the final answer in hex. For both cases show how you obtain mantissa and exponent.</li>

</ol>

For single precision use bias of 120:

For double precision use bias of 1020:

<ol>

 <li><strong>c</strong>. Consider the following 32 bit hexadecimal number 0xc1a00000. Assuming that it is a</li>

</ol>

Floating point number give its decimal equivalent. Show how you obtain mantissa and exponent.




<ol start="2">

 <li><strong>2</strong>. <strong>recursiveSummation</strong>: Write a <strong>recursive</strong> MIPS subprograms to add the digits of an .asciiz string. Assume that the string contains an integer number. For example, for</li>

</ol>

string: .asciiz   “1204”

it returns 7.

Provide a main program to properly test the subprogram. Note that this program is not related to linked list processing.

<ol start="3">

 <li><strong>3</strong>. <strong>deleteAfter_x </strong>: Study the linked list program provided.Write a <strong>non recursive</strong> subprogram, i.e. extend the given linked list program. to delete the element from the linked list that follows the node that contains the data value x: the pointer to the linked list is passed in $a0, and the integer value of the element to be deleted is provided in $a1. Note that this operation must be done for all occurrences of the x value. Assume that no two or more x value can appear consecutively. Return the number of elements deleted from the linked list in $v0 and print it after the operation.For example for a linked list containing the values 2, 7, 4, 8, 4, 9, 10 if the x value is 4 the linked list becomes 2, 7, 4, 4, 10. For the same original input string if the value of x is 10, the linked list remains the same.Are you able to return the deleted node back to the heap? If not include a comment in the program to explain why.</li>

</ol>

<strong>Part 2. <u>Lab Work</u>: Writing MIPS assembly language programs</strong>

<ol>

 <li><strong>checkPattern: </strong>Write a <strong>non recursive</strong> subprogram to count the bit pattern stored in the rightmost n bits (window of size n bits) of a given input. Following are the inputs for the problem:</li>

</ol>

$a0 – pattern to search, for example 101 (stored as 0000000…..00101 in $a0)

$a1 – input to search, for example 10000111101101000101000101101000

$a2 – n, for example 3

Note that, there is no need to check the validity of n (i.e., assume that $a2 is a valid input between 1 and 32. The search in $a1 must be performed from right to left. During pattern matching, bit pattern windows <strong>cannot</strong> overlap. For example, for the above sample input your program will divide the bit representation in $a1 as follows:

10000111101101000101000101101000 -&gt; 10 000 111 101 101 000 101 000 101 101 000

The number of windows matching the given pattern ($a0, 101 for this example) is 5. Starting from right (least significant bits),




window 1 – 000 – not matching

window 2 – 101 – matching

window 3 – 101 – matching

window 4 – 000 – not matching

window 5 – 101 – matching

window 6 – 000 – not matching

window 7 – 101 – matching

window 8 – 101 – matching

window 9 – 111 – not matching

window 10 – 000 – not matching

window 11 – 10 – cannot match by definition




For n=4 the maximum match possible is 8, since you would first check the rightmost four bits then four bits that come before rightmost four bits, etc. For n=2, maximum match can at most be 16, for n=3 it can be at most 10.




Provide a main program to properly test the subprogram and be sure it works for different patterns and inputs to search. Note that this program is not related to linked list processing.

<strong> </strong>

<ol start="2">

 <li><strong>(15 points) reverseString</strong>: Write a <strong>recursive</strong> subprogram, called reverseString, to copy an asciiz string pointed by $a0 into another asciiz string pointed by $a1 of the same size.</li>

</ol>

string1:  .asciiz  “123”

string2: .asciiz “abc”

When we invoke the subprogram after executing

la  $a0, string1

la  $a1, string2

jal  reverseString

string2 contains “321”




Provide a main program to properly test the subprogram. Note that this program should also work with inputs with sizes different than 3. Also, not that this program is not related to linked list processing.




<ol start="3">

 <li><strong> Insert_n (10 points)</strong><strong>:</strong>Study the linked list program provided.Write a <strong>non recursive</strong> program to insert an element to the linked list as the nth element: n= 1 means that the new item becomes the new list head, if n is higher than the list length the new element becomes the new last element of the linked list. The pointer to the linked list is passed in $a0, the integer value of the new element to be inserted is provided in $a1 and the position to be inserted is provided in $a2. This utility will request space in memory from the operating system, use it to create a new element, and then insert the new element correctly into the linked list.  The returned value in $v1 contains the pointer to the head of the linked list. Also note that the list can be empty before the insertion.</li>

 <li><strong> duplicateListIterative (15 points)</strong>: Study the linked list program provided.Write a <strong>non recursive</strong> subprogram to duplicate a linked list. When called $a0 points to the original list. It returns the new list head in $v0. Program also should be printing the new list, including the information of pointerToNext address and value of each node, like the given display function.</li>

 <li><strong> duplicateListRecursive (15 points)</strong>: Study the linked list program provided.Write a <strong>recursive</strong> subprogram to duplicate a linked list. When called $a0 points to the original list. It returns the new list head in $v0. Program also should be printing the new list, including the information of pointerToNext address and value of each node, like the given display function.</li>

</ol>