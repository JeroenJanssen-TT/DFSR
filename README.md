# DFSR
The DFSR (Divergence-free Spectral Representation) method is a an inflow/inlet turbulence generation method developed for large-eddy simulation of the atmospheric boundary layer(ABL) flows. The technique uses the spectral representation method to generate ABL-like turbulence with prescribed two-point flow statistics. The code is developed as a utility application using OpenFOAM as a framwork. DFSR  offers the following key features:

- Capable of running on **unstructured** meshes
- Uses **LAPACK** subroutine for matrix factorization 
- Employes the **FFT** technique for efficient time-series computation 
- Parallel implementation using **OpenMPI**    

The divergence-free condition is imposed on the generated turbulence by adding a gradient of a velocity potential instead of using the original procedure reported in the paper. The final velocity field is written for each time step in the corresponding case directory. Mathematical details of the implemented procedure can be found in [Melaku and Bitsuamlak](https://www.sciencedirect.com/science/article/pii/S0167610521000660)

## Installing DFSR
### Requirements
Before compiling the source code, you need to have the following packages already installed. 
- **OpenFOAM** preferably v8  
- Intel's oneAPI MKL package or **LAPACK** library    
- Fastest Fourier Transform in the West(**FFTW**) package

### Build from source  

Follow the following procedure to compile the source code. 

- Clone the code to your computer:

   `$ git clone https://github.com/abiyfantaye/DFSR.git DFSR` 

- Copy the `DFSR/src/DFSRTurb` directory to `$FOAM_UTILITIES/preProcessing/`:

    `$ cp -r DFSR/src/DFSRTurb $FOAM_UTILITIES/preProcessing/`

- Compile the code in `$FOAM_UTILITIES/preProcessing/DFSRTurb` directory:

    `$ cd $FOAM_UTILITIES/preProcessing/DFSRTurb`\
    `$ ./Allwclean`

The turbulence generator is now fully embedded in OpenFOAM as  `DFSRTurb` and can be launched in serial or parallel.  
## Running the test case

The directory `example/openTerrain` contains an empty domain LES case configured for open terrain condition. 
