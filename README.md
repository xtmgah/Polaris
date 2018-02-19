# Polaris

<p align="center">
<a href="../../wiki/Sample-Information">
<img src="https://img.shields.io/badge/Total%20samples%20sequenced-220-6d73f3.svg" height="30">
</a>
</p>

<p align="center">
<a href="../../wiki/Sample-Information#hiseqx-data-polaris-1">
<img src="https://img.shields.io/badge/HiSeqX%20data-Polaris%201-ed9d2d.svg" alt="HiSeqX data">
</a>
</p>

<p align="center">
<a href="release-notes/vc1_0.md#get-the-data">
<img src="https://img.shields.io/badge/Latest%20variant%20calls-VC1.0-8a6183.svg" alt="HiSeqX data">
</a>
</p>

<!-- [More information!][1.1] -->

[TOC]: #

# Table of Contents
- [Summary](#summary)
- [Latest variant call release  VC1.0](#latest-variant-call-release--vc10)
    - [Download the VCF](#download-the-vcf)
        - [AWS CLI](#aws-cli)
        - [wget](#wget)
- [Sequencing resources](#sequencing-resources)
    - [HiSeqX PCR-Free Data (Polaris 1)](#hiseqx-pcr-free-data-polaris-1)
    - [Associated resources](#associated-resources)
        - [Platinum Genomes](#platinum-genomes)
        - [HiSeqX PCR-Free](#hiseqx-pcr-free)
    - [Coming soon](#coming-soon)
        - [HiSeqX PCR-Free](#hiseqx-pcr-free)
        - [10X](#10x)
        - [NovaSeq S4 PCR-Free](#novaseq-s4-pcr-free)
- [Issues](#issues)
- [References](#references)


## Summary

The Polaris project provides
* Population sequencing resources on high throughput Illumina sequencing
  platforms
* Variant calls validated using population genetic and Mendelian methods

The variant calls currently provided in Polaris are breakpoint-resolved deletion
and insertion structural variants (SVs).

Further details of the sequencing resources, input data sources, genotyping
methods and validation methods can be found in the [project wiki][1.1].

## Latest variant call release &mdash; VC1.0

Our latest variant call release set is [VC1.0][2.1]. This call set contains
**70,706** from a candidate set of **184,988** validated breakpoint-resolved SV calls.

Candidates were identified from 4 sources:
* [Previously characterized Manta calls][2.2.1]
* [Platinum Genomes pedigree consistent events with unique population breakpoints][2.2.2]
* [Parliament insertions][2.2.3]<sup>[2](#English2015)</sup>
* [Icelandic insertions identified with PopIns][2.2.4]<sup>[3](#Kehr2017)</sup>

All candidates were jointly re-called using our
[breakpoint joint caller suite, `paragraph`][2.3].

Validation consisted of:

* [Polaris 1 Diversity Panel][3.1.1.1] / [Polaris 1 PGx Panel][3.1.2.1] HWE
  assessment
* [Platinum Genomes pedigree][2.4.1]<sup>[1](#Eberle2017)</sup> pedigree
  consistency check

PASS calls were either
* Pedigree consistent
* Homozygous in pedigree and MAF > 0.05 + HWE p-value > 0.05 in Polaris panels

Complete release notes for VC1.0 can be found [here][2.1].

### Download the VCF

The VC1.0 VCF is available can be downloaded either using `AWS CLI` or `wget`
and can also be viewed in this [S3 bucket display][2.5.1].  Using `wget` is
currently the easier of the two command line options.

#### `AWS CLI`

Polaris datasets are stored in an AWS S3 bucket called `illumina-polaris`, and
can de downloaded using the [AWS CLI][2.5.2]:

```bash
$: aws cp s3://illumina-polaris/vc1_0.vcf.gz
$: aws cp s3://illumina-polaris/vc1_0.vcf.gz.tbi
```

#### `wget`

If you don't have AWS credentials, you can use `wget` or a similar tool to
download VC1.0:

```bash
$: wget https://s3.amazonaws.com/illumina-polaris/vc1_0.vcf.gz
$: wget https://s3.amazonaws.com/illumina-polaris/vc1_0.vcf.gz.tbi
```

## Sequencing resources

Population panels with unrestricted access sequenced as part of Polaris are
available through [BaseSpace][3.1] or the
[European Nucleotide Archive (ENA)][3.2].

Additional panels are available through the [EGA][3.3] or [dbGaP][3.4] with
restricted access subject to approval through a Data Access Committee. **No
variant calls are ever reported in Polaris for restricted access panels.**

Further information the sequencing resources described below can be found in the
[project wiki][0.3].

### HiSeqX PCR-Free Data (Polaris 1)

All HiSeqX PCR-Free data was generated by Illumina Laboratory Services (ILS)
with a target whole genome coverage of 30X.

There are currently two unrestricted access panels available in Polaris, with a
third pending.

1. **[Diversity panel][3.1.1.1]** ([BaseSpace][3.1.1.2], [ENA][3.1.1.3]) &mdash;
   150 samples selected to represent a diversity of populations
2. **[PGx panel][3.1.2.1]** (BaseSpace (pending), [ENA][3.1.2.3]) &mdash; 70
   samples with orthogonally validated genotypes for 28 genes relevant for
   PGx<sup>[4](#Pratt2016)</sup>
3. *[Trio panel][3.1.3.1] (pending)* &mdash; 51 children whose parents were
   sequenced as part of the diversity panel

There is also a restricted access [repeat expansion panel][3.1.4.1] available
through [EGA][3.1.4.2].

### Associated resources

#### [Platinum Genomes][3.5]

##### HiSeq2000 PCR-free

* **Parents & grandparents**
  * [ENA][3.2.1]
  * [BaseSpace][3.2.2]
* **Children**
  * [dbGaP][3.2.3]

#### HiSeqX PCR-Free

* **Parents & grandparents**
  * *ENA* &mdash; pending
  * *BaseSpace* &mdash; pending
* **Children**
  * *dbGaP* &mdash; pending

### Coming soon

#### HiSeqX PCR-Free

* Platinum Genomes pedigree
* NIST Ashkenazi Jewish trio

#### 10X

* Platinum Genomes Pedigree

#### NovaSeq S4 PCR-Free

* Platinum Genomes pedigree
* NIST Ashkenazi Jewish trio

## Issues

Please [open an issue][4.1] to provide feedback or ask questions.

## References

1. <a name="Eberle2017"></a>Eberle, et al (2017) A reference data set of 5.4
   million phased human variants validated by genetic inheritance from
   sequencing a three-generation 17-member pedigree. *Genome Res.* 27:157-164.
   [doi:10.1101/gr.210500.116][5.2]
2. <a name="English2015"></a>English, et al (2015) Assessing structural
   variation in a personal genome-towards a human reference diploid genome. *BMC
   Genomics.* 16:286 [doi:10.1186/s12864-015-1479-3][5.4]
3. <a name="Kehr2017"></a>Kehr, et al (2017) Diversity in non-repetitive human
   sequences not found in the reference genome. *Nat Genet.* 49(4):588-593.
   [doi: 10.1038/ng.3801][5.3]
4. <a name="Pratt2016"></a> Pratt, et al (2016) Characterization of 137 Genomic
   DNA Reference Materials for 28 Pharmacogenetic Genes: A GeT-RM Collaborative
   Project. *J Mol Diagn.* 18(1):109-23. [doi:10.1016/j.jmoldx.2015.08.005][5.1]


[0.1]: ../../wiki/Sample-Information#hiseqx-data-polaris-1
[1.1]: ../../wiki/
[2.1]: release-notes/vc1_0.md
[2.2.1]: ../..//wiki/Input-Data-Sources#pop-manta
[2.2.2]: ../..//wiki/Input-Data-Sources#pg-pop
[2.2.3]: ../../wiki/Input-Data-Sources#parliament-insertions
[2.2.4]: ../..//wiki/Input-Data-Sources#popins-icelandic-insertions
[2.3]: ../../wiki/Joint-Genotyping-Methods#breakpoint-resolved-structural-variant-calls
[2.4.1]: https://github.com/Illumina/PlatinumGenomes
[2.5.1]: https://illumina.github.io/Polaris/
[2.5.2]: https://aws.amazon.com/cli/
[3.1]: https://basespace.illumina.com/home/index
[3.2]: https://www.ebi.ac.uk/ena
[3.3]: https://ega-archive.org/
[3.4]: https://www.ncbi.nlm.nih.gov/gap
[3.1.1.1]: ../../wiki/HiSeqX-Diversity-Panel
[3.1.1.2]: https://euc1.sh.basespace.illumina.com/projects/2265263
[3.1.1.3]: https://www.ebi.ac.uk/ena/data/view/PRJEB20654
[3.1.2.1]: ../../wiki/HiSeqX-PGx-Panel
[3.1.2.3]: https://www.ebi.ac.uk/ena/data/view/PRJEB19931
[3.1.3.1]: ../../wiki/HiSeqX-Trio-Panel
[3.1.4.1]: ../../wiki/HiSeqX-Repeat-Expansion-Panel
[3.1.4.2]: https://ega-archive.org/datasets/EGAD00001003562
[3.2.1]: https://www.ebi.ac.uk/ena/data/view/PRJEB3381
[3.2.2]: https://basespace.illumina.com/s/2K7LqNG7Mt1h
[3.2.3]: https://www.ncbi.nlm.nih.gov/projects/gap/cgi-bin/study.cgi?study_id=phs001224.v1.p1
[3.5]: ../../wiki/Sample-Information#platinum-genomes
[4.1]: issues
[5.1]: https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4695224/
[5.2]: http://genome.cshlp.org/content/27/1/157
[5.3]: https://www.nature.com/ng/journal/v49/n4/full/ng.3801.html
[5.4]: https://bmcgenomics.biomedcentral.com/articles/10.1186/s12864-015-1479-3
