#### comp3104 - Developer Operations

# Github Action Status Badge

[![CI](https://github.com/GozdeEBaran/comp3104/actions/workflows/ci.yml/badge.svg)](https://github.com/GozdeEBaran/comp3104/actions/workflows/ci.yml)

# Commit Msg Hook (ENforce commit message format)

```
# !/bin/sh

COMMIT_MSG_FILE=$1
COMMIT_MSG=$(cat $COMMIT_MSG_FILE)

if ! echo "$COMMIT_MSG" | grep -Eq "^(feat|fix|docs|style|refactor|test|chore): .+"; then
echo "Commit message must follow the format: <type>: <description>"
echo "Example: feat: add user authentication"
exit 1
fi

```

# Pre-Commit Hook (Lint Code Before Commit)

```
# !/bin/sh

echo "Running pre-commit hook: Linting code..."
node --version
#  npm run lint
if [ $? -ne 0 ]; then
  echo "Linting failed. Fix errors before committing."
  exit 1
fi

```

# Pre-Push Hook (Run Tests Before Push)

Runs tests before allowing a push.
File: .git/hooks/pre-push

```
# !/bin/sh
echo "Running pre-push hook: Running tests..."
npm test
if [ $? -ne 0 ]; then
  echo "Tests failed! Fix them before pushing."
  exit 1
fi
```
