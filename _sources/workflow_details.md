# Description of the 7 core workflows

## W1 - Running an Earth System Model to simulate specific events/scenarios or for systematic sensitivity studies

### Description

End users will exploit one Earth System Model using the same source code but changing different parameters. The ESM is often run in ensemble mode. A control (possibly also run in ensemble mode) is required to later compare the results and calculate anomalies.
This workflow is typically used for changing CO2 (abrupt x4, for example) or more generally forcings (or characteristics of emissions) or other model inputs, simulating eruptions (injection of various types of volcanic aerosols, with different concentrations, durations, heights, etc.), experimenting with geoengineering, or for systematic sensitivity studies where a single parameter is changed (many different values).

- **Step-1** - *Sub-Workflow 1* - 
  **Prepare and Run a control experiment**:
    - Base code is used from fully validated ESM (configuration is scientifically and technically validated on the target platform).
    - Usually performed many times by different researchers from different groups because it is hard to find published control experiments.
    - Whenever published, data may miss important information about the setup (including processor layout, target platform, options, etc.) and published control experiments may not be re-usable.

- **Step-2** -  *Sub-Workflow 2* - **Quickly analyze the ESM control experiment (to make sure everything ran correctly)**:
    - Usually done at the very end e.g. after spending a lot of CPU hours. 
    - Researchers only focus on components and variables they are familiar with, and may miss important problems (i.e., looking at outputs from the atmospheric component when a “problem” originates from the ocean, etc.).
    - Sometimes this step is skipped because researchers blindy trust the ESM, whereas obviously the core developers have not tested everything.

- **Step-3** -  *Sub-Workflow 3* - **Prepare inputs for running a customized experiment**:
    - Researchers develop their own codes for customizing their experiments but never share their programs (and not even the resulting data/forcing, etc.).

- **Step-4** -  *Sub-Workflow 1* - **Prepare and Run a “customized” experiment** 

- **Step-5** -  *Sub-Workflow 2* - **Quickly check customized experiments**:
    - Researchers usually check after the end of the simulation and not as soon as data is available.

- **Step-6** -  *Sub-Workflow 4* - **Compare two experiments from the same ESM and same configuration (components, resolution, machine, etc.)**:
    - Usually each researcher develops his own programs from scratch. Very little is shared (many researchers consider that this step is part of the “learning” process and others have to go through it also).
    - Programs developed/used are often not shared and not re-used/reproducible.

- **Step-7** -  *Sub-Workflow 5* - **Publish Control experiment e.g. archive it in a public repository**:
    - No standard procedure e.g. ad-hoc metadata (if any; except those required to publish the related paper in a journal).
    - The goal is not to be re-used but to make data public as required by publishers.

- **Step-8** -  *Sub-Workflow 5* - **Publish/archive a “customized” experiment**:
    - Usually performed together with step 7.


## W2 - Analyzing and comparing existing simulation outputs (CMIP, sensitivity studies, scenarios/events, etc.)

### Description
This workflow is used after W1 or W6. It requires all model outputs to be on the same grid and temporal resolutions. It may also involve a post-processing stage to “CMORize” the data in conformance with particular conventions or standards.

- **Step-1** -  *Sub-Workflow 6* - **CMORization or similar**:
    - This step is not always necessary when comparing with the same ESM or if the two ESMs have computed the same “variables” (or have a subset of common variables that will be used for the analysis).
    - This may be an “ad-hoc” CMORization if the variables of interest are not those used in CMIPs.

- **Step-2** -  *Sub-Workflow 7* - **Regridding (horizontal and/or vertical)**:
    - This step may not be necessary if the comparison is done between the same ESM (different experiment) or if the two models have “similar” grids.

- **Step-3** -  *Sub-Workflow 4* - **Compare model experiments (after regridding, vertical interpolation & CMORization or similar)**.

- **Step-4** -  *Sub-Workflow 8* - **Publish results from ESM analysis.**
    - Very similar to SW5 but here we do not publish ESM model outputs but post-processed ESMs (means, anomalies, etc.) and plots/figures (with only the data used for plotting).
    - Usually very ad-hoc workflow.
    - Can be published as part of additional data in the paper publication process; rarely published to be re-used/reproduced.
    - Code used for generating plots/analysis data is not always published “properly” e.g. following FAIR principles (FAIR data and FAIR software).


