# desktop-notice

Send a native desktop notification (Windows toast on WSL).

## Status

Pre-design: interface not yet specified; see [docs/design.md](docs/design.md).

## Layer

L1 (primitive). Works fully standalone.

## What it does

Shows a native desktop notification; on WSL, a Windows toast (nice-to-have). Takes `send --stdin-json` (a JSON object with `title`, `message`, `level`, `link`) or, for trusted human use, `send --title ... --message ...`. Levels are ordered `info < warn < action < error`. Escapes platform markup in title and message (no mentions, no link injection); links are only added via `link`/`--link`. Routing, quiet hours and dedup are notice-route's job; this tool only delivers.

## Indicative commands

Indicative, finalized in [docs/interface.md](docs/interface.md):

```text
desktop-notice send --stdin-json            # JSON object with title, message, level, link
desktop-notice send --title ... --message ... [--level info|warn|action|error] [--link URL]   # trusted human use
```

## Dependencies

- the platform's native notifier: binding: TBD (A/B/C), decided in this tool's design session

## Install

```text
uv tool install git+https://github.com/agent-workflow-kit/desktop-notice
```

## Documentation

- [awkit architecture](../awkit-docs/architecture.md) ([published](https://github.com/agent-workflow-kit/awkit-docs/blob/main/architecture.md))
- [awkit design guide](../awkit-docs/design-guide.md) ([published](https://github.com/agent-workflow-kit/awkit-docs/blob/main/design-guide.md))

## License

MIT — see LICENSE.
