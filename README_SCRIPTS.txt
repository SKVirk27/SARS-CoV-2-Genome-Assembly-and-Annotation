
# README for SARS-CoV-2 Genomic Analysis

This README outlines the sequence of scripts used for the genomic analysis of SARS-CoV-2 as described in the methodology.

## Initial Data Processing and Quality Control
- FastQC quality assessment:
```
fastq-dump --split-files SRRXXXXXXXX
fastqc [fastq files]
```

## Downloading Reference Genome
- Download reference genome for SARS-CoV-2:
```
wget https://ftp.ncbi.nlm.nih.gov/genomes/all/GCF/009/858/895/GCF_009858895.2_ASM985889v3/GCF_009858895.2_ASM985889v3_genomic.fna.gz
gunzip GCF_009858895.2_ASM985889v3_genomic.fna.gz
```

## Genome Assembly with SPAdes
- Assembly of the genomic sequences:
```
spades.py -o SPADES_OUT --isolate -1 [forward_reads.fq] -2 [reverse_reads.fq]
```

## Alignment with Bowtie2
- Build index and align reads to the reference genome:
```
bowtie2-build GCF_009858895.2_ASM985889v3_genomic.fna sars_cov_2_ref
bowtie2 -x sars_cov_2_ref -1 SRR11528307_1.fastq -2 SRR11528307_2.fastq -S aligned.sam
```

## Post-Alignment Processing with Samtools
- Convert SAM to BAM, sort and index alignments:
```
samtools view -bS aligned.sam > aligned.bam
samtools sort aligned.bam -o sorted_aligned.bam
samtools index sorted_aligned.bam
```

## Comparative Genomic Analysis with MUMmer
- Align contigs to reference genome and find variants:
```
nucmer --prefix=CoV_alignment GCF_009858895.2_ASM985889v3_genomic.fna SPADES_OUT/contigs.fasta
show-coords -rcl CoV_alignment.delta > alignment.txt
```

## Variant Calling with BCFtools
- Call variants with BCFtools:
```
bcftools mpileup -Ou -f GCF_009858895.2_ASM985889v3_genomic.fna sorted_aligned.bam | bcftools call -mv -Ob -o variants.bcf
bcftools view -i 'FILTER="PASS"' variants.bcf > variants.vcf
```

## Functional Annotation with SnpEff
- Annotate and predict the effects of variants:
```
snpEff build -gff3 -v SARS-CoV-2
snpEff ann SARS-CoV-2 variants.vcf > annotated_variants.vcf
```

Each script corresponds to a step in the methodology and should be run in the sequence provided to replicate the analysis.
