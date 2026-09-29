# Resume-to-Job Matching Tool

Scores how well a resume matches a job description using semantic similarity, and points out
exactly which required skills are missing -- built to replace manual resume screening.

## Problem
A recruiting team manually screens hundreds of resumes per job posting. This tool scores a
resume against a job description in seconds and produces a skill gap report a recruiter (or
candidate) can actually act on.

## What It Does
- Extracts recognizable skills from both resume and job description text against an 86-term
  skill taxonomy spanning tech, business/HR, finance, marketing, and other domains
- Embeds both texts with a free local sentence-transformer and scores semantic similarity
- Auto-selects a job posting the skill taxonomy can meaningfully engage with (scored by keyword
  hit count), instead of blindly grabbing the first row of a huge, randomly-ordered dataset
- Ranks every resume against the chosen job and reports a missing-skills gap per resume

## Real Results (real datasets -- 2,484 resumes, real LinkedIn job postings)
- Auto-selected job: **Administrative Coordinator** (18 of 86 tracked skills recognized in the
  posting text)
- Top match: an **Accountant** resume, **0.579 semantic similarity**, **50% skill coverage**
- Skill coverage across the top 10 matches ranged **22%-61%**, with specific, actionable missing
  skills reported per resume (e.g. `crm`, `payroll`, `database`, `excel`, `onboarding`)

## Tech Stack
Python, Sentence-Transformers, Scikit-learn, Pandas

## How to Run
Open in Google Colab, run all cells. Both datasets auto-download via `kagglehub` with a
synthetic fallback if either ever fails.

## Note
An earlier version of this project used a 17-term, tech-only skill list and always demoed
whichever job happened to be first in the (randomly ordered) postings file -- which sometimes
landed on a posting the skill list had zero overlap with, making the tool look broken even
though the underlying matching logic was fine. Expanding the taxonomy to 86 terms and having it
pick a job it can meaningfully score fixed that.
