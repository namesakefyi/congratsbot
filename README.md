<img src="/assets/congratsbot-avatar.png" alt="Congratsbot avatar" width="128" />

# Congratsbot

Congratsbot is a webhook for announcing code merges to Discord and celebrating contributors. 

Example:

> 🎊 **Merged!** Eva Decker: [`Release (#232)`](#)  
> _Featuring contributions by Luke Lennon! 🌟_

## Prerequisites

[Create a new Discord webhook](https://support.discord.com/hc/en-us/articles/228383668-Intro-to-Webhooks) and add the URL to your repository secrets as `DISCORD_WEBHOOK_CONGRATS`.

## Usage

```yml
name: Congratsbot

on:
  push:
    branches: [main]

jobs:
  congrats:
    uses: namesakefyi/congratsbot/.github/workflows/congratsbot.yml@main
    secrets:
      DISCORD_WEBHOOK: ${{ secrets.DISCORD_WEBHOOK_CONGRATS }}
    with:
      # Optional: Don't post to Discord if a commit matches these regex patterns
      exclude: '["^chore\\(deps\\)", "^chore:", "\\[skip\\]"]'  
```

The `exclude` parameter accepts an array of regex patterns. Messages matching any pattern will be skipped. Patterns are case-insensitive by default. For example:
- `"^chore\\(deps\\)"` - matches messages starting with "chore(deps)"
- `"^chore:"` - matches messages starting with "chore:"
- `"\\[skip\\]"` - matches messages containing "[skip]"

## Credits

The implementation of this bot was forked from [Astro Automation Tools](https://github.com/withastro/automation).

The [congratsbot avatar](/assets/congratsbot-avatar.png) is from [Emoji Kitchen](https://emoji.supply/kitchen/?%F0%9F%9A%80+%F0%9F%99%82=8x1l3a).
