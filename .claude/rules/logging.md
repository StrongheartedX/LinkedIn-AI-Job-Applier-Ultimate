
## Logs And Debug Artifacts

When debugging, agents should check `logs/` by default.

Primary log files:
- `logs/app.log` - general runtime/application log
- `logs/error_log.log` - error-focused log output
- `logs/internal_logger.log` - early logging before main logger setup
- `logs/llm_api_calls.yaml` - LLM request, token, and cost tracking

Additional runtime outputs:
- `data/debug/` - screenshots, HTML captures, and Playwright traces for debugging selector and interaction failures
- `data/output/` - `success.yaml`, `failed.yaml`, `skipped.yaml`, `interesting_jobs.yaml`, `skill_stat.yaml`, `last_run.yaml`, `resume_recommendations.txt`

If `DEBUG_MODE = True`, also inspect:
- `data/debug/*.png` - screenshots on selector or interaction failures
- `data/debug/*.html` - captured page HTML
- `data/debug/trace.zip` - Playwright trace, viewable in `https://trace.playwright.dev`

When a user asks about a runtime issue, inspect these locations before guessing.
