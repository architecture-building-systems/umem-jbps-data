This document lists the files and their contents for this repository. It is organized by folder.

# Root folder (UMEM-JBPS-Paper)

- `FILES.md` (this file)
- `README.md` (overview of the project and structure)
- `WORKFLOWS.md` (FIXME:daren-thomas: create this file and describe the workflows and their outputs)
- `T&F Art Preparation Instructions_Disk_v1_1.pdf` (FIXME:clayton-miller: what is this? what to do with this?)
- `T&F Paper Quick Style Guide.pdf` (FIXME:clayton-miller: what is this? what to do with this?)
- `T&F Paper Style Guide.pdf` (FIXME:clayton-miller: what is this? what to do with this?)
- `Taylor & Francis Online __ Journal of Building Performance Simulation - Instructions for authors.pdf` (FIXME:clayton-miller: what is this? what to do with this?)
- `tf_ChicagoAD.pdf` (FIXME:clayton-miller: what is this? what to do with this?)
- `UEMP-IFA-Figure-Guidelines.pdf` (FIXME:clayton-miller: what is this? what to do with this?)

# 0_tBPSLaTeX_template

FIXME:clayton-miller: ugh! this is ugly! what is this about? Do we even need this?

# 1_Draft1_UMEM_CoSim

FIXME:clayton-miller: rename to `paper`. We don't need to do drafts because git, ok? Call it draft by marking a version on the repo!


# citysim

contains files necessary to run CitySim

- `CitySim.exe` (the production / parallel / fast version)
- `CitySim.xml` (a support file)
- `CitySimd.exe` (the debug / single threaded / slow version)
- `libfmilib_shared.dll` (a support file)
- `libgcc_s_dw2-1.dll` (a support file)
- `libgomp-1.dll` (a support file)
- `pthreadGC2.dll` (a support file)

# ipy-notebooks

- `20150202_HPI_CalibrationStep.ipynb` (FIXME:clayton-miller document this)
- `Extract heating and cooling demand from HPZ.ipynb` (FIXME:clayton-miller document this)

# models

contains models and model fragments used in the workflows.

- `Energy+.idd` (the IDD file to use for simulations with EnergyPlus)
- `Hoenggerberg.xml` (the original CitySim model of the Hoenggerberg)
  - produced by student (FIXME:daren-thomas: find out name)
  - used in workflow `03-run-hoenggerberg.vt` (FIXME:daren-thomas: workflow not running)
  - has some geometric problems (fixed by workflow `05-fix-geometry.vt` producing `Hoenggerberg_cleaned.xml`)
- `Hoenggerberg_cleaned.xml` (fixed geometry issues with HPI building)
  - produced by workflow `05-fix-geometry.vt`
  - basis for `Hoenggerberg_HPI_vicinity.xml`
- `Hoenggerberg_HPI_OpenStudio.idf` (IDF of HPI building with fixed geometry)
  - produced by collecting the resulting `04-extract-HPI.idf` file from workflow `04-extract-HPI.vt`
  - manually opened in OpenStudio, automatic geometry fix by OpenStudio, save to `Hoenggerberg_HPI_OpenStudio.idf`
  - used in workflow `05-fix-geometry.vt` to produce `Hoenggerberg_cleaned.xml`
_ `Hoenggerberg_HPI_OpenStudio.osm` (used to create `Hoenggerberg_HPI_OpenStudio.idf`)
- `Hoenggerberg_HPI_vicinity.xml` (CitySim model of HPI and surrounding buildings)
  - derived from `Hoenggerberg_cleaned.xml`
  - manually deleted all buildings not being considered
- `Hoenggerberg_HPI_vicinity_OpenStudio.osm` (FIXME:daren-thomas: what was this used for?)
- `HPZ21_UMEM.idf` (the original HPZ model as inherited from Christian Hersberger)
  - not used as not trustworthy
