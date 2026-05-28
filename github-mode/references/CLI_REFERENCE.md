# GitHub CLI (gh) Command Reference

Complete reference for GitHub CLI commands used in GitHub Manager skill.

## gh CLI Setup

### Authentication

```bash
# Login to GitHub
gh auth login

# Check authentication status
gh auth status

# Refresh token if needed
gh auth refresh

# Setup git credential helper
gh auth setup-git
```

### Configuration

```bash
# Set preferred editor
gh config set editor vim

# View all configuration
gh config list

# Set default repo format
gh config set prompt enabled
```

### Useful gh Aliases

```bash
# Create shortcuts for efficiency
gh alias set prs 'pr status'
gh alias set prc 'pr checkout'
gh alias set prl 'pr list --author "@me"'
gh alias set mypr 'pr view --web'
gh alias set isl 'issue list --assignee "@me"'
gh alias set runl 'run list --limit 10'
gh alias set repl 'release list'
```

## Pull Request Workflow

### Create Pull Request

```bash
# Interactive creation (prompts for title and body)
gh pr create

# Create with title and body
gh pr create --title "feat(auth): add OAuth2 login" --body "## Summary\nAdded OAuth2 authentication"

# Fill from commits automatically
gh pr create --fill

# Fill from first commit only
gh pr create --fill-first

# Create draft PR
gh pr create --draft --title "WIP: feature"

# Create PR targeting specific base branch
gh pr create --base develop --head feature/my-feature

# Add reviewers
gh pr create --reviewer @me --reviewer team-name

# Add labels
gh pr create --label "enhancement" --label "priority: high"

# Add to project
gh pr create --project "Roadmap"

# Add milestone
gh pr create --milestone "v2.0"

# Create from file template
gh pr create --template pull_request_template.md

# Open in browser
gh pr create --web

# Dry run (preview without creating)
gh pr create --dry-run --title "test" --body "test"
```

### View and Manage PRs

```bash
# List PRs
gh pr list                          # All open PRs
gh pr list --state merged           # Merged PRs
gh pr list --state closed           # Closed PRs
gh pr list --limit 50               # More results
gh pr list --author "@me"           # Your PRs
gh pr list --assignee "@me"         # Assigned to you
gh pr list --label bug              # Filter by label

# View specific PR
gh pr view 123                      # By number
gh pr view                          # Current branch PR
gh pr view --web                    # Open in browser

# View PR diff
gh pr diff                          # View changes
gh pr diff --color=never            # No colors (for scripts)

# View PR checks/status
gh pr checks                        # CI/CD status

# Check out PR locally
gh pr checkout 123                  # By number
gh pr checkout feature-branch       # By branch name

# View PR status for current repo
gh pr status                        # Shows PRs for current branch
```

### Review and Merge PRs

```bash
# Add comment to PR
gh pr comment 123 --body "Great work!"

# Approve PR
gh pr review --approve

# Request changes
gh pr review --request-changes "Fix the tests first"

# Comment with suggestions
gh pr review --comment

# Merge PR
gh pr merge                          # Interactive merge
gh pr merge --admin --merge          # Merge as admin
gh pr merge --squash                 # Squash and merge
gh pr merge --rebase                 # Rebase and merge
gh pr merge --delete-branch          # Delete branch after merge

# Close PR
gh pr close 123

# Reopen PR
gh pr reopen 123

# Mark PR as ready for review
gh pr ready 123

# Update PR with latest base branch
gh pr update-branch 123
```

## Issue Management

```bash
# Create issue
gh issue create --title "Bug in login" --body "Description"
gh issue create --template bug_report.md
gh issue create --label bug --assignee @me

# List issues
gh issue list
gh issue list --state open --label "bug"
gh issue list --assignee "@me"

# View issue
gh issue view 123
gh issue view 123 --web

# Close/reopen issue
gh issue close 123
gh issue reopen 123

# Comment on issue
gh issue comment 123 --body "Fixed in PR #456"

# Edit issue
gh issue edit 123 --title "New title" --add-label feature

# Lock/unlock issue
gh issue lock 123
gh issue unlock 123

# Transfer issue to another repo
gh issue transfer 123 owner/repo

# Pin/unpin issue
gh issue pin 123
gh issue unpin 123
```

## Release Management

