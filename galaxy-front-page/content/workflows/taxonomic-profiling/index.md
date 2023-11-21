---
title: "Taxonomic Profiling"
description: ""
date: 2022-06-08
draft: true
images: ["profilling-1.png"]
categories: ["workflows", "metagenomics", "short-read"]
tags: ["profiling", "short-read", "metagenomics"]
keywords: ["profiling"]
# authors: ["Bjørn Erik Pedersen"]
---
![profilling](profilling-5.png)
### Workflow Summary
This workflow is designed for metagenomic  profiling, involving steps for quality control, taxonomic classification, and data retrieval:

1. **Input dataset collection**: 
   - The workflow starts with an input dataset collection, which is likely to be a set of sequencing reads.

2. **Kraken2**: 
   - A tool for taxonomic classification, which assigns taxonomic labels to short DNA sequences.

3. **Fastp**: 
   - A tool for fast all-in-one preprocessing for FastQ files, including quality control and read trimming.

4. **Bracken**: 
   - A tool for estimating the abundance of species in DNA sequences from a metagenomics sample.

5. **Get Galaxy Data**: 
   - This tool appears multiple times in the workflow and seems to be used for retrieving and passing data between different steps in the workflow.

6. **HUMAnN3_QIB**: 
   - This tool is likely used for functional annotation of metagenomic data, although the specific details are not clear from the provided information.

The workflow includes steps for data preprocessing, taxonomic classification, and abundance estimation, which are common tasks in metagenomic analysis. The repeated use of the "Get Galaxy Data" tool suggests that data from different steps are being retrieved and used in subsequent analyses, highlighting the interconnectivity of the workflow.

<a href="http://v1259.nbi.ac.uk/workflows/run?id=d9766ceb0bc1e3c9" class="btn btn-primary" role="button">Run the workflow</a>

| Step Name                 | Tool Version      | Tool ID                                                            |
|---------------------------|-------------------|--------------------------------------------------------------------|
| Input dataset collection  | N/A               | N/A                                                                |
| Kraken2                   | 2.1.1+galaxy0     | toolshed.g2.bx.psu.edu/repos/iuc/kraken2/kraken2/2.1.1+galaxy0    |
| Fastp                     | 0.23.2+galaxy0    | toolshed.g2.bx.psu.edu/repos/iuc/fastp/fastp/0.23.2+galaxy0       |
| Bracken                   | 2.2               | testtoolshed.g2.bx.psu.edu/repos/thanhlv/bracken/bracken/2.2      |
| Get Galaxy Data           | 1.0.0             | get_galaxy_data                                                    |
| Get Galaxy Data           | 1.0.0             | get_galaxy_data                                                    |
| HUMAnN3_QIB               | 3.6.0+galaxy0     | humann3_qib                                                        |
| Get Galaxy Data           | 1.0.0             | get_galaxy_data                                                    |
| Get Galaxy Data           | 1.0.0             | get_galaxy_data                                                    |
| Get Galaxy Data           | 1.0.0             | get_galaxy_data                                                    |
| Get Galaxy Data           | 1.0.0             | get_galaxy_data                                                    |
| Get Galaxy Data           | 1.0.0             | get_galaxy_data                                                    |

