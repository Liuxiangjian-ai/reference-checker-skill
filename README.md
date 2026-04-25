# Reference Checker Skill

**An exhaustive pre-submission reference verification skill for scholarly manuscripts.**

Reference Checker Skill helps researchers, students, editors, and academic writers audit manuscript references before journal submission.  
It is designed to reduce fake citations, DOI mismatches, incorrect metadata, duplicated references, and AI-generated reference errors.

Unlike lightweight citation checkers that only sample a few references, this skill is designed for **item-by-item exhaustive verification**.

---

## Why this skill?

Reference errors are easy to miss but costly during submission.

Common problems include:

- fabricated or non-existent references
- DOI pointing to the wrong article
- incorrect article titles
- wrong journal names
- mismatched year, volume, issue, or page numbers
- duplicated references
- preprints cited when a peer-reviewed version already exists
- inconsistent reference formatting
- AI-generated references that look plausible but are not real

This skill forces the AI to audit **every reference**, not just the suspicious ones.

---

## Key Features

- **Exhaustive reference checking**  
  Every reference must be reviewed individually unless the user explicitly requests sampling.

- **Structured metadata verification**  
  Checks title, authors, journal/source, year, DOI, PMID, volume, issue, and pages.

- **Batch-by-batch workflow for long reference lists**  
  If the reference list is too long, the skill reports which references were checked in the current round and asks whether to continue.

- **Clear severity labels**  
  Problems are classified as:
  - `Critical`
  - `Major`
  - `Minor`
  - `Manual check`

- **Final problem summary**  
  When the full audit is complete, the skill summarizes all problematic references in one place.

- **Human-review friendly tables**  
  Each output table includes the submitted title, authors, journal/source, year, DOI/PMID, verification route, match quality, status, confidence, and suggested fix.

- **No Python dependency**  
  This is a pure prompt-based skill. No scripts or external setup are required.

---

## What it checks

For each reference, the skill attempts to verify:

| Field | Checked |
|---|---|
| Reference existence | Yes |
| Article title | Yes |
| Authors | Yes |
| Journal / source | Yes |
| Publication year | Yes |
| Volume / issue | Yes |
| Page range / article number | Yes |
| DOI | Yes |
| PMID / PMCID | When available |
| Duplicate references | Yes |
| Preprint vs published version conflict | Yes |
| Retraction or source risk | When detectable |

---

## Recommended Use Cases

This skill is especially useful for:

- journal manuscript submission
- review articles with long reference lists
- biomedical and life science manuscripts
- AI-assisted academic writing
- reference lists reformatted by citation managers
- checking references generated or modified by LLMs
- pre-submission editorial quality control

---

## Example Prompt

```text
Please use the Reference Checker Skill to audit the following reference list.

Requirements:
1. Check every reference item by item.
2. Do not sample.
3. Verify title, authors, journal, year, volume, issue, pages, DOI, and PMID if available.
4. Classify problems as Critical, Major, Minor, or Manual check.
5. If the list is too long, check it in batches and ask me whether to continue.
```

---

## Output Format

Each audit round includes a table like this:

| Ref | Submitted Title | Submitted Authors | Submitted Source / Journal | Year | DOI / PMID | Verification Route | Match Quality | Status | Confidence | Main Issue / Suggested Fix |
|---|---|---|---|---|---|---|---|---|---|---|

For long reference lists, the skill ends each round with a continuation message, for example:

```text
This round checked references 1–20. References 21–58 remain unchecked.
Would you like me to continue with the next round, references 21–40?
```

When all references have been checked, the skill provides a final summary:

```text
Reference audit complete.
```

Then it lists all references with Critical, Major, Minor, and Manual check issues.

---

## Severity Definitions

| Severity | Meaning |
|---|---|
| Critical | Likely fake reference, non-existent article, wrong DOI, or DOI points to a different article |
| Major | Real article, but important metadata is wrong |
| Minor | Formatting problem, incomplete field, capitalization issue, or style inconsistency |
| Manual check | Not enough evidence to verify confidently |

---

## Repository Structure

```text
reference-checker-skill/
├── SKILL.md
├── README.md
├── templates/
│   ├── report_template.md
│   └── correction_table_template.md
└── examples/
    ├── input_references.txt
    └── expected_output.md
```

---

## Installation

Download or clone this repository, then place the folder in your AI skill directory if your environment supports skill-based workflows.

The core file is:

```text
SKILL.md
```

You can also copy the contents of `SKILL.md` into a custom instruction, project instruction, or agent workflow.

---

## Important Note

This skill is designed to support reference verification, not to replace final human review.

For journal submission, users should manually confirm all references marked as:

- `Critical`
- `Major`
- `Manual check`

The skill is intentionally strict. If a reference cannot be confidently verified, it should be flagged rather than silently accepted.

---

## License

MIT License.
