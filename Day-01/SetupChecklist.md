# Day 1 Setup and Git Checklist

## Development Tools

- [x] macOS development environment available
- [x] Homebrew installed
- [x] Visual Studio Code installed
- [x] `code` command available in Terminal
- [x] Git installed
- [x] .NET SDK installed
- [x] Node.js installed
- [x] GitHub account created
- [x] SSH key created
- [x] SSH authentication with GitHub tested
- [x] VS Code signed in or configured as preferred

## Verification Commands

```bash
sw_vers
git --version
brew --version
code --version
dotnet --version
node -v
ssh -T git@github.com
```

## Workspace

```text
~/Development/
└── DotNet-React/
    ├── Setup/
    ├── Day-01/
    ├── Day-02/
    └── ...
```

## `.gitignore`

Recommended entries:

```gitignore
.DS_Store
**/.DS_Store

bin/
obj/
```

## Repository Commands

Run from:

```bash
cd ~/Development/DotNet-React
```

Then:

```bash
git status
git add .
git commit -m "Day 1 - Create first ASP.NET Core Web API and Employee model"
git push
```

## Project Commands

Run from:

```bash
cd ~/Development/DotNet-React/Day-01/Code/EmployeeAPI
```

Then:

```bash
dotnet run
```

or:

```bash
dotnet watch run
```

## Final Verification

```bash
cd ~/Development/DotNet-React
git status
```

Expected after committing and pushing:

```text
On branch main
Your branch is up to date with 'origin/main'.
nothing to commit, working tree clean
```
