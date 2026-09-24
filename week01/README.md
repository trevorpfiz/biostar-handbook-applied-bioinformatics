What version is the samtools command in your bioinfo enviroment?
❯ samtools --version
samtools 1.24

## BPP-1 phage genome

The [Bordetella phage BPP-1](https://www.ncbi.nlm.nih.gov/datasets/genome/GCF_000841725.1/) genome encodes the `brt` reverse transcriptase. Its diversity-generating retroelement changes the `mtd` tail protein, allowing host tropism to change ([Doulatov et al., 2004](https://pmc.ncbi.nlm.nih.gov/articles/PMC344406/)).

Genome size: 42,493 bp (42.5 kb)
Number of chromosomes: 1
Number of annotations: 49 genes w/ 103 annotations
Completeness: Complete Genome

From the repository root, download the NCBI Datasets assembly package and extract its genome FASTA and GFF3 annotation:

```sh
pixi run make -C week01
pixi run make -C week01 check
```

The outputs are `fasta/NC_005357.1.fna` and `gff/NC_005357.1.gff3` inside `week01`. The Makefile requires `datasets` and `unzip`; `datasets` is already in this project's Pixi environment.
