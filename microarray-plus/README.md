# Genome Plus Microarray Panel

Konsolidiertes Single-File-Panel mit garantierter Eindeutigkeit:
- Pro (chrom, pos): nur ein Eintrag
- Pro rsID: nur ein Eintrag (Position aus All_SNPs_hg38 priorisiert)

## Inhalt (Stand 2026-05)

| Quelle | Variants | Priorität |
|---|---|---|
| All_SNPs_hg38 (WGSExtract, 13 DTC-Plattformen) | 2.078.930 | 1 (höchste) |
| + PharmCAT v3.2.0 (neue Positionen, kuratiert) | +291 | 2 |
| + PGS Catalog (Standard 5 + Autoimmune 8) | +47.197 | 3 |
| **Total unique** | **2.126.418** | – |

Davon ~2.04M mit echtem rsID, ~88k im chr:pos-Format (PGS-Files ohne rsID-Annotation).

## Format

Tab-separated, BGZF-komprimiert mit Tabix-Index. Drop-in-Ersatz für `All_SNPs_hg38_ref.tab.gz`.

## Lizenz

Aggregation: MIT. Komponenten siehe `../docs/LICENSES.md`.
