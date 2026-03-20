---
title: Stop Fearing 3,000-Line PRs: A Chrome Extension for Honest PR Reviews
date: 2026-03-20 09:52:00
---

_Not all lines are created equal — so why does GitHub treat them that way?_

![](https://github.com/gjeanmart/gh-pr-line-breakdown/blob/main/docs/full.png?raw=true)

## The Problem

You open a pull request and see "+3,214 lines changed." Your heart sinks a little. Is this a massive architectural change? A risky refactor that will take an hour to review carefully?

Then you start scrolling. Half of it is `yarn.lock`. Another 800 lines are generated snapshots. The actual logic change is 180 lines buried somewhere in the middle.

GitHub's raw line count is a blunt instrument. It doesn't distinguish between lines a reviewer needs to think about and lines that are just noise. The result: reviewers either feel overwhelmed by a number that doesn't reflect real complexity, or they learn to ignore the count entirely — and sometimes miss things as a result.

The same problem shows up for PR authors. When you're trying to communicate the scope of your work, a diff bloated by lock files or generated code undersells the real change. The signal gets lost.

## The Solution

[GitHub PR Line Breakdown](https://chromewebstore.google.com/detail/github-pr-line-breakdown/llfndpapjbmogegbhbbjckaimmlpjgkc) is a Chrome extension that overlays a categorized line-count breakdown directly on GitHub PR pages, giving reviewers and authors an honest read of what's actually in the diff.

Install it, open any pull request, and you'll see a widget just above the Files Changed tab:

```
📊 Line Breakdown
████████░░░░░░░░░░░░  Main           180  (6%)
████░░░░░░░░░░░░░░░░  Tests          234  (7%)
████████████████████  Generated    2,800  (87%)
```

Now "3,214 lines changed" becomes "180 lines of real code" — a completely different review conversation.

### How it works

The extension uses configurable glob patterns to classify every file in the diff into a named category. Out of the box it covers the most common cases:

| Category       | Matched files                                                  |
| -------------- | -------------------------------------------------------------- |
| Main           | `src/**/*.ts`, `*.py`, etc. (fallback — everything else)       |
| Tests          | `**/*.spec.ts`, `**/*.test.ts`, `**/__tests__/**`              |
| Generated      | `**/yarn.lock`, `**/package-lock.json`, `**/*.snap`, `dist/**` |
| Documentation  | `**/*.md`, `docs/**`                                           |
| CI/CD          | `.github/**`, `*.yml`                                          |
| Infrastructure | `terraform/**`, `helm/**`, `**/Dockerfile`                     |
| Config         | `**/*.json`, `**/*.toml`, `**/*.env*`                          |
| Styles         | `**/*.css`, `**/*.scss`                                        |

Everything is fully configurable from the options page — add categories, change colors, adjust glob patterns to match your repo's layout.

### More than just a counter

Beyond the widget, the extension adds a few things that directly speed up the review:

**Color badges on file headers.** Each file in the diff gets a small color-coded badge showing which category it belongs to. You can tell at a glance which files are tests, which are config, and which are the ones that actually need close reading.

**Line counts in the file tree sidebar.** The PR sidebar now shows per-category line counts alongside each file, so you can triage the diff before you even start scrolling.

**Per-category show/hide filter.** One click to collapse all files matching a category — hide all generated files, or hide all tests — so you can focus on the part of the diff that matters most to you.

**GitHub API fallback.** On very large PRs where GitHub lazy-loads files, the extension falls back to the GitHub REST API. Just add a personal access token in the settings for higher rate limits.

## What's Coming

The extension is actively developed. The short-term roadmap includes:

- **Firefox support** — same extension, broader reach
- **GitLab and Gitea** — the problem isn't GitHub-specific
- **Repository-specific config** — store a `.gh-pr-breakdown.json` in your repo so teams share the same category setup without each person configuring it manually
- **LLM-assisted review** — longer-term, using the breakdown as context to surface which parts of a PR most need human attention

## Try It

The extension is live on the Chrome Web Store and free to install:

**[Install from the Chrome Web Store](https://chromewebstore.google.com/detail/github-pr-line-breakdown/llfndpapjbmogegbhbbjckaimmlpjgkc)**

The source is fully open on GitHub:

**[github.com/gjeanmart/gh-pr-line-breakdown](https://github.com/gjeanmart/gh-pr-line-breakdown)**

If you hit a bug, have a feature request, or want to contribute — [open an issue](https://github.com/gjeanmart/gh-pr-line-breakdown/issues). The roadmap is shaped by what people actually need, so feedback is genuinely useful.
