# ECSIM (OPEM)

ECSIM (ElectroChemistry SIMulation tools) is an open-source research project that builds simulation software for applied electrochemistry, such as electrochemical power sources like fuel cells. Its main tool is **OPEM**, the Open Source PEM Fuel Cell Simulation Tool, written in Python. It models how a proton-exchange membrane (PEM) fuel cell performs: given operating conditions (temperature, gas pressures, active area, membrane thickness and so on) and a range of operating currents, it predicts quantities such as voltage, power, efficiency and thermal power.

Note: you may come across "ECsim", a plasma physics Particle-In-Cell code with a similar name. That is a different, unrelated project. 

And what is a PEM fuel cell?

A PEM fuel cell converts the chemical energy of hydrogen and oxygen directly into electricity, with water and heat as by-products. A thin polymer membrane lets protons pass from the anode to the cathode, while electrons are forced through an external circuit. That circuit is where you get useful current.

Static models: describe the cell at steady state. For each operating current they give the cell voltage and from it power and efficiency. Plotting voltage against current gives the "polarisation curve", with losses from activation, ohmic resistance and gas concentration.
Dynamic models: describe how the cell responds over time, including effects such as gas flow and valve time constants, and optionally a fuel reformer.
Sweeps: a simulation steps the operating current from a start value to a stop value (i-start, i-step, i-stop), solves the model at every point, and writes the results out.

What OPEM includes:
- Static models: Amphlett, Larminie-Dicks, Chamberline-Kim
- Dynamic models: Padulles I, Padulles II, Padulles-Hauer, Padulles-Amphlett, Chakraborty
- Output: CSV, HTML and `.opem` report files
- Use as a command-line tool (`opem`), as a Python library, in a Jupyter notebook, or through a Telegram bot


Links:
- See the website here: https://www.ecsim.site/
- OPEM page and documentation: https://www.ecsim.site/opem
- Repo (OPEM): https://github.com/ECSIM/opem
- All ECSIM repositories (OPEM, GOPEM GUI, fuel-cell datasets): https://github.com/ECSIM
- Install guide: https://github.com/ECSIM/opem/blob/master/INSTALL.md



Useful to Note:
- Read up on the project: the README and the `Documents/` folder in the repo, and the OPEM paper in the Journal of Open Source Software, https://doi.org/10.21105/joss.00676
- Version: OPEM v1.4 (released 16 March 2024)
- Each run writes report files to disk, so file output is part of the workload.
- The repo has `test/` and `Documents/` folders with example inputs and notebooks. Run the example test vectors first to confirm a working install.




