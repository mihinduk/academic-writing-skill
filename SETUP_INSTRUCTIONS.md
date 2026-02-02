# Installing the Academic Writing Skill in Claude Code

## Quick Setup

### 1. Create the Skill Directory Structure

In your terminal (before starting Claude Code), create the skill directory:

```bash
# Navigate to where Claude Code looks for user skills
# This varies by system - typically one of:
# macOS: ~/Library/Application Support/Claude/skills/user/
# Linux: ~/.config/Claude/skills/user/
# Windows: %APPDATA%/Claude/skills/user/

# Create the skill directory
mkdir -p ~/.config/Claude/skills/user/academic-writing

# Navigate to it
cd ~/.config/Claude/skills/user/academic-writing
```

### 2. Copy the Skill Files

Download or copy these files into the `academic-writing` directory:

```
academic-writing/
├── SKILL.md                                    # Main skill documentation
├── journal_specs/
│   └── bmc_bioinformatics.json                # BMC Bioinformatics requirements
└── templates/
    └── methods_bioinformatics.md              # Methods section template
```

### 3. Verify Installation

Start Claude Code from any directory:

```bash
claude
```

Then ask:
```
Do you have the academic-writing skill available? If so, list its capabilities.
```

Claude should be able to read the skill and describe its features!

---

## Full Setup with Scripts (Optional)

For the complete experience with automation scripts, you can extend the skill:

### Directory Structure

```
~/.config/Claude/skills/user/academic-writing/
├── SKILL.md
├── scripts/
│   ├── init_paper.py
│   ├── compile_manuscript.py
│   ├── reformat.py
│   └── citation_manager.py
├── journal_specs/
│   ├── bmc_bioinformatics.json
│   ├── bioinformatics.json
│   ├── plos_computational_biology.json
│   └── nature_methods.json
└── templates/
    ├── methods_bioinformatics.md
    └── reference_formats.json
```

### Creating Additional Journal Specs

Copy the `bmc_bioinformatics.json` template and modify for other journals:

```bash
cd ~/.config/Claude/skills/user/academic-writing/journal_specs/

# Create Bioinformatics journal spec
cp bmc_bioinformatics.json bioinformatics.json
# Edit bioinformatics.json with journal-specific requirements
```

Key differences for Bioinformatics journal:
- Application Notes format (2-3 pages)
- Very concise methods
- Supplementary methods allowed
- Different section structure

---

## Using the Skill

### Manual Method (Recommended to Start)

1. **Navigate to your paper directory:**
```bash
cd "/Users/handley_lab/Handley Lab Dropbox/virome/Diamond_lab_isolate_seq/2025_07_03_Diamond_NovaSeq_N1027/paper/"
```

2. **Start Claude Code:**
```bash
claude
```

3. **Ask Claude to use the skill:**
```
Using the academic-writing skill, help me create a methods section 
for VICAST following BMC Bioinformatics requirements. Review the 
current VICAST code/documentation and write an accurate methods 
section with proper citations.
```

Claude will:
- Read the academic-writing skill
- Check BMC Bioinformatics requirements
- Review your VICAST code/docs
- Generate methods with [REF:key] citation markers
- Use the docx skill to create a formatted Word document

### Automated Method (After Creating Scripts)

Once you've created the Python scripts referenced in SKILL.md:

```bash
# Initialize paper structure
python ~/.config/Claude/skills/user/academic-writing/scripts/init_paper.py \
    --journal "BMC Bioinformatics" \
    --title "VICAST" \
    --directory ./vicast_paper

# Work with Claude Code to write sections
cd vicast_paper
claude

# Then in Claude Code:
# "Write the methods section in sections/methods.md"
# "Add citations to references.bib"

# Compile final document
python ~/.config/Claude/skills/user/academic-writing/scripts/compile_manuscript.py \
    --output manuscript.docx
```

---

## Creating Citation Database

### Sample references.bib

Create a `references.bib` file in your paper directory:

