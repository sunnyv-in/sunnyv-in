name: Generate Contribution Graph

on:
  schedule:
    - cron: "0 0 * * *"   # runs every day at midnight
  workflow_dispatch:        # run manually anytime

jobs:
  generate:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3

      - name: Generate contribution graph
        uses: Platane/snk@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark

      - name: Push to repo
        uses: crazy-max/ghaction-github-pages@v3
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
<!-- Contribution Snake Animation -->
<picture>
  <source media="(prefers-color-scheme: dark)"
    srcset="https://raw.githubusercontent.com/sunnyv-in/sunnyv-in/output/github-contribution-grid-snake-dark.svg"
  />
  <source media="(prefers-color-scheme: light)"
    srcset="https://raw.githubusercontent.com/sunnyv-in/sunnyv-in/output/github-contribution-grid-snake.svg"
  />
  <img alt="Sunny's contribution snake"
    src="https://raw.githubusercontent.com/sunnyv-in/sunnyv-in/output/github-contribution-grid-snake.svg"
  />
</picture>

<!-- Live GitHub Stats Card -->
[![Sunny's GitHub stats](https://github-readme-stats.vercel.app/api?username=sunnyv-in&show_icons=true&theme=github_dark&border_color=39d353&title_color=39d353)](https://github.com/sunnyv-in)

<!-- Streak Stats -->
[![GitHub Streak](https://streak-stats.demolab.com/?user=sunnyv-in&theme=github-dark-blue&border=39d353&ring=ff4757&fire=ffd700)](https://github.com/sunnyv-in)
