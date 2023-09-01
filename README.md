# Enhanced Unsteady Vortex Lattice Aerodynamics for Nonlinear Flexible Aircraft Dynamic Simulation

This repository contains the scripts and code used for the SHARPy simulations obtained for the results shown in the journal paper

[1] Duessler, S., & Palacios, R.. Enhanced Unsteady Vortex Lattice Aerodynamics for Nonlinear Flexible Aircraft Dynamic Simulation. AIAA Journal, 2023. *to appear*

Several modelling extensions and numerical improvements to the unsteady vortex-lattice method are discussed for the simulation of very flexible aircraft dynamics. In particular, fuselage aerodynamics are included by means of linear source panels, polar corrections are incorporated into the aerodynamics under potentially large deformations, and a new wake discretization scheme is derived to accelerate the computations. The theory behind each approach is detailed and successfully verified on representative test cases. The resulting modelling environment is then exemplified in a study of the flight dynamics of a flexible aircraft demonstrator model. Results indicate that for large wing deformations, a noticeable effect of fuselage aerodynamic interference appears on the wing aeroelastic behaviour. The polar corrections improve the drag estimations and allow capturing lift decrements due to stall onset at high induced angles of attack, which then affects the gust loads. The wake discretisation scheme enables a reduction of the computational for dynamic simulations on a full aircraft model by about $\mathbf{20\,\%}$ while keeping the arising error negligible small.

This paper discusses several modelling extensions and numerical improvements to the unsteady vortex-lattice method used for the simulation of very flexible aircraft dynamics.  These enhancements include:
* Fuselage aerodynamics are included by means of linear source panels.
* Sectional polar corrections are incorporated into the aerodynamics under potentially large deformations.
* A new wake discretization scheme is derived to accelerate the computations.

These enhancements have been implemented to the nonlinear aeroelastic simulation environment [SHARPy](http://github.com/imperialcollegelondon/sharpy) which is included in this repository as a submodule, as well as the SHARPy version of the [(Super)Flexop model](http://github.com/sduess/flexop_model) used as a flexible demonstrator model.


## Installation

Clone the repository to your local computer. Navigate into the sharpy folder 
```bash
cd <path-to-repository>/lib/sharpy
```
and install SHARPy as described in the [documentation](https://ic-sharpy.readthedocs.io/en/latest/content/installation.html). 

Alternatively, you can use a SHARPy distribution that is already installed on your machine. The SHARPy version used must be at least v2.1.

## Structure of this Repository

* _01_Case_Generator_: Includes all files necessary to generate the SHARPy input files using the (Super)FLEXOP model.
* _02_Nonlifting_: Includes the scripts to generate the verification study results for the fuselage-wing effects as well as the fuselage radii effect shown on the SuperFLEXOP.
* _03_Polars_: Includes all scripts necessary to reproduce the polar results for the SuperFLEXOP.
* _04_Gust_Response_: Includes all scripts to generate the gust response results for the SuperFLEXOP including wake discretisation and polar effects.
* _05_Convergence_Study_: Generates the data for the convergence study included in the appendix.
## Running Simulations
First, activate SHARPy's conda environment 
```bash
conda activate sharpy
```
and append the location of the `flexop-model` folder to the system's path with
```bash
source <path-to-flexop-model>/bin/FLEXOP_vars.sh
```
Now, the user should be all set. Note that some scripts include the postprocessing and plotting steps in seperate scripts. If you would, for example, like to run the gust response simulations, set your desired inputs and run 
```bash
python <path-to-repository>/04_Gust_Response/generate_flexop_gust_response.py
```
and run subsequently the postprocessor followed by the plottings script (please check your inputs there too)
```bash
python <path-to-repository>/04_Gust_Response/postprocess_flexop_gust_response.py
python <path-to-repository>/04_Gust_Response/plot_flexop_gust_response.py
```
## Copyleft

We are happy to share our efforts with the community and we welcome contributions to the code base. If you found this dataset useful we would ask you to cite the paper [1] and the linked Zendono archive with doi included in [1] in any publications or reports based on it.

## Contact

If you have any questions and want to get in touch, 
[contact us](https://www.imperial.ac.uk/aeroelastics/people/duessler/).

If you have any questions on how to use the model or find any bugs please file an issue. 
