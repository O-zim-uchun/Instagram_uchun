# Architecture

This document defines the intended architecture for Instagram_uchun. The project currently contains documentation and folder structure only; implementation details will be added when development begins.

## Architectural Principles

- Clean architecture boundaries
- Single responsibility per module
- Modular and testable design
- Configuration through environment variables only
- Admin-only access by default
- Observable behavior through structured logging
- Safe handling and cleanup of temporary resources

## Module Responsibilities

### Bot Layer

The bot layer will be responsible for Telegram application startup, router registration, lifecycle management, and integration of handlers, middlewares, states, keyboards, and services.

### Handler Layer

Handlers will receive Telegram updates, validate user intent, call the appropriate service or analysis module, and return Uzbek-language responses through Telegram messages or inline keyboards.

### Service Layer

Services will contain integrations and business workflows that are independent from Telegram-specific update objects whenever possible.

### Analysis Layer

Analysis modules will contain AI-related processing steps, orchestration rules, and future analysis pipelines. Long-running analysis tasks must report progress, support cancellation, and produce detailed errors when needed.

### Keyboard Layer

Keyboard modules will define reusable inline keyboards. Inline keyboards should be preferred whenever they improve clarity or reduce unnecessary text commands.

### Middleware Layer

Middlewares will enforce cross-cutting behavior such as admin-only access, logging context, rate limiting if required, and request validation.

### State Layer

State modules will define conversation states and finite-state-machine workflows when multi-step interactions are required.

### Utility Layer

Utilities will contain small reusable helpers that do not belong to a specific feature module. Utilities must not become a dumping ground for unrelated business logic.

### Configuration Layer

Configuration modules will load and validate environment-based settings. No hardcoded runtime values should be used.

### Model Layer

Models will define shared data structures, schemas, or persistence entities if persistence becomes necessary.

## Folder Purposes

| Folder | Purpose |
| --- | --- |
| `.github/` | GitHub project metadata and automation-related files. |
| `.github/ISSUE_TEMPLATE/` | Future issue templates for structured reports and feature requests. |
| `bot/` | Telegram bot application setup and lifecycle modules. |
| `handlers/` | Telegram update handlers grouped by feature or responsibility. |
| `services/` | Business services and external integrations. |
| `analysis/` | AI analysis workflows and processing pipelines. |
| `keyboards/` | Reusable inline keyboard definitions. |
| `middlewares/` | Cross-cutting request/update processing. |
| `states/` | Conversation state definitions. |
| `utils/` | Small reusable helper utilities. |
| `config/` | Environment configuration loading and validation. |
| `models/` | Shared data models and schemas. |
| `logs/` | Local runtime logs; log files are ignored by Git. |
| `temp/` | Temporary runtime files; contents must be deleted after use and ignored by Git. |
| `tests/` | Automated tests. |
| `docs/` | Additional project documentation. |

## Data Flow

1. Telegram sends an update to the bot application.
2. Middlewares validate cross-cutting requirements such as admin access and logging context.
3. A handler receives the validated update and determines the user intent.
4. The handler delegates business work to services or analysis modules.
5. Long-running tasks edit progress messages instead of sending repeated new messages.
6. The task supports cancellation and reports meaningful progress until completion or failure.
7. Temporary files created during processing are deleted.
8. Results or detailed errors are returned to the administrator in Uzbek.
9. Operational events and errors are written to logs.

## Telegram Bot Architecture

The Telegram bot should be organized around routers or equivalent handler groups. Handlers must remain thin and delegate complex work to service and analysis modules. Middlewares must protect the bot before handlers execute. Keyboards should be reusable and centralized to keep UI behavior consistent.

The bot must never stay silent during long operations. Any workflow that takes noticeable time must provide progress feedback by editing an existing message and must expose a cancellation path.
