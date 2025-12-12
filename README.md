# A General ODE Bootstrap
A package to perform parameter estimation for ordinary differential equations (ODEs) using the Differential Evolution (DE) algorithm, with an option to perform bootstrapping.

## Requirements
For importing into your python workspace:
  - numpy
  - pandas
  - odeint from scipy.integrate
  - differential_evolution from scipy.optimize
  - Counter from collections
  - matplotlib

For running functions within this package:
  - ODE model (you need to pre-specify your ODE model)
  - Time series data (this package was written for ODE models dealing with data that has a time component)
  - Data from different treatment groups needs to be separated out before running anything
  - Initial conditions for all ODE equations

## Using this Package
1. Import all required libraries and packages:
```python
from A_General_ODE_Bootstrap import timeseries_pull, observedData_pull, CostFunction, DE_Generalized, DE_Results

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from scipy.integrate import odeint
from scipy.optimize import differential_evolution
import seaborn as sns
from collections import Counter
from matplotlib.ticker import MultipleLocator
```
2. Import data as a `pandas` dataframe:
```python
your_data = pd.read_csv('your_data_file.csv')
# OR
your_data = pd.read_excel('your_data_file.xlsx')
```
Doing this should result in a dataframe that looks, in some way, shape, or form, like:
| Time | Variable A | Variable B | $$\cdots$$ | Variable $k$ |
|-------|------------|------------|------------|--------------|
| $t_0$ | $$A_0$$    | $$B_0$$    | $$\cdots$$ | $$k_0$$      |
| $t_1$ | $$A_1$$    | $$B_1$$    | $$\cdots$$ | $$k_1$$      |
| $t_2$ | $$A_2$$    | $$B_2$$    | $$\cdots$$ | $$k_2$$      |
| $\vdots$ | $\vdots$ |$\vdots$   | $$\ddots$$ | $\vdots$     |
| $t_n$ | $$A_n$$    | $$B_n$$    | $$\cdots$$ | $$k_n$$      |

Or, if you have more than one treatment group in your dataframe:
| Time | Treatment |Variable A | Variable B | $$\cdots$$ | Variable $k$ |
|------|-----------|-----------|------------|------------|--------------|
| $t_0$ | $\alpha$ | $$A_0$$    | $$B_0$$    | $$\cdots$$ | $$k_0$$     |
| $t_1$ | $\alpha$ | $$A_1$$    | $$B_1$$    | $$\cdots$$ | $$k_1$$     |
| $t_2$ | $\alpha$ | $$A_2$$    | $$B_2$$    | $$\cdots$$ | $$k_2$$     |
| $\vdots$ | $\alpha$ | $\vdots$ |$\vdots$   | $$\ddots$$ | $\vdots$       |
| $t_n$ | $\alpha$ | $$A_n$$    | $$B_n$$    | $$\cdots$$ | $$k_n$$     |
| $t_0$ | $\beta$  | $$A_0$$    | $$B_0$$    | $$\cdots$$ | $$k_0$$     |
| $t_1$ | $\beta$  | $$A_1$$    | $$B_1$$    | $$\cdots$$ | $$k_1$$     |
| $t_2$ | $\beta$  | $$A_2$$    | $$B_2$$    | $$\cdots$$ | $$k_2$$     |
| $\vdots$ | $\beta$ | $\vdots$ |$\vdots$   | $$\ddots$$ | $\vdots$       |
| $t_n$ | $\beta$  | $$A_n$$    | $$B_n$$    | $$\cdots$$ | $$k_n$$     |






