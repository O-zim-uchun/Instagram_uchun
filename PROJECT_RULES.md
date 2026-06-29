# Project Rules

These rules are mandatory for all future development in Instagram_uchun.

## Architecture and Design

- Use clean architecture principles.
- Keep the design modular and easy to test.
- Every module must have a single responsibility.
- Keep handlers thin; move business logic into services or analysis modules.
- Keep `core/` limited to shared contracts, dependency wiring, lifecycle primitives, and cross-module abstractions.
- Keep analysis responsibilities separated by domain: scene detection, dialog detection, action detection, emotion detection, viral scoring, timeline, and preview.
- Keep service responsibilities separated by domain: Telegram, FFmpeg, progress, cleanup, and storage.
- Avoid placeholder code and unused abstractions.
- Do not install unnecessary libraries.
- Do not write business logic until the feature requirements are defined.

## Language, Localization, and User Interface

- User-facing bot UI text must be in Uzbek only.
- All future user-facing UI text must live in `locales/uz.yaml`.
- Python code must reference locale keys instead of hardcoded user-facing strings.
- No hardcoded user-facing strings are allowed in Python code.
- Use inline keyboards whenever possible.
- Inline keyboard labels must come from the localization layer.
- Progress messages must always be edited instead of sending repeated new messages.
- Bot responses must be clear, actionable, and suitable for an admin user.

## Long Operations

- The bot must never stay silent during long operations.
- Every long task must support cancellation.
- Long tasks must report progress through edited messages.
- Temporary files must always be deleted after use.
- Failures must include detailed error reporting for troubleshooting.

## Security and Access

- Bot access must be admin-only.
- Do not expose internal details to unauthorized users.
- Do not hardcode secrets, IDs, tokens, URLs, or runtime configuration values.
- Configuration must be provided only through `.env` values.

## Code Quality

- Type hints are required for Python code.
- Docstrings are required for modules, classes, and public functions.
- Logging is required for important operations and errors.
- No hardcoded values are allowed.
- Keep functions and modules focused on one responsibility.
- Prefer explicit names over vague abbreviations.

## Configuration

- Use `.env` for all runtime configuration.
- Keep `.env.example` updated whenever configuration keys are added.
- Never commit real `.env` files or secrets.

## Logging and Errors

- Log important lifecycle events, long-running task progress, cleanup actions, and exceptions.
- Error reports should include enough context to debug the issue.
- Do not silently ignore exceptions.
