<h1 align="left">Hey 👋 What's up?</h1>

###

<p align="left">✨ Hi! I’m Almira — a tech enthusiast who loves turning everyday things into cool apps!<br>From random ideas at 2AM 🌙 to real code at 9AM 💻, I enjoy creating stuff that feels close to home.<br>Currently chasing bugs, building dreams, and occasionally arguing with my code (it usually wins 😅).</p>

###

<h2 align="left">About me</h2>

###

<p align="left">✨ Creating bugs since 2019<br>📚 I'm currently learning Laravel & loving the journey<br>🎯 Goals: Build meaningful apps, grow as a fullstack dev, and land my dream job<br>🎲 Fun fact:  I fix one bug and two more appear — it’s basically hydra coding.</p>

###

<h2 align="left">I code with</h2>

###

<div align="left">
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-original.svg" height="40" alt="javascript logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/react/react-original.svg" height="40" alt="react logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/php/php-original.svg" height="40" alt="php logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/laravel/laravel-original.svg" height="40" alt="laravel logo"  />
</div>

###

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/almiraira/almiraira/output/pacman-contribution-graph-dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/almiraira/almiraira/output/pacman-contribution-graph.svg">
  <img alt="pacman contribution graph" src="https://raw.githubusercontent.com/almiraira/almiraira/output/pacman-contribution-graph.svg">
</picture>

###
name: Generate pacman animation

on:
  schedule: # execute every 12 hours
    - cron: "* */12 * * *"

  workflow_dispatch:

  push:
    branches:
    - main

jobs:
  generate:
    permissions:
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5

    steps:
      - name: generate pacman-contribution-graph.svg
        uses: abozanona/pacman-contribution-graph@main
        with:
          github_user_name: ${{ github.repository_owner }}


      - name: push pacman-contribution-graph.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
