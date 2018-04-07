- [Greetings Everyone, 😊](#sec-1)
- [What took so long?](#sec-2)
  - [**How to calculate the factorial of … say `50`?**](#sec-2-1)
  - [Factorial of `50` is a `65` digit answer!](#sec-2-2)
  - [Do we even have a `datatype` in C to store such a huge number?](#sec-2-3)
- [But why?](#sec-3)
  - [False Assumption](#sec-3-1)
  - [Wrong Test Cases](#sec-3-2)
- [How did I overcame it?](#sec-4)
    - [What if:](#sec-4-0-1)
    - [One step forward!](#sec-4-0-2)
    - [Another step forward!](#sec-4-0-3)
    - [Almost reached the Destination!](#sec-4-0-4)
- [Key Learnings](#sec-5)
- [Few more treats!](#sec-6)
- [Thank you](#sec-7)

# Greetings Everyone, 😊<a id="sec-1"></a>

Been almost two days, Did a lot of challenges in the time period.

---

# What took so long?<a id="sec-2"></a>

Umm… Basically, a question:

## **How to calculate the factorial of … say `50`?**<a id="sec-2-1"></a>

Sure, our basic logic of calculating the factorial using recursion would work perfectly:

```C
unsigned int factorial(unsigned int number) {
  if (!number)
    return 1;

  return number * factorial(number - 1);
}
```

-   It’s even efficient in terms of speed too.

---

## Factorial of `50` is a `65` digit answer!<a id="sec-2-2"></a>

You heard it right, Factorial of `50` equals to `30414093201713378043612608166064768844377641568960512000000000000`

Just way too long…

---

## Do we even have a `datatype` in C to store such a huge number?<a id="sec-2-3"></a>

Nope!

I was just shocked, that even the **factorial program** being the most elementary-level failed and I never realized of dealing with such huge numbers.

---

# But why?<a id="sec-3"></a>

Because of my false assumption and wrong test cases.

## False Assumption<a id="sec-3-1"></a>

Implementing the Pen n’ Paper logic via Code and believing - **that’s it!**

i.e. Only focusing on how to iterate the loop/function from `2` to `n`.

---

## Wrong Test Cases<a id="sec-3-2"></a>

The major reason behind such mistake:

-   **0!**: The logic gives `1` as expected.
-   **5!**: Again `120` as expected.

OR in some case,

-   **10!**: i.e. `3628800` which is under feasable range.

**But never went beyond that… ** And that was the sole mistake.

---

# How did I overcame it?<a id="sec-4"></a>

Thought processing.

Now after understanding the problem and realizing that I don’t have any such datatype to store such big values at my disposal… - I started my planning on

**How do I manage/store the result?**

After facing a lot many previous challenges, I got the habit of storing the occurrences of a digit/alphabet in the arrays as index value.

So,

At the back of my mind, I had the same thought of somehow using arrays to solve the problem. Was just calculating the factorial of `5` by-hand on a piece of paper, and I got this weird idea:

While multiplying `5` with `24`,

| 2 as carry |       |
| 2          | 4     |
|            | 5     |
|            | **0** |

---

### What if:<a id="sec-4-0-1"></a>

Instead of treating `24` as a whole number, if I store

`4` in `array[0]` and, `2` in `array[1]`

And then multiply `5` by `array[0]` and then add the carry to `array[1]` and again multiply just like I was doing on the piece of paper?

---

### One step forward!<a id="sec-4-0-2"></a>

Initially, it felt a little tough to think such a logic… But after a little-bit of practice, I finally managed develop the following logic:

```C
int factorial(int number, int value[]) {
  value[0] = 1;
  int noOfDigits = 1;

  for (int localNumber = 2; localNumber <= number; localNumber++) {
    noOfDigits = multiply(localNumber, value, noOfDigits);
  }
}
```

Using the `for` loop, I was iterating as usual, but was multiplying each intermediate number with the previous value i.e. `array` (initially set to `1` as `0!` is `1`) and updating the no of digits thus obtained.

So far, only **30%** work was done.

Tricky part of actually multiplying the numbers was still left.

---

### Another step forward!<a id="sec-4-0-3"></a>

So to ease the problem, I divided it into two sub-parts:

1.  Multiply the intermediate number.

    Taking the `24 x 5` example, Let’s say that at `array[0]`, we would get `4`. So, multiply `5` with `4`.
    
    **Answer is 20.**
    
    Now, separate out the carry digit from the intermediate product `number % 10` logic. And store the remainder in ~array[0].
    
    ```C
    for (int indx = 0; indx < noOfDigits; indx++) {
      int prod = value[indx] * localNumber + carry;
    
      value[indx] = prod % 10;
      carry = prod / 10;
    }
    ```
    
    <div class="note">
    We also need to take care of any previous carry digits. In that case, we need to add the carry too.
    
    </div>
    
    ---

2.  Update the final carry.

    Add the carry i.e `2` to `array[0 + 1]`.
    
    If again a carry is generated (ex. 9 + 1 = 10), then repeat **previous step**.
    
    ```C
    for (int indx = 0; indx < noOfDigits; indx++) {
      int prod = value[indx] * localNumber + carry;
    
      value[indx] = prod % 10;
      carry = prod / 10;
    }
    ```
    
    ---

### Almost reached the Destination!<a id="sec-4-0-4"></a>

Now only thing to be done was, print values of `array` from `0` to `noOfDigits` so as to display the final factorial.

And we are good to go!!!

---

# Key Learnings<a id="sec-5"></a>

-   Always validate the assumptions, **at any cost**.
-   Explore every other possibilities.
-   Consider general-case scenarios rather than fixed ones.
-   Always have the room to improvise/innovate.

I hope this was the experience worth sharing.🙋

---

# Few more treats!<a id="sec-6"></a>

Here’s the original source code and various others on **GitHub**:

---

**#1** CodeChef - [ **Magical Function** ](https://www.codechef.com/CBEN2018/problems/LEONARD) The goal was to recognize the pattern of a given function. [view code](https://github.com/imahajanshubham/Miscellaneous-Programs/blob/master/c_lang/problem14/magicNumbers.c)

---

**#2** CodeChef - [ **Average Halfify(keteki)** ](https://www.codechef.com/KQM82018/problems/QM8B) The goal was to calculate the recursive average of pairs of **n** numbers. [view code](https://github.com/imahajanshubham/Miscellaneous-Programs/blob/master/c_lang/problem19/halfifyaverage.c)

---

**#3** CodeChef - [ Mminimizing the Dot Product ](https://www.codechef.com/problems/bitmask2) the goal was to calculate the minimum dot product of given two vectors. we could interchange the vector positions with each other if needed. [view code](https://github.com/imahajanshubham/Miscellaneous-Programs/blob/master/c_lang/problem15/dotproduct.c)

---

**#4** CodeChef - [ **Little Chef and Sums** ](https://www.codechef.com/problems/CHEFSUM) The goal was calculate the total of **suffix-sum** and **prefix-sum** of given **n** values in an array. [view code](https://github.com/imahajanshubham/Miscellaneous-Programs/blob/master/c_lang/problem16/suffixprefixsum.c)

---

# Thank you<a id="sec-7"></a>

<a href="https://github.com/imahajanshubham/docs/blob/master/%2Bposts/lang/c-c%2B%2B/beware_of_the_assumptions.org" class="fixedbutton btn btn-social-icon btn-github" onclick="_gaq.push(['_trackEvent', 'btn-social-icon', 'click', 'btn-github']);"><span class="fa fa-github"></span></a>

<ul class="pager">
    <li class="next">
        <a href="https://imahajanshubham.github.io/docs/others/words_to_cherish.html" class="btn btn-neutral float-right" title="The greatest enemy of learning is knowing" accesskey="n" rel="next">next <span class="fa fa-arrow-circle-right"></span></a>
    </li>
    <li class="previous">
        <a href="https://imahajanshubham.github.io/docs/lang/c-c++/only_source_code/average_halfify.html" class="btn btn-neutral" title="Average Halfify (keteki)" accesskey="n" rel="prev"><span class="fa fa-arrow-circle-left"></span> previous</a>
    </li>
</ul>
