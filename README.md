# Datasets for DAISY

> Datasets for the setting of **D**istributed, **A**nomaly-Based **I**ntrusion 
> Detection in **S**ecurit**y**-Oriented Edge Computing Environments

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://github.com/daisy-field/datasets/blob/main/LICENSE.txt)

This repository contains several datasets for use with the DAISY framework, but also 
any other approaches that follow a distributed approach for intrusion detection, both 
anomaly- and misuse-based classification.

This is merely the overview of all the available datasets, for a more detailed 
description, see the respective directory and README.

## [5G Jamming Detection Dataset (5G_JDD)](5G_JDD/README.md)

This dataset includes the 5G communication monitoring indicators recorded throughout the 
project. The data was collected by our project partner HMF, and then processed and merged for further analysis.

## [CIC IDS2017](CIC_IDS2017/README.md)

This dataset is a transformation of the CIC-IDS2017 dataset 
(https://www.unb.ca/cic/datasets/ids-2017.html). It was split using the 
notebooks in the same directory into multiple CSV files.

## [V2X 2023-03-06](v2x_2023-03-06/README.md)

This dataset was generated as a proof of concept for a master's thesis. It features
two V2X communication devices and is a capture of real network traffic. The two
hosts use the identifiers 2 and 5, as they are part of a bigger network with 
several additional machines.

## [DSFIDS24](DSFIDS24/README.md)

This dataset is a live capture of eight extended road-side units (eRSU). The dataset and
attacks were collected on real infrastructure. It features captures of eight 
multi-access edge computing (MEC) units in a distributed network. It was captured on
the 22nd of July 2024, starting on the 21st at 20:00 CEST and ending on the 22nd at
20:00 CEST. The dataset is split into the eight hosts. Each host contains CSV files with
100.000 packets per file.

## Licensing

The datasets in this repository, except of the CIC IDS2017, are licensed under the 
Creative commons Attribution International Version 4.0 [(CC BY 4.0)](https://github.com/daisy-field/datasets/blob/main/LICENSE.txt)