# military_sat

Archive and utilities for entrance-exam material used in the project.

## ITA exam archive

Official ITA entrance-exam PDFs are mirrored from:

https://www.vestibular.ita.br/provas.htm

The archive contains the exam papers and the official first-phase answer keys. Second-phase answer keys are excluded.

```text
ita_provas/
├── manifest.xlsx
├── 2026/
│   ├── 2026_fase1.pdf
│   ├── gabarito_2026.pdf
│   ├── matematica_2026_2f.pdf
│   ├── fisica_2026_2f.pdf
│   └── ...
├── 2025/
├── ...
└── 2008/
```

`manifest.xlsx` contains one row per PDF with year, label, repository path, file size, SHA-256 digest, and original source URL.

### Download

```bash
python -m pip install -r requirements.txt
python scripts/download_ita_provas.py
```

To force verification against the current upstream files:

```bash
python scripts/download_ita_provas.py --refresh --min-files 95
```

## ITA datasets

`scripts/build_ita_datasets.py` processes the archived PDFs and separates numbered questions by type rather than by exam phase.

```text
ita_data/
├── ita_multiple_choice.parquet
├── ita_multiple_choice.xlsx
├── ita_multiple_choice_images.parquet
├── ita_multiple_choice_images/
├── ita_essay_questions.parquet
├── ita_essay_questions.xlsx
├── ita_essay_questions_images.parquet
└── ita_essay_questions_images/
```

`ita_multiple_choice.parquet` is long format: one row per answer alternative. `ita_essay_questions.parquet` contains one row per open-ended question. Both preserve `exam_phase`, subject, year, source PDF, page provenance, OCR/review flags, and one-to-many image relationships through separate image Parquets.

For the 2008–2018 single-phase exams, Physics, Mathematics and Chemistry questions 1–20 are classified as multiple choice and 21–30 as essay questions; English and Portuguese numbered questions are multiple choice. From 2019 onward, first-phase questions are multiple choice and second-phase Physics, Mathematics and Chemistry questions are essay questions. Writing prompts are excluded.

Build locally with:

```bash
python scripts/build_ita_datasets.py
```

## Automation

`.github/workflows/update-ita-provas.yml` updates the archive automatically on the first day of each month and can also be executed manually.

`.github/workflows/build-ita-datasets.yml` validates the unified builder in pull requests and regenerates the versioned multiple-choice and essay datasets after relevant changes reach `main`.

## Researcher

**Osvaldo L. Santos-Pereira**

<a href="mailto:olsp@if.ufrj.br"><img src="https://api.iconify.design/mdi:email.svg?color=%23888888" height="22" alt="Email" align="absmiddle"></a> **Email:** [olsp@if.ufrj.br](mailto:olsp@if.ufrj.br)  
<a href="https://ozsp12.github.io/"><img src="https://api.iconify.design/mdi:web.svg?color=%23888888" height="22" alt="Academic webpage" align="absmiddle"></a> **Academic webpage:** [https://ozsp12.github.io/](https://ozsp12.github.io/)  
<a href="http://lattes.cnpq.br/6730251976463283"><img src="https://api.iconify.design/mdi:account-school.svg?color=%23888888" height="22" alt="Lattes" align="absmiddle"></a> **Lattes:** [http://lattes.cnpq.br/6730251976463283](http://lattes.cnpq.br/6730251976463283)  
<a href="https://orcid.org/0000-0003-2231-517X"><img src="https://cdn.simpleicons.org/orcid/A6CE39" height="22" alt="ORCID" align="absmiddle"></a> **ORCID:** [https://orcid.org/0000-0003-2231-517X](https://orcid.org/0000-0003-2231-517X)  
<a href="https://scholar.google.com/citations?user=HIZp0X8AAAAJ&amp;hl=en"><img src="https://cdn.simpleicons.org/googlescholar/4285F4" height="22" alt="Google Scholar" align="absmiddle"></a> **Google Scholar:** [https://scholar.google.com/citations?user=HIZp0X8AAAAJ&hl=en](https://scholar.google.com/citations?user=HIZp0X8AAAAJ&hl=en)  
<a href="https://www.researchgate.net/profile/Osvaldo-Santos-Pereira"><img src="https://cdn.simpleicons.org/researchgate/00CCBB" height="22" alt="ResearchGate" align="absmiddle"></a> **ResearchGate:** [https://www.researchgate.net/profile/Osvaldo-Santos-Pereira](https://www.researchgate.net/profile/Osvaldo-Santos-Pereira)  
<a href="https://github.com/ozsp12"><img src="https://cdn.simpleicons.org/github/888888" height="22" alt="GitHub" align="absmiddle"></a> **GitHub:** [https://github.com/ozsp12](https://github.com/ozsp12)  
<a href="https://br.linkedin.com/in/ozsp12"><img src="https://api.iconify.design/mdi:linkedin.svg?color=%230A66C2" height="22" alt="LinkedIn" align="absmiddle"></a> **LinkedIn:** [https://br.linkedin.com/in/ozsp12](https://br.linkedin.com/in/ozsp12)  
<a href="https://substack.com/@olsp1982"><img src="https://cdn.simpleicons.org/substack/FF6719" height="22" alt="Substack" align="absmiddle"></a> **Substack:** [https://substack.com/@olsp1982](https://substack.com/@olsp1982)  
<a href="https://medium.com/@ozsp12"><img src="https://cdn.simpleicons.org/medium/888888" height="22" alt="Medium" align="absmiddle"></a> **Medium:** [https://medium.com/@ozsp12](https://medium.com/@ozsp12)  
<a href="https://www.youtube.com/@ozlsp12"><img src="https://cdn.simpleicons.org/youtube/FF0000" height="22" alt="YouTube" align="absmiddle"></a> **YouTube:** [https://www.youtube.com/@ozlsp12](https://www.youtube.com/@ozlsp12)  
<a href="https://x.com/ozsp12"><img src="https://cdn.simpleicons.org/x/888888" height="22" alt="X" align="absmiddle"></a> **X:** [https://x.com/ozsp12](https://x.com/ozsp12)
