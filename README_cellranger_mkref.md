# Get Gencode annotation- FASTA and GTF (only main chr)
from: https://www.gencodegenes.org/mouse/

```
wget ftp://ftp.ebi.ac.uk/pub/databases/gencode/Gencode_mouse/release_M24/GRCm38.primary_assembly.genome.fa.gz
wget ftp://ftp.ebi.ac.uk/pub/databases/gencode/Gencode_mouse/release_M24/gencode.vM24.annotation.gtf.gz
gunzip GRCm38.primary_assembly.genome.fa.gz gencode.vM24.annotation.gtf.gz
```
# Make reference with cellranger v3.1.0

No need to apply "cellranger mkgtf" filtering, following: https://support.10xgenomics.com/single-cell-gene-expression/software/release-notes/build
since the resulting GTF was identical (apart from adding windows carriage return characters)
Build reference:
```
cellranger mkref --genome=GRCm38_M24 --fasta=GRCm38.primary_assembly.genome.fa --genes=gencode.vM24.annotation.gtf --ref-version=3.1.0 --nthreads=4
```
