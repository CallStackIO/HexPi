# HexPi
## Brief
HexPi is a project of mine that has no definitive purpose or function yet. It will act as a way for me to explore mathematics and more specifically, mathematics surrounding pi.
I will document all my research about the various algorithms used and my progress and goals.

Hopefully by the end of it, I will have created something unique.

## Part 1

I was surfing through wikipedia pages when I came across what was called the Bailey-Borwein-Plouffe formula, which is able to calculate an nth digit of pi. 
Upon discovering this, it reignited my interest in mathematics, and I got the sudden urge to create a program that was able to use this formula.

*the Bailey-Borwein-Plouffe formula*

![Screenshot_20221119_092551](https://user-images.githubusercontent.com/108390075/202863626-2d4c7709-943e-4fb3-9da0-587255ff947c.png)

### Step 1 | Math
If we hop into desmos and take a look at this function, we can see that it is in fact able to calctulate the digits of pi.

![Screenshot_20221119_094706](https://user-images.githubusercontent.com/108390075/202864406-b13d7a96-c4be-46b2-a977-b767427fab3c.png)

As you can see, this formula is able to produce the digits of pi. However, there are 2 immidiate problems.

First of all, the sum is infinite. This is the lesser problem, as the solution is quite simple. After enough iterations of the sum, the formula will create smaller and smaller values, meaning we only have to sum up to a certian precision.

Second of all, $\frac{1}{16^k}$ gets very small very quickly. In fact, by the time k is 100, it is smaller than my chance at getting a girlfriend. That is to say, $3.8725919148*10^{-121}$. Using math at this infinitesimally small of a scale is not fun, and it gets far worse if we want to for example calculate the millionth digit. The solution to this problem? Implementing a spigot algorithm for this formula. I would have *liked* to do it myself, however I do not have even a remote idea how to do so. Luckily there is a [Wikipedia article](https://en.wikipedia.org/wiki/Bailey%E2%80%93Borwein%E2%80%93Plouffe_formula) on this formula which details and breaks down a much more computable version of the formula.

![Screenshot_20221119_102919](https://user-images.githubusercontent.com/108390075/202866088-a4c5dd43-bce4-4c39-8876-e64bb4164b3f.png)

This is the formula that I worked with. 

Now that I have a usable formula, It was time for me to begin programming. Of the two sums listed above, I started with the second. We will call it B, and the first one will be A.

### $B_N(a)=\displaystyle\sum_{k=N}^{N+P+10} \frac{16^{N-k}}{8k+a}$

Now as we can see, sum B is quite fast as it only needs to calculate a small number of terms. What makes this function a bit interesting is the upper bound of the sum. At worst, that sum may have many 0's (eg. 0.00000...) before a term may appear. For this, we will give P; the amount of precision needed to sum to. I have found that 10 is a much sufficient amount of precision + 10 to mitigate an carryover problems.

### $A_N(a)=\displaystyle\sum_{k=0}^{N-1} \frac{16^{N-k}\bmod 8k+a}{8k+a}$

Sum A is more tricky, as it requires using fast exponentiation.

### Step 2 | Coding (In C!)
