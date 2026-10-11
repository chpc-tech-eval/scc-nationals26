# ExaHyPE 2

ExaHyPE 2 is an open-source engine for simulating waves and fluids, such as sound travelling through air, shock waves, or gas flowing around an object. These problems are described by *hyperbolic partial differential equations*, which tell us how a quantity (pressure, density, velocity) changes in space and time.

The simulation splits the domain into a very large number of small cells and updates each one step by step. That is a lot of computation, which makes it a classic HPC workload. Critically, performance depends on how well your system uses its CPU cores, caches and memory bandwidth. ExaHyPE 2 is built on the Peano 4 framework and runs on multi-core processors and clusters.

And what is Peano??

Peano is an open-source C++ framework for running simulations on adaptive meshes in parallel. The mesh is the grid of cells the equations are solved on. Peano manages that grid for you:

Adaptive refinement: it uses finer cells where the action is (a shock wave perhaps) and coarse cells elsewhere, so computation isn't wasted on quiet regions.
Space-filling curve ordering: cells are ordered along the Peano space-filling curve, which keeps neighbouring cells close together in memory (good for cache use) and makes it easy to split work evenly between cores or nodes.
Parallelism: it handles shared-memory threading and distributed-memory MPI, so the physics code doesn't have to.
Python front end: you describe the project in Python scripts, and Peano generates the C++ glue code and build setup.

Note: you may come across ExaHyPE 1, an earlier generation of the engine that used a Java-based toolkit to generate code; ExaHyPE 2 is a rewrite built on Peano 4 that is configured through Python scripts, and ExaHyPE 2 is the only version used in this challenge

Links:
- See the website here: https://tobiasweinzierl.webspace.durham.ac.uk/software/exahype/
- Repo (ExaHyPE 2 is part of Peano): https://gitlab.lrz.de/hpcsoftware/Peano
- Read up on the project: see the README and the `documentation/` folder in the repo


# ExaHyPE 2 Challenge

### Ground rules:
We'll be running ExaHyPE 2 at the gitlab linked above. Use exactly this repo so results are unified.
This is a CPU-only challenge. GPU offloading is not used.


### What to expect:
You will build the software and run a simulation case on your cluster.
Expect the focus to be on getting the most out of your CPUs.
You will be expected to document how you built and ran it (compiler and version, configure line, flags, thread and rank counts, environment variables).
The exact case and run parameters will be released later.



### Getting started:
You'll need a Linux environment, a recent C++ compiler, basic python knowledge 
Allow time for the build, as it takes some patience. Get one working build first, then try optomising.
