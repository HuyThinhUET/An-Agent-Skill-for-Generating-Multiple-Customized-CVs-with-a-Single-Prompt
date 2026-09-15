---
name: write-cv-by-jd
description: "Create truthful, one-page, job-description-tailored LaTeX and PDF CVs from a candidate's local CV materials. Use for each target JD in a CV workspace; do not use for general resume advice without source files."
---

# Write CV by JD

Create one concise, ATS-readable CV for every target-JD file while keeping every claim supported by the candidate's supplied materials. The main artifact is the candidate-ready `.tex` and its compiled one-page `.pdf`, not a generic analysis.

## Workspace contract

Locate the workspace root from the folders below. Do not assume the current directory is the root.

```text
input/
  current-CV/                 existing CVs and source material
  CV-feedback/                HR feedback and writing guidance
  personal-information/       candidate facts
  Prism-data/                 existing templates and Prism exports
  projects-information/       project evidence and its summary/ cache
  target-JD/                  one file per role to tailor
output/                       final tailored CVs
```

Treat only the immediate `.txt` files in `input/target-JD/` as JD applications. Exclude `sample.txt` case-insensitively: it is a format reference and must never trigger web research, project summaries, drafting, or output. Read each remaining file according to [target-JD input](references/target-jd-input.md). Never modify the candidate's files under `input/`; create or update only project summaries and output artifacts.

## Per-JD isolation

Process eligible JD files one at a time in deterministic path order. The order is operational only: it must not affect the substance of any CV.

For each file, start a fresh application context containing only that JD, the common candidate evidence, current HR feedback, neutral project summaries, and web research performed for that employer/program and role. Do not read, compare, rank against, or reuse another target JD's requirements, company research, selected projects, draft wording, CV, output note, output filename, or reviewer feedback.

Project summaries are the sole shared cache because they record source-grounded facts about the candidate's work. They must remain role-neutral; re-check their cited source before using an important claim. Treat every tailored output and every application-specific research/evidence note as private to its own JD directory. Give independent reviewers only the current JD and its permitted evidence.

## Output paths and file names

Create one directory per application:

```text
output/<company-or-program>_<position>/
```

Derive `company-or-program` and `position` from the JD, preferring a named recruiting program when it is the application context. Use readable underscore-separated names, replacing characters that are unsafe in Windows paths. If either field is missing, use the JD's meaningful stem only for that missing field; do not guess a company or role.

Place the final source and PDF together in that directory with the same resolved basename:

```text
output/<company-or-program>_<position>/<resolved-basename>.tex
output/<company-or-program>_<position>/<resolved-basename>.pdf
output/<company-or-program>_<position>/note.txt
```

Resolve the basename in this strict order:

1. An explicit CV filename format or submission instruction in the current JD. Follow its field order, separators, capitalization, date requirements, and required extension. For the paired `.tex` artifact, use the same required base with `.tex`.
2. A filename requirement explicitly stated in current, authoritative recruitment or program instructions found during the web-research pass. An old, unofficial, or anecdotal post is not sufficient; it may only prompt a search for a current official instruction.
3. The default `<candidate-name>_<position>_CV`, using the candidate's official name from `personal-information/` in a compact ASCII-safe form. For this candidate and an AI Engineer Intern role, this is `TranHuyThinh_AI_Engineer_Intern_CV`.

Keep externally prescribed names within the application directory: remove any extension before creating the `.tex` pair and reject path separators or unsafe path components. Record the source and resolved value privately, and confirm the final output paths during handoff.

Create `note.txt` in every completed application directory. Keep it brief and actionable: include only material caveats the candidate should know before submission, such as an unverified or missing detail that was omitted, an unresolved submission requirement, or a non-default filename rule. Do not repeat normal build steps or private research logs. If there is no material caveat, its entire content must be exactly:

```text
CV is ready
```

## Evidence-first workflow

