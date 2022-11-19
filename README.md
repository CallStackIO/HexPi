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

As you can see, this is in decimal. However what we are aiming at is hexideciamal pi.
The end goal of this program was to be able to calculate any given digit of pi by utilizing this formula. However, there is an immidiate problem; the sum is infinite. To solve this problem, lets take a look at a graph of the sum.


