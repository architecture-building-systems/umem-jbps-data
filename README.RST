Journal Paper
=============

Here are some notes on writing the journal paper for the UMEM project.

The goal is to show a full stack co-simulation of the Hönggerberg site using the UMEM technologies.


Notes:
======

  - less focus on Revit->DPV->EnergyPlus/CitySim aspect

  - we need a running Hönggerberg model in CitySim
   
  - we need a running HPZ model in EnergyPlus

  - we need to convince the weather guys to do us a microclimate simulation

Outline:
========


Methods
=======

  - manual creation of Hönggerberg 3D data

    - ask Emanuel how he did this

  - matching of measured data with simulation data to figure out systems used

    - ref systems identification papers

    - similar to Florastrasse!

  - co-simulation using FMI

    - fmilib

  - RPS to connect to BIM - but wait: we're not using the BIM!

  - VisTrails to tie in everything? (should this be part of the paper?)

  - Testing of the multi-zone interface
    
    - improvement on the single-zone interface mentioned in the conference paper

    - extraction of test-model

    - running of test-model

    - comparisson to single-zone model?

