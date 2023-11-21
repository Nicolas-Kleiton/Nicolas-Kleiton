# Hello World, I'm Nicolas, be very welcome!

<table>
  <a href="https://github.com/Nicolas-Kleiton">
  <img height="150em" src="https://github-readme-stats.vercel.app/api?username=Nicolas-Kleiton&show_icons=true&theme=tokyonight&include_all_commits=true&count_private=true"/>
  <img height="150em" src="https://github-readme-stats.vercel.app/api/top-langs/?username=Nicolas-Kleiton&layout=compact&langs_count=6&theme=tokyonight"/>
  <img src="https://img.icons8.com/color/2x/html-5.png" width="120" alt="HTML5">
  <img src="https://img.icons8.com/color/2x/css3.png" width="120" alt="CSS3">
  <img src="https://img.icons8.com/color/2x/bootstrap.png" width="120" alt="Bootstrap">
  <img src="https://img.icons8.com/nolan/2x/javascript.png" width="120" alt="JavaScript">
</table>

<div> 
  <a href="https://www.instagram.com/iniihcki/" target="_blank"><img src="https://img.shields.io/badge/-Instagram-%23E4405F?style=for-the-badge&logo=instagram&logoColor=white" target="_blank"></a>
  <a href = "mailto: inicolaskleiton@gmail.com"><img src="https://img.shields.io/badge/-Gmail-%23333?style=for-the-badge&logo=gmail&logoColor=white" target="_blank"></a>
  <a href="https://www.linkedin.com/in/nicolas-kleiton-9830a8263/" target="_blank"><img src="https://img.shields.io/badge/-LinkedIn-%230077B5?style=for-the-badge&logo=linkedin&logoColor=white" target="_blank"></a> 
</div>

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/YourUser/Nicolas-Kleiton/output/github-contribution-grid-snake-dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/YourUser/Nicolas-Kleiton/output/github-contribution-grid-snake.svg">
  <img alt="github contribution grid snake animation" src="https://raw.githubusercontent.com/YourUser/Nicolas-Kleiton/output/github-contribution-grid-snake.svg">
</picture>
name: generate animation

on:
  # run automatically every 24 hours
  schedule:
    - cron: "0 */24 * * *" 
  
  # allows to manually run the job at any time
  workflow_dispatch:
  
  # run on every push on the master branch
  push:
    branches:
    - master
    
  

jobs:
  generate:
    permissions: 
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5
    
    steps:
      # generates a snake game from a github user (<github_user_name>) contributions graph, output a svg animation at <svg_out_path>
      - name: generate github-contribution-grid-snake.svg
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark
          
          
      # push the content of <build_dir> to a branch
      # the content will be available at https://raw.githubusercontent.com/<github_user>/<repository>/<target_branch>/<file> , or as github page
      - name: push github-contribution-grid-snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          
_generated with [Platane/snk](https://github.com/Nicolas-Kleiton)_
