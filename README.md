# Changelog Generator Skill

A [Claude Code](https://docs.anthropic.com/en/docs/claude-code) skill that transforms technical git commits into polished, user-friendly changelogs.

## What It Does

- Scans git history for a specific time period or between versions
- Categorizes changes into features, improvements, bug fixes, breaking changes, and security
- Translates developer-facing commits into customer-friendly language
- Filters out internal noise (refactoring, tests, CI changes)
- Verifies library/framework details using live documentation lookups

## Usage

Install as a Claude Code skill, then from any git repository:

```
Create a changelog from commits since last release
```

```
Generate changelog for all commits from the past week
```

```
Create release notes for version 2.5.0
```

```
Create a changelog for commits since v2.4.0, using my changelog guidelines from CHANGELOG_STYLE.md
```

## Installation

Add this skill to your Claude Code configuration:

```bash
claude mcp add-skill changelog-generator https://github.com/adityamparikh/changelog-generator-skill
```

Or clone into your skills directory:

```bash
git clone https://github.com/adityamparikh/changelog-generator-skill.git ~/.claude/skills/changelog-generator
```

## License

MIT
