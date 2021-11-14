# Identification of the needs

## Methodology
To collect user’s needs, we have asked individual researchers how they used to work with ESMs, and we also collected information from support staff. The methodology used for sampling and collecting inputs is known to be biased towards the NICEST2 partners e.g. very few researchers with no direct links to the NICEST2 consortium provided inputs. Therefore, the different “workflows” and steps we have identified may not fully cover all the current practices but were sufficiently varied in terms of computing & storage resources as well as tooling chain involved to be used as a starting point for the NICEST2 project.

For each workflow we have identified, we want to find out what is needed in terms of:
- Computing resources
- Storage resources
- Acceptable waiting time/expected responsiveness of the system
- Average level of “technical/modelling” expertise of users

We also describe the current practices e.g. answering to the following questions:
- Is it run on a “traditional” HPC managed at national level?
- Is the storage accessible from the computing resources without copying back and forth?
- Is it stored on a national storage resource?
- Is a workflow management system (automation) used in the Nordics for executing this workflow? If yes, which one?
- Is a workflow management system used elsewhere for executing this workflow? If yes, which one?
- Is there a specific data management plan and/or template for this workflow?

## Current practices & needs
In this section we summarized our findings for each identified workflow and sub-workflow. 

### On the level of expertise of end-users
When interviewing researchers and/or discussing their usage of Earth System Models, we found out that very few have a good knowledge of the Earth System Modelling ecosystem (including aspects related parallelization, discretization, optimization, etc.) and how to efficiently run an ESM on a given platform. Most reported following “recipes” provided by either a more senior scientific staff (usually a postdoc) and/or a support staff and/or online documentation.

Most researchers do not make any code changes but customize their ESM experiments by creating new forcing/inputs, changing parameters in the model, developing custom scenarios, etc. The programs used to make these changes are rarely released or published. If requested by the publisher, a github repository will be created or the code will be dumped in an archive such as zenodo.

However, some researchers make very simple code changes and what we found most surprising is that they usually do not plan to report their changes back to the main repository (this applies in particular to PhD students) even when the code is fully open (such as CESM and/or NorESM): many said that they do not understand the procedure, and/or have not directly contacted the main developers, and/or think that their changes may not be inline with the planned developments. When publishing their research, they usually find it sufficient to describe their code modifications (if that is required by the publisher).
More substantial code changes are made in collaboration with the main developers.

ESMs are used by a wide range of scientists whose main objectives are not necessarily climate modelling. Modellers have an increasing need to work with non-model specialists (for instance field ecologists, economists, social scientists) to improve ESMs and need a framework that can “simplify” the use of Earth System Models. For instance, field ecologists need to be able to set-up new ESM experiments (update forcings/inputs, model parameters, etc.) and compare them with observations.
Other examples given by researchers are studies on the impact of climate changes on the economy, on health related matters, on urbanism, on vegetation and landscape, on agriculture and more generally land use.
These researchers cannot invest as much time as (future) modellers to master the use of ESMs. Several of these researchers would welcome Graphical User Interface for submitting and analyzing their ESM experiments. We would need to take these requirements into consideration when selecting a workflow management system.

### On the use/existence of Data Management Plan templates
It is of course not really a surprise but templates for Data Management Plan (DMP) related to Climate Modelling & climate data analysis are not available. Researchers welcome the availability of DMP templates and some have already notified us of the possibility to share their current DMP as a starting point: this information is useful for NICEST2 WP3 (deliverable D3.5). Guidance on where to run and where to store inputs & model outputs or more generally results from their research based on the type of simulations and/or analysis has been requested by a small number of researchers. 
More importantly, researchers think that automatically updating their DMPs while running their ESM experiments & analysis would be very useful and they would be more interested in having detailed and accurate DMPs.

### On the use of Computing & storage resources
Researchers believe they have no choice when it comes to running ESMs: they prefer to request computing resources on platforms where the corresponding ESM has been scientifically validated. Access to model inputs is also critical (the goal is to avoid having to copy model inputs for each ESM experiment).
Most researchers run on national HPC resources and store model research outputs on national storage resources. In some Nordic countries, there is no need to transfer data from the storage resource to the HPC since there is a shared file system
Researchers who develop ESMs often use their laptop to edit, compile and check their code changes but need to quickly move to an HPC for running any experiments (other than a single column model). Many researchers would welcome the use of cloud computing for their model developments but would like to have an “environment” similar to what they have on their laptop or HPC (which is mostly a terminal where they can run ESMs from the command line).

Most researchers never use containers (docker, singularity, etc.) but would not mind trying it out. However, all the researchers we have contacted believe that the usage of containers will be limited to small use cases (or model development) and were surprised to learn that NorESM can run on HPC-cloud with singularity containers and be as efficient as on Betzy. 
Many researchers have expressed an interest in having training and/or hackathons on containers. 

### On the use of Workflow Management Systems
The main result from our analysis is related to the lack of use of Workflow Management Systems in the Nordics and worldwide. A few large teams/projects in the USA and UK have started to use cylc (https://cylc.github.io/documentation/) and/or Autosubmit but very little is said about the underlying reasons, and it has not been done in the context of Open Science & FAIR research: it is mostly derived from the use of similar workflow management systems by meteorological services, for instance for running their operational forecasts. A more detailed discussion on the pros and cons of some Workflow Management Systems will be given in the next section.