```bibtex
@article{blast,
  author = {Altschul, Stephen F. and Gish, Warren and Miller, Webb and Myers, Eugene W. and Lipman, David J.},
  title = {Basic local alignment search tool},
  journal = {Journal of Molecular Biology},
  year = {1990},
  volume = {215},
  number = {3},
  pages = {403-410},
  doi = {10.1016/S0022-2836(05)80360-2}
}

@article{snpeff,
  author = {Cingolani, Pablo and Platts, Adrian and Wang, Le Lily and Coon, Melissa and Nguyen, Tung and Wang, Luan and Land, Susan J. and Lu, Xiangyi and Ruden, Douglas M.},
  title = {A program for annotating and predicting the effects of single nucleotide polymorphisms, SnpEff},
  journal = {Fly},
  year = {2012},
  volume = {6},
  number = {2},
  pages = {80-92},
  doi = {10.4161/fly.19695}
}

@article{lofreq,
  author = {Wilm, Andreas and Aw, Pauline Poh Kim and Bertrand, Denis and Yeo, Gracia Hui Ting and Ong, Swee Hoe and Wong, Charn Hui and Khor, Chiea Chuen and Petric, Rosemary and Hibberd, Martin L. and Nagarajan, Niranjan},
  title = {LoFreq: a sequence-quality aware, ultra-sensitive variant caller for uncovering cell-population heterogeneity from high-throughput sequencing datasets},
  journal = {Nucleic Acids Research},
  year = {2012},
  volume = {40},
  number = {22},
  pages = {11189-11201},
  doi = {10.1093/nar/gks918}
}

@misc{github_vicast,
  author = {Hinton, K. M. and Handley, S. A.},
  title = {VICAST: Viral Cultured-virus Annotation and SnpEff Toolkit},
  year = {2025},
  publisher = {GitHub},
  url = {https://github.com/mihinduk/VICAST},
  note = {Version 1.0}
}
```

---

## Quick Start Workflow for VICAST Paper

### Step 1: Set up paper directory
```bash
cd "/Users/handley_lab/Handley Lab Dropbox/virome/Diamond_lab_isolate_seq/2025_07_03_Diamond_NovaSeq_N1027/paper/"

# Create structure
mkdir -p sections figures output
touch references.bib
```

### Step 2: Start Claude Code
```bash
claude
```

### Step 3: Ask Claude
```
Using the academic-writing skill, help me write a methods section for 
VICAST for BMC Bioinformatics. 

First, read:
1. The academic-writing skill to understand journal requirements
2. The BMC Bioinformatics journal spec
3. The methods template for bioinformatics papers
4. The current VICAST repository (clone from https://github.com/mihinduk/VICAST.git)

Then create:
- sections/methods.md with [REF:key] citation markers
- references.bib with all cited software
- A compiled Word document using the docx skill

Follow BMC Bioinformatics requirements for:
- Software version reporting
- Parameter documentation
- Availability statement
- Numbered citation style
```

### Step 4: Review and Refine
Claude will generate the methods section and you can iterate:
```
Add more detail about the polyprotein handling algorithm
Include the QC thresholds in a more visible way
Add a citation for Biopython
```

### Step 5: Compile Final Document
```
Create the final Word document with proper BMC Bioinformatics formatting
```

---

## Troubleshooting

### Skill Not Found
If Claude Code says it can't find the skill:

1. Check the skill location:
```bash
ls -la ~/.config/Claude/skills/user/academic-writing/
```

2. Verify SKILL.md exists and is readable:
```bash
cat ~/.config/Claude/skills/user/academic-writing/SKILL.md
```

3. Try the full path in your request:
```
Read the skill at ~/.config/Claude/skills/user/academic-writing/SKILL.md
```

### Permission Issues
```bash
# Make sure you own the files
sudo chown -R $USER ~/.config/Claude/skills/user/

# Make sure they're readable
chmod -R u+r ~/.config/Claude/skills/user/
```

### Path Differences by OS

**macOS:**
```bash
~/Library/Application Support/Claude/skills/user/academic-writing/
```

**Linux:**
```bash
~/.config/Claude/skills/user/academic-writing/
```

**Windows:**
```
%APPDATA%\Claude\skills\user\academic-writing\
```

---

## Next Steps

1. **Install the skill** (copy files to skill directory)
2. **Verify it works** (ask Claude Code if it can see the skill)
3. **Create your first methods section** (for VICAST!)
4. **Extend as needed** (add more journals, create automation scripts)

Once working, you can use this skill for ALL your papers - just change the journal specification!
