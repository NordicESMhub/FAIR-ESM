# Workflow Management Systems

## Introduction to workflow management system
We have selected a subset of Workflow Management Systems, based on current usage within the Earth System Modelling community, the maturity and ease of use for a wide range of users, including scientists that usually do not run Earth System Models but need to analyze and collaborate with Earth System modellers (such as field ecologists, economists, urban planners, etc.). A more comprehensive list of Workflow management Systems is available at https://github.com/common-workflow-language/common-workflow-language/wiki/Existing-Workflow-systems.

A few Workflow Management Systems have been considered and evaluated within the climate modelling community for instance within the [IS-ENES2](https://portal.enes.org/community/projects-and-initiatives/projects/is-enes2)
project. Most of these tools were initially developed by the Numerical Weather Prediction community (for instance [ecFlow](https://confluence.ecmwf.int/display/ECFLOW/ecflow+home),
[Cylc](https://cylc.github.io/)). To our knowledge [Autosubmit](https://www.bsc.es/research-and-development/software-and-apps/software-list/autosubmit) is the only Workflow Management System that was directly developed by the climate community. None of these tools considered interoperability with other existing WMS as a requirement, and cross-disciplinary research has not been taken into account. 

For NICEST2, and based on the current usage and potential use of Workflow Management Systems, we have considered:

- CWL
- Cylc
- ecFlow
- Autosubmit
- Galaxy
- Snakemake

All the selected WMSs allow describing workflows and tools that makes them portable and scalable from workstations to clusters, cloud, and high performance computing (HPC) environments. Below, you will find a short description of the Workflow Management Systems we considered and for each of them, we answered to the following questions:
- Is it currently widely used by the Climate community?
- Are there any workflows available/shared for running and analysing ESMs?
- Is it attempting to be interoperable with existing standards such as the Common Workflow Language (CWL) standard?
- Is there a Graphical User Interface (GUI) to compose workflows?
- Does it support running tasks with containers?

## Expected added value of using a workflow management system

### Automation

Less errors and easier to set up experiments (from blue sky research to CMIP experiments) as well as any ensemble experiments.

### FAIR tools and FAIR data

FAIR stands for Findable, Accessible, Interoperable and Re-usable (Reproducible).

When selecting a workflow management system, we also aim at supporting the climate community to apply FAIR principles (FAIR tools and
data) and ease their move to Open Science.

To get a better overview of what we mean by FAIR computational workflows, we strongly recommend reading the paper 
“FAIR computational workflows” written by Goble et al., 2019 (DOI: [10.1162/dint_a_00033](http://dx.doi.org/10.1162/dint_a_00033)) and 
Workflows Community Summit: Advancing the State-of-the-art of Scientific Workflows Management Systems Research and Development, Ferreira 
da Silva et al., 2021, (DOI: [10.5281/zenodo.4915801](https://doi.org/10.5281/zenodo.4915801)).

### Sharing and collaboration 

Most scientists have shown a strong interest in being able to share their data, software and workflows whenever these are considered “ready for publication”. Therefore, being able to control permissions/access is a must and scientists have requested an easy way to transition from private/shared with their collaborators only (before publication) to fully public data, software and workflows. WorkflowHub (https://workflowhub.eu/) is a registry for describing, sharing and publishing scientific computational workflows. We strongly recommend the climate community to upload their workflows in WorkflowHub to increase the FAIRness of their research work.

## Required effort for migrating/using workflow management systems

We have explored several existing Workflow Management Systems to identify possible re-use and/or existing expertise within the Nordic countries, in Europe or worldwide; both within the Earth System Modelling community but also outside (in particular with communities that already engage/collaborate with the ESM community). In each case, the objective is also to assess the possible support the Nordic Earth System Modelling Community could get for migrating/using a specific workflow management system.

In relation to NICEST2 work package 3 “FAIR climate data for NorESM and EC-Earth”, we have taken into account the capabilities and/or existing work/tools of the corresponding workflow management system to facilitate the creation of:
- FAIR computational workflows, 
- FAIR data and
- FAIR software.

## Results on the analyzed workflow management systems

Detailed information about each considered workflow management system and answers to each of the questions can be found in Annex-B. In this section, we summarize our findings.

There is not one workflow management system standing out among the others. Workflow Management Systems are relatively new to the climate community, especially to researchers at Universities. Several of the analysed workflow management systems were very similar: Cylc, ecFlow and to some extent Autosubmit. These three workflow management systems are mostly used/developed by the Numerical Weather Prediction Community and only more recently adopted by the Climate Community. While promising, the community is rather small and no consideration for cross-disciplinary research has been made. 

Most workflow management systems are considering the possibility to add metadata for FAIR computational workflows (see FAIR Computational Workflows, Goble 
et al., 2019, DOI: [10.1162/dint_a_00033](http://dx.doi.org/10.1162/dint_a_00033)) but we found that Galaxy (because it is more than just a workflow 
management system) has already implemented most of the FAIR workflow principles. In addition, there is already an ongoing collaboration with the Galaxy 
Community ([EOSC-Nordic](https://www.eosc-nordic.eu/), [INES](https://www.ines.noresm.org/)). In the next section, we give more details on why we have chosen Galaxy and also why we think this choice will not restrict the Climate Community to a single workflow management system. Indeed, the main objective is first to democratize the use of WMSs within the Climate community and in particular encourage/train researchers to decompose their work into FAIR workflows.

### Why Galaxy?

- Galaxy supports a wide range of users from novices (through its web interface) to advanced users (via command line); thanks to its GUI, it would make it possible to teach and expose undergraduate students to Earth System Modelling and more generally introduce the notions of automated workflow and reproducible research.
- Adding a new tool to Galaxy (if it is not already in the [Galaxy Toolshed](https://toolshed.g2.bx.psu.edu/)) is done by making a little Python wrapper and a description in XML where metadata
 can be easily added to improve the FAIRness of the tools. 
- All Galaxy tools already accommodate metadata, including metadata from the [EDAM ontology](http://edamontology.org/page) that can significantly improve the FAIRness of our workflows. The EDAM ontology will be extended for the climate/geosciences community as part of the EOSC-Nordic project. End-users can then use the new tool from the command line or the Galaxy web interface.
- Galaxy is already an EOSC service (listed on the EOSC market place) with free/public access to Galaxy Europe; There is also the possibility to book virtual classroom (dedicated computing & storage resources) for teaching 
([Training Infrastructure as a Service](https://galaxyproject.eu/tiaas.html));.A scientific collaboration within EOSC-Nordic and EOSC-Life has been put in place for adopting the [EOSC-Life tool roadmap](https://github.com/eosc-life/tools-collaboratory-roadmap) and following best software practices from the development until the deployment of tools (including containerization of any tools). As a result, we get support (staff) from Galaxy Europe & ELIXIR Europe for our training events & hackathons.
- The Galaxy community is large and there is significant effort to onboard new communities (not only bioinformatics for which Galaxy has been initially developed). For instance, Galaxy Europe supports more than 20 communities with their own subdomain (see https://galaxyproject.eu/about).
- Many tools of interest for the Climate community (such as machine learning tools) have been included. Interactive tools such as Jupyter notebooks are also already available.
- Among CWL, Cylc, ecFlow, autosubmit, galaxy and snakemake, Galaxy is the only workflow management system allowing end-users to compose workflows from both the command line and via a graphical user interface (see [Galaxy tutorial on creating, editing and importing galaxy workflows](https://training.galaxyproject.org/training-material/topics/galaxy-interface/tutorials/workflow-editor/tutorial.html)). This GUI makes it easier to clearly see dependencies and provides guidance while the workflow is being composed and later published (with also check lists for improving FAIRness, etc.). Galaxy is also working on supporting CWL standard: galaxy2cwl is a lightweight tool to convert Galaxy workflow files to abstract CWL.
- Galaxy is “coarse-grained” and also includes the notion of “workflows of workflows” e.g. a workflow can become a new “Galaxy tool”: for the climate community, it means that an ESM workflow (for instance written with Cylc and/or CWL) could be added as a new tool to Galaxy (and therefore be used both from the command line and via a graphical user interface).