## W3 - Analyzing and comparing model outputs against observations (co-design)

### Description
This workflow is used for instance before W5 or as a standalone study. In addition to selecting an area of interest and sometimes interpolating model outputs to observation locations, end users often need to derive new parameters either from the model outputs or from observations so that they can be compared. This workflow can be executed either by modellers or by “observers”.

- **Step-1** -  *Sub-Workflow 9* - **Select area or location of interest from existing ESM model outputs**
    - from a previous simulation, CMIP, etc. with possibly time-interpolation/rescaling (mean, etc.).

- **Step-2** -  *Sub-Workflow 10* - **Extract/fetch observations to prepare them for comparisons. This step may include some bias corrections.**

- **Step-3** -  *Sub-Workflow 11* - **Compare model results with observations:**
    - Usually very ad-hoc plots when done within a research context.

- **Step-4** -  *Sub-Workflow 8* - **Publish ESM vs observation analysis/visualization**
    - Only when mandatory (as part of a publication) and not following any FAIR principles (but mostly following publisher’s guidelines if any).

## W4 - ESM outputs used as input for different models or studies (downscaling, transport modelling/tracking, impacts)

### Description
This workflow requires re-formatting/regridding model outputs to specific format/grid and/or time range. It is specific to the ESM and model used for the study. Therefore, it is possible to provide a general framework but the actual workflow would need to be adapted for each use case.

- **Step-1** -  *Sub-Workflow 7* - **Regridding (time & space):**
    - May not be a separate step and performed together with Step-2.
    
- **Step-2** -  *Sub-Workflow 12* - **Reformat data to prepare it for the model to be used**
    - Sometimes the program to regrid and reformat data is provided by the model to be used (for instance WRF has a Preprocessing System called WPS)
    - If not provided, researchers develop ad-hoc programs that are usually not shared and not meant to be reused.

- **Step-3** -  *Sub-Workflow 13* - **Run a new model (regional/transport, etc.)**
    - Steps required for running this model are usually very similar to an ESM (prepare, run, post-process/visualize, publish data). 

- **Step-4** -  *Sub-Workflow 16* - **Publish model results:**
    - Usually very little information regarding the provenance of the input data is provided, only the file name (and there is no way to find out if a particular file has been modified).

## W5 - Developing an Earth System Model with source modifications, new parameterizations

### Description
This workflow is used to test source code changes (such as new parameterizations, introduction of new physical processes, bug fixes, etc.). Ideally, the source code changes are first tested locally by the end users, then the modified code undergoes automated testing when pushed to github/gitlab (or similar). Finally the scientific validity has to be verified, and there will often be several iterations until the approved changes become an integral part of a new release.

- **Step-1** -  *Sub-Workflow 14* - **Make a source code change to an ESM, compile and test it**
    - very short run, sometimes only a few time steps or days.

- **Step-2** -  *Sub-Workflow 1* - **Make a “control” experiment.**

- **Step-3** -  *Sub-Workflow 1* - **Make a “customized” experiment**
    - to test the code changes from a scientific point of view (duration may vary depending on the code changes).

- **Step-4** -  *Sub-Workflow 2* - **Quickly check control experiment.**

- **Step-5** -  *Sub-Workflow 2* - **Quickly check customized experiments.**

- **Step-6** -  *Sub-Workflow 11* - **Compare the model with observations (for instance when running a single column model).**
    - This step may be skipped by researchers who only perform model development from a “theoretical” point of view (and only evaluate how the models “behaves” against the theory, without necessarily any reference measurements).

- **Step-7** -  *Sub-Workflow 17* - **Feedback results to “observers”**
    - or field experimentalists for instance to define new/different measurement campaigns (i.e., to better specify which quantities should be measured and how).

- **Step-8** -  *Sub-Workflow 4* - **Compare two experiments (control & customized with code changes).**

- **Step-9** -  *Sub-Workflow 14* - **May start again from step-1 to improve the code changes using feedback from modellers and observers.**

