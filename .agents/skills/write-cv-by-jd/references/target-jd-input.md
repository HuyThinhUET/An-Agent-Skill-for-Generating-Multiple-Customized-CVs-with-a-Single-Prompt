# Target-JD input files

`input/target-JD/sample.txt` is the format reference. Do not process it. On each run, enumerate the other immediate `.txt` files in `input/target-JD/`; ignore subdirectories and every non-`.txt` file.

Read JD files as UTF-8. The normal headings are:

```text
Tên chương trình/ công ty tuyển dụng:
Vị trí muốn ứng cử:
Link thông tin của chương trình tuyển dụng:
JD chi tiết:
```

Fields are optional. Empty, missing, reordered, or variably spaced headings must not stop the pipeline. Extract only what is actually present; unlabeled text can count as JD detail when it clearly describes the opportunity. Treat the program-information link as an additional source for the web-research pass, not as verified candidate evidence.

If the company/program field is absent, use the JD stem only for the missing output-directory component. If the position is absent, use an explicit title found in the JD or its meaningful stem for naming, but do not invent a role. If the detailed JD is absent, tailor only to the verified company/program and role information that remains.

Skip a file, with a concise handoff explanation, only when it contains no meaningful company/program, role, link, or substantive JD text. Do not create a speculative CV for an empty or unusable file. Process every other eligible `.txt` file through the full pipeline.
