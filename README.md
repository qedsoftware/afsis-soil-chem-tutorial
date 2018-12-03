# AfSIS Soil Chemistry Data - Phase I
---

# Dataset Description

This dataset contains field and laboratory data collected through the Africa Soil Information Service (AfSIS) project, which lasted from 2009 through 2018. In this initial release, we are including data collected during Phase I, which spanned from 2009 through 2013. Georeferenced soil samples were collected from many countries throughout Sub-Saharan Africa, and their nutrient content was analyzed using *both* wet chemistry (e.g. Mehlich-3) and dry chemistry (e.g., infrared spectroscopy, x-ray fluorescence). The two types of data can be paired to form a training dataset for machine learning, such that certain wet chemistry nutrients can be well predicted from infrared spectroscopy.


## Folder Structure

The folders contained in this archive are as follows:

    .
    ├── LICENSE.txt
    ├── Georeferences
    ├── Dry_Chemistry
    │   └── ICRAF
    │        ├── Bruker_Alpha_KBr
    │        ├── Bruker_Alpha_ZnSe
    │        ├── Bruker_HTSXT
    │        ├── Bruker_MPA
    │        ├── Bruker_TXRF
    │        └── SOP
    └── Wet_Chemistry
        ├── ICRAF
        │    ├── Carbon_and_Nitrogen
        │    ├── LDPSA
        │    ├── Soil_Moisture
        │    └── SOP
        ├── CROPNUTS
        │    ├── Carbon_and_Nitrogen
        │    ├── LDPSA
        │    ├── Soil_Moisture
        │    ├── Mehlich_3
        │    └── SOP
        └── Rothamsted_Research     
             ├── Carbon_and_Nitrogen
             ├── LDPSA
             ├── Soil_Moisture
             ├── Mehlich_3
             └── SOP
        
A quick overview of the contents:

* The CSV in the `Georeferences` table describes the places and times where soil samples were taken by field teams. In this dataset, we only include samples for which there exist *both* wet and dry chemistry measurements.

* The chemistry is partitioned into two subfolders: dry chemistry (e.g., infrared spectroscopy, x-ray fluorescence), and wet chemistry. There are then nested subfolders for each lab that performed measurements of the data. 

* Folders starting with "Bruker_" contain dry chemistry measuremements usually stored in the OPUS binary format, which can be unpacked either by using the Bruker OPUS Lab software, or the [brukeropusreader](https://github.com/qedsoftware/brukeropusreader) Python package. 

* Other folders, such as `Carbon_and_Nitrogen`, `LDPSA`, `Soil_Moisture`, and `Wet_Chemistry`, contain CSV files.

* The SOP folders contain documents describing the protocols that each lab followed to conduct their chemistry measurements. For exmaple, the SOPs used by ICRAF were sourced from here: [ICRAF Soil Plant Spectral Diagnostics Lab SOPs](http://www.worldagroforestry.org/sd/landhealth/soil-plant-spectral-diagnostics-laboratory/sops)



## Laboratory Protocols

The makes and models of laboratory machines used for taking these measurements are shown below:

### ICRAF

| machine | model |
|:-----------|:------------|
| Alpha ZnSe | Bruker Alpha 1\_FT-MIR\_Zn Se |
| Alpha KBr | Bruker Alpha 1_FT-MIR\_KBr |
| Htsxt | Bruker Tensor27/HTs -XT_FT-IR |
| LDPSA | Horiba LA-950V |
| MPA | Bruker Multi-Purpose Analyzer \_FT-NIR |
| TXRF | Bruker Picofox S2 |
| Carbon and Nitrogen | Thermo Scientific Flash 2000 Organic Elemental Analyzer |
| Soil Moisture |  Eijelkamp Sandbox Agrisearch Equipment |

### Rothamsted Research

[WIP]

### CROPNUTS

[WIP]



# Acknowledgments

AfSIS has been an enormous undertaking made possible through the joint efforts of many people. This people have included not only analytical chemists and soil scientists working in laboratories, but also intrepid field crews that traversed deserts and scaled mountains under the hot sun to extract soils out of the ground in some of the world’s most remote places. The institutions that have been responsible for the collection, measurement, and organization of this data include:

* [World Agroforestry Centre (ICRAF)](https://www.worldagroforestry.org/)
* [Quantitative Engineering Design (QED)](https://qed.ai)
* [Center for International Earth Science Information Network (CIESIN)](http://ciesin.org)
* [The International Center for Tropical Agriculture (CIAT)](https://ciat.cgiar.org/)
* [Crop Nutrition Laboratory Services (CROPNUTS)](https://cropnuts.com/)

All data is shared using the ODC-By license referenced at LICENSE.txt, and should be attributed to the Africa Soil Information Service (AfSIS).

We thank all our partners for their tireless contributions to the AfSIS project.



# Future Work

In the future we plan to extend this dataset in the following ways:

- Include alternative wet chemistry analyses of Phase I samples, conducted at Rothamsted Research.
- Include data from Phase II, which spanned from 2014 through 2018.


# Contact
 
Point of Contact: William Wu <w@qed.ai> | QED | https://qed.ai
