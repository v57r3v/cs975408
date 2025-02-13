java c
MODEL BUILDING IN MATHEMATICAL PROGRAMMING
13.24 Yield management


In order to solve this problem, a stochastic program (as mentioned in Section 1.2) will be built. This will be a three-period model. Solving the model for the first time will give recommended price levels and sales three weeks from departure and recommended price levels and sales for subsequent weeks under all possible scenarios. Account will be taken of the probabilities of these scenarios in order to maximize expected yield. A week later the model will be rerun, taking into account the committed sales and revenue in the first week, to redetermine recommended prices and sales for the second week (i.e. with ‘recourse’) and the third week under all possible scenarios. The procedure will be repeated again a week later.




13.24.1 Variables




p1ch = 1 if price option h chosen for class c in week 1
= 0 otherwise (c = 1, 2, 3, h = 1, 2, 3)
p2ich = 1 if price option h chosen for class c in week 2 as a result of scenario i in week 1
= 0 otherwise (c = 1, 2, 3, h = 1, 2, 3, i = 1, 2, 3)
p3ijch = 1 if price option h chosen for class c in week 3 as a result of scenario i in week 1 and scenario j in week 2
= 0 otherwise
s1ich = number of tickets sold in week 1 for class c under price option h and scenario i
s2ijch = number of tickets sold in week 2 for class c under price option h if scenario i holds in week 1 and scenario j in week 2
s3ijkch = number of tickets sold in week 3 for class c under price option if scenario i holds in week 1, scenario j in week 2 and scenario k in week 3
r 1ich = revenue in week 1 from class c under price option h and scenario i
r 2ijch = revenue in week 2 from class c under price option h if scenario i holds in week 1 and scenario j in week 2
r 3ijkch = revenue in week 3 from class c under price option h if scenario i holds in week 1, scenario j in week 2 and scenario k in week 3
uijkc = slack capacity in class c under scenarios i, j, k in successive weeks
vijkc = excess capacity in class c under scenarios i, j, k in successive weeks
n = number of planes to fly
While it is necessary to make the p variables 0–1 integer and n integer, the s variables can be treated as continuous and their values rounded.
13.24.2 Constraints
If a particular price option is chosen (under certain scenarios), then the sales cannot exceed the estimated demand and the revenue must be the product of the price and sales. These conditions can be imposed using the device described in




Section 9.2 for modelling the product of a continuous and 0–1 integer variable.


r1ich − P1chs1ich ≤ 0,
P1chs1ich − r1ich + P1chD1ichP1ch ≤ P1chD1ich for all i, c, h,
r2ijch − P2chs2ijch ≤ 0代 写MODEL BUILDING IN MATHEMATICAL PROGRAMMINGR
代做程序编程语言,
P2chs2ijch − r2ijch + P2chD2jchP2ich ≤ P2chD2jch for all i, j, c, h,
r3ijkch − P3chs3ijkch ≤ 0,
P3chs3ijkch − r3ijkch + P3chD3kchp3ijch ≤ P3chD3kch for all i, j, k, c, h,




where P and D are the given prices and demands for the corresponding periods, scenarios, classes and options.
The seat capacities must be abided by for all scenarios:
s1ich + s2ijch + s3ijkch + uijkc − vijkc − Ccn ≤ 0 for all i, j, k, c,
where Cc is the given capacity per plane for class c.
Adjustment is possible between classes:

Exactly one price option must be chosen in each class under each set of scenarios:

The above set of constraints could be replaced by SOS1 sets without the need to declare the p variables integer.
Numbers sold cannot exceed demand:
s1ich ≤ D1ichp1ch for all i, c, h,
s2ijch ≤ D2jchp2ich for all i, j, c, h,
s3ijkch ≤ D3kchp3ijch for all i, j, k, c, h.




Up to six planes can be flown:
n ≤ 6.
13.24.3 Objective

(measuring in £1000) where Qi is the probability of scenario i.
This model has 1200 constraints, one bound and 982 variables, of which 117 are 0–1 integer and one general integer.
In defining the data, it is desirable that the demands in the scenarios cover the extremes as well as the most likely cases. The recommended sales will not exceed those of the most extreme scenario in the solution to this model. In this example, it can be seen that final demands (known with hindsight) exceed those of all scenarios in a few cases. As a result, the solution will not result in sales to meet all of these demands.
Models for subsequent weeks (with recourse) are obtained from this model by fixing prices and sales for weeks that have elapsed.
13.25 Car rental 1
We model this problem as a deterministic linear programme. There would be advantage to be gained from modelling it as a stochastic programme. In order to do this, we would need to obtain data to quantify the uncertain demand.
13.25.1 Indices
i, j = Glasgow, Manchester, Birmingham, Plymouth
t = Monday, Tuesday, Wednesday, Thursday, Friday, Saturday
k = 1, 2, 3 (days hired)
Although this is a ‘dynamic’ problem, we seek a steady-state solution and can therefore regard the set of days as ‘circular’, that is, Monday of a week ‘follows’ after the subsequent Saturday; that is, if t = Monday then t − 1 = Saturday.
13.25.2 Given data
Dit = estimated rental demand at depot i on day t as given in Table 12.19
Pij = proportion of cars rented at depot i to be returned to depot j as given in Table 12.21
Cij = cost of transfer of a car from depot i to depot j as given in Table 12.22
Qk = proportion of cars hired for k days









         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
