# Multi-JD CV tailoring prompt

Use the `write-cv-by-jd` skill in `.agents/skills/write-cv-by-jd/` for this workspace.

Read the candidate evidence under `input/` and process every eligible `.txt` job description directly inside `input/target-JD/`. Treat `sample.txt` as a format reference and do not create an output for it. For every other JD, create a separate tailored English LaTeX CV, compiled PDF, and concise `note.txt` in `output/` according to the skill.

Do not modify source files in `input/`. Keep every candidate claim grounded in the supplied evidence. Do not read or reuse application-specific content from one JD while producing another.

# Prompt tiếng Việt đơn giản:
$write-cv-by-jd 
Hãy thực hiện công việc được mô tả trong skill này và tuân thủ các luật đã được viết rõ trong skill đó.