# Autoimmune & MS Polygenic Risk Scores

8 kuratierte PGS Catalog Scores für Autoimmun-Erkrankungen (Stand 2024–2025).
Kompakt (~930 Variants total, 40 KB) für direkte Microarray-Anwendung.

| PGS-ID | Trait | Variants | Jahr | Bemerkung |
|---|---|---|---|---|
| **PGS004699** | Multiple Sclerosis (Non-HLA) | 307 | 2024 | Non-HLA Genetic Risk Score |
| **PGS004700** | Multiple Sclerosis (HLA) | 12 | 2024 | HLA-only komplementär zu 4699 |
| **PGS004117** | Type 1 Diabetes | 131 | 2024 | GCST90013445 LDpred-clump |
| **PGS004133** | Rheumatoid Arthritis | 155 | 2024 | GCST90013534 nested-CV |
| **PGS005307** | Psoriasis (komplett) | 65 | 2025 | GWS — neueste Studie |
| **PGS005308** | Psoriasis (Non-HLA) | 64 | 2025 | komplementär zu 5307 |
| **PGS003960** | Systemic Lupus Erythematosus | 57 | 2023 | GRS57_SLE etabliert |
| **PGS004105** | Inflammatory Bowel Disease | 139 | 2024 | GCST004131 |

## Anwendungs-Hinweise

- **MS**: Kombiniere PGS004699 + PGS004700 für maximale Sensitivität (HLA-Region trägt ~50% der MS-Heritabilität)
- **Psoriasis**: Wie MS — kombiniere PGS005307 + PGS005308 für getrennte HLA/Non-HLA-Auswertung
- **Alle Scores sind GRCh38-harmonisiert** (hmPOS_GRCh38)
- **EUR-bias**: die meisten Scores sind in europäischen Kohorten validiert. Anwendung bei nicht-europäischen Personen erfordert Vorsicht (reduzierter prädiktiver Wert).

## Lizenz

Alle Scores aus dem PGS Catalog stehen unter der Original-Publikations-Lizenz. Zitations-Hinweise siehe Header der jeweiligen `.txt.gz` Datei.
