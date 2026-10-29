# ThinkReview for Cursor

Cursor plugin that reviews a pull request or merge request through [ThinkReview](https://thinkreview.dev). Installing the plugin is free. A review uses the signed-in user's ThinkReview account and review credits.

The plugin connects Cursor to the hosted MCP server at `https://mcp.thinkreview.dev/v1`. The review engine stays on ThinkReview infrastructure and is not in this repository.

## What you get

- **MCP server** `thinkreview`, with one tool: `review_url_code`
- **Skill** `review-pull-request`, so Cursor calls that tool when you ask it to review a PR or MR URL

Supported hosts: GitHub and GitHub Enterprise Server, GitLab.com and self-managed GitLab, Azure DevOps Cloud and on-premise, Bitbucket Cloud and Bitbucket Data Center.

## Before you install

1. A [ThinkReview](https://thinkreview.dev) account with an active plan or available review credits.
2. Git credentials for the pull request host, saved under **Settings → Integrations** in the [ThinkReview portal](https://portal.thinkreview.dev).

## Install

Marketplace listing is submitted separately. To try this repo locally:

1. Copy this folder to `~/.cursor/plugins/local/thinkreview`.
2. Reload the window (**Developer: Reload Window**).
3. Open **Customize** and confirm the ThinkReview skill and the `thinkreview` MCP server.
4. Enable the server and click **Authenticate**. Finish consent in the browser on the ThinkReview portal.

The plugin config is URL-only. It does not store a token. OAuth happens in Cursor after you authenticate.

## Review a pull request

Ask Cursor to review a URL, for example:

> Review https://github.com/org/repo/pull/42

Cursor should call `review_url_code` with that URL. Optional arguments:

| Argument | Required | Description |
| --- | --- | --- |
| `prUrl` | Yes | Full or domain-style PR/MR URL |
| `language` | No | Response language. Default is English |
| `mrId` | No | Tracking id for your own workflow |
| `forceRegenerate` | No | `true` to bypass a cached review |

## Privacy and terms

- [Privacy Policy](https://thinkreview.dev/privacy-policy.html)
- [Terms of Service](https://thinkreview.dev/terms-of-service.html)
- [MCP docs](https://thinkreview.dev/docs/mcp-integration/)
- [Support](https://thinkreview.dev/contact)

This repository is MIT licensed. The ThinkReview hosted service, APIs, and review infrastructure remain proprietary to Thinkode / ThinkReview.
