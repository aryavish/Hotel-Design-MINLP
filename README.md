**Application of Mixed Integer Non-Linear Optimization in Commercial
Real Estate Development**

**Introduction**

In commercial real estate development, the generally accepted
methodology in the design of hotel projects is to commission a market
study to ascertain the economic supply and demand of a local market the
hotel will serve, and then construct the hotel such that it will contain
on average the mean number of room types (1 bedroom, 2 bedroom, suites,
etc) and amenities (meeting rooms, restaurants, fitness center, pool,
etc) as its market competitors. In doing so, the developer aims to
achieve a mean rate of return on his building, assuming the market is
stable and he is able to capture the mean economic demand of the local
market. The only way in which the developer can maximize his returns to
equity is thus to add leverage or debt to his capital structure to
finance construction of the project. His return mathematically is
presented below[^1]:

*Total Equity Return Rate (IRR) = Return~equity~ + (Return~equity~ --
Cost~debt~)\*Debt/Equity*

Thus as he increases leverage (debt/equity ratio) and under normal
financing transactions as his cost of debt is less than his cost of
equity (Return~equity~), the developer will maximize his equity returns
and achieve superior risk adjusted returns for his project than if he
financed construction with 100% equity.

The purpose of this study (the Study) will be to apply mixed integer
non-linear optimization (MINLP) in the design of a hotel property in
order to maximize the annual profit of the asset subject to various
design and construction constraints. NPS formulation will be utilized in
the definition of the objective function and formulation of the MINLP
model throughout this Study.

**Study Model Formulation**

The Study is a special application of the union of two disjoint knapsack
linear optimization problems subject to the same convex set defined by
the problem constraints hyperplanes. Specifically, the Study aims to
achieve optimal profit from the union of two disjoint assets in a
commercial real estate hotel design project: the number of hotel room
types and amenities the hotel offers. We define profit as Net Operating
Income (NOI), which is equivalent to: *Revenue~rooms+amenities~ --
Variable_Costs~rooms+amenities~ -- Fixed_Costs~hotel~*[^2]. For purposes
of this Study we explicitly exclude the effect of income taxes and
financing costs on profit, consistent with the manner in which NOI is
computed[^3].

We thus define the objective function for the Study as follows[^4]:

![](media\image1.png){width="6.5in" height="0.857891513560805in"}

By simple inspection we note the objective function is multivariate,
nonlinear and non-convex since various decision variables interact with
each other.

We define the relevant constraint functions below that serve to create
the convex hull of feasible solutions and provide a brief discussion of
each[^5].

![](media\image2.png){width="6.5in" height="3.176591207349081in"}

Constraints (C01 and C02) limit the quantity of hotel room types and
number of restaurants and meeting rooms the property can build subject
to the maximum gross square footage allocated to each in the building.
Constraint (C03) limits the quantity of room types, restaurants, and
meeting rooms built subject to the maximum allowable budget. Here the
constraint resource of time, represented by decision variables
BUILDDAYS~i~, BUILDDAYSREST, and BUILDDAYSMTGROOM is an unconstrained
resource and thus unbounded, but bounds (C03) by assessing an interest
cost penalty per diem of construction days (time) used. Constraint (C04)
limits the annual quantity of rooms demanded to the maximum annual
quantity of the total number of rooms built and similarly constraints
(C07 and C08) require a minimum number of restaurants and maximum number
of meeting rooms to be built on the subject asset, respectively.
Constraints (C06 and C07) serve to approximate the quantity demanded of
a room type as a function of its price utilizing a linear approximation
of an exponential function that captures the elasticity of demand with
respect to price for the specific room type. As further discussed below
in Section "Data Gathering", the short run natural log demand
elasticity, dQ/dP was found to be -0.7. Thus we formulate a function to
estimate the annual demand of a room type as: Q~i~(p) =
*mean_roomnights~i~\*e\^(-0.07p)*. Since the coefficient -0.7 represents
the per cent change in quantity per the per cent change in price, we
define p to be the per cent change from the mean room price of a
particular room type in the hotel property. For the purposes of the
Study we created five intervals within which to measure ROOMNIGHTS~i~ =
Q~i~(p) and ROOMPRICE~i~ to optimize the objective function.

**Data Gathering**

The MINLP model formulated in this Study can be applied to any hotel
asset type in any location. For the purposes of this Study, however we
define the hotel asset to be a five star, luxury asset that will be
centrally located in a submarket of the City of Seattle, WA. Using a
previously commissioned market study and appraisal for a similar asset
in the same submarket, six hotel competitors were identified as
follows[^6]:

