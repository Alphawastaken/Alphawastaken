<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&text=👋+Hello+World,+I'm+Alpha&height=120" alt="header"/>
</p>

### 👨‍💻 About Me
I’m a self‑proclaimed **professional bad‑code writer**, currently leveling up in:

- 🔭 **C** & **Python** — diving into memory management & scripting  
- 🛠 **MongoDB** & **PostgreSQL** — mastering both NoSQL and relational databases  

Always open to creatively unpredictable projects… especially in C and Python! Let’s break things (and fix them).

---

### 🤝 What I’m Looking For
- **Collaboration** on C/Python projects—from quirky CLI tools to database‑driven apps  
- **Mentorship** to refine terrible code into solid structure  

---

### 🛠 Technologies & Tools
<p align="left">
  <img alt="C" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/c/c-original.svg" width="40"/>
  <img alt="Python" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg" width="40"/>
  <img alt="MongoDB" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/mongodb/mongodb-original-wordmark.svg" width="40"/>
  <img alt="PostgreSQL" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/postgresql/postgresql-original-wordmark.svg" width="40"/>
  <img alt="Linux" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/linux/linux-original.svg" width="40"/>
  <img alt="Git" src="https://www.vectorlogo.zone/logos/git-scm/git-scm-icon.svg" width="40"/>
  <img alt="Azure" src="https://www.vectorlogo.zone/logos/microsoft_azure/microsoft_azure-icon.svg" width="40"/>
</p>

---

### 📊 GitHub Stats
![Top Langs](https://github-readme-stats.vercel.app/api/top-langs?username=alphawastaken&show_icons=true&layout=compact)

---

### 🚀 Fun & Dynamic Additions

#### **Visitor Counter**  
<img src="https://komarev.com/ghpvc/?username=alphawastaken&label=Profile+views&color=0e75b6&style=flat" alt="profile views"/>

---

#### 🐍 Snake Animation on Contribution Graph

Workflow file: `.github/workflows/snake.yml`
```yaml
name: Snake generator
on:
  schedule:
    - cron: "0 */12 * * *"
  workflow_dispatch:
jobs:
  generate:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-snake.svg
            dist/github-snake-dark.svg?palette=github-dark
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
      - uses: crazy-max/ghaction-github-pages@v3
        with:
          target_branch: output
          build_dir: dist
          commit_message: "Update snake animation"
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```
<picture>
  <source media="(prefers-color-scheme: dark)"
          srcset="https://raw.githubusercontent.com/Alphawastaken/Alphawastaken/output/github-snake-dark.svg" />
  <source media="(prefers-color-scheme: light)"
          srcset="https://raw.githubusercontent.com/Alphawastaken/Alphawastaken/output/github-snake.svg" />
  <img alt="GitHub Snake" src="https://raw.githubusercontent.com/Alphawastaken/Alphawastaken/output/github-snake.svg" />
</picture>
