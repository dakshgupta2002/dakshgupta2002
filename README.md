### Hi there 👋
![Daksh Gupta's GitHub stats](https://github-readme-stats.vercel.app/api?username=dakshgupta2002&show_icons=true&theme=outrun)


[![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=dakshgupta2002&layout=compact)](https://github.com/dakshgupta2002/github-readme-stats)

<!--
**dakshgupta2002/dakshgupta2002** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->


name: Dynamic Template

on:
  push:
    branches:
      - main
  workflow_dispatch:

jobs:
  update_templates:
    name: "Update Templates"
    runs-on: ubuntu-latest
    steps:
      - name: "📥  Fetching Repository Contents"
        uses: actions/checkout@main

      - name: "💾  Github Repository Metadata"
        uses: varunsridharan/action-repository-meta@main
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}

      - name: "💫  Dynamic Template Render"
        uses: varunsridharan/action-dynamic-readme@main
        with:
          GLOBAL_TEMPLATE_REPOSITORY: {repository-owner}/{repository-name}
          files: |
            FILE.md
            FILE2.md=output_filename.md
            folder1/file.md=folder2/output.md
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
