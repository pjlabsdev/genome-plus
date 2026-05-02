# Genome Plus Microarray Panel

Konsolidiertes klinisches Panel — All_SNPs + PharmCAT + 13 PGS Catalog Risk Scores.

## Stats (Stand 2026-05, Build 2)

| Metrik | Wert |
|---|---|
| Total Positionen | 2.125.603 |
| Eindeutige rsIDs | 2.037.505 |
| chr:pos-Format (PGS-Files ohne rsID) | ~88.000 |
| Position-Validation gegen Ensembl REST API (dbSNP) | **99.5% bestätigt** |
| Cross-Chromosomen-Mismatches korrigiert | 746 |
| 1-Base-Anchor-Offsets korrigiert (Indel-Konvention) | 8.506 |
| Andere Position-Korrekturen | 700 |

## Format

Tab-separated, BGZF-komprimiert mit Tabix-Index. Drop-in-Ersatz für `All_SNPs_hg38_ref.tab.gz`.

```
#CHROM   POS        ID
chr1     58814      rs114420996
chr1     69869      rs548049170
...
```

## Dedup-Garantien

- 0 Duplikate auf (chrom, pos)-Ebene
- 0 Duplikate auf rsID-Ebene
- Nur Standard-Chromosomen (chr1-22, chrX, chrY, chrM)
- Alle Positionen innerhalb GRCh38-Bereich
- chrMT → chrM vereinheitlicht (GRCh38-Konvention)

## Quellen

| Quelle | Variants | Lizenz |
|---|---|---|
| All_SNPs_hg38 (WGSExtract, 13 DTC-Plattformen) | 2.080.318 Basis | open |
| PharmCAT v3.2.0 (PGx, 22 Gene) | +291 | MPL-2.0 |
| PGS Catalog Standard 5 (BC, PC, CAD, AD, T2D) | +47.000 | mixed open |
| PGS Catalog Autoimmune 8 (MS, T1D, RA, Pso, SLE, IBD) | +210 | PGS Catalog Terms |

Komponenten-Lizenzen siehe `../docs/LICENSES.md`.