1. Read a JD first. Extract company, title, language, required and preferred skills, core responsibilities, seniority signals, keywords, and the evidence most worth foregrounding.
2. Read `current-CV/` and `personal-information/` next. Treat `current-CV/` as the primary, high-trust raw-content source: it contains the candidate's established claims, achievements, scope, outcomes, and metrics. Use it as the default source of identity, education, work history, achievements, links, project outcomes, and metrics. Its wording is a useful starting point, not a protected final draft: rewrite it for the current JD and the HR feedback. Use `personal-information/` to complete or clarify facts that the current CV does not cover.
3. Read `CV-feedback/` before drafting. Apply its advice when it does not conflict with a truthful, role-relevant one-page CV; otherwise retain the safer existing presentation.
4. Do not run broad web research by default. A detailed JD is normally sufficient for targeting. Use a short, official-source check only when it could resolve a submission filename requirement, clarify a named recurring program, or fill a material gap in a sparse JD; follow [web research](references/web-research.md). Stop once that narrow question is answered.
5. Use project summaries from `projects-information/summary/` before opening full project artifacts. Create or refresh the summaries as described in [project summaries](references/project-summaries.md). Open underlying reports, notebooks, README files, and supplied project links only when a relevant summary is missing, stale, or insufficient to substantiate a proposed bullet.
6. Maintain a private evidence map during drafting: every selected bullet must map to a supplied file and, when feasible, a line, page, cell, or link. Do not put the map in the final CV unless requested.

Do not invent experience, ownership, technologies, results, users, awards, dates, grades, publication status, ranking, or metrics. Prefer an accurate but less dramatic bullet to a potentially inflated one. Do not infer an implementation detail merely because it is common for the named technology. If evidence is incomplete, remove the claim, describe only what is verified, or retain a clearly supported prior-CV formulation.

Web research may improve prioritization and wording, but it is never evidence for a candidate claim. Do not state web-derived information, reviews, employer preferences, or past-program details in the CV as though they were the candidate's experience.

### Evidence precedence and preservation

For candidate-facing content, use this precedence unless the candidate explicitly corrects it:

1. `current-CV/` is the canonical raw-content frame and the first authority for the candidate's established claims, outcomes, metrics, and scope.
2. `personal-information/` supplements missing biographical or personal facts.
3. `CV-feedback/` guides presentation and targeting, but never overrides a true candidate fact.
4. `projects-information/` and Prism artifacts add useful detail, clarify methods, and support tailoring. They are supporting evidence, not a reason to replace, weaken, or omit a supported current-CV claim simply because a report is shorter, more technical, or does not repeat it.

Source priority governs facts, not prose. Start from the strongest relevant *claims* in the current CV, then paraphrase them for the current JD and the HR feedback. Preserve their substantive information and competitive signal: do not compress a strong experience or project claim into a generic task statement just to make it resemble the project report. Improve wording when it makes the claim easier for HR to scan, makes the verified result and beneficiary clearer, removes unnecessary jargon, or foregrounds a truthfully matched JD keyword. Use reports to make the existing claim clearer, add verified JD-relevant detail, or resolve genuine ambiguity. If a material factual contradiction would create a misleading CV, retain neither disputed version without a clear candidate-approved basis; record the concise caveat in `note.txt` instead of silently substituting a weaker claim.

## Drafting and targeting

Select the most appropriate existing `.tex` CV from `Prism-data/` as a visual and structural base when one is available; otherwise recreate only the minimum needed structure from the current CV. Copy the base to the output location and edit the copy.

### Mandatory output language

Write every candidate-facing CV sentence in clear, professional English, regardless of the JD's or source material's language. This includes the header, title, section labels, dates/labels, bullets, descriptions, and any explanatory text in the `.tex` and rendered PDF. Never output Vietnamese, including Vietnamese written without diacritics, or mix Vietnamese and English within a sentence. Preserve only official proper names, personal names, addresses, URLs, and source-code identifiers as needed. Write `note.txt` in English as well.

### Standing HR-feedback rules

Apply the non-conflicting rules extracted from `input/CV-feedback/feedback1.txt`:

