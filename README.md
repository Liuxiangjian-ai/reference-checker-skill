# Reference Checker Skill v1.3

An exhaustive pre-submission reference verification skill for checking manuscript reference lists before journal submission.

## What it does

This skill forces item-by-item reference auditing rather than sample-based checking. It checks whether each reference is real, accurate, complete, and formatted consistently.

## v1.3 update

The per-reference audit table now includes bibliographic identification fields:

- Submitted title
- Submitted authors
- Submitted source / journal
- Year
- DOI / PMID

This makes it easier for users to verify results without repeatedly returning to the original reference list.

## Key features

- Exhaustive audit by default
- Batch-by-batch processing for long reference lists
- Explicit continuation prompt when references remain unchecked
- Final completion message when all references are checked
- Cumulative summary of all problematic references
- Severity categories: Critical, Major, Minor, Manual check
- No Python or external script dependency

## Suggested use

Ask:

> Please use the reference-checker skill to audit all references exhaustively. Do not sample. For each reference, include title, authors, journal, year, DOI/PMID, verification route, match quality, status, confidence, and suggested fix.

