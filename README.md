# In Silico CRISPR-Cas9 Guide-RNA Design & Automated PCR Primer Validation for Human *SLURP1*

## 📌 Project Overview
Loss-of-function mutations in the human ***SLURP1*** (*Secreted Ly6/uPAR-Related Protein 1*) gene cause **Mal de Meleda**, an autosomal recessive palmoplantar keratoderma. Normally, SLURP1 interacts with the **α7 nicotinic acetylcholine receptor (α7-nAChR)** on epidermal keratinocytes to regulate cell proliferation and suppress **TNF-α** inflammatory signaling.

This repository provides a reproducible computational (*in silico*) bioinformatics pipeline for **CRISPR-Cas9 guide-RNA (gRNA) design**, **genome-wide off-target evaluation**, and **automated PCR primer validation** targeting the human *SLURP1* locus (*Homo sapiens*, GRCh38/hg38).

---

## 🧬 Bioinformatics Workflow

### 1. Target Selection & PAM Screening (`CHOPCHOP`)
- Screened coding exons of human *SLURP1* (`NM_020427`, GRCh38/hg38) for canonical `5'-NGG-3'` PAM sites recognized by *SpCas9*.
- Evaluated candidate 20-nucleotide gRNAs based on **GC content (40%–60%)**, **cleavage efficiency**, **self-complementarity**, and genome-wide mismatch profiles (`MM0`, `MM1`, `MM2`, `MM3`).
- Selected the top candidate gRNA (`TCGGAACTCTGAACCCAGGG` + PAM `CGG`) achieving **60% GC content**, **76.55% cleavage efficiency**, and **zero off-targets (`MM0 = 0, MM1 = 0, MM2 = 0`)**.

### 2. Automated PCR Primer Filtering (`Python` / `Pandas`)
- Parsed raw CHOPCHOP flanking primer outputs (`primers_2.tsv`) using Python in Google Colab.
- Automated filtering to retain only high-specificity forward and reverse primer pairs with **zero genomic off-targets** (`Left`, `Right`, and `Pair off-targets == 0`) and matched melting temperatures (`Tm ~60°C`) for wet-lab Sanger sequencing validation.

---

## 📂 Repository Contents
* `CRISPR_gRNA_primer_validation.ipynb` — Google Colab notebook containing the Python/Pandas script for automated off-target filtering and primer selection.
* `verified_slurp1_primers.csv` — Filtered dataset of top-ranked, off-target-free PCR primer pairs ready for experimental validation.

---

## 🛠️ Tools & Technologies
* **Genomic Databases & Tools:** NCBI Gene, CHOPCHOP (*Homo sapiens* hg38/GRCh38)
* **Programming & Data Analysis:** Python 3, Pandas, Google Colab
* **Version Control:** Git, GitHub

---

## 👩‍🔬 Author
**Tayyaba**  
MS Bioinformatics Student | Department of Biosciences, COMSATS University Islamabad  
*Research Interests: Structural Bioinformatics, CRISPR Computational Design, Molecular Docking, and Drug Repurposing*