- Preserve a tidy, clearly organized, one-page presentation that makes achievements and experience easy to scan.
- Write first for a time-constrained, non-technical HR reader. Each section must communicate the candidate's role, action, practical result, and JD relevance on a quick scan; technical reviewers can infer the deeper implementation from accurate keywords. Keep only necessary technical terms, pair unfamiliar terms with a plain-language purpose when space permits, and avoid jargon-heavy bullets or acronyms that obscure impact.
- Extract the JD's important keywords before drafting. Reuse only truthful, demonstrated keywords naturally across the title, skills, experience, and projects; do not keyword-stuff or add unsupported terms.
- **Outcome-first bullet test (mandatory):** Every Experience and Projects bullet must lead with a source-supported result, operational outcome, or practical purpose, and make clear who or what benefits when the evidence establishes one. Write the action and tools as the reason for that result, not as the whole message. Prefer a supported metric when available; otherwise use a verified qualitative outcome or capability (for example, detecting errors and producing correction suggestions for digitized documents). A task-only sentence such as "Developed X using Y" fails this test when the evidence supports what X achieved, enabled, or was for. Never invent a beneficiary, time saving, accuracy gain, adoption, or business impact merely to pass the test. If the evidence contains no outcome or purpose at all, select stronger evidence-backed content; if the claim must remain, state only the narrow verified capability and record the material limitation in `note.txt`.

Preserve the chosen base CV's section order, visual hierarchy, and overall layout. Tailoring should change relevance and wording, not redesign the CV. Apply these default content-shape rules unless the candidate explicitly asks to override them:

- **Education:** retain the base education content and structure. If one-page fit requires a cut, remove only the gifted-high-school GPA line before removing university education details.
- **Experience:** retain the base roles, dates, and bullet structure. Rebuild the descriptive wording from the verified current-CV facts so it passes the mandatory outcome-first bullet test, is more relevant to the JD, and is easier for HR to scan; do not add JD keywords unsupported by the evidence.
- **Achievements:** retain the three achievement bullets from the chosen base CV unchanged in wording and order.
- **Publications:** retain the base publication entry unchanged. Its explanatory sub-bullet may be paraphrased for relevance if it stays fully supported.
- **Projects:** show exactly two selected projects. Give each exactly three information-rich bullets, with each bullet fitting on one rendered line; therefore, each project has exactly three rendered description lines. A bullet must not wrap to a sparse second line. Keep each line meaningfully filled with substantiated detail and relevant JD keywords, but never add filler, keyword stuffing, or unsupported claims merely to fill space. During rendered review, if a project line has material unused width, revisit the selected project summary: add a source-supported JD keyword or a concise, interview-useful implementation, reliability, evaluation, or purpose detail when one is available. Phrase that added detail in HR-friendly language. If no JD-matched detail exists, use another verified detail that helps an IT interviewer understand the work without overwhelming HR; never pad with jargon or invent a claim.
- **Skills:** use four or five skill groups, with one rendered line per group.

Use the template's `\item` marker as the only list notation throughout the CV. Never create manual hyphen, en-dash, or em-dash pseudo-bullets, and never mix dash-led lists with bullet-marked lists. This applies to descriptions, achievements, publications, skills, and any nested list.

For each section, protect high-value facts already present in the current CV before adding report-derived technical detail. Experience is particularly important: begin from the current CV's concrete scope, ownership, results, and beneficiaries, then paraphrase so the revision is more specific, competitive, JD-relevant, and HR-clear than the source. Tailor by foregrounding the verified outcome and plain-language business or user value; never turn a strong contribution into an abstract list of tools, a vague team-only statement, or a lower-impact task description. A bullet that only lists what the candidate did is not acceptable when supported evidence can state what it produced, enabled, or was intended to help. Use a clear active verb and an unambiguous subject when needed to show the candidate's contribution, while avoiding repeated filler such as “the team.”

Run a lexical-variety pass after drafting. Paraphrase repeated lead verbs and result phrases across nearby bullets so the CV does not mechanically repeat words such as “Delivered” or “Enabled.” Preserve the exact evidence and outcome-first meaning; vary the sentence structure when useful (for example, lead with a verified metric, capability, or beneficiary rather than forcing another synonym). Do not use a thesaurus merely to sound different, and do not replace an accurate technical term that an HR or IT reader needs to recognize.

Rank content by the JD's needs and available evidence, but retain the current CV as the baseline of competitiveness. Make the title, summary (only if it adds information), technical skills, experience, projects, and achievements mutually reinforce the role. Use the JD's terminology naturally where it truthfully matches demonstrated work. Put the most relevant, substantiated work first; deprioritize unrelated content rather than stretching it to fit. Explain context, action, and result in compact bullets, leading with the strongest verified contribution and language a generalist HR screener can understand.

