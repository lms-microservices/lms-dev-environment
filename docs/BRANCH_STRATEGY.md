# LMS Mono-Repo Git Workflow

## How to start working on a feature
- `git checkout dev`
- `git pull origin dev`
- `git checkout -b feature/login-api`

  ... do your work ...

- `git add .`
- `git commit -m "feat: add login endpoint"`
- `git push origin feature/login-api`
- `Then open a Pull Request on GitHub`


## Branching Strategy
- `main` → production-ready, stable
- `dev` → ongoing development
- `feature/<feature-name>` → feature branches from dev
- `bugfix/<bug-name>` → bug fixes from dev

## Branch Naming Rules
- Feature branches: `feature/login-ui`, `feature/auth-jwt`
- Bugfix branches: `bugfix/fix-login-error`

## Commit Message Format
- Format: `<type>: <short description>`
- Types:
    - feat → new feature
    - fix → bug fix
    - docs → documentation changes
    - style → formatting, linting
    - refactor → code restructuring
- Example: `feat: implement login form validation`

## Pull Request Rules
- PR target: always merge into `dev`
- Include description of changes
- Assign reviewer(s)
- Resolve conflicts before merge
- Delete feature branch after merge