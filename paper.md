---
title: "Closing the Genomic Gap: A Nurse-Built Tool for Pharmacogenomic Equity Across Ancestry Groups in UK Clinical Practice"
authors: "Lincoln Gombedza"
affiliation: "Nurse Citizen Developer, Clinical Quality Artificial Intelligence (CQAI)"
date: 2026-03-18
tags: [pharmacogenomics, health-equity, nursing, NHS, clinical-safety, global-majority, DPYD, G6PD, open-source]
layout: modern
---

<div class="header">

# Closing the Genomic Gap

## A Nurse-Built Tool for Pharmacogenomic Equity Across Ancestry Groups in UK Clinical Practice

<div class="authors">
Lincoln Gombedza — Nurse Citizen Developer, Clinical Quality Artificial Intelligence (CQAI)
</div>

<div class="date">
March 2026 · Submitted as a practice development paper
</div>

<div class="links">

[🧬 Live Tool](https://huggingface.co/spaces/NurseCitizenDeveloper/genomics-health-equity) · [🔬 VirtualGeneScope](https://huggingface.co/spaces/NurseCitizenDeveloper/VirtualGeneScope) · [💻 GitHub](https://github.com/Clinical-Quality-Artifical-Intelligence) · [📖 Blog](https://notes.liiib.re/docs/d0263fc9-e813-43ba-bed6-09e339f943a1/)

</div>

</div>

---

## Abstract

<div class="abstract">

Current NHS pharmacogenomic (PGx) testing panels were developed primarily using European-ancestry genomic data, creating systematic equity gaps for patients of African, South Asian, East Asian, and mixed heritage backgrounds. This paper presents the **CQAI Genomics Health Equity Tool** — a free, open-source Streamlit application developed by a registered nurse and citizen developer — that maps 10 pharmacogenomic tests across 10 ancestry groups to identify, communicate, and act on these gaps at the clinical point of care.

Key findings include: the NHS DPYD panel omits the c.557A>G variant enriched in African-ancestry patients, flagged by the NHS Race and Health Observatory (July 2024) as requiring urgent inclusion in the National Genomic Test Directory; G6PD deficiency affects approximately 400 million people globally yet has no routine NHS PGx panel; UGT1A1\*6 is absent from UK panels despite a 23% population frequency in East Asian communities; and NAT2 slow acetylator phenotype — affecting isoniazid metabolism in TB treatment — is not routinely tested despite an approximately 80% frequency in South Asian populations.

The tool equips nurses with ancestry-aware coverage assessments, pre-filled SBAR and MDT report templates, NMC-compliant patient notes, clinical advocacy toolkits, an equity heatmap, and downloadable `.docx` reports — all without requiring API keys, institutional login, or advanced technical literacy. It is aligned with NMC Standards of Proficiency (2018) and designed in accordance with DCB0129 clinical safety guidance. This is the first nurse-built, equity-focused pharmacogenomics tool designed specifically for UK frontline clinical practice.

</div>

---

## 1. Introduction

Pharmacogenomics — the study of how an individual's genes affect their response to drugs — is one of the most clinically significant and yet most inequitably implemented advances in modern medicine. The NHS Genomic Medicine Service has mandated pre-treatment DPYD genotyping for fluoropyrimidine chemotherapy since 2020, representing a landmark commitment to personalised care. Yet the implementation of this mandate contains a structural blind spot: the testing panels in routine use were designed around variants identified in European-ancestry populations.

<div class="key-insight">
💡 <strong>Key Clinical Insight</strong>: A "normal" result on an NHS PGx panel does not mean a patient is safe to proceed with standard dosing — it may simply mean that the variant relevant to their ancestry was never included in the panel.
</div>

This paper presents the motivation, design, and clinical utility of two nurse-built genomics tools:

1. **VirtualGeneScope** — an interactive genomics learning platform for student nurses
2. **Genomics Health Equity Tool** — a clinical equity assessment and advocacy tool for frontline nurses

Both tools were developed by a registered nurse and citizen developer, inspired by a conversation at the **CAHN Rising Together: Global Majority Nursing and Midwifery Leadership Conference**, Manchester, February 2026 — where the imperative to bring genomics equity into nursing practice was made plain.

### 1.1 Why Nurses?

Nurses are the professionals most likely to be present at the moments that matter: the pre-medication check, the allergy and ancestry assessment, the administration of a first cycle of chemotherapy. The NMC Code (2018) requires nurses to act in the best interests of every patient and to escalate concerns when patient safety is at risk. Yet nurses are rarely taught to ask: *does the standard test actually cover this patient's genetic background?*

This tool exists to change that.

---

## 2. Background

### 2.1 Pharmacogenomics in UK Clinical Practice

Pharmacogenomics identifies genetic variants that predict how a patient will metabolise a given drug. Clinically significant examples include:

| Gene | Drug class | Clinical risk | Testing status |
|------|-----------|---------------|----------------|
| DPYD | Fluoropyrimidine chemotherapy (5-FU, capecitabine) | Severe/fatal toxicity | NHS-mandated (2020) |
| G6PD | Rasburicase, dapsone, primaquine | Haemolytic anaemia | Not routinely tested |
| UGT1A1 | Irinotecan | Severe neutropenia | Not routinely tested |
| NAT2 | Isoniazid (TB treatment) | Peripheral neuropathy, hepatotoxicity | Not routinely tested |
| CYP2C19 | Clopidogrel, SSRIs, PPIs | Therapeutic failure or toxicity | Partial testing only |

### 2.2 The Ancestry Gap

The current NHS DPYD panel tests four variants:
- \*2A (rs3918290)
- \*13 (rs55886062)
- c.1236G>A/HapB3 (rs56038477)
- c.2846A>T (rs67376798)

All four were identified primarily in studies of European-ancestry populations. The NHS Race and Health Observatory's July 2024 DPD Testing Lay Summary identified **c.557A>G** — a variant enriched in patients of African ancestry — as absent from the panel despite clear clinical evidence of its functional significance and toxicity risk. The RHO recommended its inclusion in the National Genomic Test Directory.

<div class="definition">
⚠️ <strong>The Equity Gap</strong>: A Black patient receiving fluoropyrimidine chemotherapy could carry the c.557A>G DPYD variant, suffer catastrophic toxicity, and the standard NHS panel would show "no variant found." This is not a clinical error — it is a structural gap in the testing infrastructure.
</div>

### 2.3 NMC Accountability

Under Platform 6 of the NMC Standards of Proficiency (2018), nurses must demonstrate the ability to raise concerns immediately when patient safety is at risk. Under the NMC Code (2018), the Duty of Candour applies when patients are harmed. These obligations create a clear professional imperative for nurses to understand PGx equity gaps — and to have the tools to act on them.

---

## 3. Tool Design and Methodology

### 3.1 VirtualGeneScope

**Purpose**: Interactive genomics education for student nurses.

**Architecture**: Streamlit application using the AlphaGenome API (Google DeepMind) for molecular phenotype prediction. No API keys required for educational mode.

**Key features**:
- Gene selection covering clinically significant PGx genes
- Named variant picker including NHS RHO 2024 variants
- Equity alert banners for ancestry-relevant variants not in current panels
- Gene Quiz (5 questions per gene, NMC aligned)
- Clinical Case Studies (including Adaeze — a Nigerian-British patient whose c.557A>G variant was missed)
- Population frequency data across global ancestry groups
- Full genomics glossary

**NMC alignment**: Platforms 1, 4, and 6 of the Standards of Proficiency (2018).

### 3.2 Genomics Health Equity Tool

**Purpose**: Ancestry-aware PGx equity assessment and clinical advocacy for frontline nurses.

**Architecture**: Streamlit application with curated static data, python-docx report generation, and matplotlib equity heatmap. No external API dependencies for core function.

**Coverage**: 10 PGx tests × 10 ancestry groups

**PGx tests covered**:

| Test | Drugs affected | Key equity gap |
|------|---------------|----------------|
| DPYD | 5-FU, capecitabine, tegafur | c.557A>G missing (African ancestry) |
| G6PD | Rasburicase, dapsone, primaquine | No routine NHS panel |
| UGT1A1 | Irinotecan | \*6 variant missing (East Asian) |
| NAT2 | Isoniazid | Not routinely tested |
| CYP2C19 | Clopidogrel, SSRIs, PPIs | Partial panel coverage |
| CYP2D6 | Codeine, tamoxifen, antipsychotics | Partial coverage |
| HLA-B\*57:01 | Abacavir (HIV) | Well covered |
| TPMT/NUDT15 | Thiopurines | Partial — NUDT15\*3 missing (Asian) |
| CYP3A5 | Tacrolimus (transplant) | African ancestry variants underrepresented |
| SLCO1B1 | Statins | Limited panel coverage |

**Ancestry groups covered**: African, Caribbean, South Asian, East Asian, Southeast Asian, Middle Eastern, European, Mixed, Latin American, Unknown/Unspecified

**Assess coverage logic**: The tool uses a canonical ancestry mapping with explicit `equity_for_european` flags per test, distinguishing between panels appropriate for European-ancestry patients and those that carry risk for non-European patients.

### 3.3 Clinical Communication Features

The tool generates seven categories of clinical documentation:

1. **Equity Assessment Report** — ancestry-specific coverage finding with gap list
2. **SBAR Handover** — pre-filled verbal/written handover template (.docx)
3. **Patient Notes Entry** — NMC-compliant clinical record wording (.docx)
4. **Email to Consultant/Pharmacist** — formal escalation template (.txt)
5. **MDT Report** — structured multi-disciplinary team document (.docx)
6. **Incident Report Guidance** — Datix, MHRA Yellow Card, PSIRF pathways
7. **Referral Contacts** — UKAS-accredited genomics laboratories by region

### 3.4 Equity Heatmap

A 2D matplotlib visualisation maps ancestry groups against PGx tests, colour-coded:

- 🔴 **Limited** (score 1) — panel not designed for this ancestry
- 🟡 **Partial** (score 2) — some coverage, significant gaps
- 🟢 **Adequate** (score 3) — panel appropriate for this ancestry

This provides an at-a-glance population-level view of where the NHS testing infrastructure currently fails.

---

## 4. Clinical Case Examples

### Case 1: DPYD c.557A>G — Adaeze, 45, Nigerian-British

Adaeze is referred for adjuvant chemotherapy following colorectal cancer surgery. Standard DPYD genotyping returns no variant found. She receives full-dose capecitabine. On Day 7 she presents with grade 4 mucositis and neutropenia.

**The equity gap**: The c.557A>G variant, enriched in African-ancestry patients, was not tested. Her result was not false — the panel simply never asked the right question for her ancestry.

**Tool output**: The Genomics Health Equity Tool, when run with African ancestry + DPYD prior to drug administration, would have flagged this gap, generated an SBAR for the prescribing team, and prompted referral for enzyme phenotyping (DPD enzyme activity assay) — an ancestry-independent alternative.

### Case 2: G6PD — Kwame, 28, Ghanaian-British, Acute Leukaemia

Kwame requires rasburicase for tumour lysis syndrome management. Standard pre-treatment screening does not include G6PD testing. He develops acute haemolytic anaemia.

**The equity gap**: G6PD deficiency has an estimated population frequency of 25% in West African males. There is no routine NHS PGx panel for G6PD. The G6PD enzyme activity assay is the appropriate pre-treatment test — available but not consistently requested.

### Case 3: NAT2 — Priya, 34, South Asian, New TB Diagnosis

Priya commences standard-dose isoniazid. At 8 weeks she develops peripheral neuropathy. NAT2 slow acetylator status was not tested — a phenotype present in approximately 80% of South Asian populations, significantly increasing isoniazid plasma concentration and toxicity risk.

---

## 5. Equity Heatmap Findings

Analysis of the tool's equity heatmap reveals:

- **European-ancestry patients** receive adequate panel coverage for 7/10 tests
- **African-ancestry patients** receive adequate coverage for 3/10 tests
- **East Asian patients** receive adequate coverage for 4/10 tests
- **South Asian patients** receive adequate coverage for 4/10 tests
- **G6PD and NAT2** show "limited" coverage for all non-European ancestry groups due to absence of any routine NHS panel

These findings are consistent with published literature on PGx equity gaps (Mwenifumbo & Carleton, 2011; Gaedigk et al., 2017; NHS RHO, 2024).

---

## 6. Discussion

### 6.1 The Role of Nurse-Built Tools

This tool was not built in an academic laboratory. It was built by a registered nurse, using free cloud infrastructure (Hugging Face Spaces), open APIs, and curated clinical evidence — during evenings and weekends. This is not an argument against academic rigour. It is a demonstration that the expertise to identify clinical equity gaps exists in the nursing profession, and that nurses should be empowered and supported to translate that expertise into tools.

The Nurse Citizen Developer model — nurses who code, build, and deploy clinical tools — represents an underutilised form of clinical innovation. The NMC's Digital Proficiency Standards (2023) explicitly recognise that nurses must engage with digital health tools. This paper proposes that some nurses should also *build* them.

### 6.2 The WRES Connection

The Workforce Race Equality Standard (WRES) documents that Global Majority NHS staff are underrepresented in senior roles, disproportionately subject to disciplinary action, and less likely to access leadership development. The genomics equity gap described in this paper is a mirror of this broader pattern: systems designed without full representation tend to serve some populations better than others.

Addressing PGx equity is therefore not only a clinical patient safety issue — it is part of the same equity agenda that drives WRES, the NHS Race and Health Observatory, and the work of organisations like CAHN Rising Together.

### 6.3 Limitations

<div class="limitations">

⚠️ <strong>Current Limitations</strong>:

1. The equity heatmap scores are based on curated clinical evidence and expert judgement — not prospective outcomes data
2. The tool does not integrate with EPR systems or NHS SPINE — documentation must be manually transferred
3. Population frequency data represents literature estimates and may not reflect local demographic variation
4. The tool is designed for educational awareness and advocacy — it does not replace formal genomics laboratory assessment or clinical genetics consultation
5. notes.liiib.re hosting resets monthly — a self-hosted instance is recommended for permanent deployment

</div>

### 6.4 Future Directions

- **Integration with NHS SPINE / FHIR R4**: Publishing findings as FHIR DocumentReference resources for EPR integration
- **NCLEX/NMC question bank**: Embedding genomics equity questions across the CQAI student tool suite
- **Railway self-hosted deployment**: Permanent infrastructure funded by AWS Activate credits ($1,000 awarded)
- **Submission to National Genomic Test Directory**: Formal engagement with NHS England Genomics team regarding c.557A>G and other missing variants
- **Prospective validation**: Partnership with NHS genomics laboratories to validate equity gap identification against real panel results

---

## 7. Conclusion

<div class="conclusion">

The CQAI Genomics Health Equity Tool demonstrates that:

1. ✅ **Pharmacogenomic testing equity gaps are systematic and clinically significant** — they are not edge cases but predictable consequences of panels designed from non-representative data
2. ✅ **Nurses are uniquely positioned to identify and act on these gaps** — at the point of drug administration, before harm occurs
3. ✅ **Free, open-source tools can bridge the gap** between policy recommendations (NHS RHO 2024) and frontline clinical practice — without waiting for institutional IT procurement cycles
4. ✅ **The nursing profession contains the clinical expertise to build its own tools** — the Nurse Citizen Developer model is viable, replicable, and necessary

The whisper that started this work — *"don't forget about genomics"* — was an act of clinical leadership. This paper, and the tools it describes, are the answer.

</div>

---

## Reproducibility

<div class="reproducibility">

### Code & Spaces

- **Genomics Health Equity Tool**: [huggingface.co/spaces/NurseCitizenDeveloper/genomics-health-equity](https://huggingface.co/spaces/NurseCitizenDeveloper/genomics-health-equity)
- **VirtualGeneScope**: [huggingface.co/spaces/NurseCitizenDeveloper/VirtualGeneScope](https://huggingface.co/spaces/NurseCitizenDeveloper/VirtualGeneScope)
- **GitHub Organisation**: [github.com/Clinical-Quality-Artifical-Intelligence](https://github.com/Clinical-Quality-Artifical-Intelligence)
- **All CQAI Tools**: Free, open-source, no API keys required

### Citation

```bibtex
@article{gombedza2026genomic,
  title={{Closing the Genomic Gap: A Nurse-Built Tool for Pharmacogenomic Equity
          Across Ancestry Groups in UK Clinical Practice}},
  author={Gombedza, Lincoln},
  year={2026},
  note={CQAI Practice Development Paper. Available at:
        https://huggingface.co/spaces/NurseCitizenDeveloper/genomics-health-equity}
}
```

</div>

---

## References

1. NHS Race and Health Observatory (2024). *DPD Testing Lay Summary*. NHS RHO, July 2024.
2. NHS England (2020). *Genomic Medicine Service — DPYD genotyping mandate for fluoropyrimidine chemotherapy*. NHS England.
3. CPIC (2023). *Clinical Pharmacogenomics Implementation Consortium Guidelines for DPYD and Fluoropyrimidines*. cpicpgx.org.
4. NMC (2018). *The Code: Professional standards of practice and behaviour for nurses, midwives and nursing associates*. Nursing and Midwifery Council.
5. NMC (2018). *Future Nurse: Standards of Proficiency for Registered Nurses*. Nursing and Midwifery Council.
6. Mwenifumbo JC & Carleton BC (2011). Pharmacogenomics and adverse drug reactions. *Translational Research*, 159(1): 27–35.
7. Gaedigk A et al. (2017). The Pharmacogene Variation (PharmVar) Consortium. *Clinical Pharmacology & Therapeutics*, 103(3): 399–401.
8. NHS England (2023). *Workforce Race Equality Standard (WRES) — 2023 Data Analysis Report*.
9. CAHN (2026). *Rising Together: Global Majority Nursing and Midwifery Leadership Conference*. Caribbean and African Health Network, Manchester, 5 February 2026.
10. Google DeepMind (2025). *AlphaGenome: AI model for genomic variant effect prediction*. DeepMind.

---

## Acknowledgements

To **Professor Habib** — for the whisper.

To **CAHN Rising Together** — for the room.

To every student nurse who has ever wondered whether the standard answer was the right answer for every patient — keep asking.

---

<div class="disclaimer">

**Disclaimer**: This paper represents the personal practice development work of Lincoln Gombedza in his capacity as a Nurse Citizen Developer. It does not represent the views of any employer, NHS organisation, university, or professional body. All tools described are for educational purposes and support but do not replace clinical judgement. Clinical decisions regarding pharmacogenomic testing must be made by qualified clinicians in accordance with local protocols, NICE and CPIC guidelines, and NMC professional standards.

</div>

---

<style>
.header { text-align: center; margin-bottom: 2em; }
.authors { font-size: 1.1em; margin: 0.5em 0; color: #444; }
.date { color: #888; margin: 0.5em 0; font-size: 0.95em; }
.links { margin-top: 1em; font-size: 1.05em; }
.abstract { background: #f0f7ff; padding: 1.5em; border-radius: 8px; margin: 1em 0; border-left: 4px solid #1565C0; }
.key-insight { background: #e8f4f8; border-left: 4px solid #2196F3; padding: 1em; margin: 1em 0; border-radius: 4px; }
.definition { background: #fff8e1; border-left: 4px solid #FFA000; padding: 1em; margin: 1em 0; border-radius: 4px; }
.limitations { background: #fff3e0; border-left: 4px solid #E65100; padding: 1em; margin: 1em 0; border-radius: 4px; }
.conclusion { background: #e8f5e9; border-left: 4px solid #2E7D32; padding: 1.5em; margin: 1em 0; border-radius: 4px; }
.reproducibility { background: #f5f5f5; padding: 1.5em; border-radius: 8px; margin: 2em 0; }
.disclaimer { background: #fafafa; border: 1px solid #ddd; padding: 1em; border-radius: 4px; font-size: 0.9em; color: #555; margin-top: 2em; }
</style>
