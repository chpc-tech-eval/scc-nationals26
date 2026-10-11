# SPECFEM3D Cartesian  

SPECFEM3D Cartesian models seismic wave propagation in local and regional domains. It handles acoustic (fluid), elastic (solid), coupled acoustic-elastic, and poroelastic media. The code uses the continuous spectral-element method (SEM) on conforming hexahedral meshes, which lets it resolve wavefields at high resolution. Researchers use it to study ground shaking after earthquakes, how waves behave in regional geology such as sedimentary basins, and non-destructive material testing.  

### Links for use:
- Source code and repository: https://github.com/SPECFEM/specfem3d
- Documentation and getting started: https://specfem3d.readthedocs.io/en/latest/
Planned Version: We plan to use the latest stable release, v4.1.1.

## SPECFEM3D challenge

### What to expect:  
- Seismic Activity Modeling
- Stress Testing
- Visualisation

### Ground rules:
- Build SPECFEM3D Cartesian v4.1.1 from the repository above. Do not modify the source code.
- Use the mesh, source and station files provided in the case. Do not change them.
- HDF5 file I/O is required. Build with HDF5 support.

### Getting started:
You'll need a Linux environment, Fortran and C compilers, an MPI library, and HDF5 built with MPI support. Run the default example on your as a test before the case is released(The exact case, parameters and scoring weights will be released later). This will confirm the install and show the run times to expect.