Keep the CV truly one page. First reduce redundancy, low-relevance bullets, and weak detail; then make modest wording changes while retaining the strongest verified claims. If this is still insufficient, use one consistent, legible font-size setting for every body bullet at the same typographic level across the entire CV. Never shrink only one project, one section, or an individual line. Do not solve overflow with unreadably small type, dense walls of text, clipped content, or deceptive margins. Preserve legible hierarchy, contact details, and links.

### Frozen layout guardrail

Treat the selected approved base CV's layout as frozen. Do not change section, heading, entry, project, list, line, margin, or paragraph spacing to fit content; do not add or alter global `titlesec`, `enumitem`, or `\vspace` settings after selecting the base. Keep its normal separation between every project title/technology line and its first bullet, and apply the same protection to publication sub-bullets. If content must fit differently, change content first and only then use the uniform typography fallback above. Change spacing only when the candidate explicitly requests it.

## Independent compliance audit

Write an initial draft, then run up to three audit-and-revision cycles (at most four drafts total). Stop early when no material violation remains.

When delegation is available, use a separate reviewer agent solely as a compliance auditor. Give it the JD, the candidate evidence needed to verify selected claims, the HR feedback, the relevant content and validation rules from this skill, and the draft—but not the writer's rationale or proposed fixes. It must report violations only, not rewrite the CV, rank alternative content, suggest new projects or keywords, or act as a content strategist.

The auditor must check every constrained content rule in this skill that applies to the draft: candidate-evidence support; truthful JD keyword use; outcome-first bullet test for every Experience and Projects bullet; HR readability and jargon limits; required section, bullet, project, achievement, publication, skills, and frozen-layout rules; ATS/list consistency; lexical repetition; and one-page/rendering risks. It must also flag a materially underfilled project bullet when the cited project summary contains an unused, source-supported detail relevant to the JD or useful for a technical interviewer. For each failure, report severity, the exact rule breached, the draft location, and the evidence citation. For the outcome-first audit, explicitly classify every Experience and Projects bullet as pass or fail and name the exact supported result, purpose, or beneficiary used to justify each pass. A result-free task statement must be failed unless the draft or `note.txt` records the evidence limitation required by the rule.

The auditor must receive no other JD, application-specific research, draft, output, or prior reviewer feedback. Revise only substantiated audit findings. An auditor cannot authorize new claims, and a pass cannot create evidence. If no independent reviewer is available, perform this same checklist as a clearly separated internal compliance audit; do not represent it as independent. Do not exceed three audits.

## Build and validate

Use the engine required by the selected template. Prefer `latexmk` for repeatable builds, or `pdflatex` when that is what the template supports. Compile with non-interactive, halt-on-error options. Resolve LaTeX source errors in the output copy, then rebuild until successful.

Verify all of the following for each JD:

- The `.tex` source and PDF exist at the expected output path.
- `note.txt` exists and is either the exact default text or contains only concise, material submission notes.
- The directory and basename follow the output naming precedence above.
- The final compilation has no fatal errors or unresolved source failures.
- The PDF is exactly one page. Use an available PDF page-count tool and, when possible, visually inspect a rendered page for clipping, overlapping text, broken icons, or illegible layout. Follow the PDF skill when it is available.
- The rendered Projects section has exactly two projects; each has exactly three bullet-marked, single-line description bullets and no sparse wrapped continuation line.
- In the rendered PDF, every project heading and its technology label are visually distinct from the first bullet below; no title, label, bullet marker, or bullet text may touch or overlap.
- Every list in the rendered PDF uses the same bullet marker; no manually typed dash-led pseudo-bullet remains.
- All candidate-facing text in the `.tex`, PDF, and `note.txt` is English-only, except necessary proper names, addresses, URLs, and source-code identifiers.
- The content is tailored to that JD and every material claim remains supported by the candidate evidence.

Keep temporary compiler files and rendered inspection files outside the final CV directory when practical. Leave the final `.tex` and `.pdf` easy to find. In the handoff, list the produced files, state any constrained omissions, and mention only material source fixes made to output copies.
