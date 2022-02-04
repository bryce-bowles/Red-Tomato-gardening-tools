# Red-Tomato-gardening-tools
Red Tomato Gardening Tools and Sporting Goods Company. Demand forecast optimization problem model using Python, Pyomo and GLPK in Python. Multifactor objectives and constraints solved using algebraic formulation to allocate and minimize cost.   Excel Solver used to allocate how much of each product to produce so that profit is maximized


Red Tomato Gardening Tools

March 09, 2020

1	Problem
1. (from Chopra and Meindl, Ch. 8).  Solve using Pyomo.
The demand for Red Tomato Tools gardening tools is highly seasonal, peaking in the summer when people plant their gardens. Red Tomato has decided to use aggregate planning to overcome this obstacle of seasonal demand and maximize their profits. The options Red Tomato has for handling the seasonality are adding workers during the peak season, subcontracting out some of the work, building up inventory during the slow months and building up backlog of orders that will be delivered late to customers.

To determine how to best use these options through an aggregate plan, Red Tomato’s VP for Supply Chain Operations starts with demand forecasts for its tools over the next six months. These are shown in Table 1.

<img width="418" alt="image" src="https://user-images.githubusercontent.com/65502025/152539432-a3d58108-472e-4d03-81da-90f33359a64f.png">

Red Tomato sells each tool to retailers for $40. The company has a starting inventory in January of 1,000 tools. At the beginning of January, the company has a work-force of 80 employees. The plant has a total of 20 working days each month, and each employee earns $4.00 per hour regular time. Each employee works a total of eight hours a day on straight time and the rest on overtime. The capacity of the production operation is determined primarily by the total labor hours worked. Due to labor rules, no employee works more than 10 hours of overtime per month.

Other costs are shown in Table 2. Currently, Red Tomato has no limits on subcontracting, inventories and stock-outs/backlogs. All stock-outs are backlogged and supplied from the following month’s production. Inventory costs are incurred on the ending inventory in the month. The supply chain planner’s goal is to obtain the optimal aggregate plan that allows Red Tomato to end June with at least 500 units which means no stock-outs at the end of June and at least 500 units of inventory.

The optimal aggregate plan is one that results in the highest profit over the six-month planning horizon. Given Red Tomato’s desire for a very high level of customer service, we will assume all demand is met. Therefore, revenues earned over the planning horizon are fixed given the fixed price. In this case, minimizing cost over the planning horizon is the same as maximizing profit.

Table 2: Costs for Red Tomato

<img width="548" alt="image" src="https://user-images.githubusercontent.com/65502025/152539511-58dc50a9-c71b-4fe2-8bfa-8ccaff2d2909.png">

2	Data

<img width="473" alt="image" src="https://user-images.githubusercontent.com/65502025/152539576-c3fa4d07-fdb2-4d03-acc7-ee239b94127d.png">

3	Objective in Words
Decide how much to produce each month so that total cost is minimized (profit is maximized) while demand is met. Minimizing cost of: 
	* Cost of regular time labor 
	* Cost of overtime labor 
	* Cost of hiring
	* Cost of layoffs
	* Cost of holding inventory
	* Cost of stocking out
	* Cost of subcontracting
	* Cost of materials

Subject to: 
	* Demand being met
	* Due to labor rules, no employee works more than 10 hours of overtime per month
	* No Stockouts at the end of June
	    * End June with at least 500 units of inventory

4	Algebraic Formulation
Decision Variables:

<img width="311" alt="image" src="https://user-images.githubusercontent.com/65502025/152539859-47fc1c67-227a-4409-87eb-2fd9853ac771.png">

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

<img width="219" alt="image" src="https://user-images.githubusercontent.com/65502025/152539954-b832652a-8aa1-4ed4-ba02-bf3b7fb019e1.png">

Let
	1. P = {Basketball, Football} be the set of products
	2. profit〗_i = profit ($) for product i, i∈P; 
	3. rubberAval = rubber available for either product
	4. leatherAval = leather available for either product
 
3	Objective\ in Words: 
Decide how much of each product to produce so that profit is maximized 
	* At most, 500 lb’s of rubber are used
	* At most, 800 sq ft are used

4	Algebraic Formulation

<img width="271" alt="image" src="https://user-images.githubusercontent.com/65502025/152540151-9b798b63-e58c-49c0-8464-8711d20bbd9e.png">

5 Implementation
See attached file, HW3sporting_goods.xlsx, for the implementation and solution of the model using Excel Solver.

6 Interpret the Results

<img width="479" alt="image" src="https://user-images.githubusercontent.com/65502025/152540399-47810a65-ca8f-44f0-bc0e-efb4a47c8bda.png">
