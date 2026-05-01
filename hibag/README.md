# HIBAG Multi-Ethnic Models

HIBAG-Modelle für HLA-Imputation sind aufgrund ihrer Größe (~30 MB) und Lizenz-Verteilungs-Komplexität nicht direkt in diesem Repository hinterlegt.

## Manuelle Installation

### Variante A: Via R + Bioconductor (empfohlen)

```bash
# R installieren (falls nicht vorhanden)
brew install r

# Bioconductor + HIBAG installieren
R -e 'if (!requireNamespace("BiocManager", quietly = TRUE)) install.packages("BiocManager"); BiocManager::install("HIBAG")'

# Multi-Ethnic Models laden + extrahieren
R -e 'library(HIBAG); data(HLA_Model_List); saveRDS(HLA_Model_List, "hibag_models.rds")'
```

Lege das resultierende `hibag_models.rds` in `<reference-library>/genome-plus/hibag/` ab.

### Variante B: Direct-Download (falls verfügbar)

Aktuelle Mirror-Quellen (Stand 2026, kann veraltet sein):
- ⚠️ hlares.org/HIBAG/ (war Standard, derzeit offline)
- Bioconductor Daten-Packages

Genome wird beim ersten HLA-Imputing-Aufruf prüfen ob die Modelle vorhanden sind und ggf. Anweisungen geben.

## Welche HLA-Loci werden abgedeckt?

Multi-Ethnic Models (4-digit Resolution, ~95% Sensitivität in EUR):
- HLA-A
- HLA-B
- HLA-C
- HLA-DRB1
- HLA-DQA1
- HLA-DQB1
- HLA-DPB1

Dies löst u.a. das `rs3135388 / HLA-DRB1*15:01` Tag-SNP-Problem präziser als reine Tag-SNP-Auswertung.

## Lizenz

GPL-3 (R-Package) + Models von Zheng et al. — sieh Original-Quellen für vollen Lizenz-Text.
