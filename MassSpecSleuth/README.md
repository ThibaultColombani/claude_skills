# MassSpecSleuth — Claude Skill

A Claude skill that runs [MassSpecSleuth](https://github.com/ThibaultColombani/MassSpecSleuth), a mass spectrometry QC report generator, directly from Claude. Drop your search engine output files, and Claude will generate an interactive HTML quality-control report.

Supported search engines: **DIA-NN**, **Jmod**, **MaxQuant**, **Sage**, **FragPipe**, **ProteomeDiscoverer**.

Developed by [@thibaultcolombani](https://github.com/ThibaultColombani) — skill source: [claude_skills](https://github.com/ThibaultColombani/claude_skills)

---

## Prerequisites

- A Claude account (Free, Pro, Max, Team, or Enterprise)
- **Code execution** must be enabled in your Claude settings

### Enable code execution

- **Free / Pro / Max:** Go to [Settings > Capabilities](https://claude.ai/settings/capabilities) and toggle on **Code execution and file creation**.
- **Team / Enterprise:** An organization Owner must enable both **Code execution and file creation** and **Skills** in [Organization settings > Skills](https://claude.ai/admin-settings/skills).

---

## Installation

### Option A — Claude web (claude.ai)

Works on **macOS, Windows, and Linux** (any OS with a browser).

1. Download the `massspecsleuth.skill` file from the [releases](https://github.com/ThibaultColombani/claude_skills).
2. Go to [Customize > Skills](https://claude.ai/customize/skills).
3. Click the **"+"** button, then **"+ Create skill"**.
4. Select **"Upload a skill"**.
5. Upload the `massspecsleuth.skill` file.
6. Toggle the skill **on**.

### Option B — Claude Desktop (Cowork mode)

Requires [Claude Desktop](https://claude.ai/download) installed on your machine.

#### macOS

1. Download Claude Desktop from [claude.ai/download](https://claude.ai/download) or install via `brew install --cask claude`.
2. Open the `massspecsleuth.skill` file — Claude Desktop will prompt you to install it. Alternatively, go to **Customize > Skills > "+" > Upload a skill**.
3. Toggle the skill **on**.

#### Windows

1. Download Claude Desktop from [claude.ai/download](https://claude.ai/download).
2. Open the `massspecsleuth.skill` file — Claude Desktop will prompt you to install it. Alternatively, go to **Customize > Skills > "+" > Upload a skill**.
3. Toggle the skill **on**.

#### Linux

1. Download Claude Desktop from [claude.ai/download](https://claude.ai/download) (Debian/Ubuntu `.deb` package available).
2. Open the `massspecsleuth.skill` file or go to **Customize > Skills > "+" > Upload a skill**.
3. Toggle the skill **on**.

---

## Usage

Once the skill is installed and enabled, just ask Claude to generate a report. The skill triggers automatically when you mention MassSpecSleuth, mass spec QC, or any supported search engine.

### Example prompts

- *"Run MassSpecSleuth on my DIA-NN results"*
- *"Generate a QC report from these MaxQuant files"*
- *"I have Sage output, can you make a mass spec report?"*

### Workflow

1. **Upload your data** — Claude will ask you to upload your search engine output files. See the supported files table below.
2. **Specify your enzyme** *(optional)* — Claude will ask if you want to specify the enzyme used to cleave peptides (e.g., trypsin, lys-c).
3. **Wait for the report** — Claude clones MassSpecSleuth, installs dependencies, and runs the analysis in a sandboxed environment.
4. **Download** — The HTML report is shared directly in the chat for you to download.

### Supported files by search engine

| Search Engine | Required files | Optional files |
|---|---|---|
| **DIA-NN** | `*report*.parquet` or `report.tsv` | `features.tsv`, `fill_times.tsv`, `tic.tsv`, `sn.tsv` |
| **MaxQuant** | `evidence.txt` | `msms.txt`, `msmsScans.txt`, `allPeptides.txt`, `summary.txt`, `parameters.txt`, `msScans.txt` |
| **Sage** | `*.sage.tsv` | `lfq.tsv` |
| **FragPipe** | `psm.tsv` | — |
| **Jmod** | `all_IDs.csv` or `all_IDs_filtered.parquet` | — |
| **ProteomeDiscoverer** | `*PSMs*.txt` | `*ProteinGroups*.txt`, `*Proteins*.txt`, `*InputFiles*.txt` |

The tool auto-detects the search engine from the file names — you don't need to specify it.

### Opening the report

The report is a single HTML file. Open it in any modern browser (Chrome, Firefox, Safari, Edge). It requires an internet connection to load charts (Chart.js is fetched from a CDN).

---

## Supported enzyme filters

When prompted, you can choose from: `arg-c`, `asp-n`, `asp-n/d`, `bnps-skatole`, `chymotrypsin`, `chymotrypsin/p`, `clostripain`, `cnbr`, `elastase`, `formic-acid`, `glu-c`, `glu-c-bic`, `lys-c`, `lys-c/p`, `lys-n`, `ntcb`, `pepsin-ph2`, `pepsin-ph13`, `proteinase-k`, `thermolysin`, `trypsin`, `trypsin/p`, `v8`.

Multiple enzymes can be combined.

---

## Troubleshooting

**Claude doesn't use the skill** — Make sure the skill is toggled on in [Customize > Skills](https://claude.ai/customize/skills) and code execution is enabled. Try being explicit: *"Use MassSpecSleuth to generate a QC report."*

**"No supported data found"** — Check that your files are the direct output from a supported search engine. The tool auto-detects the engine from the file format.

**Report charts don't load** — The report needs internet access to load Chart.js from CDN. Open it in a browser with network access.

---

## Standalone Python tool

MassSpecSleuth also works as a standalone command-line Python tool, independent of Claude. Install and run it directly: [github.com/ThibaultColombani/MassSpecSleuth](https://github.com/ThibaultColombani/MassSpecSleuth)

---

## Links

- Skill source: [github.com/ThibaultColombani/claude_skills](https://github.com/ThibaultColombani/claude_skills)
- Python tool: [github.com/ThibaultColombani/MassSpecSleuth](https://github.com/ThibaultColombani/MassSpecSleuth)
- Claude skills documentation: [support.claude.com](https://support.claude.com/en/articles/12512180-use-skills-in-claude)
