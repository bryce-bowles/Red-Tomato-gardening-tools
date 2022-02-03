# Red-Tomato-gardening-tools
Red Tomato Gardening Tools and Sporting Goods Company. Demand forecast optimization problem model using Python, Pyomo and GLPK in Python. Multifactor objectives and constraints solved using algebraic formulation to allocate and minimize cost.   Excel Solver used to allocate how much of each product to produce so that profit is maximized


Red Tomato Gardening Tools

March 09, 2020

1	Problem
1. (from Chopra and Meindl, Ch. 8).  Solve using Pyomo.
The demand for Red Tomato Tools gardening tools is highly seasonal, peaking in the summer when people plant their gardens. Red Tomato has decided to use aggregate planning to overcome this obstacle of seasonal demand and maximize their profits. The options Red Tomato has for handling the seasonality are adding workers during the peak season, subcontracting out some of the work, building up inventory during the slow months and building up backlog of orders that will be delivered late to customers.

To determine how to best use these options through an aggregate plan, Red Tomato’s VP for Supply Chain Operations starts with demand forecasts for its tools over the next six months. These are shown in Table 1.
Table 1: Demand Forecasts
Month	Demand Forecast
January	1,600
February	3,000
March	3,200
April	3,800
May	2,200
June	2,200

Red Tomato sells each tool to retailers for $40. The company has a starting inventory in January of 1,000 tools. At the beginning of January, the company has a work-force of 80 employees. The plant has a total of 20 working days each month, and each employee earns $4.00 per hour regular time. Each employee works a total of eight hours a day on straight time and the rest on overtime. The capacity of the production operation is determined primarily by the total labor hours worked. Due to labor rules, no employee works more than 10 hours of overtime per month.

Other costs are shown in Table 2. Currently, Red Tomato has no limits on subcontracting, inventories and stock-outs/backlogs. All stock-outs are backlogged and supplied from the following month’s production. Inventory costs are incurred on the ending inventory in the month. The supply chain planner’s goal is to obtain the optimal aggregate plan that allows Red Tomato to end June with at least 500 units which means no stock-outs at the end of June and at least 500 units of inventory.

The optimal aggregate plan is one that results in the highest profit over the six-month planning horizon. Given Red Tomato’s desire for a very high level of customer service, we will assume all demand is met. Therefore, revenues earned over the planning horizon are fixed given the fixed price. In this case, minimizing cost over the planning horizon is the same as maximizing profit.

Table 2: Costs for Red Tomato
Item	Cost
Material Cost	$10/Unit
Inventory Holding Cost	$2/Unit/Month
Marginal Cost of Stock-out/Backlog	$5/Unit/Month
Hiring and Training Costs	$300/Worker
Layoff Cost	$500/Worker
Labor hours Required	4/Unit
Regular Time Cost	$4/Hour
Overtime Cost	$6/Hour
Cost of Subcontracting	$30/Unit

2	Data
	M = month {January, February, March, April, May, June}
	D = demand {1600, 3000, 3200, 3800, 2200, 2200}
	dema〖nd〗_i = demand for month ⅈ, ⅈ∈M
	〖workforce〗_i = workforce size for month ⅈ, ⅈ∈M
	〖hired〗_i = number of employees hired at the beginning of month ⅈ, ⅈ∈M
	〖layoff〗_i = number of employees laid off at the beginning of month ⅈ, ⅈ∈M
	X_i = number of units produced in month ⅈ, ⅈ∈M
	〖inventory〗_i = inventory at the end of month ⅈ, ⅈ∈M
	〖stockout〗_i = number of units stockout/backlogged at the end of month ⅈ, ⅈ∈M
	〖subcontract〗_i= number of units subcontracted for month ⅈ, ⅈ∈M
	〖overtime〗_i= number of overtime hours in month ⅈ, ⅈ∈M

3	Objective in Words
Decide how much to produce each month so that total cost is minimized (profit is maximized) while demand is met. Minimizing cost of: 
	Cost of regular time labor 
	Cost of overtime labor 
	Cost of hiring
	Cost of layoffs
	Cost of holding inventory
	Cost of stocking out
	Cost of subcontracting
	Cost of materials

Subject to: 
	Demand being met
	Due to labor rules, no employee works more than 10 hours of overtime per month
	No Stockouts at the end of June
	End June with at least 500 units of inventory

