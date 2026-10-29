---
name: review-pull-request
description: >-
  Review a pull request or merge request with ThinkReview. Use when the user
  asks to review, check, or audit a GitHub, GitLab, Azure DevOps, or Bitbucket
  PR/MR URL, or asks Cursor to run ThinkReview on a change.
---

# Review a pull request

Use the ThinkReview MCP server and its `review_url_code` tool. ThinkReview fetches the changed files with the user's stored git credentials and returns a structured review: summary, suggestions, security notes, best practices, and follow-up questions.

## When to use it

Call `review_url_code` when the user provides or points at a pull request or merge request URL, including:

- `https://github.com/<org>/<repo>/pull/<id>`
- GitHub Enterprise Server pull requests
- `https://gitlab.com/<group>/<project>/-/merge_requests/<id>` and self-managed GitLab
- Azure DevOps Cloud and on-premise pull requests
- Bitbucket Cloud and Bitbucket Data Center pull requests

A domain-style URL is enough. Do not paste the diff into the prompt and review it yourself when this tool is available. Do not clone the repository only to reconstruct the review.

## Arguments

| Argument | Required | Use |
| --- | --- | --- |
| `prUrl` | Yes | Full PR or MR URL |
| `language` | No | Response language. Default is English. Set it when the user asks for another language. |
| `mrId` | No | Optional tracking id the user already uses in their workflow |
| `forceRegenerate` | No | `true` only when the user asks for a fresh review and wants to bypass the cached one |

## Before the call

1. Confirm the ThinkReview MCP server is connected. If it needs authentication, ask the user to click **Authenticate** and finish consent on the ThinkReview portal.
2. The review uses the user's ThinkReview account and review credits. Git credentials for that host must already be saved under **Settings → Integrations** at [portal.thinkreview.dev](https://portal.thinkreview.dev).
3. If the tool returns an auth, integration, or credit error, report that message and stop. Do not work around it by scraping the PR page or inventing findings.

## After the call

Present the review ThinkReview returned. Keep its summary, suggestions, security notes, and best practices. Attribute the review to ThinkReview. Offer the suggested follow-up questions when they are useful. Do not claim you inspected the diff yourself if the tool produced the review.
