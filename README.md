# Daily Vocab Agent

A reusable Codex skill that coordinates two sequential bots:

1. Translate English text or images into Chinese and extract CET-4-and-above vocabulary.
2. Deduplicate the vocabulary and update a configured vocabulary app, defaulting to the `日常积累` list.

Each vocabulary record contains an English term, a context-appropriate Chinese meaning, and IPA. Newly updated entries are ordered before older entries by update time.

The workflow also enforces a release check: every imported entry receives a batch timestamp, offline caches are versioned when data changes, and the live target list is opened after deployment to confirm the new batch appears first.

## Install

Copy this repository into your personal Codex skills directory, then start a new Codex chat:

```text
~/.codex/skills/daily-vocab-agent/
```

Configure your app target in `references/app-target.md` before enabling Bot 2.

## Use

Attach English text or an image and invoke:

```text
$daily-vocab-agent Translate this content, extract CET-4-and-above vocabulary, and add it to 日常积累.
```

You can also request translation or vocabulary extraction without updating an app.

## Privacy

This public package contains no personal app data, credentials, access tokens, or machine-specific paths.
