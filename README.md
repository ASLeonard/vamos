# Vamos: VNTR Annotation tool using efficient MOtifs Sets
## Getting Started

Install vamos (g++, htslib, abpoa, edlib, alglib and seqan required)
htslib and abpoa are installed by bioconda
libalglib.a and libedlib.a are distributed along with vamos)

### Download source code
```sh
git clone https://github.com/ChaissonLab/vamos.git
conda create --name vamos
conda activate vamos
```

### Install requirement libraries
```
conda install -c bioconda --file requirements.txt
```
### Compile vamos
```
cd vamos/src && make
```
### Help page
```
vamos -h
```
### Run Vamos
#### Lift-over the VNTR sequences from alignment file
```
vamos --conseq      [-i in.bam] [-v vntrs.bed] [-o output.fa] (ONLY FOR SINGLE LOCUS and SINGLE THREAD!!) 
```
#### Annotate the consensus sequence from reads with motifs
```
vamos --conseq_anno [-i in.fa]  [-v vntrs.bed] [-m motifs.csv] [-o output.vcf] [-s sample_name] (ONLY FOR SINGLE LOCUS and SINGLE THREAD!!)
```
#### Lift-over the VNTR sequences from alignment file + Annotate every VNTR sequence + Aggregate the annotations per VNTR locus
```
vamos --raw_anno    [-i in.bam] [-v vntrs.bed] [-m motifs.csv] [-o output.vcf] [-s sample_name] [-t threads] (SUPPORT MULTIPLE LOCI and MULTI-THREAD!!)
```

## Output VCF files
Vamos generates a separate VCF record for each VNTR with information about VNTR's location and genotype. The records for alternate VNTR alleles are demarcated by <VNTR> symbolically.

The header of the VCF file contains a detailed description of each record.

### Example

The following VCF entry describes the state of a VNTR locus in a sample with
name `sample`

```
#CHROM	POS	ID	REF	ALT	QUAL	FILTER	INFO	FORMAT	sample
seq0;chr1:906874-907014;chr3:91637349,91642348,91642349,91647348	5001	.	N	<VNTR>	.	PASS	END=9009;RU=TCGCTTCCCCTTTAAGCACACTCATTCACCACACCCGAGGAGGCCAGAGGTGCAGGGAGCATGGGCTG,TCGCTTCCCCTTTAAGCACACTCATTCACCACACCCGAGGAGGCCAGAAGTGCAGGGAGCATGGGCTG,TCGCTTCCCCTTTAAGCACACTCATTCACCACACCTGAGGAGGCCAGAAGTGCAGGGAGCATGGGCTG,TCGCTTCCCCTTTAAGCACACTCATTCACCACACCCGAGGAGGCCAGAAGTGCAGGGAGCAGCTG;SVTYPE=VNTR;ALTANNO_H1=MOTIF_1,MOTIF_2,MOTIF_1,MOTIF_1,MOTIF_1,MOTIF_0,MOTIF_3,MOTIF_2,MOTIF_1,MOTIF_1,MOTIF_1,MOTIF_1,MOTIF_1,MOTIF_1,MOTIF_0,MOTIF_1,MOTIF_1,MOTIF_0,MOTIF_0,MOTIF_0,MOTIF_0,MOTIF_1,MOTIF_1,MOTIF_0,MOTIF_0,MOTIF_0,MOTIF_0,MOTIF_1,MOTIF_0,MOTIF_1,MOTIF_0,MOTIF_1,MOTIF_0,MOTIF_1,MOTIF_1,MOTIF_0,MOTIF_1,MOTIF_0,MOTIF_0,MOTIF_1,MOTIF_0,MOTIF_0,MOTIF_0,MOTIF_0,MOTIF_0,MOTIF_0,MOTIF_2,MOTIF_0,MOTIF_1,MOTIF_1,MOTIF_0,MOTIF_0,MOTIF_1,MOTIF_0,MOTIF_0,MOTIF_0,MOTIF_0,MOTIF_2,MOTIF_0;LEN=4009;	GT	1/1
```

## Special Notes


## Known issues


## Preliminary results
