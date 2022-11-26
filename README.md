# HexPi
## Brief
HexPi is a project of mine that has no definitive purpose or function yet. It will act as a way for me to explore mathematics and more specifically, mathematics surrounding pi.



## Part 1

I was surfing through wikipedia pages when I came across what was called the Bailey-Borwein-Plouffe formula, which is able to calculate an nth digit of pi. 
Upon discovering this, it reignited my interest in mathematics, and I got the sudden urge to create a program that was able to use this formula.

*the Bailey-Borwein-Plouffe formula*

![Screenshot_20221119_092551](https://user-images.githubusercontent.com/108390075/202863626-2d4c7709-943e-4fb3-9da0-587255ff947c.png)

### An Explanation of the Math
If we hop into desmos and take a look at this function, we can see that it is in fact able to calctulate the digits of pi.

![Screenshot_20221119_094706](https://user-images.githubusercontent.com/108390075/202864406-b13d7a96-c4be-46b2-a977-b767427fab3c.png)

Through some manipulation, the formula is turned into something computable. All the math can be found on the [wikipedia article](https://en.wikipedia.org/wiki/Bailey%E2%80%93Borwein%E2%80%93Plouffe_formula) for the formula.

![Screenshot_20221119_102919](https://user-images.githubusercontent.com/108390075/202866088-a4c5dd43-bce4-4c39-8876-e64bb4164b3f.png)

This is the formula that I worked with. 

Now that I have a usable formula, It was time for me to begin programming. Of the two sums listed above, I started with the second. We will call it B, and the first one will be A.

### $B_N(a)=\displaystyle\sum_{k=N}^{N+P+10} \frac{16^{N-k}}{8k+a}$

Now as we can see, sum B is quite fast as it only needs to calculate a small number of terms. What makes this function a bit interesting is the upper bound of the sum. At worst, that sum may have many 0's (eg. 0.00000...) before a non-zero number may appear. For this, we will give P; the amount of precision needed to sum to. I have found that 10 is a much sufficient amount of precision + 10 to mitigate an carryover problems.

### $A_N(a)=\displaystyle\sum_{k=0}^{N-1} \frac{16^{N-k}\bmod 8k+a}{8k+a}$

Sum A is more tricky, as it requires using fast exponentiation. However, by using fast exponentiation, we are able to utilize a trick that allows us to calculate only the fractional part of this sum, which is what we're interested in anyways.

We can calculate the fractional part of $\frac{16^{N-k}\bmod 8k+a}{8k+a}$ by re-writing it as $\frac{(16\cdot 16 \bmod 8k+a)(16\cdot 16 \bmod 8k+a)(...)}{8k+a}$. And boom, we no longer have to deal with $16^{N-k}$ becoming too big to store in an int.
