# Architecture

This document defines the intended architecture for Instagram_uchun. The project currently contains documentation and folder structure only; implementation details will be added when development begins.

## Architectural Principles

- Clean architecture boundaries.
- Single responsibility per module.
- Modular and testable design.
- Configuration through environment variables only.
- User-facing Telegram UI text loaded from locale files only.
- Admin-only access by default.
- Observable behavior through structured logging.
- Safe handling and cleanup of temporary resources.

## High-Level Layers

### Core Layer

The `core/` package is reserved for application-wide primitives such as dependency wiring, shared interfaces, lifecycle contracts, and cross-module abstractions. It must not contain business workflows or Telegram handler logic.

### Bot Layer

The `bot/` package is reserved for Telegram application startup, router registration, lifecycle management, and integration of handlers, middlewares, states, keyboards, and services.

### Handler Layer

The `handlers/` package will receive Telegram updates, validate user intent, call the appropriate service or analysis module, and return Uzbek-language responses through locale keys and Telegram messages or inline keyboards.

### Service Layer

The `services/` package contains operational services and external integrations. Services should be independent from Telegram-specific update objects whenever possible.

### Analysis Layer

The `analysis/` package contains feature-specific AI analysis domains. Each submodule owns one analysis responsibility and must not mix unrelated concerns.

### Presentation Support Layer

The `keyboards/`, `locales/`, and `assets/` folders support the user-facing experience. User-facing strings must live in locale files, reusable inline keyboards must be centralized, and static design/runtime assets must be separated from Python code.

## Folder Purposes

| Folder | Purpose |
| --- | --- |
| `.github/` | GitHub project metadata and automation-related files. |
| `.github/ISSUE_TEMPLATE/` | Future issue templates for structured reports and feature requests. |
| `core/` | Application-wide contracts, dependency wiring, shared abstractions, and lifecycle primitives. |
| `bot/` | Telegram bot application setup and lifecycle modules. |
| `handlers/` | Telegram update handlers grouped by feature or responsibility. |
| `services/` | Operational service packages and external integrations. |
| `analysis/` | AI analysis domain packages. |
| `keyboards/` | Reusable inline keyboard definitions. |
| `middlewares/` | Cross-cutting request/update processing. |
| `states/` | Conversation state definitions. |
| `utils/` | Small reusable helper utilities. |
| `config/` | Environment configuration loading and validation. |
| `models/` | Shared data models and schemas. |
| `assets/` | Static assets used by documentation, design, or future runtime workflows. |
| `locales/` | Localized user-facing UI text; Uzbek text belongs in `locales/uz.yaml`. |
| `logs/` | Local runtime logs; log files are ignored by Git. |
| `temp/` | Temporary runtime files; contents must be deleted after use and ignored by Git. |
| `tests/` | Automated tests. |
| `docs/` | Additional project documentation grouped by topic. |

## Analysis Domains

| Folder | Responsibility |
| --- | --- |
| `analysis/scene_detector/` | Future scene detection analysis. |
| `analysis/dialog_detector/` | Future dialog and speech/dialogue detection analysis. |
| `analysis/action_detector/` | Future action and activity detection analysis. |
| `analysis/emotion_detector/` | Future emotion detection analysis. |
| `analysis/viral_score/` | Future viral scoring and ranking analysis. |
| `analysis/timeline/` | Future timeline segmentation and event mapping. |
| `analysis/preview/` | Future preview generation analysis and recommendations. |

## Service Domains

| Folder | Responsibility |
| --- | --- |
| `services/telegram/` | Telegram API interaction helpers and delivery services. |
| `services/ffmpeg/` | Future media processing integration boundary for FFmpeg operations. |
| `services/progress/` | Progress reporting, edited-message updates, and cancellation coordination. |
| `services/cleanup/` | Temporary file cleanup and resource disposal workflows. |
| `services/storage/` | Future storage abstraction for local or remote persistence. |

## Documentation Domains

| Folder | Responsibility |
| --- | --- |
| `docs/architecture/` | Architecture decisions and deeper technical design notes. |
| `docs/development/` | Development setup, coding workflow, and contributor guidance. |
| `docs/design/` | Product, UX, and interaction design notes. |
| `docs/workflow/` | Operational workflows and process documentation. |

## Localization and UI Text Flow

1. User-facing text is defined as Uzbek locale keys in `locales/uz.yaml`.
2. Python code references locale keys and must not hardcode user-facing strings.
3. Handlers or presentation services resolve locale keys before sending Telegram messages.
4. Inline keyboards should use localized labels from the same locale source.
5. Tests should verify that new user-facing flows do not introduce hardcoded UI text.

## Telegram Bot Data Flow

1. Telegram sends an update to the bot application.
2. Middlewares validate cross-cutting requirements such as admin access and logging context.
3. A handler receives the validated update and determines the user intent.
4. The handler resolves any required Uzbek UI text from `locales/uz.yaml`.
5. The handler delegates business work to services or analysis modules.
6. Long-running tasks use the progress service to edit progress messages instead of sending repeated new messages.
7. The task supports cancellation and reports meaningful progress until completion or failure.
8. Cleanup services delete temporary files created during processing.
9. Results or detailed errors are returned to the administrator in Uzbek.
10. Operational events and errors are written to logs.

## Telegram Bot Architecture

The Telegram bot should be organized around routers or equivalent handler groups. Handlers must remain thin and delegate complex work to service and analysis modules. Middlewares must protect the bot before handlers execute. Keyboards should be reusable and centralized to keep UI behavior consistent.

The bot must never stay silent during long operations. Any workflow that takes noticeable time must provide progress feedback by editing an existing message and must expose a cancellation path.
