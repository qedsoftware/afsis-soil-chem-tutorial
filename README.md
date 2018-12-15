# AfSIS Soil Chemistry Data - Tutorial
---

# Short Description

The dataset hosted at `arn:aws:s3:::afsis` contains field and laboratory measurements of soil samples collected through the Africa Soil Information Service (AfSIS) project, which spanned from 2009 through 2018. Georeferenced soil samples were collected from many countries throughout Sub-Saharan Africa, and their nutrient content was analyzed using *both* wet chemistry (e.g. Mehlich-3) and dry chemistry (e.g., infrared spectroscopy, x-ray fluorescence). The two types of data can be paired to form a training dataset for machine learning, such that certain nutrients measured by wet chemical analyses can be well predicted from dry chemistry.


# Detailed Description

## Standards for Inclusion

To maximize the utility of this dataset for spectral inference and geospatial mapping, we are _only_ including data satisfying the following constraints:

* The soil sample corresponding to this measurement can be associated with a georeference inside Africa.
* A dry chemistry measurement is included only if there exists some wet chemistry measurement of the same soil sample.
* A wet chemistry measurement is included only if there exists some dry chemistry measurement of the same soil sample.

The chemical analyses of soils were performed by three different labs, all ISO/IEC 17025:2005 certified: the World Agroforestry Centre (ICRAF), Crop Nutrition Laboratory Services Ltd. (CROPNUTS), and Rothamsted Research (RRES). Careful documentation for all procedures used by the labs have also been included in this dataset.


## Folder Structure

We are partitioning the data into two sets: 2009-2013 (Phase I), and 2014-2018 (Phase II, pending).  The folders contained in the archive are as follows:

    .
    ├── 2009-2013
    │   ├── Dry_Chemistry
    │   │   └── ICRAF
    │   │       ├── Bruker_Alpha_KBr
    │   │       ├── Bruker_Alpha_ZnSe
    │   │       ├── Bruker_HTSXT
    │   │       ├── Bruker_MPA
    │   │       ├── Bruker_TXRF
    │   │       └── SOP
    │   ├── Georeferences
    │   │   └── georeferences.csv
    │   ├── LICENSE.txt
    │   ├── README.md
    │   └── Wet_Chemistry
    │       ├── CROPNUTS
    │       │   ├── README.md
    │       │   ├── SOP
    │       │   └── Wet_Chemistry_CROPNUTS.csv
    │       ├── ICRAF
    │       │   ├── README.md
    │       │   ├── SOP
    │       │   └── Wet_Chemistry_ICRAF.csv
    │       └── RRES
    │           ├── README.md
    │           ├── SOP
    │           └── Wet_Chemistry_RRES.csv
    └── 2014-2018 (pending)

Below is a quick overview of the contents:

* The CSV in the `Georeferences` table describes the places and times where soil samples were taken by field teams.

* The chemistry data has been partitioned into two folders: `Dry_Chemistry` and `Wet_Chemistry`. Inside each folder, we present data measured by different labs.

* Within `Dry_Chemistry`, there are multiple subfolders starting with "Bruker_", partitioned based on the make and model of the spectrometer used. Each subfolder contains dry chemistry measuremements usually stored in the OPUS binary format. These files can be unpacked either by using the Bruker OPUS Lab software, or the [brukeropusreader](https://github.com/qedsoftware/brukeropusreader) Python package. 

* Within each laboratory in `Wet_Chemistry`, all the measurements were merged into a single CSV. Physical properties such as soil moisture and particle diffraction size (ICRAF) have also been grouped under wet chemistry for the sake of organizational simplicity.

* The `SOP` folders contain the Standard Operating Procedures used by each lab, presented as PDF documents. RRES has also provided ontological codes for the methods and reagents used by their wet chemistry lab.


### Why This Folder Structure?

Lastly, a comment about folder organization. One may ask why we have taken different approaches toward the organization of the dry and wet chemistry folders, in which the former is based on makes and models of machines, while the latter merges all data into a single CSV. Some of the reasons are as follows:

* Dry chemistry measurements should not be in a spreadsheet. Each spectrogram consists of thousands of columns, and these spectograms constitute the majority of the data volume. Merging all of that data into a CSV would result in an extremely unwieldy spreadsheet, and also sacrifice numerical accuracy when converting binary floating-point representations to textual format, whereas we prefer to present the raw data as it was originally recorded. This data should be targeted for machine learning and not human inspection.

* Wet chemistry measurements also could have been separated into subfolders based on the makes and models of machines used, which differ for different nutrients and properties (e.g., Carbon and Nitrogen, Mehlich-3, pH, Electrical Conductivity, LDPSA). However, this would split the spreadsheet into five or six different spreadsheets, which the data scientist would then have to merge. From experimenting with many different approaches here, we concluded this semantic consistency is not worth the unnecessary burden imposed on the data scientist. In future releases, we may create an alternative bucket that also splits this wet chemistry data based on machine type.



## Laboratory Machines

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

### CROPNUTS

This is proprietary knowledge that will not be publicized.

### Rothamsted Research

[WIP]


# Using the Data

See this [Jupyter notebook](https://github.com/qedsoftware/afsis-soil-chem-tutorial/blob/master/afsis-soil-chem-tutorial.ipynb) for a very simple example of how to load the data and train a regressor to predict certain nutrients from dry chemistry.

The AfSIS dataset will give you a springboard to start with. In practice, you may wish to compute more sophisticated models that involve more feature engineering, include business-specific penalty functions, and also incorporate local covariates such as crop yields, weather patterns, farming practices, and dry and wet chemical measurements of soil samples localized to your region of interest.


# Historical Context

Soil is vital to life on Earth. It is our natural reservoir for storing and moving all the nutrients, liquids, and gases needed for life, including 90% of all water for food production, and 2300 Gigatons of organic carbon. And yet, while humankind has depended on soil since the beginning of civilization, we still know extremely little about it. In most parts of the world, both the public and private agricultural sectors remain extremely uninformed about the nutrient content and overall health of the soil beneath our feet.

The Africa Soil Information Service (AfSIS) was created to address this information gap in Africa and develop clever strategies for collecting the missing soil data. We focus on Africa because the future of the continent depends on Africa’s agricultural growth, and Africa’s soils are enduring widespread nutrient depletion and erosion. The data scarcity problem in Africa is also exceptional --- prior to the AfSIS project, the amount of publicly available soil chemistry data across the continent of Africa was no more than 18533 samples. (See [QED: Legacy African Soil Data, Descriptive Statistics](https://africa-legacy-soil-data.qed.ai) for more details.)

One of the main bottlenecks in scaling soil surveillance has been the high cost of wet chemical methods for soil nutrient measurements. AfSIS has pioneered the usage of lower-cost dry chemical methods that run only on the cost of electricity, and which, when calibrated against wet chemistry and coupled with machine learning, can infer the concentrations of certain nutrients quite well. The dataset here provides a start for building these inference models, and will be updated over time as more data comes in. All data is first collected by our partner labs into [AfSIS DB](https://afsisdb.qed.ai), a web-based data portal providing centralized storage and lookup of raw soil chemistry data sans transformations, and curated archives can now also be disseminated through the Registry of Open Data on AWS.

For a quick and casual introduction to the big picture, you are invited to view our [Goalkeepers 2018 video](https://www.youtube.com/watch?v=Fb9R0CnPMkc) about soil mapping.


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

In the future we plan to extend this dataset to include data from Phase II, which spanned from 2014 through 2018.


# Contact

Point of Contact: William Wu <w@qed.ai> | QED | https://qed.ai
