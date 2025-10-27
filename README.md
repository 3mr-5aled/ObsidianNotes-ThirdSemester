# ObsidianNotes — Third Semester

A personal Obsidian vault containing notes, summaries, resources, and study materials for the third semester. This repository is organized to make it easy to find course notes, revision sheets, templates, and reference resources while keeping content portable and friendly for collaboration (via Git/GitHub).

---

Table of contents
- [About](#about)
- [Features](#features)
- [Folder structure](#folder-structure)
- [Getting started](#getting-started)
- [Usage & conventions](#usage--conventions)
- [Templates & frontmatter](#templates--frontmatter)
- [Backups & sync](#backups--sync)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

---

## About
This vault collects notes taken during the third semester of studies. It’s meant to be:
- readable in Obsidian,
- searchable and linkable with Obsidian’s graph/backlink features,
- shareable and versioned via Git.

Use this repo as your study hub: link concepts across courses, keep revision notes concise, and track resources you refer to regularly.

## Features
- Course-specific folders for clean separation of topics
- Revision notes and cheat sheets for quick review
- Reusable templates for lectures, lab reports, and summaries
- Tags and YAML frontmatter to enable custom Obsidian queries
- Example workflows for daily notes and spaced-repetition links

## Folder structure
A recommended/typical layout used in this vault:

- Courses/
  - CourseA/
    - Lectures/
    - Labs/
    - Assignments/
    - Summary.md
  - CourseB/
- Templates/
  - lecture-template.md
  - lab-template.md
  - summary-template.md
- Daily/
  - YYYY-MM-DD.md (daily notes)
- Resources/
  - Papers.md
  - Links.md
  - Tools.md
- Assets/
  - images/
  - diagrams/
- README.md
- .obsidian/ (optional Obsidian settings — usually excluded from repo unless intentionally shared)

Adjust names to match your courses and preferences.

## Getting started
1. Install Obsidian: https://obsidian.md
2. Clone this repository:
   git clone https://github.com/3mr-5aled/ObsidianNotes-ThirdSemester.git
3. Open Obsidian → Open vault → Select the cloned folder.
4. (Optional) Install recommended community plugins:
   - Templates
   - Daily notes / Periodic Notes
   - Quick Switcher++
   - Advanced URI (if you use links from external apps)
5. Open `Templates/` to see and start using templates for new notes.

## Usage & conventions
To keep notes consistent and easy to navigate, follow these conventions:

- Filenames:
  - Lecture notes: CourseName - Lecture <number> - <topic>.md
  - Summaries: CourseName - Summary.md
  - Daily notes: YYYY-MM-DD.md
- Use YAML frontmatter at the top of important notes:
  ---
  title: "Short descriptive title"
  course: "CourseName"
  tags: ["lecture","week3"]
  date: 2025-02-14
  ---
- Tagging:
  - #lecture, #lab, #summary, #todo, #concept
  - Tags help you create saved searches and queries in Obsidian.
- Links and backlinks:
  - Link related notes with [[Note Title]] to form a knowledge graph.
  - When summarizing, link back to full lecture/lab notes for context.

## Templates & frontmatter
Templates allow rapid, consistent note creation. Example entries:
- Templates/lecture-template.md:
  ---
  title: "{{title}}"
  course: "{{course}}"
  date: {{date}}
  tags: ["lecture"]
  ---
  ## Topic
  - Key points
  - Definitions
  - Examples
  ## References
  - [[Related Note]]

Use the Templates plugin to insert these quickly.

## Backups & sync
- Use Git to version notes and keep history:
  - Commit regularly with clear messages (e.g., "Add lecture 05 summary for Signals class").
  - Consider branches for experiments or major reorganizations.
- For mobile sync, consider Obsidian Sync, third-party cloud providers, or Git-based sync solutions (e.g., git-annex, Syncthing).
- Keep .obsidian hidden or excluded if you don't want sharing of plugin/settings.

## Contributing
Contributions are welcome — whether adding missing lecture notes, improving summaries, or fixing typos.

Suggested workflow:
1. Fork the repo.
2. Create a branch: git checkout -b feat/<course>-add-notes
3. Add or update notes.
4. Commit with a meaningful message.
5. Open a Pull Request describing what you added or changed.

Guidelines:
- Keep each file focused (lecture vs summary vs assignment).
- Respect naming and frontmatter conventions.
- If adding images, keep them in Assets/images and reference with relative paths.

## License
No license file detected in this repository. If you want others to reuse or modify these notes, add a LICENSE file (for example, MIT). If you prefer keeping it private/copyrighted, add a license that reflects that choice.

## Contact
Maintained by: 3mr-5aled  
Repository: https://github.com/3mr-5aled/ObsidianNotes-ThirdSemester

If you'd like the README customized (for specific courses, or to include sample notes or a LICENSE), tell me how you want it and I’ll update it.
