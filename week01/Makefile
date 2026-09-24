ASSEMBLY := GCF_000841725.1
SEQUENCE := NC_005357.1
PACKAGE := .cache/$(ASSEMBLY).zip
PACKAGE_DIR := ncbi_dataset/data/$(ASSEMBLY)
FASTA := fasta/$(SEQUENCE).fna
GFF := gff/$(SEQUENCE).gff3

.DEFAULT_GOAL := all
.DELETE_ON_ERROR:

.PHONY: all clean check

all: $(FASTA) $(GFF)

$(PACKAGE):
	mkdir -p $(@D)
	datasets download genome accession $(ASSEMBLY) --include genome,gff3 --filename $@.tmp --no-progressbar
	unzip -tq $@.tmp
	mv $@.tmp $@

$(FASTA): $(PACKAGE)
	mkdir -p $(@D)
	unzip -p $< $(PACKAGE_DIR)/$(ASSEMBLY)_ViralProj14353_genomic.fna > $@
	test -s $@

$(GFF): $(PACKAGE)
	mkdir -p $(@D)
	unzip -p $< $(PACKAGE_DIR)/genomic.gff > $@
	test -s $@

check: all
	grep -q '^>$(SEQUENCE) ' $(FASTA)
	grep -q '^##sequence-region $(SEQUENCE) 1 42493$$' $(GFF)
	grep -q 'product=Reverse transcriptase' $(GFF)

clean:
	rm -f $(FASTA) $(GFF) $(PACKAGE)
	rmdir fasta gff .cache 2>/dev/null || true