```bash
# List releases
gh release list

# View release
gh release view v1.2.0
gh release view v1.2.0 --web

# Create release
gh release create v1.2.0
gh release create v1.2.0 --title "Release v1.2.0" --notes "## Changes\n- New feature"
gh release create v1.2.0 --draft                 # Draft release
gh release create v1.2.0 --prerelease           # Pre-release
gh release create v1.2.0 --latest               # Mark as latest

# Upload assets to release
gh release upload v1.2.0 ./dist/app.tar.gz

# Edit release
gh release edit v1.2.0 --title "Updated Title"
gh release edit v1.2.0 --notes-file CHANGELOG.md

# Delete release
gh release delete v1.2.0
gh release delete v1.2.0 --yes  # Skip confirmation

# Download release assets
gh release download v1.2.0
gh release download v1.2.0 --pattern "*.tar.gz"
```

## Label Management

```bash
# List labels
gh label list

# Create new label
gh label create "breaking-change" --description "Breaking changes" --color "ff0000"

# Edit label
gh label edit "bug" --name "issue" --color "cccccc"

# Delete label
gh label delete "wontfix"

# Clone labels from another repo
gh label clone owner/repo
```

## Repository Operations

```bash
# View repository info
gh repo view
gh repo view --web

# List repositories
gh repo list
gh repo list owner --limit 10

# Clone repository
gh repo clone owner/repo

# Fork repository
gh repo fork

# Sync fork with upstream
gh repo sync owner/fork --base owner/upstream

# Create new repository
gh repo create my-repo --public --description "My new repo"

# Edit repository settings
gh repo edit --description "Updated description" --enable issues=false

# Archive repository
gh repo archive

# Transfer repository
gh repo transfer owner/new-repo
```

## GitHub Projects

```bash
# List projects
gh project list

# View project
gh project view 1
gh project view 1 --web

# Create project
gh project create "My Project" --owner "@me"

# Add item to project
gh project item-add 1 --body "New task"

# Create item in project
gh project item-create 1 --title "New issue" --field "Status" "Todo"

# Edit project item
gh project item-edit 1 --field "Status" "Done"

# List project items
gh project item-list 1
```

## Search

```bash
# Search issues
gh search issues "bug login"
gh search issues --state open --label "priority: high"

# Search PRs
gh search prs "feat: add"
gh search prs --state merged --author "@me"

# Search commits
gh search commits "fix: memory leak"

# Search code
gh search code "function login"

# Search repositories
gh search repos "react component"
```

## Workflow and Run Management

```bash
# List workflows
gh workflow list

# View workflow
gh workflow view 12345

# Run workflow manually
gh workflow run "Build and Test"

# Disable/enable workflow
gh workflow disable "Deploy"
gh workflow enable "Deploy"

# View workflow runs
gh run list
gh run list --workflow "Build" --limit 10

# View run details
gh run view 12345
gh run view 12345 --log           # View logs
gh run view 12345 --web           # Open in browser

# Rerun workflow
gh run rerun 12345
gh run rerun 12345 --failed       # Only failed jobs

# Cancel workflow
gh run cancel 12345

# Download workflow artifacts
gh run download 12345
gh run download 12345 --pattern "*.zip"
```

## Fork Workflow

```bash
# Fork a repo (creates fork under your account)
gh repo fork owner/repo

# Clone your fork
gh repo clone your-username/repo

# Add upstream remote
git remote add upstream git@github.com:owner/repo.git

# Sync fork with upstream
gh repo sync your-username/repo --base owner/upstream

# Create PR from fork
git checkout -b feature-branch
# ... make changes ...
git push origin feature-branch

# Create PR from fork (gh will detect fork)
gh pr create --title "feat: my contribution" \
  --body "Description of changes" \
  --head your-username:feature-branch
```

## PR Template

Create `.github/pull_request_template.md`:

```markdown
## Summary
[Brief description of what this PR does]

## Type
- [ ] Bug fix
- [ ] Feature
- [ ] Refactor
- [ ] Documentation
- [ ] Other: [describe]

## Checklist
- [ ] Tests added/updated
- [ ] Code follows project style guidelines
- [ ] Self-review completed
- [ ] Documentation updated (if needed)

## Testing
[Describe how to test these changes]

## Breaking Changes
- [ ] Yes - describe the breaking change
- [ ] No

## Related Issues
Closes #[issue number]
```

**Usage:**
```bash
gh pr create --template .github/pull_request_template.md --title "Your title"
```

## Quick Commands Reference

```bash
# Check PR status
gh pr status

# View your PRs
gh pr list --author "@me"

# View PR details
gh pr view

# Check out PR for review
gh pr checkout 123

# Add approval
gh pr review --approve --body "LGTM!"

# Check authentication
gh auth status

# View your issues
gh issue list --assignee "@me"

# View workflows
gh workflow list

# View recent runs
gh run list --limit 10
```
