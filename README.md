# Stateline Shipping Company Transportation Problem
Transportation Optimal path to Stateline Shipping company has been found using LPSolver on R
### Problem Statement
* Rachel Sundusky is the manager of Stateline Shipping and Transport Company. She signed a contract with Polychem, a company that manufactures chemicals for industrial use. 
* Polychem wants Stateline to pick up and transport waste products from its six plants to three waste disposal sites. 
* In addition to shipping directly from each of the six plants to one of the three waste disposal sites, Rachel is also considering using each of the plants and waste disposal sites as intermediate shipping points. Trucks would be able to drop a load at a plant or disposal site to be picked up and carried on to the final destination by another truck, and vice versa. 
* She particularly wants to know if it would be cheaper to ship directly from the plants to the waste sites or if she should drop and pick up some loads at the various plants and waste sites. 
### Agenda
![Agenda](https://user-images.githubusercontent.com/54346057/71422688-074ecd00-2652-11ea-88fa-aa60c2149678.JPG)


### Approach
* Our aim is to construct a model by considering the optimal approaches that would minimize the cost
* Waste products can be shipped directly from waste disposal sites to each of six plants
* Considering using each of the plants and waste disposal sites as intermediate shipping points 
* Trucks would be able to drop a load at a plant or disposal site to be picked up and carried on to the final destination by another truck, and vice versa. 

## Cost and Optimal Path Findings using LPSolver
### Transportation Analysis 
### Network Diagram
![Network](https://user-images.githubusercontent.com/54346057/71422689-07e76380-2652-11ea-8f6d-7f1b2de06824.JPG)
#### Mathematical Formulation
```
Minimum Z:  12 x1A + 15 x1B + 17 x1C + 14 x2A + 9 x2B + 10 x2C + 13 x3A + 20 x3B + 11 x3C + 17 x4A + 16 x4B + 19 x4C + 7 x5A + 14 x5B + 12 x5C + 22 x6A + 16 x6B + 18 x6C + 0 x7A + 0 x7B + 0 x7C;

#Constraints
x1A + x1B + x1C = 35;
x2A + x2B + x2C = 26;
x3A + x3B + x3C = 42;
x4A + x4B + x4C = 53;
x5A + x5B + x5C = 29;
x6A + x6B + x6C = 38;
x7A + x7B + x7C = 27;

x1A + x2A + x3A + x4A + x5A + x6A + x7A = 65;
x1B + x2B + x3B + x4B + X5B + x6B + x7B = 80;
x1C + x2C + x3C + x4C + x5C + x6C + x7C = 105;

```
```{r}
library(lpSolveAPI)
x <- read.lp("TP.lp")
solve(x)
get.objective(x)
get.variables(x)
```
 Cost is *$2822*
 ### TransShipment Analysis
 ### Network Diagram
![Net2](https://user-images.githubusercontent.com/54346057/71422686-074ecd00-2652-11ea-96ce-a4d8323bb0e9.JPG)
#### Mathematical Formulation
```
Min Z : 6X12 + 4X13 + 9X14 + 7X15 + 8X16 + 6X21 + 11X23 + 10X24 + 12X25 + 7X26 + 5X31 + 11X32 + 3X34 + 7X35 + 15X36 + 9X41 + 10X42 + 3X43 + 3X45 + 16X46 + 7X51 + 12X52 + 7X53 + 3X54 + 14X56 + 8X61 + 7X62 + 15X63 + 16X64 + 14X65 + 12X1A + 15X1B + 17X1C + 14X2A + 9X2B + 10X2C + 13X3A + 20X3B +11X3C + 17X4A + 16X4B + 19X4C + 7X5A + 14X5B + 12X5C + 22X6A + 16X6B + 18X6C + 12XAB + 10XAB + 12XBA + 15XBC + 10XCA + 10XCB;

#Constraints
X12 + X13 + X14 + X15 + X16 = 35;
X21 + X23 + X24 + X25 + X26 = 26;
X31 + X32 + X34 + X35 + X36 = 42;
X41 + X42 + X43 + X45 + X46 = 53;
X51 + X52 + X53 + X54 + X56 = 29;
X61 + X62 + X63 + X64 + X65 = 38;
X71 + X72 + X73 + X74 + X75 + X76 = 27;

X21 + X31 + X41 + X51 + X61 + X71 = X1A + X1B + X1C; 
X12 + X32 + X42 + X52 + X62 + X72 = X2A + X2B + X2C;
X13 + X23 + X43 + X53 + X63 + X73 = X3A + X3B + X3C;
X14 + X24 + X34 + X54 + X64 + X74 = X4A + X4B + X4C;
X15 + X25 + X35 + X45 + X65 + X75 = X5A + X5B + X5C;
X16 + X26 + X36 + X46 + X56 + X76 = X6A + X6B + X6C;


X1A + X2A + X3A + X4A + X5A + X6A + XBA + XCA = 65;
X1B + X2B + X3B + X4B + X5B + X6B + XAB + XCB = 80;
X1C + X2C + X3C + X4C + X5C + X6C + XAC + XBC = 105;
```
 
 ```{r}
library(lpSolveAPI)
y <- read.lp("tssp2.lp")
solve(y)
get.objective(y)
get.variables(y)
```
Cost is *$3693*

# Conclusion
![conclusion](https://user-images.githubusercontent.com/54346057/71422685-074ecd00-2652-11ea-82cb-13b910aa2c2a.JPG)




