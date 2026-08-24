# LinkedIn AI Job Applier Ultimate - CLAUDE.md

## Project Overview

AI-powered job application bot that automates job search, resume generation, and form filling using Playwright browser automation and LLM integration. Supports **LinkedIn** and **Indeed**. Active fork of [Jobs_Applier_AI_Agent_AIHawk](https://github.com/feder-cr/Jobs_Applier_AI_Agent_AIHawk).

## Project Overview

AI-powered job application bot for LinkedIn and Indeed using Playwright browser automation, LLM-based job evaluation and form answering, and resume generation.

Primary entry point:
- `main.py`

Core areas:
- `src/job_manager/` - authentication, search, job parsing, Easy Apply flow
- `src/llm/` - LLM integration and prompts
- `src/resume_builder/` - resume generation
- `src/pydantic_models/` - config and data validation
- `src/utils/` - browser and shared helpers
- `src/telegram/` - notifications and error reporting

## Running Commands

Always use `uv run` to execute Python files within the project environment:

```bash
uv run python main.py
uv run python <python_file_name>
uv run pytest tests/
```

## Architecture

`src/job_manager/` has abstract base classes (`BaseJobManager`, `BaseEasyApplier`) with platform-specific subpackages for LinkedIn and Indeed. The active platform is selected at runtime via `JOB_SITE` in `app_config.py`:

```python
if JOB_SITE == "indeed":
    from src.job_manager.indeed.authenticator import IndeedAuthenticator as Authenticator
    ...
else:  # "linkedin"
    from src.job_manager.linkedin.authenticator import LinkedInAuthenticator as Authenticator
    ...
```
Both easy applier implementations cache question answers in `data/output/answers.yaml` and consult the cache before calling the LLM.

## Project rules

See `.claude/rules/` directory for detailed rules.

## Debugging Artifacts

When debugging runtime or browser issues, inspect `data/debug/` for screenshots, captured HTML, and Playwright traces.
