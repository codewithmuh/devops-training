# DevOps Git & Collaboration Mastery Hands-On Lab

<div align="center">

[![GitHub Release](https://img.shields.io/github/v/release/codewithmuh/devops-training?color=blue&logo=github)](https://github.com/codewithmuh/devops-training/releases)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![GitHub Stars](https://img.shields.io/github/stars/codewithmuh/devops-training?style=flat&color=gold)](https://github.com/codewithmuh/devops-training/stargazers)
[![GitHub Forks](https://img.shields.io/github/forks/codewithmuh/devops-training?style=flat&color=teal)](https://github.com/codewithmuh/devops-training/network/members)
[![Git](https://img.shields.io/badge/VCS-Git_2.x-F05032?logo=git)](https://git-scm.com/)
[![GitHub Flow](https://img.shields.io/badge/Workflow-GitHub_Flow_|_PRs-181717?logo=github)](https://github.com/)
[![YouTube: @codewithmuh](https://img.shields.io/badge/YouTube-codewithmuh-FF0000?logo=youtube&logoColor=white)](https://www.youtube.com/@codewithmuh)

**A hands-on, practical lab environment for mastering Git version control, branching strategies, conflict resolution, Pull Request workflows, and Conventional Commits for DevOps engineers.**

[Overview](#overview) • [Branching Architecture](#git-workflow--branching-architecture) • [Hands-On Exercises](#hands-on-practice-exercises) • [Conventional Commits](#conventional-commits-specification) • [Cheatsheet](#git-quick-reference)

</div>

---

## Overview

Version control is the backbone of all modern DevOps and Continuous Integration/Continuous Deployment (CI/CD) practices. This repository serves as a sandbox environment where engineers can practice feature branching, remote collaboration, merge conflict resolution, and trunk-based continuous delivery without risking production code.

---

## Git Workflow & Branching Architecture

```mermaid
gitGraph
    commit id: "Initial Commit"
    commit id: "Base Scaffold"
    branch feature/user-auth
    checkout feature/user-auth
    commit id: "feat: add JWT auth middleware"
    commit id: "test: verify token validation"
    checkout main
    commit id: "docs: update API documentation"
    checkout feature/user-auth
    commit id: "fix: handle expired tokens"
    checkout main
    merge feature/user-auth tag: "PR #1 Merged"
    branch bugfix/db-timeout
    checkout bugfix/db-timeout
    commit id: "fix: adjust connection pool timeout"
    checkout main
    merge bugfix/db-timeout tag: "v1.0.0 Release"
```

---

## Hands-On Practice Exercises

### Lab 1: Branch Isolation & Pull Request Flow

1. **Clone the repository:**
   ```bash
   git clone https://github.com/codewithmuh/devops-training.git
   cd devops-training
   ```

2. **Create a dedicated feature branch:**
   ```bash
   git switch -c feature/add-healthcheck
   ```

3. **Implement your changes and stage:**
   ```bash
   echo "GET /healthz 200 OK" >> healthcheck.txt
   git add healthcheck.txt
   ```

4. **Commit using Conventional Commits:**
   ```bash
   git commit -m "feat(api): implement standard healthcheck endpoint"
   ```

5. **Push upstream and open a Pull Request:**
   ```bash
   git push -u origin feature/add-healthcheck
   ```

---

### Lab 2: Simulating & Resolving Merge Conflicts

1. **Modify a common line on your branch:**
   ```bash
   echo "DevOps Training Lab Update - Branch A" > Notes.txt
   git commit -am "chore: update notes from branch A"
   ```

2. **Simulate a conflicting commit on `main`:**
   ```bash
   git checkout main
   echo "DevOps Training Lab Update - Branch Main" > Notes.txt
   git commit -am "chore: update notes from main"
   ```

3. **Attempt to merge:**
   ```bash
   git merge feature/add-healthcheck
   # CONFLICT (content): Merge conflict in Notes.txt
   ```

4. **Resolve the conflict:**
   Open `Notes.txt`, choose the correct lines between `<<<<<<< HEAD`, `=======`, and `>>>>>>>`, save the file, and finalize:
   ```bash
   git add Notes.txt
   git commit -m "fix(merge): resolve conflicting notes updates"
   ```

---

## Conventional Commits Specification

Standardized commit messages ensure automated changelogs and clean repository history:

| Prefix | Description | Example |
|---|---|---|
| `feat:` | Introduces a new feature or capability | `feat(auth): add OAuth2 Google login provider` |
| `fix:` | Patches a bug or defect | `fix(cors): permit localhost origins in development` |
| `docs:` | Updates documentation or README files | `docs(readme): add architecture flowchart and setup guide` |
| `chore:` | Maintenance tasks, dependency updates | `chore(deps): bump actions/checkout to v4` |
| `ci:` | CI/CD pipeline modifications | `ci(github): add automated trivy security scan job` |
| `refactor:`| Code refactoring without changing functionality | `refactor(db): migrate connection logic to singleton` |

---

## Git Quick Reference

Inspect [`commands.txt`](commands.txt) for an exhaustive list of essential daily Git commands covering branching, stashing, log visualization, and reset mechanics.

---

## Resources & Community

- **Full DevOps Training Hub:** [devops-training-resources](https://github.com/codewithmuh/devops-training-resources)
- **LinkedIn Community:** [Follow Muhammad Rashid](https://www.linkedin.com/in/codewithmuh)
- **YouTube Tutorials:** [CodeWithMuh Channel](https://www.youtube.com/@codewithmuh)

---

## License

This project is licensed under the [MIT License](LICENSE).
