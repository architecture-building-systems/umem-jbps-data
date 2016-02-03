This document lists the files and their contents for this repository. It is organized by folder.

# Root folder (UMEM-JBPS-Paper)

- FILES.md (this file)
- README.md (overview of the project and structure)
- WORKFLOWS.md (FIXME:daren-thomas: create this file and describe the workflows and their outputs)
- T&F Art Preparation Instructions_Disk_v1_1.pdf (FIXME:clayton-miller: what is this? what to do with this?)
- T&F Paper Quick Style Guide.pdf (FIXME:clayton-miller: what is this? what to do with this?)
- T&F Paper Style Guide.pdf (FIXME:clayton-miller: what is this? what to do with this?)
- Taylor & Francis Online __ Journal of Building Performance Simulation - Instructions for authors.pdf (FIXME:clayton-miller: what is this? what to do with this?)
- tf_ChicagoAD.pdf (FIXME:clayton-miller: what is this? what to do with this?)
- UEMP-IFA-Figure-Guidelines.pdf (FIXME:clayton-miller: what is this? what to do with this?)

# 0_tBPSLaTeX_template

FIXME:clayton-miller: ugh! this is ugly! what is this about? Do we even need this?

# 1_Draft1_UMEM_CoSim

FIXME:clayton-miller: rename to `paper`. We don't need to do drafts because git, ok? Call it draft by marking a version on the repo!


# citysim

contains files necessary to run CitySim

- CitySim.exe (the production / parallel / fast version)
- CitySim.xml (a support file)
- CitySimd.exe (the debug / single threaded / slow version)
- libfmilib_shared.dll (a support file)
- libgcc_s_dw2-1.dll (a support file)
- libgomp-1.dll (a support file)
- pthreadGC2.dll (a support file)

# ipy-notebooks

- 20150202_HPI_CalibrationStep.ipynb (FIXME:clayton-miller document this)
- Extract heating and cooling demand from HPZ.ipynb (FIXME:clayton-miller document this)

# models

contains models and model fragments used in the workflows.

- Energy+.idd (the IDD file to use for simulations with EnergyPlus)
- Hoenggerberg.xml (the original CitySim model of the Hoenggerberg)
  - produced by student (FIXME:daren-thomas: find out name)
  - used in workflow 03-run-hoenggerberg.vt (FIXME:daren-thomas: workflow not running)
  - has some geometric problems (fixed by workflow 05-fix-geometry.vt producing Hoenggerberg_cleaned.xml)
- Hoenggerberg_cleaned.xml (fixed geometry issues with HPI building)
  - produced by workflow 05-fix-geometry.vt
  - basis for Hoenggerberg_HPI_vicinity.xml
- Hoenggerberg_HPI_OpenStudio.idf (IDF of HPI building with fixed geometry)
  - produced by collecting the resulting 04-extract-HPI.idf file from workflow 04-extract-HPI.vt
  - manually opened in OpenStudio, automatic geometry fix by OpenStudio, save to Hoenggerberg_HPI_OpenStudio.idf
  - used in workflow 05-fix-geometry.vt to produce Hoenggerberg_cleaned.xml
  - FIXME:daren-thomas: causality of workflows not clear here!!
_ Hoenggerberg_HPI_OpenStudio.osm (used to create Hoenggerberg_HPI_OpenStudio.idf)
- Hoenggerberg_HPI_vicinity.xml (CitySim model of HPI and surrounding buildings)
  - derived from Hoenggerberg_cleaned.xml
  - manually deleted all buildings not being considered
- Hoenggerberg_HPI_vicinity_OpenStudio.osm (FIXME:daren-thomas: what was this used for?)
- HPZ21_UMEM.idf (the original HPZ model as inherited from Christian Hersberger)
  - not used as not trustworthy
- template.idf (template of non-geometry IDF for co-simulation)
  - to be merged with CitySimToEnergyPlus
  - uses "SINGLE_ZONE" as zone name
  - used in workflow 06-cosim-HPI.vt
- template_HPI.idf (template of non-geometry IDF for energyplus-simulation)
  - to be merged with CitySimToEnergyPlus
  - uses zone name as defined in CitySim xml
  - based on template.idf
  - used in workflow 08-energyplus-HPI.vt
- Variables_cosim.txt (list of energyplus output variables for co-simulation)
  - to be used with VisTrails AddOutputVariableList
  - used in workflow 06-cosim-HPI.vt
- Variables_solo.txt (list of energyplus output variables for energyplus solo simulation)
  - to be used with dpw module AddOutputVariableList
  - used in workflow 08-energyplus-HPI.vt
- internal-loads-01.idf (template of non-geometry IDF for co-simulation)
  - based on template.idf
  - includes electric equipment and lighting and people


# pictures

contains pictures and screenshots

- 2016-01-05 16_28_38-Untitled - SketchUp Make.png (HPI building)
- 2016-01-07 11_01_22-HPI - before radical simplification.png (closeup of HPI building)
  - after passing through dpw module SimplifyCitySimGeometry 
- HPI-before-simplification.png (HPI building in context)
  - note how windows are not shown properly. they're there, but not visible!!
