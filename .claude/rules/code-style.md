## Code Standards

### Logging
```python
from config.logger_config import logger

logger.info("...")
logger.debug("...")
logger.warning("...")
logger.error("...", exc_info=True)
```

### Imports Order
1. Standard library
2. Third-party
3. Local (grouped by module)

### Error Handling
- Catch specific exceptions, never bare `except:`
- Log context (job URL, form field, etc.)
- Continue processing other jobs on single-job failures
- Use `src/telegram/telegram_error_handler.py` for critical errors

### Pydantic Validation
All config and data loaded through models in `src/pydantic_models/`:
- `Secrets`, `SearchConfig` — configuration
- `Job`, `JobManagerCache`, `Question` — job application data
- `ResumeStructure` — resume parsing
- `LLMCall` — LLM cost tracking

### Development Rules
- Use the centralized logger from `config/logger_config.py`
- Catch specific exceptions, not bare `except:`
- Log useful context like job URL, selector, field name, or current step
- Continue processing other jobs when one job fails unless the failure is global
- Keep prompts centralized in `src/llm/prompts.py`
- Validate config and structured data with Pydantic models in `src/pydantic_models/`
- Keep imports ordered as standard library, third-party, then local imports