![](media\image3.png){width="5.009015748031496in"
height="0.798507217847769in"}

Thus, the *mean_roomprice~i~* for the hotel in the Study was taken as
the mean ADR of each room type across the six competitor hotels. The
*mean_roomnights~i~*, which reflects the mean quantity of room nights
demanded (sold) by room type of the hotel asset in the Study assuming
ROOMPRICE~i~ = *mean_roomprice~i~* was computed as the average of the
(i) maximum room nights quantity demanded per room type and (ii) the
mean room nights quantity demanded per room type, assuming the 75%
occupancy was distributed uniformly over the composition % per room
type. The basis of this assumption is that the quantity demanded per
room type varies by competitor notwithstanding the same price due to
non-price factors including: location, recent build, network effect
(guest rewards program), height (views), distance to public
transportation, among other factors.

Elasticity of demand for a hotel property is most directly impacted by
the market in which the hotel operates and the chain scale of the
property (luxury, midscale, economy, etc). The selected asset for the
Study is defined to be an upper luxurious property in a top 50 MSA
market. Thus, the demand elastic value of -0.7 was chosen, which
reflects the per unit natural log change in quantity of rooms sold by
the per unit natural log change in price[^7].

**Obtaining an Optimal Solution**

The MINLP model was formulated in MS Excel and solved using the GRG
Nonlinear solver algorithm in approximately three minutes. An optimal
solution was found that maximized NOI to approximately \$26.5MM with a
room type composition for single, double and suite rooms of 50%, 25%,
and 25% respectively, in comparison to the competitive set of 40%, 40%,
20%. Pricing per room was higher than mean room ADR rates in the optimal
solution by approximately 20%, 35%, and 34% per room type,
respectively[^8]. The most common measure of profitability for a
developer for a newly constructed asset is yield to cost, defined as NOI
/ total project costs. The yield to cost found by the nonlinear solver
is 22.60% on total project cost of \$117MM. The model was also run with
decision variables set to the mean parameters of the competitive set
(the Developer Scenario), which a developer would typically follow under
standard hotel development assumptions. Under this scenario, the NOI was
computed to be \$14.22MM on total project costs of \$122MM, resulting in
a yield to cost of 11.65%. Mathematical optimization thus resulted in a
1.97x improved yield over standard development assumptions under a
Developer Scenario.

**Conclusion & Limitations**

MINLP optimization for commercial real estate design and development is
a special application of the knapsack optimization problem and lends
itself well to optimizing the return of the asset subject to resource,
time and capital constraints to construct the asset. Although the Study
yielded superior returns compared the traditional Developer Scenario,
further refinement of the MINLP model in this Study is warranted.
Specifically, the demand curve, which is exponential in nature can be
better approximated by increasing the number of intervals by which the
curve is linearly approximated. Further refinement of the demand elastic
coefficient is also necessary, through a combination study of market
research and predictive modeling/multivariate regression techniques.
Computation of interest cost per day, which serves as the cost
coefficient for the time constraints can be better approximated since
interests costs are not linear but represent a cubic shape with respect
to total construction costs, congruent with the total construct project
S-curve that is commonly exhibited in the market. Finally, although
MINLP found a superior optimal solution, its building efficiency use,
defined as % of total buildable sq ft was 87% compared to 95% of
buildable square ft under the Developer Scenario. Common industry
practice in commercial real estate development is to use 100% of
buildable square feet. Additional decision variables such as penalty
costs for non-utilized buildable square feet and alternative leasing
revenue for non-utilized buildable square feet, where applicable in the
building design, can be introduced into the model to better maximize
building efficiency and achieve more widespread adoption of mathematical
optimization in the commercial real estate development industry.

**Appendix 1 -- NPS Formulation**

![](media\image4.png){width="6.325694444444444in" height="7.5in"}

![](media\image5.png){width="6.5in" height="3.877192694663167in"}

[^1]: Moglidiani & Miller, Proposition II

[^2]: Not in NPS formulation

[^3]: The Dictionary of Real Estate Appraisal, The Appraisal Institute

[^4]: Refer Appendix 1 for NPS Formulation definitions

[^5]: Refer Appendix 1 for entire problem formulation

[^6]: Sources: Jones Lang Lasalle Market Research report, Seattle, Sep

    2017; www.hotelplanner.com

[^7]: Journal of Hospitality Financial Management, Hotel Industry Demand

    Curves, 2012

[^8]: For full table of decision variable results, refer Appendix 2
