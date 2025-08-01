# CRISPR-Based-DNA-Storage：A Versatile Tool for ID-DNA Generation, Image Encoding, and Hybridization Simulation  
For Article "CRISPR-Cas12a-Based Querying of DNA-Stored MRI and PET Imaging Data"[Already submitted]

## Overview  
`test1` is a command-line utility designed to support three core functionalities in molecular informatics and bio-data processing: **ID-DNA sequence generation**, **image encoding via DNA embedding**, and **hybridization simulation between ID-DNA and target DNA sequences**. This tool enables researchers to create synthetic DNA sequences with tunable properties, convert image data into molecular representations, and analyze molecular interaction dynamics.  

---

## Key Features  

### 1. ID-DNA Generation  
Generate synthetic "Identifier-DNA" (ID-DNA) sequences with customizable biological properties, including length, maximum homopolymer repeat, and GC content ratio. Ideal for creating unique molecular identifiers (UMIs) or synthetic DNA tags.  

### 2. Image Encoding (EDS Method)  
Encode raster image data (e.g., DICOM medical images) into DNA sequences using an Embedding Data Structure (EDS) algorithm. This bridges digital imaging with molecular storage, enabling potential applications in bioinformatics and data archiving.  

### 3. Hybridization Simulation  
Simulate molecular hybridization between ID-DNA sequences and target DNA sequences. Analyze binding behavior, stability, and sequence complementarity to evaluate molecular recognition properties.  

---

## Usage  

### Basic Syntax  
```bash
./test1 [OPTIONS]
```  

### Function 1: Generate ID-DNA Sequences  
Create ID-DNA sequences with user-defined parameters.  

**Required Option**:  
- `-n/--number`: Number of sequences to generate (e.g., `100` for 100 sequences).  

**Optional Options**:  
- `-l/--length`: Length of each sequence (default: `20`).  
- `-o/--homo`: Maximum allowed homopolymer repeat (e.g., `3` to limit runs like `AAAA` to ≤3).  
- `-g/--gcratio`: GC content ratio (0.0–1.0; default: `0.5` for balanced GC/AT content).  

**Example**:  
```bash
./test1 -n 100 -l 20 -o 3 -g 0.5  
```  
*Generates 100 ID-DNA sequences, each 20 nucleotides long, with a maximum homopolymer run of 3 and 50% GC content.*  

---

### Function 2: Encode Image to DNA (EDS Method)  
Convert image files into DNA sequences using the EDS embedding algorithm.  

**Required Option**:  
- `-m/--imagepath`: Path to the input image (e.g., DICOM files like `mri.dcm`).  

**Example**:  
```bash
./test1 -m mri.dcm  
```  
*Encodes the DICOM image `mri.dcm` into a DNA sequence file (output format depends on implementation).*  

---

### Function 3: Hybridization Simulation  
Simulate hybridization between two DNA sequences (e.g., ID-DNA and target DNA).  

**Required Options**:  
- `-s/--seqpath`: Path to the ID-DNA sequence file (one sequence per line).  
- `-i/--indexpath`: Path to the target DNA sequence file (one sequence per line).  

**Optional Options**:  
- `-t/--type`: Sequence type (e.g., `dna` or `rna`; default: `dna`).  

**Example**:  
```bash
./test1 -s seq.txt -i index.txt -t dna  
```  
*Simulates hybridization between sequences in `seq.txt` (ID-DNA) and `index.txt` (target DNA), returning analysis results (e.g., binding affinity, mismatches).*  

---

## Options Reference  

| Short Option | Long Option         | Description                                                                 | Default       |  
|--------------|---------------------|-----------------------------------------------------------------------------|---------------|  
| `-h`         | `--help`            | Display help message and exit.                                              | -             |  
| `-s`         | `--seqpath`         | Path to ID-DNA sequence file (required for hybridization).                  | -             |  
| `-i`         | `--indexpath`       | Path to target DNA sequence file (required for hybridization).              | -             |  
| `-t`         | `--type`            | Sequence type (`dna` or `rna`; default: `dna`).                             | `dna`         |  
| `-n`         | `--number`          | Number of ID-DNA sequences to generate (required for ID-DNA generation).    | -             |  
| `-l`         | `--length`          | Length of generated ID-DNA sequences (default: `20`).                       | `20`          |  
| `-o`         | `--homo`            | Max homopolymer repeat length (default: `3`).                               | `3`           |  
| `-g`         | `--gcratio`         | GC content ratio (0.0–1.0; default: `0.5`).                                 | `0.5`         |  
| `-m`         | `--imagepath`       | Path to input image file (required for image encoding).                     | -             |  

---

## Input/Output Specifications  

- **Sequence Files** (for `-s`, `-i`): Text files with one nucleotide sequence per line (e.g., `ATCGATCG...`).  
- **Image Files** (for `-m`): Currently supports DICOM format (`.dcm`). Other formats may be added in future updates.  
- **Outputs**: Generated sequences or simulation results are saved to the current working directory (file names follow conventions like `id_dna_100x20.txt` or `hybridization_results.csv`).  

---

## Notes & Limitations  

- Ensure input files (sequences, images) exist at specified paths before execution.  
- Invalid parameters (e.g., `--gcratio 1.5`) will trigger errors; use `-h` to check valid ranges.  
- Performance depends on input size (e.g., generating 10,000 sequences of length 100 requires more memory than smaller datasets).  

---

## Citation  

This code has been submitted to a SCI-indexed journal for peer review. Future we will updates the full code without encryption.

--- 

*For questions or feedback, please contact  at [hongjingwei@qz-jk.com].*