4	Algebraic Formulation
Decision Variables:
Let x_i= amount produced in month ⅈ,  ⅈ∈M
Objectives and constraints: 
Total Cost: 
∑_(i∈M)▒〖640〖workforce〗_i 〗+ ∑_(i∈M)▒〖60〖overtime〗_i 〗+ ∑_(i∈M)▒〖300〖hired〗_i+ 〗 ∑_(i∈M)▒〖500〖layoff〗_i  +∑_(i∈M)▒〖2〖inventory〗_i+ 〗 ∑_(i∈M)▒〖5〖stockout〗_i+〗〗 ∑_(i∈M)▒〖10X_i+ 〗 ∑_(i∈M)▒〖30〖subcontract〗_i  〗
Inventory Balance:
〖inventory〗_(i-1)+〖reg〗_i+〖overtime〗_i+〖subcontract〗_i-〖demand〗_i-〖stockout〗_(i-1)= 〖inventory〗_i-〖stockout〗_i for i∈M
Worker, hiring, and layoff: 
〖workforce〗_i- 〖workforce〗_(i-1)+〖hired〗_i-〖layoff〗_i for i∈M
Starting: 〖workforce〗_0=80
Capacity: 
X_i≤  〖40workforce〗_i + 〖overtime〗_i/4 for i∈M
Overtime Limit: 
〖overtime〗_i≤  10〖workforce〗_i for i∈M

5	Implementation
See attached file, HW_3_RedTomatoes.ipynb and RedTomatoes.xlsx, for the implementation and solution of the model using Pyomo and GLPK in Python.

6	Results and Interpretation
The optimal solution for Red Tomatoes is… 
 
 Sporting Goods Company Problem Solution

March 09, 2020

1	Problem
(from Taylor 3.7).  A sporting goods company makes basketballs and footballs.  Each product is produced from two resources - rubber and leather.  Each basketball produced results in a profit of $12 and each football earns $16 in profit.  The resource requirements for each product are:  basketball (3 lb rubber, 4 sq ft leather) and football (2 lb rubber and 5 sq ft leather).  There are 500 lb of rubber and 800 sq ft of leather available.  For your implementation, implement and solve the problem using Microsoft Excel and turn in your workbook.  In addition, answer the following questions, explaining your reasoning:
	How much does the profit need to change per basketball before it is optimal to produce basketballs?
	Suppose a source for leather offers 100 square feet at $3 per square foot.  Should the company make the purchase?
	Suppose a source for rubber offers 100 pounds at $3 per pound.  Should the company make the purchase?
	What would be the effect on the optimal solution if the profit for a basketball changed from $12 to $13?
	What would be the effect on the optimal solution if the profit for a football changed from $16 to $15.50?
Update 2/27: For both problems, you do not need to specify that the decision variables are integer.  Assume that fractional values are acceptable.

2	Data: 

Basketball	Football
Rubber (lb)	3	2
Leather (sq ft)	4	5
Profit	 $12.00 	 $16.00 

Let
	P = {Basketball, Football} be the set of products
	〖profit〗_i = profit ($) for product i, i∈P; 
	rubberAval = rubber available for either product
	leatherAval = leather available for either product
 
3	Objective\ in Words: 
Decide how much of each product to produce so that profit is maximized 
	At most, 500 lb’s of rubber are used
	At most, 800 sq ft are used

4	Algebraic Formulation
Decision Variables:
Let x_i = amount produced of product i, ⅈ∈P.
Objective and constraints:
max∑_(i∈P)▒x_i *〖profit〗_i  ,i∈P
(Profit)	max∑_(i∈P) ∑_(j∈M)  ∑_(k∈T)▒x_ijk *〖price〗_ik  ,i∈P,k∈T
	(Profit)
∑_(i∈P)▒x_i *〖rubberAvail〗_i  ,i∈P≤500  	(Rubber Constraint)		
∑_(i∈P)▒x_i *〖leatherAvail〗_i  ,i∈P≤800  
	(Leather Constraint)		
5 Implementation
See attached file, HW3sporting_goods.xlsx, for the implementation and solution of the model using Excel Solver.

6 Interpret the Results

How much does the profit need to change per basketball before it is optimal to produce basketballs? 
The profit needs to increase by greater than $.80. 
Suppose a source for leather offers 100 square feet at $3 per square foot.  Should the company make the purchase?
Yes, Shadow price is $3.2 so they would buy it
Suppose a source for rubber offers 100 pounds at $3 per pound.  Should the company make the purchase?
No they should not, the shadow price for rubber is $0.
What would be the effect on the optimal solution if the profit for a basketball changed from $12 to $13?
Then you would produce 128.57 basketballs and 57.14 footballs for an optimal solution profit of $2,585.17
What would be the effect on the optimal solution if the profit for a football changed from $16 to $15.50?
Then you would produce 0 basketballs and 160 footballs for an optimal solution profit of $2,480.00