- `template.idf` (template of non-geometry IDF for co-simulation)
  - to be merged with CitySimToEnergyPlus
  - uses "SINGLE_ZONE" as zone name
  - used in workflow `06-cosim-HPI.vt`
- `template_HPI.idf` (template of non-geometry IDF for energyplus-simulation)
  - to be merged with CitySimToEnergyPlus
  - uses zone name as defined in CitySim xml
  - based on `template.idf`
  - used in `workflow 08-energyplus-HPI.vt`
- `Variables_cosim.txt` (list of energyplus output variables for co-simulation)
  - to be used with VisTrails AddOutputVariableList
  - used in workflow `06-cosim-HPI.vt`
- `Variables_solo.txt` (list of energyplus output variables for energyplus solo simulation)
  - to be used with dpw module AddOutputVariableList
  - used in workflow `08-energyplus-HPI.vt`
- `internal-loads-01.idf` (template of non-geometry IDF for co-simulation)
  - based on `template.idf`
  - includes electric equipment and lighting and people
- `internal-loads-02.idf` (template of non-geometry IDF for co-simulation)
  - based on `internal-loads-01.idf`
  - electric equipment and lighting * 5


# pictures

contains pictures and screenshots. We should collect more pictures and screenshots as we will need those for publications / conferences etc.

- `2016-01-05 16_28_38-Untitled - SketchUp Make.png` (HPI building)
- `2016-01-07 11_01_22-HPI - before radical simplification.png` (closeup of HPI building)
  - after passing through dpw module SimplifyCitySimGeometry 
- `HPI-before-simplification.png` (HPI building in context)
  - note how windows are not shown properly. they're there, but not visible!!

# raw-data

contains raw data used for the DAYFILTER process to create the measured data sets.

FIXME:clayton-miller: describe the files in this folder
FIXME:clayton-miller: move screenshots / images to the `pictures` folder

# results

contains a folder for each workflow that produces results. The results are
those collected by the dpw SaveCoSimResults, SaveCitySimResults and
SaveEnergyPlusResults modules. Each folder is named after the workflow that produced it. 

- `04-extract-HPI`
- `06-cosim-HPI`
- `07-citysim-HPI`
- `08-energyplus-HPI`
- `09-cosim-HPI`

# weatherfiles

contains the weatherfiles used for the simulations.

- `Zurich-Kloten_2013.cli` (CitySim weather file, extracted from `Zurich-Kloten_2013.epw`)
- `Zurich-Kloten_2013.epw` (EnergyPlus weather file)
- `Zurich-Kloten_2013_SW.out` (short wave radiation file automatically produced by CitySim)

# workflows

- `01-run-hpz.vt` (run legacy HPZ model from Christian Hersberger)
  - obsolete / non-functional
  - input
    - `models/HPZ21_UMEM.idf`
    - `weatherfiles/Zurich-Kloten_2013.epw`
  - output (results/01-run-hpz)
- `02-bim-energyplus.vt` (run EnergyPlus on a Revit BIM model - DPV-style)
  - obsolete / non-functional
  - input
    - Revit BIM model (from application)
    - `weatherfiles/Zurich-Kloten_2013.epw`
  - output (results/02-bim-energyplus)
- `03-run-hoenggerberg.vt` (run original Hoenggerberg model with CitySim)
  - obsolete / non-functional
  - could be quickly fixed to run by using dpw RelativePath
  - input
    - `Hoenggerberg.xml` (could be moved to `Hoenggerberg_cleaned.xml`)
    - `Zurich-Kloten_2013.cli`
  - output (results/03-run-hoenggerberg)
- `04-extract-HPI.vt` (run the HPI building with EnergyPlus)
  - obsolete / non-functional
  - input
    - `models/Hoenggerberg.xml` (yes, the original Hoenggerberg model)
    - `models/template.idf`
    - `weatherfiles/Zurich-Kloten_2013.epw`
  - output (results/04-extract-HPI)
