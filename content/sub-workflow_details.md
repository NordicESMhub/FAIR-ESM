# Description of sub-workflows
For this deliverable, we do not detail each sub-workflow but provide information on the computing & storage resources and where it is usually run, by who (novice, competent practitioner, etc.) and whether a workflow management system is used, etc.

## SW1- Prepare and run an ESM experiment:

- **Run on**: HPC (national)
- **Store data on**: disk directly on the HPC
- **Level of expertise required:** advanced. So often experiments are prepared by skilled staff and handed over to researchers (prone to errors and may have to wait for technical staff to support scientists).
- **Required responsiveness/expected waiting time**: need a very responsive system for creating the experiment (set-up, compilation, etc.) but not for running the ESM experiment (researchers can wait quite a long time for their experiment to start and to finish).
- **Data transfer**: from HPC to National Research Data storage resources (NIRD project area, Swestore, Allas).
- **Workflow Management System**: Not used in the Nordics. Cylc is sometimes used by some international teams but not well established; the goal is not to be FAIR.
- **Data Management Plan (template)**: No. Everyone writes their own and may not follow best practices.

## SW2- Quickly check experiment:
- **Run on**: Sometimes on HPC (same as for running ESM) to avoid transfer of data. Most of the time on post-processing nodes/cloud computing resources.
- **Store data on**: disk often in temporary folders as the data and/or plots produced are not meant to be kept or published.
- **Level of expertise required**:  intermediate (may require some programming experience; at least to open/plot data).
- **Required responsiveness/expected waiting time**: yes. Usually interactive work (no queuing system and X Window System expected)
- **Data transfer**: No
- **Workflow Management System**:  No
- **Data Management Plan (template)**:  No. data/plots are not kept.

## SW3- Prepare input data for running with an ESM:
- **Run on**:  usually on the same HPC where the ESM is to be run. However, it could be run anywhere if input data, etc. are available. Preferably run on a system with no queuing time; where researchers can make use of interactive tools (such as Jupyter notebooks). Need to visualize and may require several iterations/versions before researchers are “satisfied” so cloud computing is more appropriate than HPC or HPC-cloud.
- **Store data on**:  HPC
- **Level of expertise required**: Intermediate (programming expertise is required and many researchers struggle because of a lack of knowledge).
- **Required responsiveness/expected waiting time**:  yes. Usually interactive work (no queuing system and X Window System expected); at least for developing the algorithm/program.
- **Data transfer**:  A copy may be kept on more “permanent” storage such as NIRD project area, Swestore or Allas.  
- **Workflow Management System**:  No
- **Data Management Plan (template)**:  No. This step is usually not taken into account when submitting a DMP. No versioning of the data and no persistent identifier. No “link” between a custom experiment and its corresponding input data. Customized input data may be publicly available (even when associated with a scientific paper).

## SW4- Compare two experiments from the same ESM and same configuration (components, resolution, machine, etc.):
- **Run on**:  post-processing platform such as NIRD toolkit. Could be run on any cloud computing platform (no need for HPC or HPC cloud). May require GPUs for visualization and processing (could significantly speed-up analysis & visualization).
- **Store data on**:  disk on semi-permanent storage such as NIRD project area, Swestore or Allas. 
- **Level of expertise required**: Intermediate to advanced. Very often customized programs are used and the quality of the resulting analysis and visualizations greatly vary from one researcher to another. There are no standard procedures and ad-hoc programs are rarely published and shared. No best software practices followed.
- **Required responsiveness/expected waiting time**:  for large experiments, users are expected to submit a batch job to process all their data. However, researchers have asked to be able to use a more responsive system/platform; possibly with GPUs to speed-up analysis; but at least with lots of memory. Interactive usage with Jupyter notebooks (and dask for parallelism) is often requested by researchers.
- **Data transfer**:  No. Everything is done on the same post-processing platform where data is usually accessible without copying it.
- **Workflow Management System**:  No. Very ad-hoc and interactive step.
- **Data Management Plan (template)**: No. Data produced as part of the analysis are stored as is, with very few or no metadata (except those kept in netCDF files; metadata may be wrong; not checked). Programs used for creating this data and plots are usually not shared and when published there is no “link” between the data and the software used to generate it. No persistent identifiers are generated during this process.

## SW5 - Publish an ESM experiment e.g. archive it in a public repository:
- **Run on**:  any platform where data to be published is accessible (cloud computing, post-processing platform, etc.). No need to use HPC or HPC-cloud.
- **Store data on**:  public archive/repository. When available researchers use their national data archive service. Otherwise Pangea, zenodo (if not too big) and any other public repositories. 
- **Level of expertise required**: novice
- **Required responsiveness/expected waiting time**: researchers are expected to be able to quickly submit an “archive” request but do not mind to wait quite a lot of time before that is completed. They have asked to be able to make this request through a command line API and not having to switch from a GUI for instance to add additional metadata (NIRD archive).
- **Data transfer**:  Yes. From storage to Archive.
- **Workflow Management System**:  No.
- **Data Management Plan (template)**: Sometimes but not really. What is missing is clear information on metadata required for making the published data FAIR. This metadata should be collected during the experiment (and not created at the end) to make sure published experiments can be found and reused.

