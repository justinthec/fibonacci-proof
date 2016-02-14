## fibonacci-proof
Looking to make an O(1) nth-fibonacci number generator

TODO: Host the proof with proper markdown on GoogleDocs or something.

# Foundation / Proof
*Disclaimer: I credit much of being able to figure this out to Math 239, testing equations on Wolfram Alpha, and the [Golden Ratio Wikipedia page](https://en.wikipedia.org/wiki/Golden_ratio).*

---
We are going to find an explicit expression for the nth-fibonacci number for any n>=0.

Here is the Fibonacci sequence: 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, ...

---
This can be expressed as a recurrence relation:

**a{n} = a{n-1} + a{n-2}** *for n>=2*

with initial values:

**a{0} = 0** and **a{1} = 1**

---

**a{n} - a{n-1} - a{n-2} = 0**

From this homogeneous equation we get the Characteristic Polynomial:

**x^2 - x - 1**

Roots:

x = **(1 + root5)/2** *(aka lowercase* **phi** *also known as the Golden Ratio)*

x = **(1 - root5)/2** *(aka uppercase* **Phi** *the Golden Ratio Conjugate)*

---
From these roots We can now obtain a general formula for the solution to the recurrence relation a{n} with unknowns **A** and **B**.

**a{n} = A((1 + root5)/2)^n + B((1 - root5)/2)^n**

**0 = A + B** *from Initial value a{0} = 0*

**1 = A((1 + root5)/2) + B((1 - root5)/2)** *from Initial value a{1} = 1*

**1 = (-B)(1/2 + root5/2) + B(1/2 - root5/2)**

**1 = -B/2 - Broot5/2 + B/2 - Broot5/2**

**1 = -2(Broot5)/2**

**B = -1/root5**

**A = 1/root5**

---
**a{n} = (1/root5)((1 + root5)/2)^n + (-1/root5)((1 - root5)/2)^n** (*Subbing in* **A** *and* **B** *into the equation from earlier*)

**a{n} = (phi^n)/root5 + (-1/root5)((1 - root5)/2)^n**

**a{n} = (phi^n)/root5 - (((1 - root5)/2)^n)/root5**

**a{n} = (phi^n - ((1 - root5)/2)^n)/root5**

**a{n} = (phi^n - ((1 - (2phi - 1))/2)^n)/root5** *(Sub-proof 1 below)*

**a{n} = (phi^n - ((1 - 2phi + 1)/2)^n)/root5**

**a{n} = (phi^n - ((2 - 2phi)/2)^n)/root5**

**a{n} = (phi^n - (1 - phi)^n)/root5**

**a{n} = (phi^n - (-(phi - 1))^n)/root5**

**a{n} = (phi^n - (-(1/phi))^n)/root5** *([Definite property of the golden ratio](https://en.wikipedia.org/wiki/Golden_ratio#Golden_ratio_conjugate))*

**a{n} = (phi^n - (-(phi))^(-n))/root5**

**a{n} = (phi^n - (-phi)^(-n))/root5**

---
**Our final expression for a{n} is (phi^n - (-phi)^(-n))/root5 with accordance to Wolfram Alpha**

![image](http://i.imgur.com/cTHshLT.png?)

**QED**

##Our next step is to implement the expression using some good ol JavaScript (Coming Soon™)
---

###Sub-proof 1: *root5 = 2phi - 1*

**root5**

**= (2root5)/2**

**= (2(root5 + 1 - 1))/2**

**= (2(root5 + 1) - 2)/2**

**= 2(root5 + 1)/2 - 2/2**

**= 2(root5 + 1)/2 - 1**

**= 2((1 + root5)/2) - 1**

**= 2(phi) - 1**

**QED**
