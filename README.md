# Experiment-2-Fitting-Poisson-Distribution
Aim: 
To fit Poisson distribution for the arrival of objects per minute from the feeder. 
# Software required: 

Python and Visual Component Tool
# Theory: 

1. The Poisson distribution gives the probability of a number of events occurring in a fixed interval of time or space when events occur independently and at a constant average rate (λ).
2. The probability mass function (PMF) is:  
<img width="1171" height="73" alt="image" src="https://github.com/user-attachments/assets/e28da9e9-3b3f-4969-baa9-2ff06c3358ba" />
3. Here, λ = mean number of occurrences, and e = 2.718 (base of natural logarithm).
4. The mean and variance of a Poisson distribution are both equal to λ.
5. Applicable when events occur independently, singly, and at a constant rate.
# Algorithm
<img width="1144" height="412" alt="image" src="https://github.com/user-attachments/assets/6bf357bd-7ba2-4908-8c93-ef74e4747a4f" />

# Program:
# Name: Ritika. S
# Reg No: 25009202
# Slot Name: 3P1-1

```
import numpy as np
import math
import scipy.stats
L = [int(i) for i in input().split()]
N = len(L)
M = max(L)
X = list()
f = list()
for i in range(M + 1):
    c = 0
    for j in range(N):
        if L[j] == i:
            c = c + 1
    f.append(c)
    X.append(i)
sf = np.sum(f)
p = list()
for i in range(M + 1):
    p.append(f[i] / sf)
mean = np.inner(X, p)
p = list()
E = list()
xi = list()
print("X   P(X=x)   Obs.Fr   Exp.Fr   xi")
print("-------------------------------")
for x in range(M + 1):
    p.append(math.exp(-mean) * mean**x / math.factorial(x))
    E.append(p[x] * sf)
    xi.append(((f[x] - E[x])**2) / E[x])
    print("%2d   %.3f   %4d   %.2f   %.3f" % (x, p[x], f[x], E[x], xi[x]))
print("-------------------------------")
cal_chi2_sq = np.sum(xi)
print("Calculated value of Chi square is %.4f" % cal_chi2_sq)
table_chi2 = scipy.stats.chi2.ppf(1 - 0.01, df=M)
print(f"Table value of Chi square at 1% level is {table_chi2:.4f}")
if cal_chi2_sq < table_chi2:
    print("The given data can be fitted in Poisson Distribution at 1% LOS")
else:
    print("The given data cannot be fitted in Poisson Distribution at 1% LOS")
```
# Collab Link:
https://colab.research.google.com/drive/10EMWMxUI9IvyziVSsNRHWgPpBuE7PJg2?usp=sharing





# Output
```
9 9 9 8 8 8 7 7 5 6 3
X   P(X=x)   Obs.Fr   Exp.Fr   xi
-------------------------------
 0   0.001      0   0.01   0.008
 1   0.005      0   0.06   0.060
 2   0.020      0   0.22   0.216
 3   0.047      1   0.52   0.453
 4   0.084      0   0.93   0.927
 5   0.121      1   1.33   0.083
 6   0.145      1   1.59   0.221
 7   0.149      2   1.64   0.081
 8   0.133      3   1.47   1.599
 9   0.106      3   1.17   2.854
-------------------------------
Calculated value of Chi square is 6.5026
Table value of Chi square at 1% level is 21.6660
The given data can be fitted in Poisson Distribution at 1% LOS

[14]
52s
```



# Result
The Poisson Distribution is fitted for the objects arrived from feeder per minute and the data is tested using Chi-square test. 

