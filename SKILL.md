---
name: changelog-generator
description: Automatically creates user-facing changelogs from git commits by analyzing commit history, categorizing changes, and transforming technical commits into clear, customer-friendly release notes. Turns hours of manual changelog writing into minutes of automated generation.
allowed-tools: Bash(*), Glob(*), Grep(*), Read(*), WebFetch(*), WebSearch(*), mcp__claude_ai_Context7__*, mcp__plugin_context7_context7__*
---

# Changelog Generator

This skill transforms technical git commits into polished, user-friendly changelogs that your customers and users will actually understand and appreciate.

## When to Use This Skill

- Preparing release notes for a new version
- Creating weekly or monthly product update summaries
- Documenting changes for customers
- Writing changelog entries for app store submissions
- Generating update notifications
- Creating internal release documentation
- Maintaining a public changelog/product updates page

## Verify Library and Framework Usage

The model's training data has a knowledge cutoff. When changelog commits reference library upgrades, new framework features, or dependency changes, **actively verify** that descriptions are accurate:

1. **Identify versions** — Check `pom.xml`, `build.gradle.kts`, `package.json`, or other dependency files to determine the exact versions of libraries and frameworks mentioned in commits.
2. **Look up current documentation** — Use Context7 (`mcp__claude_ai_Context7__resolve-library-id` then `mcp__claude_ai_Context7__query-docs`) to retrieve up-to-date documentation for any library or framework where:
   - The version is newer than what the model may have been trained on
   - You need to accurately describe what a library upgrade or new feature does in user-friendly terms
3. **Search the web** — Use `WebSearch` and `WebFetch` to check for:
   - Release notes and changelogs for upgraded dependencies to accurately summarize what changed
   - Feature announcements that help translate technical commits into user-friendly language
4. **Check GitHub** — Use `gh` CLI to check release notes, changelogs, or issues for dependencies when needed (e.g., `gh api repos/{owner}/{repo}/releases/latest`)

**Do not assume** that a library feature or behavior is correct based solely on model knowledge. When in doubt, look it up.

## What This Skill Does

1. **Scans Git History**: Analyzes commits from a specific time period or between versions
2. **Categorizes Changes**: Groups commits into logical categories (features, improvements, bug fixes, breaking changes, security)
3. **Translates Technical → User-Friendly**: Converts developer commits into customer language
4. **Formats Professionally**: Creates clean, structured changelog entries
5. **Filters Noise**: Excludes internal commits (refactoring, tests, etc.)
6. **Follows Best Practices**: Applies changelog guidelines and your brand voice

## How to Use

### Basic Usage

From your project repository:

```
Create a changelog from commits since last release
```

```
Generate changelog for all commits from the past week
```

```
Create release notes for version 2.5.0
```

### With Specific Date Range

```
Create a changelog for all commits between March 1 and March 15
```

### With Custom Guidelines

```
Create a changelog for commits since v2.4.0, using my changelog
guidelines from CHANGELOG_STYLE.md
```

## Example

**User**: "Create a changelog for commits from the past 7 days"

**Output**:
```markdown
# Updates - Week of March 10, 2024

## ✨ New Features

- **Team Workspaces**: Create separate workspaces for different
  projects. Invite team members and keep everything organized.

- **Keyboard Shortcuts**: Press ? to see all available shortcuts.
  Navigate faster without touching your mouse.

## 🔧 Improvements

- **Faster Sync**: Files now sync 2x faster across devices
- **Better Search**: Search now includes file contents, not just titles

## 🐛 Fixes

- Fixed issue where large images wouldn't upload
- Resolved timezone confusion in scheduled posts
- Corrected notification badge count
```

**Inspired by:** Manik Aggarwal's use case from Lenny's Newsletter

## Tips

- Run from your git repository root
- Specify date ranges for focused changelogs
- Use your CHANGELOG_STYLE.md for consistent formatting
- Review and adjust the generated changelog before publishing
- Save output directly to CHANGELOG.md

## Related Use Cases

- Creating GitHub release notes
- Writing app store update descriptions
- Generating email updates for users
- Creating social media announcement posts
