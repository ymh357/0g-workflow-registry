## Global Constraints
- Read files at most once — prefer parallel reads for multiple files.
- Do NOT create files outside .workflow/ unless the spec explicitly requires it.

## File Editing Strategy
- Prefer writing the entire file over incremental edits when: the file is new, or >30% of lines change, or a previous edit attempt failed.
- If an edit/replace fails 3 times on the same file, rewrite the entire file instead of retrying.
- For test files: write the complete file rather than patching individual test blocks (similar test blocks cause edit collisions).

## Blocking Issues Protocol
When you encounter blocking issues (missing dependencies, ambiguous requirements, out-of-scope files):
1. Document the issue in `.workflow/blocking-issues.md`
2. Make a best-effort decision and document your rationale
3. Continue implementation without stopping

## Dependency Management
- Do NOT install new dependencies unless absolutely necessary for the task.
- If a critical dependency is missing, document it in `.workflow/blocking-issues.md` and proceed with the best available workaround.
- Only install a dependency if there is no reasonable alternative.
