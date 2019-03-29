[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

Problem: use Cohen's d to investigate whether first babies are lighter or heavier than others  
Solution: grouped data appropriately  
```python
preg = nsfg.ReadFemPreg()
live = preg[preg.outcome == 1]

firsts = live[live.birthord == 1]
others = live[live.birthord != 1]
```
Wrote function to compute Cohen's d:  
```python
def CohenEffectSize(group1, group2):  
    mean_diff = group1.mean() - group2.mean()
    pooled_var = (len(group1)*group1.var() + len(group2)*group2.var())/(len(group1) + len(group2))
    d = mean_diff/np.sqrt(pooled_var)
    return d
```
computed Cohen's d for the weight of first babies and others:  
```python 
CohenEffectSize(firsts.totalwgt_lb, others.totalwgt_lb)```  
The result was -0.089, compared to 0.029 for the differences in pregnancy length. These two are roughly the same, on the same order of magnitude, and are small enough not to indicate any significant difference between the two groups (both are less than 0.2)