## SW6 - CMORization or similar e.g. compute new variables, change units, interpolate on pressure levels, etc.:
- **Run on**:  post-processing platform where data is accessible. It could be run anywhere e.g. from any cloud services provided data is accessible.
- **Store data on**:  usually same storage resources as non-CMORized data.
- **Level of expertise required**: advanced. Only a few people really know how to CMORize ESM data.
- **Required responsiveness/expected waiting time**: intermediate. Habitually uses a batch queuing system. Mostly I/Os. Researchers do not expect to get results very quickly; especially when processing large experiments. However, sometimes, when a deadline approaches, this has to be done in an emergency.
- **Data transfer**:  No. 
- **Workflow Management System:  No. Even though there is often some kind of procedure in place because the person who runs the CMORization is not the person who ran the simulation.
- **Data Management Plan (template)**: No. And at the end both raw and CMORized data are kept on disks. 

## SW7 - Regridding (time & space):
- **Run on**:  Very often on HPC because post-processing resources are too limited (not enough memory and/or CPUs). This SW could be run on any cloud computing resources (no need for HPC or HPC-cloud). It can be very time consuming and cumbersome task.
- **Store data on**:  if run on cloud or any processing platforms, data may need to be transferred if the next step is run on HPC.
- **Level of expertise required**: advanced. Most researchers do not regrid data and know very little about regridding.
- **Required responsiveness/expected waiting time**: for testing and setting up the system must be very responsive (no waiting time; interactive work). For regridding large amounts of data (production), researchers usually submit jobs or wait for quite a while before getting all their data regridded.
- **Data transfer**:  Most of the time, it is not necessary.
- **Workflow Management System**:  No
- **Data Management Plan (template)**: No.

## SW8 - Publish results from ESM analysis e.g. post-processed model outputs such as means, anomalies, etc. and plots/figures (with data used for plotting):
- **Run on**:  post-processing platform with direct access to data. Could be run on any cloud resources provided the data is accessible. 
- **Store data on**:  disk storage such as NIRD project area, SWestore or Allas.
- **Level of expertise required**: novice. Anyone should be capable of publishing data they have produced. In practice, whatever is published is usually lacking metadata information that would make it FAIR. 
- **Required responsiveness/expected waiting time**: Researchers do not want to wait to publish their results; at least to initiate the process of publication. They particularly like zenodo where the publication process is fast and efficient.
- **Data transfer**:  From data storage to archive/public repository.
- **Workflow Management System**:  No. Very ad-hoc procedure.
- **Data Management Plan (template)**: Partially. Often forgotten when writing DMPs (or very vague). There is no “standard” procedure so publication can differ from one researcher to another (and even from one experiment to another).

## SW9 - Select area or location of interest from existing ESM model outputs with possibly time-interpolation/rescaling (mean, etc.) for future comparisons with for instance observations:
- **Run on**:  post-processing platform. Any cloud computing resource with access to data would be suitable.
- **Store data on**:  disk; usually on private project area. Intermediate data is often not kept.
- **Level of expertise required**: novice. 
- **Required responsiveness/expected waiting time**: usually run as an interactive task (jupyter notebook). Low tolerance to waiting time even with large amounts of data to be processed. It is therefore important to store data to speed-up time series access.
- **Data transfer**:  No. Sometimes data is streamed. Usually stored locally and/or in memory.
- **Workflow Management System**:  No. At best a jupyter notebook or a script.
- **Data Management Plan (template)**: Never part of a DMP. Mostly intermediate data.

## SW10 - Retrieve observations, select area/location (for instance when using satellite or global/regional gridded observation) and apply some bias-corrections:
- **Run on**:  post-processing platform or any cloud resources. 
- **Store data on**:  locally and/or in-memory for further processing.
- **Level of expertise required**: novice (need basic programming experience). However a higher level of expertise may be required depending on the observations (some are stored in complex data format).
- **Required responsiveness/expected waiting time**: high. No batch queue system expected.
- **Data transfer**:  From data provider (where observations are stored) to local storage.
- **Workflow Management System**:  No. Scripts are often shared as examples on how to retrieve the corresponding type of observations.
- **Data Management Plan (template)**: Data providers are usually mentioned in the DMP; however data size is often difficult to estimate and not reported once downloaded.

