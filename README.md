
# Table of Contents

1.  [Basics of structures…](#org95a3d13)
    1.  [Definition](#orgeecfd2e)
        1.  [But what do we mean by that?](#orgaf9359e)
    2.  [Syntax](#orgc3afc3f)
    3.  [Properties of a structure…](#org2d9d383)
2.  [A basic Students Record program…](#org93fd1f0)
    1.  [using standard approach…](#orgd431434)
    2.  [using structural approach…](#org8457521)
    3.  [Structure Declaration with ’typedef’](#org469f463)
3.  [Thank You!](#org82c8240)



<a id="org95a3d13"></a>

# Basics of structures…


<a id="orgeecfd2e"></a>

## Definition

A structure simply is a collection of finite set of similar (heterogeneous)
collection of data elements under a single name.


<a id="orgaf9359e"></a>

### But what do we mean by that?

Consider a scenario where we want to maintain a College record of a student.
Now, let’s try to visualize the various variables we are going to deal with:

-   student-Name
-   student-Email
-   student-Branch
-   student-Mobile
-   student-Year
-   student-Age
-   student-Gender
-   student-DOB
-   student-RollNo
-   student-Course
-   student-Father-Name
-   student-Mother–Name
-   student-Subjects
-   student-Marks
-   student-Percentage
-   student-Curr-Semester
-   student-Aggregate-Marks

and the list goes on…

<span class="underline">**Phew!!! So much clutter in all these variables, very hard to keep track of each
one of them individually.**</span>

The best approach to follow in a programming environment is **“Divide
n’Conquer”**. Instead of dealing with all these variables at once, let’s try to
**divide them into groups**:

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left"><span class="underline">GROUP - A</span></th>
<th scope="col" class="org-left">**student-Personal-Details**</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">&#xa0;</td>
<td class="org-left">- name</td>
</tr>


<tr>
<td class="org-left">&#xa0;</td>
<td class="org-left">- age</td>
</tr>


<tr>
<td class="org-left">&#xa0;</td>
<td class="org-left">- gender</td>
</tr>


<tr>
<td class="org-left">&#xa0;</td>
<td class="org-left">- DOB</td>
</tr>


<tr>
<td class="org-left">&#xa0;</td>
<td class="org-left">- email</td>
</tr>


<tr>
<td class="org-left">&#xa0;</td>
<td class="org-left">- mobile</td>
</tr>


<tr>
<td class="org-left">&#xa0;</td>
<td class="org-left">- father-Name</td>
</tr>


<tr>
<td class="org-left">&#xa0;</td>
<td class="org-left">- mother-name</td>
</tr>
</tbody>
</table>

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<tbody>
<tr>
<td class="org-left"><span class="underline">GROUP - B</span></td>
<td class="org-left">**student-College-Details**</td>
</tr>


<tr>
<td class="org-left">&#xa0;</td>
<td class="org-left">- rollNo</td>
</tr>


<tr>
<td class="org-left">&#xa0;</td>
<td class="org-left">- year</td>
</tr>


<tr>
<td class="org-left">&#xa0;</td>
<td class="org-left">- branch</td>
</tr>


<tr>
<td class="org-left">&#xa0;</td>
<td class="org-left">- course</td>
</tr>


<tr>
<td class="org-left">&#xa0;</td>
<td class="org-left">- semester</td>
</tr>
</tbody>
</table>

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<tbody>
<tr>
<td class="org-left"><span class="underline">GROUP - C</span></td>
<td class="org-left">**student-Academic-Details**</td>
</tr>


<tr>
<td class="org-left">&#xa0;</td>
<td class="org-left">- subjects</td>
</tr>


<tr>
<td class="org-left">&#xa0;</td>
<td class="org-left">- marks</td>
</tr>


<tr>
<td class="org-left">&#xa0;</td>
<td class="org-left">- percentage</td>
</tr>


<tr>
<td class="org-left">&#xa0;</td>
<td class="org-left">- aggregate</td>
</tr>
</tbody>
</table>

Now it’s pretty easy to keep track of each of the variables with the help of their
corresponding groups. Isn’t it? That’s exactly the idea behind the concepts of structure.


<a id="orgc3afc3f"></a>

## Syntax

In C Language, The syntax of writing a block of structure is follows:

    struct <structure_name> {
      data_element#1;
      data_element#2;
      data_element#3;
        .
        .
        .
      data_element#n;
    };

<span class="underline">**Note: ’semi-colon’ at the end of a structure.**</span>  
Let’s take a look at an example:

    struct student_Personal_Details {
      char *name;
      int age;
      int DOB;
      char *email;
      char father_Name;
      char mother_Name;
    };


<a id="org2d9d383"></a>

## Properties of a structure…

-   Structure in itself is user-defined data-type.
-   The `<structure_name>` is a pointer, pointing the first data-element of
    it’s collection.
-   All the data-elements of a structure are stored in a contiguous memory fashion
    i.e in above example, if `student_Personal_Details` is a structure name then it would
    point/store the address of it’s first element: `char *name;`. We’ll later
    explore how it works internally.
-   A structure can hold as many data-elements as required and that too
    heterogeneous elements (different data-type).
-   Structures are defined globally.
-   All data-elements of a structure are private/only known to structure and
    it’s variables. They can’t be directly accessed outside the structure.
-   The data-elements in a structure are called `members` of that structure.
-   Structures and it’s members are accessed via their `structure name` and the
    `DOT (.)` operator i.e.

    struct <structure_name <structure_variable>; 

For example:

    struct student_Personal_Details std1;
    std1.<element-name>; 

So, `std1` is a variable name of `struct student_Personal_Details` data-type.


<a id="org93fd1f0"></a>

# A basic Students Record program…


<a id="orgd431434"></a>

## using standard approach…

Writing ’Students Record’ program using only single main/normal function.

![img](/home/imahajanshubham/Downloads/profile.jpg)

    #include <stdio.h>
    #include <stdlib.h>
    
    int main (void) {
      int rollNo;
      char *name;
      char *email;
      char *branch;
    
      printf("Roll No - ");
      scanf(”%d“, &rollNo);
    
      printf("Name - ");
      fgets(&name, 25, stdin);
    
      printf("Branch - ");
      fgets(&branch, 10, stdin);
    
      printf("Email - ");
      fgets(&email, 50, stdin);
    
      return EXIT_SUCCESS;
    }


<a id="org8457521"></a>

## using structural approach…

Same program, but instead using structure.

    #include <stdio.h>
    #include <stdlib.h>
    
    struct student_Personal_Details {
      int rollNo;
      char *name;
      char *email;
      char *branch;
    };
    
    // Creating a new structure variable as ’std1’.
    struct student_Personal_Details std1;
    
    void populate_Structure(void) {
      printf("Roll No. - ");
      scanf(”%d“, &std1.rollNo);
    
      printf("Name - ");
      fgets(&name, 25, std1.stdin);
    
      printf("Branch - ");
      fgets(&branch, 10, std1.stdin);
    
      printf("Email - ");
      fgets(&email, 50, std1.stdin);
    }
    
    int main (void) {
      populate_Structure();
    
      return EXIT_SUCCESS;
    }


<a id="org469f463"></a>

## Structure Declaration with ’typedef’

Instead of using:

    struct student_Personal_Details std1;
    struct student_Personal_Details std2;
    struct student_Personal_Details std3;

we can take create our own data-type using `typedef` as follows:

    typedef <datatype> <alias/new_name>;
    
    typedef struct student_Personal_Details stdRecord;
    
    stdRecord std1;
    stdRecord std2;
    stdRecord std3;

NOTE: `typedef` stands for `type definition`. So using `typedef`, we can give a
new alias/name to already existing data-type i.e. same as one person can have
two names.


<a id="org82c8240"></a>

# Thank You!

[Description] - Coming soon…

