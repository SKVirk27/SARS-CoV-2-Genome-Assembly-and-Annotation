# SARS-CoV-2-Genome-Assembly-and-Annotation

## Methodology Overview
Our genomic exploration of SARS-CoV-2, leveraging next-generation sequencing, commenced with a rigorous FASTQC quality assessment, safeguarding data fidelity. The SPAdes toolkit orchestrated precise genome assembly, augmented by Bandage for intuitive genomic visualization. Alignments, crafted with Bowtie2 precision, paved the way for variant discovery via Samtools and BCFtools. SnpEff was paramount in annotating these variants, offering functional insights, and predicting phenotypic consequences, thereby enriching the tapestry of our viral genetic understanding. This methodological amalgamation fortified the foundation of our genomic discoveries.

## Dataset Analysis
Employing Illumina MiniSeq's paired-end sequencing, we explored into datasets SRR11528306 and SRR11528307, each a genomic compendium of over 177M and 186.5M bases. The datasets, reflective of the viral genome with an average read length of 131 bp and a GC content nearing 38%, were pivotal for elucidating viral replication and mutation dynamics within Vero E6 cells. Published on April 15, 2020, their analysis has been indispensable in tracing the evolutionary trajectory of the virus, a cornerstone for public health intervention strategies.

## Initial Data Processing and Quality Control
The fidelity of our sequencing data underwent stringent scrutiny with FASTQC, Andrews (2010) describes FastQC as a quality control tool for high throughput sequence data. Establishing a quality baseline critical for trustworthy assembly.

## Genome Assembly
Employing SPAdes, According to Prjibelski et al. (n.d.), the SPAdes tool is used for genome assembly. We navigated the complexities of metagenomic assembly, stitching high-quality reads into contiguous genomic sequences.

## Comparative Analysis
Prior to alignment, a comparative genomic analysis was conducted using MUMmer, aligning our assembled contigs with reference genomes. This crucial step allowed us to discern structural variations and highlight genomic rearrangements that may play pivotal roles in the virus's evolution and pathogenicity.

## Visualization and Annotation
Post-assembly, the Bandage tool provided a visual assessment of the genomic structure, (Wick et al., 2015) pinpointing regions for targeted analysis. Subsequent automated annotation of genes within the contigs was carried out by PROKKA (Seemann, 2014), generating a detailed genomic annotation necessary for understanding viral function. Buels et al. (2016) provide JBrowse as a web platform for genome analysis. We visualized our gene annotation and location in JW Browser to get better understanding.

## Alignment and Variant Calling
Post-comparative analysis, the accurate alignment of our sequences to a reference genome was executed with Bowtie2 (Langmead, 2010). This foundational step paved the way for the critical phase of variant detection and calling through Samtools and BCFtools, uncovering mutations that hold the key to the virus's evolutionary dynamics (Li, Handsaker, Danecek, & the samtools team, n.d.). For in-depth functional annotation and impact assessment of the identified variants, SnpEff was utilized, Cingolani et al. (2012) discuss how SnpEff annotates and predicts the effects of single nucleotide polymorphisms. Providing a comprehensive annotation that encompasses both predicted phenotypic impacts and potential changes to protein function.

## Database Construction for SnpEff Annotation
To facilitate detailed annotation of SARS-CoV-2 variants, we constructed a specialized SnpEff database. This was achieved by downloading the nucleotide, protein sequences, CDS FASTA files, and corresponding GFF3 annotation files from the NCBI database, using the RefSeq accession number NC_045512. The integration of these files into SnpEff allowed for an enriched analysis, linking genomic variations to potential functional changes in the viral genome — a crucial step for interpreting the impact of mutations observed during our study.

Each step in this methodology is designed to build upon the previous, ensuring a robust and comprehensive analysis of the SARS-CoV-2 genome. This structured approach underlines the reliability of our results and the potential impact of our findings on the broader scientific community's understanding of this novel coronavirus.