## SW11 - Compare model results with observations e.g. plot time series:
- **Run on**:  post-processing platform or any cloud computing with access to the data.
- **Store data on**:  could be anywhere if accessible (such as minio or s3-compatible storage).
- **Level of expertise required**: intermediate. Programming experience usually required; researchers often struggle to adopt a good strategy (to avoid loading too much data in memory, etc.)
- **Required responsiveness/expected waiting time**: usually interactive workflow so do not expect queuing time, except when run routinely as part of large experiments.
- **Data transfer**:  data could be streamed. Usually run on a platform with direct access to storage. Results stay on the same platform.
- **Workflow Management System**:  No. sometimes a script or jupyter notebook. Often not shared.
- **Data Management Plan (template)**: No. Plots and derived products are usually not mentioned in the DMP.

## SW12 - Reformat data to prepare it for the model to be used. WRF Preprocessing System is an example:
- **Run on**:  HPC where the model will run. Could be run on HPC-cloud.
- **Store data on**:  HPC
- **Level of expertise required**: novice to intermediate, depending on the model (for instance WRF is quite simple because it already has a WRF Preprocessing System which is well documented; other models can be seen as more difficult). 
- **Required responsiveness/expected waiting time**: usually run as an interactive task even with a large number of input files to process.
- **Data transfer**:  ESM data that will be prepared to be used as inputs need to be transferred from an archive or at least storage project area (NIRD project area, Swestore or Allas) if data is not accessible from HPC.
- **Workflow Management System**:  No. Even though steps are very well defined, users need to execute them manually.
- **Data Management Plan (template)**: Usually mentioned in the DMP. However, the resulting data (used as input to the model) are considered as intermediate data and not always kept.

## SW13 - Run a model (regional/transport, etc.) that uses ESM outputs as inputs:
- **Run on**:  HPC even though HPC-cloud or cloud computing could be used.
- **Store data on**:  locally on the HPC or cloud storage.
- **Level of expertise required**: novice to advanced depending on the model to be run.
- **Required responsiveness/expected waiting time**: same as for running an ESM e.g. users usually expect to submit a batch job and can wait.
- **Data transfer**:  No except if model inputs are not available on the compute platform yet.
- **Workflow Management System**:  No but some models use very complex scripts and sometimes cylc.
- **Data Management Plan (template)**: Data generated is usually mentioned in the DMP.

## SW14 - Make a source code change to an ESM, compile and test it (short run):
- **Run on**:  HPC while it could be run on any cloud computing resources or HPC-cloud. Performance is not necessary but may require a sufficient number of CPUs for testing. This is an area where containers would bring considerable benefits (having the same compilers and software environment should ensure consistent model behavior).
- **Store data on**:  locally. Data is not expected to be kept for long.
- **Level of expertise required**: advanced. Only a few researchers make code changes to an ESM. Do not always follow best software practices (especially at PhDs level so their code changes may be “lost”).
- **Required responsiveness/expected waiting time**: high. Users do not expect to wait but usually have to when on HPC (queues). Would greatly benefit from using cloud computing (or HPC-cloud).
- **Data transfer**:  sometimes for input data. Outputs are usually analysed locally and then removed.
- **Workflow Management System**:  No. Very manual process.
- **Data Management Plan (template)**: Not mentioned. Data is not kept.

## SW15 - Publish ESM code changes:
- **Run on**:  HPC if tests on HPC. Could be done anywhere (from the computing resources used for testing).
- **Store data on**:  locally and on a repository such as github or gitlab
- **Level of expertise required**: intermediate (requires knowledge of a version control system and best software practices).
- **Required responsiveness/expected waiting time**: high. Do not expect to wait.
- **Data transfer**:  local to remote repository (github/gitlab).
- **Workflow Management System**:  No. Very manual work.
- **Data Management Plan (template)**: Software changes are not often mentioned in the DMP.

## SW16 - Publish results from regional/downscaling simulations:
For instance model outputs from WRF or any other regional model, transport model such as FLEXPART, etc. Information on the ESM data used as inputs is not always well reported:
- **Run on**:  HPC or any platforms used to run the model simulations.
- **Store data on**:  public repository/archive such as pangea, NIRD archive.
- **Level of expertise required**: novice.
- **Required responsiveness/expected waiting time**: do not want to wait to initiate transfer/publication.
- **Data transfer**:  from local storage to archive.
- **Workflow Management System**:  No. Always very manual while this task could be automated with creation of all the necessary metadata.
- **Data Management Plan (template)**: usually mentioned in the DMP but data size is not mentioned (not known when writing the DMP and never updated).

