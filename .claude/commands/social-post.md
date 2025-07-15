---
name: social-post
description: Generate appreciation tweets for open source packages
arguments:
  - name: type
    description: The type of content to analyze (commit, package, feature, last)
    required: true
  - name: value
    description: The value for the selected type (sha, package name, description, or number)
    required: true
---

# /social-post

Generate appreciation tweets for open source maintainers based on your code usage.

## Usage

`/social-post [type]:[value]`

## Examples

- `/social-post commit:abc123` - Generate tweets for a specific commit
- `/social-post package:react-query` - Appreciate a specific package you're using
- `/social-post feature:"added real-time updates with ActionCable"` - For a feature implementation
- `/social-post last:5` - Analyze the last 5 commits for tweet-worthy content

## What it does

This command spawns a subagent to:

1. Analyze the specified content for package usage
2. Generate 2 draft tweets focused on thanking maintainers
3. Save drafts to `.social/tweets/manual-[timestamp].md`
4. Return a preview of the generated tweets

Using a subagent keeps your main conversation clean and focused while tweets are generated in the background.

The tweets focus on appreciation and recognition of open source maintainers' work.