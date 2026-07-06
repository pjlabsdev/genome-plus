# Genome Plus Microarray Panels

Konsolidierte klinische Microarray-Panels fuer Genome (hg38 / GRCh38, 3-Spalten `#CHROM POS ID`, BGZF + Tabix).

---

## Genome Plus Panel (`Genome_Plus_hg38_ref.tab.gz`)

Konsolidiertes klinisches Panel: All_SNPs + PharmCAT + 13 PGS Catalog Risk Scores, ergaenzt um die nicht-ueberlappenden Marker eines MTHFR-Labor-Arrays.

### Stats (Stand 2026-07, Build 3 + AQP4)

| Metrik | Wert |
|---|---|
| Total Positionen | 2.146.099 |
| Eindeutige rsIDs | 2.058.000 |
| chr:pos-Format (PGS-Files ohne rsID) | ~88.000 |
| **Build-3-Ergaenzung: MTHFR-Array-Marker (GRCh38 direkt)** | **+20.495** |
| **AQP4-Ergaenzung: rs72878794 (AQP4, chr18:26866839)** | **+1** |
| Position-Validation gegen Ensembl REST API (dbSNP), Basis-Panel | 99.5% bestaetigt |
| Cross-Chromosomen-Mismatches korrigiert (Basis) | 746 |
| 1-Base-Anchor-Offsets korrigiert (Indel-Konvention, Basis) | 8.506 |
| Andere Position-Korrekturen (Basis) | 700 |

> Die +20.495 Build-3-Marker stammen aus einem MTHFR-Labor-Array, dessen Rohdaten bereits in **GRCh38** vorliegen. Die Positionen werden daher direkt uebernommen (KEIN Liftover). Nur die rsIDs, die nicht bereits im Basis-Panel sind, werden aufgenommen; Standard-Chromosomen-Filter und (chrom,pos)-Dedup (bestehende Eintraege haben Vorrang) sind angewandt.

> **AQP4 (2026-07):** rs72878794 (AQP4, `chr18:26866839`, GRCh38, gegen Ensembl REST verifiziert) manuell ergaenzt — deckt das AQP4-glymphatische-Aβ-Clearance-Modul im DiseaseRisk-Bericht ab. Ein seltener AQP4-Marker fehlt in den DTC-Array-Plattformen und war daher nicht im Basis-Panel.

## MTHFR-Genetics Panel (`MTHFR-Genetics_hg38_ref.tab.gz`)

Vollstaendiges Markerset eines MTHFR-Labor-Arrays (GRCh38, rsID-Positionen). Erlaubt, den Array 1:1 aus einem hg38-WGS-BAM zu reproduzieren.

### Stats (Stand 2026-06)

| Metrik | Wert |
|---|---|
| Positionen | 663.592 |
| Quelle (rsIDs gesamt im Array) | 663.577 |
| Koordinaten-Build der Rohdaten | GRCh38 (direkt uebernommen, kein Liftover) |
| MT-Konvention | rCRS, als chrM (= GRCh38 chrM) |
| Filter | nur Standard-Chromosomen, (chrom,pos)-Dedup |

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
| MTHFR-Labor-Array (GRCh38 direkt) | +20.495 (Genome Plus) / 663.592 (MTHFR-Panel) | privat |

Komponenten-Lizenzen siehe `../docs/LICENSES.md`.
