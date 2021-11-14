# Roadmap

We plan to leverage the existing collaboration between EOSC-Nordic and EOSC-Life for Tool roadmap (packaging, containerization, etc.) to implement tools and workflows as identified in Annex-A. 
When it comes to data management, we will explore different solutions in collaboration with EOSC-Nordic. The need to streamline data movement (and overall to reduce data copies as much as possible) has been clearly identified (it is currently one major bottleneck for researchers and it definitely hinders their ability to smoothly move to cloud computing, including HPC-cloud). As part of EOSC-Nordic, we have already tested different solutions, for instance converting netCDF model outputs to data formats that are more efficient on cloud resources (zarr, caterva; zarr is compatible with xarray so it would not significantly change researchers’ day to day habits), creating online catalog with intake or SpatioTemporal Asset Catalogs and finally offering remote access (public or private) with s3 and/or s3-compatible object storage (such as minio). 

One major task, in several of the identified workflows, is to run an Earth System Model: CESM, the community Earth System Model developed and maintained by NCAR is already available in Galaxy and NorESM could also be added (a conda package and corresponding container are already available). Below is an example of Galaxy workflow (see Figure-1):


![Figure-1](figure-1.png)
**Figure-1**: Workflow for running a CESM B1850 f18_g17 experiment on Galaxy. This example workflow sets-up the case, compiles the code, runs one month and generates plots (surface temperature). 

While Galaxy is highly configurable and flexible on how to run tools e.g. Galaxy can use different back-end and queuing systems, we have made all our tests on Galaxy Europe where Galaxy tools are run either as conda packages (from conda-forge and/or bioconda) and/or within containers (docker, singularity).
To introduce CESM in Galaxy Europe we have:
- Packaged CESM in bioconda 
- Generated automatically containers
- Created an XML wrapper with metadata (EDAM ontology and Galaxy metadata) so that CESM Galaxy tool can be called from the Galaxy Graphical Interface, command line (from any terminal) or JupyterLab (for instance the Galaxy Climate JupyterLab).

Then whenever a user creates a workflow (or runs the CESM Galaxy tool), he/she can:
- Share his/her history either with everyone or only with his/her collaborators (end-users have full control on permissions/access to data and histories);
- Reference/add his/her Galaxy history to Rohub (https://www.rohub.org/) as a Research Object (public or private);
- Publish his/her workflow in Workflow Hub (https://workflowhub.eu/) as a FAIR workflow.

EC-EARTH is not open source which makes it more difficult to be included in Galaxy. However, EC-EARTH containers (registered in private repositories) will be developed and tested within NICEST2. As a consequence, all workflows in Annex-A where an ESM needs to be run will be demonstrated with NorESM and/or CESM. For any other workflows, we will make use of both NorESM and EC-EARTH model outputs (or more generally any model outputs publicly available from either researchers’ simulations or CMIP6).
