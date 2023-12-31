---
title: "De-novo assembly long read"
description: "De-novo assembly refers to the process of assembling genomes from scratch, without the use of a reference genome."
date: 2023-05-30
draft: true
images: ["dna.png"]
categories: ["workflows"]
tags: ["nanopore","long-read","assembly"]
keywords: ["nanopore","long-read","assembly"]
# authors: ["Mark Otto"]
---

![Bootstrap 5 3](dna.png)
<div class="alert alert-danger" role="alert">
  This is pseudo content generated by ChatGPT.
</div>

# De-novo Assembly for Long Read Nanopore Data

De-novo assembly refers to the process of assembling genomes from scratch, without the use of a reference genome. This is particularly useful for studying novel organisms or strains. Long-read sequencing technologies, such as Oxford Nanopore, provide reads that are much longer than those generated by short-read technologies, allowing for more accurate and contiguous genome assemblies.

## Prerequisites

- **Quality Long-Read Data**: Ensure that you have high-quality nanopore sequencing data.
- **Computational Resources**: Access to a computer with sufficient memory and computational power.
- **Software Installation**: Install required bioinformatics tools and software.

## Steps

### 1. Data Quality Check

- **FastQC**: Use FastQC or a similar tool to assess the quality of your sequencing data.

  ```bash
  fastqc input_reads.fastq
  ```

### 2. Read Trimming and Filtering

- **NanoFilt**: Trim adapters and filter reads based on quality and length.

  ```bash
  cat input_reads.fastq | NanoFilt -q 7 --minlength 1000 > filtered_reads.fastq
  ```

### 3. De-novo Assembly

- **Canu**: Use Canu or a similar assembler for nanopore data.

  ```bash
  canu -p assembly -d assembly_out genomeSize=your_genome_size -nanopore-raw filtered_reads.fastq
  ```

### 4. Assembly Polishing

- **Racon**: Use Racon to correct errors in the assembly using the original reads.

  ```bash
  racon -t number_of_threads input_reads.fastq assembly.sam assembly.fasta > polished_assembly.fasta
  ```

- **Medaka**: Further polish the assembly with Medaka.

  ```bash
  medaka_consensus -i input_reads.fastq -d polished_assembly.fasta -o medaka_out -t number_of_threads -m r941_min_high_g360
  ```

### 5. Assembly Evaluation

- **QUAST**: Evaluate the quality of the assembled genome.

  ```bash
  quast -o quast_out -t number_of_threads polished_assembly.fasta
  ```

- **BUSCO**: Assess the completeness of the assembly.

  ```bash
  busco -i polished_assembly.fasta -o busco_out -l lineage_dataset -m genome
  ```

### 6. Optional: Scaffolding (If Necessary)

- If you have additional data (e.g., Hi-C, optical mapping), you may use it to scaffold the assembly and improve contiguity.

### 7. Annotation (Optional)

- **Prokka**: Annotate the assembled genome (for bacterial genomes).

  ```bash
  prokka polished_assembly.fasta
  ```

---

## Notes

- Ensure that all software tools are properly installed and configured.
- Adjust `number_of_threads`, `your_genome_size`, and other parameters according to your specific needs and computational resources.
- Always refer to the official documentation of each software tool for the most accurate and up-to-date information.

## References

- [Canu: a single molecule sequence assembler](https://github.com/marbl/canu)
- [Racon: Consensus module for raw de novo DNA assembly of long uncorrected reads](https://github.com/isovic/racon)
- [Medaka: Sequence correction provided by ONT Research](https://github.com/nanoporetech/medaka)
- [QUAST: Quality Assessment Tool for Genome Assemblies](http://quast.sourceforge.net/quast)
- [BUSCO: Assessing Genome Assembly and Annotation Completeness](https://busco.ezlab.org/)
- [Prokka: Rapid prokaryotic genome annotation](https://github.com/tseemann/prokka)

---
