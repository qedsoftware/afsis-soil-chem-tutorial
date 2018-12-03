AfSIS Soil Chemistry Data - Phase I
==

# Dataset Description

This archive represents the entirety of field and laboratory data collected through Phase I of the Africa Soil Information Service (AfSIS) project, which spanned from 2009 through 2013. Georeferenced soil samples were collected from many countries throughout Sub-Saharan Africa, and their nutrient content was analyzed using *both* wet chemistry and dry chemistry (infrared spectroscopy). The two types of data can be paired to form a training dataset for machine learning, such that certain wet chemistry nutrients can be well predicted from infrared spectroscopy.

The folders in this archive are as follows:

    .
    ├── Bruker_Alpha_KBr
    ├── Bruker_Alpha_ZnSe
    ├── Bruker_HTSXT
    ├── Bruker_MPA
    ├── Carbon_and_Nitrogen
    ├── Georeferences
    ├── LDPSA
    ├── LICENSE.txt
    ├── Soil_Moisture
    └── TXRF

The makes and models of laboratory machines used for taking these measurements are shown below:

| machine | model |
|:-----------|------------:|
| Alpha ZnSe | Bruker Alpha 1\_FT-MIR\_Zn Se |
| Alpha KBr | Bruker Alpha 1_FT-MIR\_KBr |
| Htsxt | Bruker Tensor27/HTs -XT_FT-IR |
| LDPSA | Horiba LA-950V |
| MPA | Bruker Multi-Purpose Analyzer \_FT-NIR |
| TXRF | Bruker Picofox S2 |
| Carbon and Nitrogen | Thermo Scientific Flash 2000 Organic Elemental Analyzer |
| Soil Moisture |  Eijelkamp Sandbox Agrisearch Equipment |


# Acknowledgments

Many institutions have been responsible for working on the collection, measurement, and organization of this data, including:

* Quantitative Engineering Design (QED)
* World Agroforestry Centre (ICRAF)
* Center for International Earth Science Information Network (CIESIN)
* The International Center for Tropical Agriculture (CIAT)
* International Soil Reference and Information Centre (ISRIC)
* Crop Nutrition Laboratory Services (CROPNUTS) 

The data is shared using the ODC-By license referenced at LICENSE.txt, and should be attributed to the Africa Soil Information Service (AfSIS).

# Tutorials

A basic tutorial of how to load and run basic computations on the AfSIS Soil Chemistry Dataset, hosted on AWS, can be found here: 

    https://github.com/qedsoftware/afsis-soil-chem-tutorial/blob/master/afsis-soil-chem-tutorial.ipynb

# Future Work

In the future we plan to extend this dataset in the following ways:

- Include alternative wet chemistry analyses of samples from Phase I, conducted at Rothamsted Research.
- Include data from Phase II, which spanned from 2014 through 2018.


# Contact

Point of Contact: William Wu <w@qed.ai> | QED | https://qed.ai
