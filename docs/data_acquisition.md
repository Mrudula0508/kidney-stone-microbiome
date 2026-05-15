# Data Acquisition  
### Urinary Microbiome & Kidney Stone Formation Project


## 1. Literature Search Strategy

A structured literature search was conducted using PubMed to understand the current scientific landscape of microbiome–kidney stone associations.

- **Search terms:**  
  - “microbiome AND kidney stone”  
  - “kidney stone AND microbiome”

- **Filters applied:**  
  - Publication date: after 2020

- **Total results identified:** 171 studies

### Key Findings
- Kidney stones affect approximately 1 in 11 adults in the United States (NHANES 2024).
- Gut microbiota such as *Oxalobacter formigenes* play a role in oxalate metabolism and may reduce stone risk.
- Reduced abundance of oxalate-degrading bacteria is associated with increased kidney stone formation risk.
- Additional taxa such as *Lactobacillus* and *Bifidobacterium* may contribute to metabolic regulation relevant to stone formation.

Similar microbiome–disease association frameworks have been observed in conditions such as Crohn’s disease and neurological disorders.

---

## 2. Dataset Selection

The publicly available dataset **NCBI BioProject PRJNA856314**, titled  
*"Multi-site microbiota alteration is a hallmark of kidney stone formation"*, was selected for analysis.

### Dataset Overview
- 16S rRNA gene sequencing data (Illumina platform)
- Includes kidney stone formers and healthy controls
- Multiple body sites (urine, gut, oral, stone samples)
- Only urinary microbiome samples were used in this study

### Selection Rationale
- Publicly accessible and well-documented
- Contains both case and control groups
- Generated using Illumina MiSeq 16S rRNA sequencing, compatible with QIIME2 workflows
- Includes metadata suitable for demographic and confounder analysis

---

## 3. SRA Run Selector Filtering Strategy

The NCBI SRA Run Selector was used to filter samples for consistency and quality control.

### Filtering Criteria
- AvgSpotLen: 440–489
- Bases: 0–50M
- Bytes: 0–50 MB
- Ethnicity: White
- Host disease: kidney calculi / healthy
- Host sex: male and female
- Library layout: PAIRED
- Sequencing platform: Illumina MiSeq
- Environment: renal system

### Rationale
These filters were applied to ensure:
- Uniform read length across samples
- Consistent sequencing depth
- Reduced technical variability
- Inclusion of both sexes for biological representativeness
- Minimization of confounding due to environmental and sequencing differences

---

## 4. Metadata Download and Structure

Filtered metadata was downloaded from the NCBI SRA database, resulting in **134 samples**.

### Metadata Columns Included
- Run (SRR ID)
- Assay Type
- AvgSpotLen
- Bases
- Bytes
- env_local_scale
- ethnicity
- host_disease
- kidney_disord
- host_sex
- organism

Each SRR ID corresponds to a unique sequencing sample.

---

## 5. Data Acquisition Workflow Summary

The data acquisition pipeline followed these steps:

1. Literature review and study selection  
2. Identification of BioProject PRJNA856314  
3. Application of SRA Run Selector filters  
4. Download of metadata from NCBI SRA  
5. Initial metadata inspection and structuring  
6. Export of SRR list for downstream processing (FASTQ retrieval)

---

## 6. Reproducibility and Data Availability

- All datasets are publicly available through the NCBI SRA database  
- No human subject recruitment was performed in this study  
- No personally identifiable information (PII) or protected health information (PHI) is included  
- All preprocessing and analysis steps (including SRA Toolkit, fastp, and QIIME2 workflows) are documented in separate files within this repository  

---