- `05-fix-geometry.vt` (updates HPI geometry with OpenStudio fixes to produce `models/Hoengerberg_cleaned.xml`)
  - `Hoenggerberg_HPI_OpenStudio.idf` created manually, see `models/Hoenggerberg_HPI_OpenStudio.idf` description above
  - dwp module MapEnergyPlusGeometryToCitySim matches floors, walls, roofs and
    shading surfaces in IDF with CitySim model based on naming convention of dpw module CitySimToEnergyPlus
  - input
    - `models/Hoenggerberg.xml`
    - `models/Hoenggerberg_HPI_OpenStudio.idf`
  - output (`models/Hoenggerberg_cleaned.xml`)
- `06-cosim-HPI.vt` (co-simulate HPI building with CitySim and EnergyPlus)
  - simplification of CitySim geometry (merging of surfaces)
  - simplification of EnergyPlus geometry (merging of surfaces)
  - input
    - `models/Hoenggerberg_HPI_vicinity.xml`
    - `models/template.idf`
    - `weatherfiles/Zurich-Kloten_2013.cli`
    - `models/Variables_cosim.txt`
  - output (results/06-cosim-HPI)
- `07-citysim-HPI.vt` (simulate CitySim vicinity of HPI)
  - input
    - `models/Hoenggerberg_HPI_vicinity.xml`
    - `weatherfiles/Zurich-Kloten_2013.cli`
  - output (results/07-citysim-HPI)
- `08-energyplus-HPI.vt` (run EnergyPlus for HPI building)
  - no simplification of shading / geometry
  - input
    - `models/Hoenggerberg_HPI_vicinity.xml`
    - `models/template.idf`
    - `weatherfiles/Zurich-Kloten_2013.epw`
    - `models/Variables_solo.txt`
  - output (results/08-energyplus-HPI)
- `09-cosim-HPI.vt` (like `06-cosim-HPI.vt`, but replaced `models/template.idf` with `models/internal-loads-01.idf`)
  - no simplification of shading / geometry (FIXME:daren-thomas: check that this doesn't make a difference to the results of `06-cosim-HPI.vt`)
  - input
    - `models/Hoenggerberg_HPI_vicinity.xml`
    - `models/internal-loads-01.idf`
    - `weatherfiles/Zurich-Kloten_2013.cli`
    - `models/Variables_cosim.txt`
  - output (09-cosim-HPI)
- `10-cosim-HPI.vt` (like `09-cosim-HPI.vt`, but uses `models/internal-loads-02.idf` instead
  - input see 09-cosim-HPI
  - output (10-cosim-HPI)
- `12-energyplus-HPI.vt` (like `10-cosim-HPI.vt`, but just EnergyPlus, writes out `models/12-HPI.idf`)
- `13-energyplus-HPI.vt` (simple EnergyPlus run with a modified version of `models/12-HPI.idf`)
  - input
    - `models/13-HPI.idf` - removed all shading from `models/12-HPI.idf`
- `14-energyplus-HPI.vt` (simple EnergyPlus run with a modified version of `models/13-HPI.idf`)
  - input
    - `models/14-HPI.idf` - messing with constructions based on `models/13-HPI.idf`
- `15-energyplus-HPI.vt` - messing with setpoints...
- `16-energyplus-HPI.vt` - more messing with setpoints...
- `17-energyplus-HPI.vt` - constructions as in 13, everything else like 16...
- `18-energyplus-HPI.vt` - more messing with setpoints (based on 16)...
- `19-cosim-HPI.vt` - based on 11-cosim-HPI.vt, with constructions from 18 and setpoints from 18
- 20-cosim-HPI.vt - based on 19, but with new schedules (SCHEDULE:FILE)
  - input: internal-loads-03.idf
  - input: schedules-01.idf and HPI_Schedules.csv
  - output: cooling is calibrated! now to calibrate heating!
- 21-cosim-HPI.vt - based on 20, but with new schedules
  - input: schedules-21.idf
  - input: HPI_Schedules-21.idf
- 22-cosim-HPI.vt - based on 21, but use HPI_Schedules for occupancy and internal loads
