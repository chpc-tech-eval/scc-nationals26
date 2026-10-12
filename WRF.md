# WRF

WRF (the Weather Research and Forecasting model) is an open-source weather simulation code. It is used to forecast things like storms, rainfall, wind and temperature, and it is run by universities, national weather services and researchers all over the world. It is written mostly in Fortran, with some C for I/O and build tooling, and has been developed for decades, led by NCAR in the United States.

The simulation splits the atmosphere into a 3D grid of boxes and steps forward in time, updating the wind, temperature, pressure and moisture in every box. It does this again, thousands of times. That is a lot of data moving through the CPU. Performance depends on how well your system uses memory bandwidth, how the grid is split across cores and nodes, and how well the nodes talk to each other. WRF runs on multi-core processors and clusters using MPI, OpenMP, or both at once (WRF calls these `dmpar`, `smpar` and `dm+sm`).

### What is a "domain decomposition"?

A weather grid is too big for one core, so WRF cuts it into rectangular *patches* and gives one patch to each MPI rank. Each rank updates its own patch, then swaps a thin strip of boundary cells (the halo) with its neighbours before the next step. More patches means more ranks share the work but more halo traffic. Fewer, larger patches means less halo traffic but each rank has more to do. The *shape* of the patches matters too: a long thin patch has more boundary per unit of interior than a square one. Finding the sweet spot for your hardware is a big part of tuning WRF.

Inside each patch there is a second level of splitting. WRF cuts a patch into *tiles*, which is how it hands work to OpenMP threads and keeps the working set small enough to sit in cache. Decomposition is about patches across ranks; tiling is about tiles within a patch. Both are set in the namelist. You will want to understand both.

Note: WRF has two things people mix up. The *model* (`wrf.exe`) is what we benchmark. The *WRF Preprocessing System* (WPS) is a separate toolchain for preparing real-world input data, and you will not need it in this challenge. The inputs will be provided already prepared.

Links:
- Website: https://www2.mmm.ucar.edu/wrf/users/
- Official GitHub repository: https://github.com/wrf-model/WRF
- Read up on the project: the README in the GitHub repo, the User's Guide linked from the website, and NCAR's own benchmark pages (search "WRF benchmark cases"). The benchmark pages are worth a careful read: they describe how NCAR times and validates WRF, and that is close to how we will do it.

# WRF Challenge

### Getting started:
You'll need a Linux environment, Fortran and C compilers, an MPI library, and NetCDF installed. Basic familiarity with editing a namelist file helps, but you don't need to know any meteorology.