## SW17 - Feedback results to “observers” (or field experimentalists) for instance to define new/different measurement campaigns. 
Usually as a report with plots and possibly data that can be easily manipulated by non-modeller specialists:
- **Run on**:  laptop and/or shared document such as google or hackMD.
- **Store data on**:  not very secure and long-term.
- **Level of expertise required**: novice. 
- **Required responsiveness/expected waiting time**: high. Researchers expect to access this resource immediately.
- **Data transfer**:  sometimes info is sent by email.
- **Workflow Management System**:  No.
- **Data Management Plan (template)**: Never documented and not taken into account in the DMP. Often information is not published and may be lost.

## SW18 - Scientific validation of an ESM experiment
- **Run on**:  HPC. Could be run on any cloud computing resources with access to ESM experiment results.
- **Store data on**:  locally and then transfer to storage such as NIRD project area, Swestore or Allas.
- **Level of expertise required**: intermediate. Very often used existing packages that create lots of plots and the study is completed with customized analysis/plots.
- **Required responsiveness/expected waiting time**: many researchers are used to submit batch jobs for this task. It can take quite a while when the experiment to analyse is long.
- **Data transfer**:  Not always. Sometimes data is still available on HPC. Often need to transfer data from storage (NIRD project area, Swestore or Allas) to HPC if data is not directly accessible.
- **Workflow Management System**:  No but scripts/tools are usually available (at least for the standard validation). Customized scripts, programs are not always shared.
- **Data Management Plan (template)**: Often mentioned because plots are published “online”.

## SW19 - Publish ESM outputs to ESGF (after CMORization)

- **Run on**:  usually on post-processing platform or on HPC (depending on where the data is).
- **Store data on**:  ESGF node (usually on a national storage resource in the Nordics)
- **Level of expertise required**: high. Only a few people know how to publish to ESGF. It requires special “permissions” so not everyone can publish to ESGF.
- **Required responsiveness/expected waiting time**: researchers do not expect this step to be interactive. They can wait for quite a long time before having their data published and it is not a problem.
- **Data transfer**:  from storage to ESGF node if necessary.
- **Workflow Management System**:  No but scripts are usually available (but not necessarily shared).
- **Data Management Plan (template)**: Yes. Usually very clear and detailed information as researchers follow a well established protocol.

## SW20 - Collect needs from scientists for developing new diagnostics. 

Reports, questionnaire, plots showing mock-up diagnostics, etc.:
- **Run on**:  google forms or any university/institutional questionnaire “system”
- **Store data on**:  varies but usually on institution premises.
- **Level of expertise required**: novice.
- **Required responsiveness/expected waiting time**: high. Do not expect to wait to collect results and analyze results.
- **Data transfer**:  often not.
- **Workflow Management System**:  No. If a program is developed to analyse the results, it is usually not shared and often not kept in a repository (github/gitlab).
- **Data Management Plan (template)**: Rarely mentioned in the climate science community (not really considered as “data”).

## SW21 - Develop/update diagnostics and test it (not from a scientific point of view but to make sure that at least it does not fail)

- **Run on**:  laptop, post-processing platform. Could be run on any cloud computing resources (no need for HPC or HPC-cloud).
- **Store data on**:  locally (data is not meant to be kept and code changes are expected to be versioned with a proper version control system such as git).
- **Level of expertise required**: advanced. Only very few scientists develop new diagnostics.
- **Required responsiveness/expected waiting time**: high. Do not expect to wait; very interactive.
- **Data transfer**:  Should not be necessary except for testing e.g. test data sets are usually required.
- **Workflow Management System**:  No.
- **Data Management Plan (template)**:  This development phase is never mentioned in the DMP.

## SW22 - Scientific validation of an ESM diagnostic

- **Run on**:  HPC or post-processing platform (e.g. where data is available).
- **Store data on**:  locally. Data is not necessarily kept once the validation is finished.
- **Level of expertise required**: intermediate. Mostly require scientific expertise. Data/plots may be generated and made available to the scientists who will make the validation.
- **Required responsiveness/expected waiting time**: medium. With a large dataset, it can take some time to run (sometimes a batch system is used). Generation of plots/data products could easily be automated.
- **Data transfer**:  usually the code is transferred/copied where data is available. 
- **Workflow Management System**:  No. Some scripts may be available.
- **Data Management Plan (template)**: partially mentioned (if data is meant to be kept). Storage necessary to run the diagnostics (intermediate files) is not assessed (or even known).

## SW23 - Publish/release new diagnostics (tool)

- **Run on**:  laptop or cloud computing resource.
- **Store data on**:  on a repository such as github/gitlab.
- **Level of expertise required**: intermediate (requires knowledge of version control system).
- **Required responsiveness/expected waiting time**: high. Do not expect to wait at least for pushing changes (but may have to wait for their PR to be merged).
- **Data transfer**:  from local storage to remote & public repository.
- **Workflow Management System**:  No but not really necessary.
- **Data Management Plan (template)**: Never mentioned. 

