# PDDL_Numeric_Planning-For-Factory-Manufacturing-Process
The idea of this project is to optimize production schedules to minimize costs and maximize efficiency, ensuring timely delivery of products while maintaining inventory and coordinating with robotic machines.This project aims to create an efficient production plan for a factory that manufactures a single type of product. 
<div>
<img src="https://github.com/shahkarKhan24/PDDL_Numeric_Planning-For-Factory-Manufacturing-Process/blob/main/Images/Fac%20prod.jpeg" width="600" alt="Dataset"/>
</div>
<h3>Domain</h3>
The domain of our project is basically divided into five station: i.e Assembly station, Painting station, Packaging station, Shipping station and inventory station
The predicate/fluents that we use are:
At(robot, station)
Next(station1, station2)
Flags(f)
Functions:
(inventry ?s - station)    (assembled ?s - station)    (painted ?s - station)    (packaged ?s - station)    (ship ?s - station)    (total-cost)
Actions: we have total of 6 actions 
Move robot_1/2 , check_Inventory, Assembling, Painting, Packaging, Shipping and Restocking


<h3>Problems</h3>
We have design 5 problem instances , starting from very simple to more complex problem by imposing different constraints and objects.
Problem 1: Order 1 products
Problem 2: Order 15 products
Problem 3: Order of products with inventory (some products already manufactured in the inventory)
Problem 4: Restocking - order o product with instruction to maintain inventory for the future orders 
Problem 5: Using two robotics manipulators/crane/lifter to transfer products within production stages
<h3>Planner</h3>
To solve the numerical planning problem we have decided ENHSP, Expressive Numeric Heuristic Search Planner, is a PDDL automated planning system that supports classical and Numeric Planning (PDDL2.1).
ENHSP transforms the PDDL descriptions into a graph-search problem where nodes represent states visited by the planner. The planner builds this graph in an incremental-forward fashion, and is guided by a heuristic function to explore only those nodes whose associated state is reachable from the init and get the planner closer to the goals.
To run the ENHSP from the shell we nee to us the command as : java -jar enhsp.jar -o <domain_file> -f <problem_file> -planner <configuration> where configuration represent the heuristic we want use

<h3>Heuristics</h3>
The heuristics that we use are 
sat-hmrp;
sat-hadd;
opt-hmax.
1. MRP Heuristic (h_mrp): mrp heuristics is a rule base heuristics.It starts with a GBFS and then uses the MRP heuristic to improve the solution..
2.  Numeric h_add (hadd) Heuristic : The h_add heuristic is an additive heuristic often used in automated planning. It is a relaxed heuristic, meaning it simplifies the problem to provide an estimate of the cost to reach the goal.
3. Numeric h_max (hmax) Heuristic: The h_max heuristic is another relaxed heuristic used in automated planning. It provides an estimate of the cost to reach the goal by considering the maximum cost of achieving any single subgoal.

