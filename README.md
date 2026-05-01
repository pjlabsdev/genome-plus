# Genome Plus Reference Library

Erweiterte Reference-Bundles für die [Genome](https://pjlabs.dev) macOS-App.

Ergänzt die Standard-Microarray-Panels (`All_SNPs_hg38_ref.tab.gz`, `Genome_SNPs_hg38_ref.tab.gz`) um klinisch hochwertige, kuratierte Datensätze für Pharmakogenetik, Polygenic Risk Scores und HLA-Typing.

## Inhalt

| Bundle | Inhalt | Lizenz | Größe | Quelle |
|---|---|---|---|---|
| **pharmcat/** | PharmCAT positions.vcf v3.2.0 — ~250 PGx-Positionen, deckt 95% CPIC-Empfehlungen | MPL-2.0 | 64 KB | [PharmGKB/PharmCAT](https://github.com/PharmGKB/PharmCAT) |
| **pgs-catalog/** | 5 klinisch validierte Polygenic Risk Scores (Brust, Prostata, CAD, Alzheimer, T2D) | CC0/Open | 1.3 MB | [PGS Catalog (EBI)](https://www.pgscatalog.org) |
| **hibag/** | HLA-Imputation-Modelle (Multi-Ethnic) — Install-Anleitung | GPL-3 | extern | [HIBAG/Bioconductor](https://bioconductor.org/packages/HIBAG) |

## 23andMe V5/V5.1 SNP-Coverage

Die SNP-Listen der 23andMe-Chips sind Illumina-proprietär (GSA Custom Add-On) und nicht öffentlich verfügbar. Sie sind aber im Genome-Standard-Panel `All_SNPs_hg38_ref.tab.gz` (WGSExtract-konsolidiert über 13 Plattformen) bereits weitgehend abgedeckt.

23andMe V6 ist (Stand 2026) **nicht freigegeben** — kein öffentliches Manifest existiert.

## Lizenzhinweise

Die einzelnen Bundle-Komponenten haben unterschiedliche Lizenzen — siehe `docs/LICENSES.md` für Details. Die Aggregation als „Genome Plus" steht unter MIT-Lizenz, jede Komponente behält ihre Original-Lizenz.

## Integration in Genome

In der Genome-App (Referenzen-Tab) erscheint „Genome Plus" als optionaler Bundle-Download. Die Inhalte werden in `<reference-library>/genome-plus/` extrahiert.

---

Erstellt von [PJ Labs](https://pjlabs.dev) für die Genome macOS-App.
