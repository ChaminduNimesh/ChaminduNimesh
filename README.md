<div data-importer="image" align="center">
  <img data-importer="image" height="150" src="https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExaXQxcWJ6NTRud21rem93aTB1ZWJ4aThobzI3cjM2b3EwaDNjc3J0dSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/RbDKaczqWovIugyJmW/giphy.gif"  />
</div>

###

<div data-importer="socials" align="center">
  <a href=" https://www.linkedin.com/in/chamindu-nimesh-6831a526b/" target="_blank">
    <img src="https://img.shields.io/static/v1?message=LinkedIn&logo=linkedin&label=&color=0077B5&logoColor=white&labelColor=&style=for-the-badge" height="25" alt="linkedin logo"  />
  </a>
  <a href="https://www.youtube.com/@chamindunimesh1498" target="_blank">
    <img src="https://img.shields.io/static/v1?message=Youtube&logo=youtube&label=&color=FF0000&logoColor=white&labelColor=&style=for-the-badge" height="25" alt="youtube logo"  />
  </a>
  <a href="https://web.facebook.com/chamindu.nimesh.9" target="_blank">
    <img src="https://img.shields.io/static/v1?message=Facebook&logo=facebook&label=&color=1877F2&logoColor=white&labelColor=&style=for-the-badge" height="25" alt="facebook logo"  />
  </a>
</div>

###

<div data-importer="profile-views" align="center">
  <img data-importer="profile-views" src="https://visitor-badge.laobi.icu/badge?page_id=ChaminduNimesh.ChaminduNimesh&right_color=cadetblue"  />
</div>

###

<h1 data-importer="text" align="center">Hey there 👋 I'm Chamindu</h1>

###

<p data-importer="text" align="left">Full-stack developer | .NET • React • Flutter • Docker • AWS | Building things that scale 🚀</p>

###

<h3 data-importer="text" align="left">🛠 Language and tools</h3>

###

<div data-importer="techs" align="left">
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/dot-net/dot-net-plain-wordmark.svg" height="40" alt="dot-net logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/firebase/firebase-plain-wordmark.svg" height="40" alt="firebase logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/amazonwebservices/amazonwebservices-line-wordmark.svg" height="40" alt="amazonwebservices logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/kubernetes/kubernetes-plain.svg" height="40" alt="kubernetes logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/docker/docker-plain-wordmark.svg" height="40" alt="docker logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/anaconda/anaconda-original.svg" height="40" alt="anaconda logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/dart/dart-original.svg" height="40" alt="dart logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/figma/figma-original.svg" height="40" alt="figma logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/flask/flask-original.svg" height="40" alt="flask logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/jupyter/jupyter-original.svg" height="40" alt="jupyter logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/linux/linux-original.svg" height="40" alt="linux logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/mongodb/mongodb-original.svg" height="40" alt="mongodb logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/postgresql/postgresql-original.svg" height="40" alt="postgresql logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/react/react-original.svg" height="40" alt="react logo"  />
</div>

###

<h3 data-importer="text" align="left">🔥   My Stats :</h3>

###

<div data-importer="stats" align="center">
  <img src="https://streak-stats.demolab.com?user=ChaminduNimesh&locale=en&mode=daily&theme=dark&hide_border=false&border_radius=5&order=3" height="220" alt="streak graph"  />
</div>

###

<picture data-importer="pacman">
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/ChaminduNimesh/ChaminduNimesh/pacman-output/pacman-contribution-graph-dark.svg?game=pacman">
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/ChaminduNimesh/ChaminduNimesh/pacman-output/pacman-contribution-graph.svg?game=pacman">
  <img alt="pacman contribution graph" src="https://raw.githubusercontent.com/ChaminduNimesh/ChaminduNimesh/pacman-output/pacman-contribution-graph.svg?game=pacman">
</picture>

###
name: Generate arcade animation

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
    timeout-minutes: 20

    steps:
      - name: generate pacman-contribution-graph.svg
        uses: abozanona/pacman-contribution-graph@main
        with:
          github_user_name: ${{ github.repository_owner }}
          games: 'pacman'


      - name: push pacman-contribution-graph.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: pacman-output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
