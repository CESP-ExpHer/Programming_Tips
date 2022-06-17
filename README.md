# Some Tips for Programming

## Calculation of Very Very Small Values for P-value (P-value calculation based on beta and se)
If there is no column for **P_value** in the original GWAS Summary Statistics data, **P-value** could be calculated based on **beta** and **se** using **chi2** distribution.
### Python
```python
from scipy.stats.distributions import chi2
p = chi2.sf( (beta/se)**2, 1 )
```
Example:
```python
beta = -0.246192				
se = 0.00802599	
z2 = (beta/se)**2
chi2.sf(z2,1)
1.251669043223986e-206
```
### R
```R
p = pchisq( (beta/se)**2, 1, lower.tail = FALSE )
```
Example:
```R
beta = -0.246192				
se = 0.00802599	
z2 = (beta/se)**2
pchisq(z2, 1, lower.tail = FALSE)
1.251669e-206
```
