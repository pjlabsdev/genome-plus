# Genome Plus Microarray Panel

Konsolidiertes Single-File-Panel für die Genome macOS-App: enthält
**alle SNPs aus All_SNPs_hg38** plus die zusätzlichen Positionen aus
**PharmCAT + 13 PGS Catalog Risk Scores**.

## Inhalt

| Quelle | Variants |
|---|---|
| All_SNPs_hg38 (2M-Basis aus WGSExtract, 13 DTC-Plattformen) | 2.080.318 |
| + PharmCAT positions v3.2.0 (PGx) | +304 (eindeutig neu) |
| + PGS Catalog Standard 5 (BC, PC, CAD, AD, T2D) | +47.000 |
| + PGS Catalog Autoimmune 8 (MS, T1D, RA, Pso, SLE, IBD) | +210 |
| **Total unique** | **2.127.818** |

## Format

Tab-separated, BGZF-komprimiert mit Tabix-Index (`.tbi`):
```
#CHROM   POS        ID
chr1     58814      rs114420996
chr1     69869      rs548049170
...
```

Drop-in-Ersatz für `All_SNPs_hg38_ref.tab.gz` mit zusätzlicher klinischer Coverage.

## Lizenz

Aggregation: MIT. Komponenten siehe `../docs/LICENSES.md`.
