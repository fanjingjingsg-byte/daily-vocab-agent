# App configuration and data rules

## Required configuration

Before Bot 2 runs, configure these values for your own vocabulary app:

- `APP_PROJECT_ROOT`: absolute path to the local app project.
- `APP_DATA_FILE`: vocabulary data file relative to the project root, such as `app/words.json`.
- `APP_PAGE_FILE`: page or list logic relative to the project root, such as `app/page.tsx`.
- `APP_URL`: current published app URL.
- `HOSTING_PROJECT_ID_SOURCE`: file or command that returns the existing hosting project ID.
- `DEFAULT_TRACK`: defaults to `日常积累`.
- `DEFAULT_CATEGORY`: defaults to `日常积累`.

Keep personal paths, credentials, tokens, and private URLs out of a public copy of this skill.

## Suggested data structure

```json
{
  "id": "daily-20261106-example",
  "term": "example",
  "meaning": "例子；实例",
  "ipa": "/ɪɡˈzɑːmpəl/",
  "speech": "example",
  "category": "日常积累",
  "track": "日常积累",
  "updatedAt": "2026-11-06T10:30:00+08:00"
}
```

Do not change an existing entry's ID, because user favorites or learning progress may depend on it.

## Deduplication and ordering

- Deduplication key: `term.trim().toLocaleLowerCase()`.
- Deduplicate only within the target track; the same term may appear in another track for a different learning purpose.
- For an existing target entry, update `meaning`, `ipa`, `speech`, and `updatedAt` from the newly verified source.
- After filtering, sort by `updatedAt` descending. Put undated legacy entries after dated entries while retaining their original relative order.

## Bot handoff

Bot 1 must send only verified vocabulary entries to Bot 2. JSON is preferred. For spreadsheet handoff, use the exact headers `英文单词`, `中文释义`, and `音标`.

