# Genome Plus Microarray Panels

Konsolidierte klinische Microarray-Panels fuer Genome (hg38 / GRCh38, 3-Spalten `#CHROM POS ID`, BGZF + Tabix).

---

## Genome Plus Panel (`Genome_Plus_hg38_ref.tab.gz`)

Konsolidiertes klinisches Panel: All_SNPs + PharmCAT + 13 PGS Catalog Risk Scores, ergaenzt um die nicht-ueberlappenden Marker eines MTHFR-Labor-Arrays.

### Stats (Stand 2026-06, Build 3)

| Metrik | Wert |
|---|---|
| Total Positionen | 2.148.375 |
| Eindeutige rsIDs | 2.060.277 |
| chr:pos-Format (PGS-Files ohne rsID) | ~88.000 |
| **Build-3-Ergaenzung: MTHFR-Array-Marker (Liftover hg19 -> hg38)** | **+22.772** |
| Position-Validation gegen Ensembl REST API (dbSNP), Basis-Panel | 99.5% bestaetigt |
| Cross-Chromosomen-Mismatches korrigiert (Basis) | 746 |
| 1-Base-Anchor-Offsets korrigiert (Indel-Konvention, Basis) | 8.506 |
| Andere Position-Korrekturen (Basis) | 700 |

> Die +22.772 Build-3-Marker stammen aus einem hg19->hg38-Liftover (UCSC-Chain) der nicht im Basis-Panel enthaltenen Array-Positionen. Sie durchliefen NICHT die Ensembl-REST-Validierung des Basis-Panels, aber den Standard-Chromosomen-Filter und (chrom,pos)-Dedup (bestehende Eintraege haben Vorrang).

## MTHFR Panel (`MTHFR_hg38_ref.tab.gz`)

Vollstaendiges Markerset eines MTHFR-Labor-Arrays (rsID-Positionen), auf hg38 gebracht. Erlaubt, den Array 1:1 aus einem hg38-WGS-BAM zu reproduzieren.

### Stats (Stand 2026-06)

| Metrik | Wert |
|---|---|
| Positionen / eindeutige rsIDs | 662.558 |
| Quelle (rsIDs gesamt) | 663.577 |
| davon hg38 direkt aus Genome-Plus-Panel uebernommen (Overlap) | 639.750 |
| davon per hg19->hg38-Liftover (UCSC-Chain) | 22.808 |
| verworfen: nicht liftbar | 996 |
| verworfen: Alt-Contig (non-primary) | 3 |
| verworfen: interne (chrom,pos)-Kollision | 20 |

## Format

Tab-separated, BGZF-komprimiert mit Tabix-Index (`tabix -s1 -b2 -e2`). Drop-in fuer `bcftools mpileup -T` bzw. `bcftools annotate -a -c CHROM,POS,ID`.

```
#CHROM   POS        ID
chr1     58814      rs114420996
chr1     69869      rs548049170
...
```

## Dedup- & Build-Garantien (beide Panels)

- 0 Duplikate auf (chrom, pos)-Ebene
- Nur Standard-Chromosomen (chr1-22, chrX, chrY, chrM)
- Alle Positionen innerhalb GRCh38-Bereich
- chrMT -> chrM vereinheitlicht (GRCh38-Konvention)

## Quellen

| Quelle | Variants | Lizenz |
|---|---|---|
| All_SNPs_hg38 (WGSExtract, 13 DTC-Plattformen) | 2.080.318 Basis | open |
| PharmCAT v3.2.0 (PGx, 22 Gene) | +291 | MPL-2.0 |
| PGS Catalog Standard 5 (BC, PC, CAD, AD, T2D) | +47.000 | mixed open |
| PGS Catalog Autoimmune 8 (MS, T1D, RA, Pso, SLE, IBD) | +210 | PGS Catalog Terms |
| MTHFR-Labor-Array (Liftover hg19->hg38) | +22.772 (Genome Plus) / 662.558 (MTHFR-Panel) | privat |

Komponenten-Lizenzen siehe `../docs/LICENSES.md`.
