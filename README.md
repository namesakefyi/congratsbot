# Congratsbot

Congratsbot is a webhook for announcing code merges to Discord and celebrating contributors. 

Example:

> 🎊 **Merged!** Congratsbot (Bot): [`[ci] release (#232)`](#)  
> _Featuring contributions by github-actions[bot]! 🌟_

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
```

## Credits

The implementation of this bot was forked from [Astro Automation Tools](https://github.com/withastro/automation).