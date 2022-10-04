# Production Planning
Integer Linear Program applied at Production Planning. The notebook is based on a real-life situation encountered at a high tech manufacturing firm in the Netherlands. The repo consists of .csv files that are input files for the main notebook 'Production Planning Optimisation at a High Tech Manufacturing Firm.ipynb'. There are other .ipynb files which are used to randomly generate supply, conversion matrix and the onhand inventory in the beginning of the time frame. It is not necessary to run these notebooks since input files are provided. However, these notebooks show how these input files are created. 

**Problem Statement**
For information about the problem statement I refer to my medium article. 

https://medium.com/p/116c78f09742/edit 

**Code**
Decision variables
- X_{t, a}, integer decision variable indicating the number of assemblies _a_ produced at week _t_.
