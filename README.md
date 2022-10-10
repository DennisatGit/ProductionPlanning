# Production Planning
Integer Linear Program applied at Production Planning. The notebook is based on a real-life situation encountered at a high tech manufacturing firm in the Netherlands. The repo consists of the main notebook, additional notebooks to generate inputs, and input files that might result from the additional notebooks or are directly specified. The objective of the notebook is to maximise production for a certain supply and set of constraints. Constraints include capacity constaints, inventory balance equations, and maximum number of products allowed to be manufactured of one type in a specified time window. For more info about the constraints check out my medium article (see below).

The main notebook that contains the optimisation.
* Production Planning Optimisation at a High Tech Manufacturing Firm.ipynb

Notebooks used to randomly generate supply, onhand inventory and the material requirements.
* Supply Input Materials.ipynb
* Inventory Onhand.ipynb
* Material Requirements.ipynb

Input .csv files. The first three are generated with the notebooks above. 
* supply_input_materials.csv
* inventory_onhand.csv
* material_requirements.csv
* final_assemblies.csv
* input_materials.csv


**Problem Statement**
For information about the problem statement I refer to my medium article. 

https://medium.com/p/116c78f09742/edit 

**Code**
Decision variables in the PULP formulation.
* $X_{t, a}$ - integer decision variable indicating the number of assemblies _a_ produced at week _t_.
* $I_{t, d}$ - integer decision variable indicating the number of input materials _d_ at time _t_ that are in inventory. 
* $D_{t, d}$ - integer decision variable indicating the number of required input materials for input _d_ at time _t_.


**Sets**
Sets that help specify the problem. For example, the number of final assemblies or the time window. 
* W - weeks, time window of the problem.
* A - assemblies, the number of final assemblies that can be made.
* D - demanded input material, the different input materials that can be demanded (set is specified as D since the more logical I is reserved for inventory).


**Other Parameters**
Imported from .csv files
* $s_{t, d}$ - supply at time _t_ for input material _d_. Supply arrives during the period, so cannot be used for the production in that period.
* $m_{a, d}$ - material requirements to produce assembly _a_ in terms of input materials _d_.
* $o_{d}$ - onhand inventory at time $t=0$ for input material _d_.

Specified in the notebook
* $r_{t}$ - revenue parameters, are based on time and decrease over time. Consequently, early production is favoured. 
* $br$ - constant indicating the bottleneck rate in assemblies in a week. 
* $t_{a}$ - total production allowed for assembly _a_. Indicates that production in the given time window cannot exceed an upper limit. 

**Final Notes**
The solution is sensitive to specific input paramaters. Under certain circumstances the notebook finds an optimal solution in reasonable time. However, in many cases it takes a far longer time to come up with an optimal solution. To counter this problem I posed a time limit of 60s and an allowed performance gap of 10%. Still it might occur that the formulation won't find a feasible solution under specific parameter settings. Another solution might be to use one of the paid services of Gurobi, which are known to perform much better than the standard option. 
