# Git Workflow & Branching

## Branch Types
- `main`: Stable, production-ready code
- `dev`: Integration branch for new features
- `feature/*`: Feature branches (e.g., feature/graph-view)
- `bugfix/*`: Bugfix branches
- `hotfix/*`: Hotfixes for production

## Workflow
1. Branch from `dev` for new features or fixes.
2. Open a pull request (PR) to `dev`.
3. PRs require review and must pass CI before merging.
4. Release branches are merged to `main` after QA.

---

For more, see `project_management/documentation_plan.md`.
