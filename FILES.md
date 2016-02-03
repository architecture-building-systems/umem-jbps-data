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
  - used in workflow 05-fix-geometry.vt to produce 
