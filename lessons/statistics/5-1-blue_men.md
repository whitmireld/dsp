[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

Problem: if the distribution of heights is roughly normal, with parameters µ = 178 cm and σ = 7.7 cm for men, what percentage of the male population is between 5’10” and 6’1”?

Solution: inputted parameters into scipy.stats normal distribution 
```python
mu = 178
sigma = 7.7
normal = scipy.stats.norm(loc=mu, scale=sigma)
```

Converted low and high height barriers to centimeters:  
```python
low = (5 + 10/12)*12*2.54
high = (6 + 1/12)*12*2.54
```

Calculated the percentile difference between the barriers:  
```python
normal.cdf(high) - normal.cdf(low)
```

Resulting in: 34.27%