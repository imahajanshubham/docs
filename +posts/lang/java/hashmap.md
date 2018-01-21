
# Table of Contents

1.  [Basics of Hash Maps](#org29005ff)
    1.  [Definition](#orga99846d)
        1.  [But what do we mean by that?](#orga28835b)
        2.  [What did we observed?](#org706b1bf)
2.  [Syntax](#orge6525e8)
3.  [Properties of a HashMap](#orga47a5fe)
4.  [A sample program](#orga082e24)
5.  [The test case](#org4833985)
6.  [A humble solution](#org3df976e)
    1.  [Step - 1](#orgc0ef6b1)
    2.  [Step - 2](#org11a6224)
    3.  [Step - 3](#org41d6111)
    4.  [Step - 4](#org6683ec8)
    5.  [Step - 5](#org2bdb882)
    6.  [Step - 6](#org863291f)
7.  [Thank You!](#orgecc7f31)

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides" width="100% class=&quot;center&quot;">


<colgroup>
<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<tbody>
<tr>
<td class="org-left">Home</td>
<td class="org-left">Featured Blogs</td>
<td class="org-left">[GitHub](https://github.com/imahajanshubham)</td>
</tr>
</tbody>
</table>


<a id="org29005ff"></a>

# DONE Basics of Hash Maps


<a id="orga99846d"></a>

## Definition

Java HashMap is one of the most popular Collection classes in java. Java Hash  printf("Hello World!\n");
Map
is Hash table based implementation. HashMap in java extends AbstractMap class
that implement(setq org-hide-emphasis-markers t)  printf("Hello World!\n");
s Map interface.


<a id="orga28835b"></a>

### But what do we mean by that?

Before trying to understand the definition of Hash Map, we should try to understand
the concept behind the Hash Map.

Let’s say we want make a record of a phone-book (person’s name and phone no) as
follows:

<div class="NOTE">
For the sake of simplicity (to avoid rehashing), let’s assume:

-   Each name is unique.
-   A single person can have only one phone no.

</div>

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">**Name**</th>
<th scope="col" class="org-right">**Phone No.**</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">Raj</td>
<td class="org-right">2345671001</td>
</tr>


<tr>
<td class="org-left">Nisha</td>
<td class="org-right">4464832994</td>
</tr>


<tr>
<td class="org-left">Sonu</td>
<td class="org-right">4858830685</td>
</tr>


<tr>
<td class="org-left">Nitin</td>
<td class="org-right">8739111330</td>
</tr>


<tr>
<td class="org-left">Akshay</td>
<td class="org-right">8743193003</td>
</tr>


<tr>
<td class="org-left">Muskan</td>
<td class="org-right">9899363086</td>
</tr>
</tbody>
</table>

and so on…

Now what we want to do is:
If we say a name, we wanna know his/her phone no.

For ex:

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-right" />
</colgroup>
<tbody>
<tr>
<td class="org-left">Input</td>
<td class="org-right">Raj</td>
</tr>


<tr>
<td class="org-left">Output</td>
<td class="org-right">2345671001</td>
</tr>
</tbody>
</table>


<a id="org706b1bf"></a>

### What did we observed?

-   We don’t know the exact no of names/phone-nos.

<div class="tip">
The no of entries (name/phone no) in the Hash Map is called **Hash-Size**.

</div>

So the Hash-Size is not fixed. But there are ways via which we can fix the
Hash-Size (using constructors).

-   The order of the entries (Raj -> Nisha or Nisha -> Raj) doesn’t matter for us
    to fetch their phone nos. So Hash Map doesn’t require sorted input.
-   Person’s name (input) is the `KEY` to find the `VALUE` i.e. phone no. (output)
    i.e **name is mapped with phone no**.
-   Instead of phone record, we can create any type of record. So the data-type of
    Keys/Values depends upon the user.
-   Each `Name - phone no` is in the form of pair similar to `Key - Value`.

Till know, we came to understand a little-bit about something known as
Hash-Size, Keys and Values. Now let’s try to understand more about Hash Map in
technical terms.


<a id="orge6525e8"></a>

# DONE Syntax

In Java, the HashMap class’ object is declared as follows:

    Map<Key, Value> obj = new HashMap<Key, Value>();

For ex:

    Map<String, Integer> record1 = new HashMap<String, Integer>();
    Map<String, String> record2 = new HashMap<String, String>();


<a id="orga47a5fe"></a>

# TODO Properties of a HashMap

-   HashMap is denoted as `HashMap<Key, Value>`.
-   No need to specify the size of HashMap.
-   No need of sorted input.
-   Neither it sorts the stored input.
-   Similar to `Hashtable` class except it permits null values and keys.
-   You need to import `java.util.HashMap` class in order to use the HashMap class
    and its methods.

<div class="note">
There are a lot many other important properties too such:

-   Rehashing
-   Load Factor
-   Various methods.

But we will study all these and others during our lifelong journey ♥.

</div>


<a id="orga082e24"></a>

# DONE A sample program

What better way to understand more than to learn it by implementation? With that
spirit, let’s try to make a program in java to implement a phonebook
as follows:

1.  Get ’n’ (`INTEGER` value) from the user, denoting the no of entries/records
    to be filled in the phonebook.
2.  Now, get ’n’ no of names-phoneno (`STRING-INTEGER`) space separated pairs from the user.
    
    For ex:
    
    <table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">
    
    
    <colgroup>
    <col  class="org-left" />
    </colgroup>
    <tbody>
    <tr>
    <td class="org-left">Raj 34745910</td>
    </tr>
    
    
    <tr>
    <td class="org-left">Sonu 86988901</td>
    </tr>
    
    
    <tr>
    <td class="org-left">Ravi 87240393</td>
    </tr>
    </tbody>
    </table>

3.  Get unknown no of names (`STRING`) from the user and for each of the these
    names, print:

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<tbody>
<tr>
<td class="org-left">If name is present in the phonebook</td>
<td class="org-left">**name=phoneno**</td>
</tr>


<tr>
<td class="org-left">If name is not present</td>
<td class="org-left">**Not found**</td>
</tr>
</tbody>
</table>


<a id="org4833985"></a>

# DONE The test case

Input:

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />
</colgroup>
<tbody>
<tr>
<td class="org-left">3</td>
</tr>


<tr>
<td class="org-left">Raj 34745910</td>
</tr>


<tr>
<td class="org-left">Sonu 86988901</td>
</tr>


<tr>
<td class="org-left">Ravi 87240393</td>
</tr>


<tr>
<td class="org-left">Raju</td>
</tr>


<tr>
<td class="org-left">Ravi</td>
</tr>
</tbody>
</table>

Output:

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />
</colgroup>
<tbody>
<tr>
<td class="org-left">Not found</td>
</tr>


<tr>
<td class="org-left">Ravi=87240393</td>
</tr>
</tbody>
</table>


<a id="org3df976e"></a>

# DONE A humble solution


<a id="orgc0ef6b1"></a>

## Step - 1

Let’s create testMain class with main function and initialize `Scanner` and `Map`
classes:

    import java.util.*;
    import java.io.*;
    
    class testMain {
      public static void main(String []args) {
        Map<String, Integer> phoneBook = new HashMap<String, Integer>();
        Scanner scan = new Scanner(System.in);
      }
    }    


<a id="org11a6224"></a>

## Step - 2

Now let’s get the value of ’n’ (`INTEGER`) i.e. the no of phone records to be entered:

    int n = scan.nextInt();


<a id="org41d6111"></a>

## Step - 3

Now let’s fill ’n’ records (`STRING INTEGER`) in the phonebook.

    for(int i = 0; i < n; i++){
      String name = scan.next();
      int phone = scan.nextInt();
    
      phoneBook.put(name, phone);
    }

<div class="tip">
To put the data (name, phoneno) in the HashMap/phonebook, `put()` method is used.

**Syntax:**
       `put(Key, Value)`

</div>


<a id="org6683ec8"></a>

## Step - 4

Now comes a little tricky part:

1.  Get unknown no of names (`STRING`) from the user and for each of the these
    names, print:

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<tbody>
<tr>
<td class="org-left">If name is present in the phonebook</td>
<td class="org-left">**name=phoneno**</td>
</tr>


<tr>
<td class="org-left">If name is not present</td>
<td class="org-left">**Not found**</td>
</tr>
</tbody>
</table>

Let’s to do it one-by-one:

-   get unknown no of names (`STRING`).

    while(scan.hasNext()) {
      String s = scan.next();
    }


<a id="org2bdb882"></a>

## Step - 5

-   print the required output.

    while(scan.hasNext()) {
      String s = scan.next();
      Integer phoneNumber = phoneBook.get(s);
    
      System.out.println((phoneNumber != null) ? s + "=" + phoneNumber : "Not found");
    }

<div class="tip">
To get the data (phone no) from the HashMap, `get()` method is used.

**Syntax:**
       `get(Key)`

So, `phoneBook.get(Raj)` will return the phone no of ’Raj’ if he’s
present. To check whether a Name/Key is present in the `HashMap` or not, `HashMap` uses `equals()` method internally.

</div>


<a id="org863291f"></a>

## Step - 6

Let’s connect the dots:

    import java.util.*;
    import java.io.*;
    
    class testMain {
      public static void main(String []args) {
        Map<String, Integer> phoneBook = new HashMap<String, Integer>();
        Scanner scan = new Scanner(System.in);
    
        int n = scan.nextInt();
    
        for(int i = 0; i < n; i++) {
          String name = scan.next();
          int phone = scan.nextInt();
    
          phoneBook.put(name, phone);
        }
    
        while(scan.hasNext()) {
          String s = scan.next();
          Integer phoneNumber = phoneBook.get(s);
    
          System.out.println((phoneNumber != null) ? s + "=" + phoneNumber : "Not found");
        }
    
        scan.close();
      }
    }

That’s it, the program to implement HashMap Logic in Java. I hope if not all,
we learned something :)


<a id="orgecc7f31"></a>

# Thank You!