- **Step-10** -  *Sub-Workflow 15* - **Publish ESM code changes:**
    - May be a very long process so the researcher may simply make a copy of the original code and add his/her changes in a separate repository.
    - The changes may never be added to the main code (depending on the type of change, on the ESM, and on the core developers’ policy in this matter).

- **Step-11** -  *Sub-Workflow 5* - **Publish Control experiment e.g. archive it in a public repository.**

- **Step-12** -  *Sub-Workflow 6* - **Publish customized experiment (with code changes) e.g. archive it in a public repository:**
    - Usually no link with code changes.

- **Step-13** -  *Sub-Workflow 8* - **Publish ESM vs. observation analysis/visualization**
    - Only if required by the publisher.



## W6 - Running an Earth system model in a model intercomparison framework (well defined protocol)

### Description
This workflow is usually developed by a modeller who has a very good overview of the protocol to be followed (for instance within CMIP6). The role of the person running the workflow is to monitor and make sure everything is running seamlessly (i.e., that the model does not crash and, should that happen, fix the problem then resubmit, that none of the files produced are “lost” during the transfer or archiving processes, etc.). Most of the time, simulations are performed in ensemble mode and a post-processing (such as CMORization) is included to prepare model outputs for ESGF publication. ESGF publication is also included after all the quality checks have passed.

- **Step-1** -  *Sub-Workflow 3* - **Prepare inputs for running a CMIP-like experiment:**
    - Follows a very well defined protocol or some inputs may already exist (scripts/codes used to generate the input files for the purpose of the experiment are not usually publicly available and the whole process is not always transparent).

- **Step-2** -  *Sub-Workflow 1* - **Prepare and run the experiments.**

- **Step-3** -  *Sub-Workflow 2* - **Quickly check experiment**
    - Usually done after running quite a lot while it could be done more regularly to spot any problems early.

- **Step-4** -  *Sub-Workflow 18* - **Scientific validation of the experiment.**
    - Usually not an in-depth analysis of the data before publication (this is why data may be retracted afterwards and updated).

- **Step-5** -  *Sub-Workflow 6* - **CMORization**
    - Very often the CMORization is not done by the person who ran the simulation, it requires a lot of manual interventions which are potentially a source of errors. Some modelling groups accumulate all the simulations outputs for a “CMORization person” to transfer and convert after the end of the runs.

- **Step-6** -  *Sub-Workflow 19* - **Publication to ESGF**
    - Follows a strict protocol; the person who is in charge of publishing data to ESGF is usually not the one who ran the simulations.



## W7 - Developing diagnostics and performance metrics tools for routine evaluation of Earth system models in CMIP

## Description
In this workflow, the end-user will modify and/or further develop existing diagnostic tools (using for instance ESMValTool or other ESM diagnostic packages). ESM outputs are already CMORized.

- **Step-1** -  *Sub-Workflow 20* - **Collect needs from scientists:**
    - For large projects such as CMIPs, diagnostic tools are usually developed by dedicated staff.
    - Often use a framework that they already know without trying to find out if the diagnostic has already been developed by others or if new “tools” exist, or how it will be maintained.

- **Step-2** -  *Sub-Workflow 21* - **Code changes/new diagnostic and test it**
    - not necessarily from a scientific point of view but to make sure that at least it does not fail. 
    - For development, it may be run/developed with a sample dataset rather than CMIP/large dataset. 
    - Version control should be used to keep track of code changes (not always the case e.g. researcher may only push/deposit changes at the very end of the process).
    - Automatic testing could be put in place to facilitate code development.

- **Step-3** -  *Sub-Workflow 22* - **Scientific validation of the newly developed diagnostic**
    - May require copying large datasets to the post-processing platform, especially if the diagnostic tool cannot open/manipulate remote files.
    - May be done by another person.

- **Step-4** -  *Sub-Workflow 23* - **Publish/release new diagnostics:**
    - May not be part of a specific publication (software publication is not very much used yet in the climate community).
    - May not be reported/merged to a larger/main base code (for instance ESMValTool).
    - May not follow best software practices (both for development and deployment).



