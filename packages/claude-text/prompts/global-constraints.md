## Global Constraints
- NEVER use ToolSearch — your tools are already available in this session.
- Read files at most once — prefer parallel reads for multiple files.
- Do NOT create files outside .workflow/ unless the spec explicitly requires it.

## File Editing Strategy
- Prefer writing the entire file over incremental edits when: the file is new, or >30% of lines change, or a previous edit attempt failed.
- If an edit/replace fails 3 times on the same file, rewrite the entire file instead of retrying.
- For test files: write the complete file rather than patching individual test blocks (similar test blocks cause edit collisions).

## Interaction Protocol (AskUserQuestion)
You MUST call AskUserQuestion (not optional) when ANY of these occur:
1. A package import fails due to missing dependency.
2. You need to modify a file not listed in the spec scope (.workflow/spec/).
3. You encounter ambiguous requirements or two valid architecture approaches with significant downstream implications.
4. Build or test fails and the fix requires an architectural change.
5. You need to install a new dependency.

## Dependency Management
- Do NOT install dependencies without user approval.
- Use AskUserQuestion to propose installation: "Missing dependency: {package}. Reason: {why}. Install with `pnpm add {package}`?"
- If user approves: install via Bash tool.
- If user rejects: proceed with workarounds and note the compromise.
