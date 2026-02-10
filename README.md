# Extratâtonnement 



This repository contains a Jupyter notebook experimenting with tâtonnement and extratatonnement. Tâtonnement is a price adjustment algorithm suggested by Léon Walras in 1874, known to converge to Walrasian equilibria in economies satisfying the Weak Axiom of Revealed Preferences (WARP). Extratâtonnement is a class of price adjustment algorithms that arise from applying the class of mirror extragradient algorithms to a variational inequality problem corresponding to the Walrasian equilibrium problem under consideration. We show that extratâtonnement overcomes a challenge encountered by the tâtonnement process: convergence to an equilibrium in a pathological economy known as the Scarf economy. On top of this, we show that extratâtonnement efficiently converges to ε-Walrasian equilibria in large Arrow-Debreu exchange economies.



## Overview



### Arrow-Debreu Exchange Economies



The notebook simulates commodity prices in large exchange economies populated by consumers with different preferences:



* Linear utilities
* Cobb–Douglas utilities
* Leontief utilities
* CES utilities



Prices evolve according to (extra)tâtonnement updates which consider the excess demand of commodities. For each experiment, convergence to Walrasian equilibrium is tracked with Walrasian violation.



### Scarf Economy



(Extra)Tâtonnement is also run on the Scarf economy and convergence is once again tracked with Walrasian violation.





## File Contents



### Core Functions



##### Demand functions



Returns the Marshallian demand of a consumer for each commodity.



* ```get\_linear\_marshallian\_demand```: Marshallian demand for a consumer with linear utility
* ```get\_CD\_marshallian\_demand```: Marshallian demand for a consumer with Cobb-Douglas utility
* ```get\_leontief\_marshallian\_demand```: Marshallian demand for a consumer with Leontief utility
* ```get\_ces\_marshallian\_demand```: Marshallian demand for a consumer with CES utility



##### Algorithms



* ```tatonnement```: price adjustment using tâtonnement algorithm
* ```extratatonnement```: price adjustment using extratâtonnement algorithm



##### Experiment setup



* ```init\_experiment```: randomly generates endowments, valuations, CES parameters, and initial prices with normalized aggregate supply (summing up to MAX\_SUPPLY)



##### Experiments



The notebook includes a sequence of experiments comparing tâtonnement and extratâtonnement. For each experiment, the following are recorded:



* Walrasian violation over time
* Lipschitz coefficients (applicable only to extra-tâtonnement for checking pathwise Bregman continuity)
* (Optional) History of prices and excess demand of each commodity



During these experiments, prices and demands are clipped to avoid extremely large values. Prices are clipped to be between ```\[0, PRICE\_SCALE]```, whereas demand of a consumer for any commodity is clipped to be between ```\[0, 2 \* MAX\_SUPPLY]```. ```PRICE\_SCALE``` is a parameter acting as the upper-bound for prices, whereas ```MAX\_SUPPLY``` is a parameter that represents the maximum supply of each commodity in the economy.





## Usage



The cells of the notebook should be run sequentially to ensure all variables are initialized correctly. The values of experiment variables (number of goods, number of iterations, step size, etc.)  can be changed to observe the convergence of tâtonnement and extratâtonnement in these new scenarios.







&nbsp;

