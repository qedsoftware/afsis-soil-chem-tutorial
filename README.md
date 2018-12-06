# AfSIS Soil Chemistry Data - Phase I
---

# Short Description

This dataset contains field and laboratory data collected through the Africa Soil Information Service (AfSIS) project, which lasted from 2009 through 2018. In this initial release, we are including data collected during Phase I, which spanned from 2009 through 2013. Georeferenced soil samples were collected from many countries throughout Sub-Saharan Africa, and their nutrient content was analyzed using *both* wet chemistry (e.g. Mehlich-3) and dry chemistry (e.g., infrared spectroscopy, x-ray fluorescence). The two types of data can be paired to form a training dataset for machine learning, such that certain nutrients measured by wet chemical analyses can be well predicted from dry chemistry.


# Detailed Description

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
        │    ├── pH_Hp_EC
        │    ├── Soil_Moisture
        │    ├── Mehlich_3
        │    └── SOP
        └── RRES
             ├── Carbon_and_Nitrogen
             ├── pH
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


## Historical Context

Soil is vital to life on Earth. It is our natural reservoir for storing and moving all the nutrients, liquids, and gases needed for life, including 90% of all water for food production, and 2300 Gigatons of organic carbon. And yet, while humankind has depended on soil since the beginning of civilization, we still know extremely little about it. In most parts of the world, both the public and private agricultural sectors remain extremely uninformed about the nutrient content and overall health of the soil beneath our feet.

The Africa Soil Information Service (AfSIS) was created to address this information gap in Africa and develop clever strategies for collecting the missing soil data. We focus on Africa because the future of the continent depends on Africa’s agricultural growth, and Africa’s soils are enduring widespread nutrient depletion and erosion. The data scarcity problem in Africa is also exceptional --- prior to the AfSIS project, the amount of publicly available soil chemistry data across the continent of Africa is no more than 18533 samples. (See [QED: Legacy African Soil Data, Descriptive Statistics](https://africa-legacy-soil-data.qed.ai) for more details.)

One of the main bottlenecks in scaling soil surveillance has been the high cost of wet chemical methods for soil nutrient measurements. AfSIS has pioneered the usage of lower-cost dry chemical methods that run only on the cost of electricity, and which, when calibrated against wet chemistry and coupled with machine learning, can infer the concentrations of certain nutrients quite well. The dataset here provides a start for building these inference models, and will be updated over time as more data comes in. All data is first collected by our partner labs into [AfSIS DB](https://afsisdb.qed.ai), a web-based data portal providing centralized storage and lookup of raw soil chemistry data sans transformations, and curated archives can now also be disseminated through the Registry of Open Data on AWS.

For more information about the big picture, you are invited to view our [Goalkeepers 2018 video](https://www.youtube.com/watch?v=Fb9R0CnPMkc) about soil mapping.


# Acknowledgments

AfSIS has been an enormous undertaking made possible through the joint efforts of many people. This people have included not only analytical chemists and soil scientists working in laboratories, but also intrepid field crews that traversed deserts and scaled mountains under the hot sun to extract soils out of the ground in some of the world’s most remote places. The institutions that have been responsible for the collection, measurement, and organization of this data include:

* [World Agroforestry Centre (ICRAF)](https://www.worldagroforestry.org/)
* [Quantitative Engineering Design (QED)](https://qed.ai)
* [Center for International Earth Science Information Network (CIESIN)](http://ciesin.org)
* [The International Center for Tropical Agriculture (CIAT)](https://ciat.cgiar.org/)
* [Crop Nutrition Laboratory Services (CROPNUTS)](https://cropnuts.com/)
* [Rothamsted Research (RRES)](https://www.rothamsted.ac.uk/)

All data is shared using the ODC-By license referenced at LICENSE.txt, and should be attributed to the Africa Soil Information Service (AfSIS).

We thank all our partners for their tireless contributions to the AfSIS project.


# Future Work

In the future we plan to extend this dataset in the following ways:

- Include alternative wet chemistry analyses of Phase I samples, conducted at Rothamsted Research.
- Include data from Phase II, which spanned from 2014 through 2018.


# Contact

Point of Contact: William Wu <w@qed.ai> | QED | https://qed.ai
