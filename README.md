# Make every commit a 'thank you' 🤝 with Claude Code

I kept forgetting to publically thank the many open source projects and maintainers that drive my professional and side-project life.  So I've enlisted Claude Code to help remind me.

### The project in a nutshell

This project (root CLAUDE.md instructions / custom slash command) helps you remember to say "thank you" by automatically drafting appreciation tweets whenever you create a commit that:

- Adds new packages to your projects
- Makes significant use of existing packages (performance improvements, bug fixes)
- Solves complex problems using open source tools
- Discovers creative ways to combine packages

Claude Code creates draft tweets - little reminders for you to show appreciation - that you can fine-tune and make your own.

### Example Tweet Drafts

**Commit:** `Add discourse_api gem for forum integration`

**Thank you tweet draft:**
```
🙏 Huge thanks to the discourse_api maintainers! Just integrated it 
for real-time forum monitoring. Your clean API design made it a joy 
to implement. #RubyGems #OpenSource
```

**Commit:** `Implement CSV export using papaparse library`

**Thank you tweet draft:**
```
✨ papaparse just made CSV handling a breeze! Streaming large files 
without memory issues. Thank you to the maintainers for this reliable 
parser that just works! 🎯 #JavaScript #OpenSourceHeroes
```

## How It Works

### Automatic Mode (Background)
1. **Subagent Analysis**: When you commit code, Claude spawns a subagent to analyze changes
2. **Smart Detection**: The subagent identifies new packages or significant package usage
3. **Draft Generation**: If worthy (score ≥ 7), it creates appreciation tweet drafts
4. **Non-Intrusive**: All happens in the background without interrupting your workflow

### Manual Mode (On-Demand)
Use the `/social-post` slash command to generate tweets whenever you want:
- `/social-post commit:abc123` - For a specific commit
- `/social-post package:react-query` - Appreciate a specific package
- `/social-post feature:"real-time updates"` - For features using packages
- `/social-post last:5` - Review recent commits

## Setup

1. Append the contents of this repository's CLAUDE.md instructions to your repo's CLAUDE.md file
2. Copy the slash command from the repo [.claude/commands/social-post.md](https://github.com/neonwatty/claude-social/tree/main/.claude/commands)
3. Commit normally - appreciation drafts appear automatically or manually at your command

### Always Your Choice
- Review generated drafts in `.social/tweets/`
- Edit as needed
- Post only what you're comfortable sharing
- Help maintainers feel valued

## Why use Subagents?

The automatic analysis uses Claude's Task tool to spawn subagents because:
- **Preserves Context**: Your main conversation stays focused on your primary work
- **Background Processing**: Tweet generation happens without interrupting you
- **Efficient**: Only uses resources when commits contain packages worth appreciating
- **Clean Output**: No clutter in your main chat about tweet generation
