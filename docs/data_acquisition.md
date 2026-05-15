Data Acquisition & Preprocessing Steps

Dataset Source
This study uses publicly available 16S rRNA sequencing data from NCBI BioProject PRJNA856314 titled “Multi-site microbiota alteration is a hallmark of kidney stone formation.”
Link: https://www.ncbi.nlm.nih.gov/bioproject/PRJNA856314
This dataset includes microbiome samples from multiple body sites; however, only urinary microbiome samples were selected for this analysis.

Rationale for Dataset Selection
Publicly accessible high-quality 16S rRNA sequencing data
Contains both kidney stone (case) and healthy (control) groups
Suitable for microbiome diversity and community composition analysis
Enables case-control comparative study design

2. Sample Selection Strategy
Initial dataset:
276 total samples available in the BioProject.
134 samples downloaded using SRA Toolkit
Only urinary microbiome samples retained
Final dataset construction:
	30 healthy samples available (limited cohort size)
	30 kidney stone formers selected to maintain balance

Balanced sampling strategy:
To avoid bias due to unequal group sizes, a balanced case-control design was used:
	30 Healthy controls
	30 Stone formers
Total final dataset = 60 samples

Sex-Stratified Sampling (Stone Former Group)
To preserve original dataset structure:
	Male : Female ratio ≈ 3 : 2
Final stone former subset:
	18 males
	12 females
Selection was performed using randomized sampling (Excel RAND() function), ensuring proportional representation.

3.Raw Data Processing Workflow
1. Data Download
SRR accessions retrieved from metadata file
Data downloaded using SRA Toolkit:
	prefetch → downloads sequencing runs
	fasterq-dump → converts to FASTQ format
2. Sequence Output
Each sample produced paired-end reads:
	Forward reads (R1)
	Reverse reads (R2)
For 1 sample → 2 FASTQ files
For total 60 samples → 120 FASTQ files


3. Quality Control (Preprocessing)

Low-quality reads were removed using fastp:
	Trimming low-quality bases at read ends
	Removing sequencing artifacts

Output:	120 cleaned (trimmed) FASTQ files

4. File Mapping for QIIME2
A custom script generated a manifest.tsv file linking:
	Sample IDs
	Trimmed FASTQ file paths
This ensured compatibility with QIIME 2 import format.

5. QIIME2 Import
Manifest file + 120 trimmed FASTQ files imported into QIIME2
Total dataset size: ~680 MB paired-end reads
