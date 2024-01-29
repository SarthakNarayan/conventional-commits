## Conventional commits format

```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

- Use imperative mood for the description:
  - The imperative mood is a grammatical mood that forms a command, or request.
  - For example instead of "Added feature to add todos" use "add feature to add todos".
  - Use smallcase for the summary.

### Different types in conventional commits

- `fix`: a commit of the type fix patches a bug in your codebase (this correlates with `PATCH` in Semantic Versioning).
- `feat`: a commit of the type feat introduces a new feature to the codebase (this correlates with `MINOR` in Semantic Versioning).
- BREAKING CHANGE: a commit that appends a `!` after the type/scope, introduces a breaking API change (correlating with `MAJOR` in Semantic Versioning). A BREAKING CHANGE can be part of commits of any type.
- Other non major types are:

  - `build`: Changes that affect the build system or external dependencies
  - `ci`: Changes to our CI configuration files and scripts (example GitHub Actions)
  - `docs`: Documentation only changes
  - `perf`: A code change that improves performance
  - `refactor`: A code change that neither fixes a bug nor adds a feature
  - `style`: Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc)
  - `test`: Adding missing tests or correcting existing tests
  - `chore`: Commits with the type chore are used to indicate routine tasks, maintenance, or other non-functional changes that are not directly related to user-facing features or bug fixes. No production code change.
    - For example updating dependencies or creating releases if it needs a commit.

- Additional types are not mandated by the Conventional Commits specification, and have no implicit effect in Semantic Versioning (unless they include a BREAKING CHANGE).

### Scopes

- A scope may be provided to a commit’s type, to provide additional contextual information and is contained within parenthesis, e.g., `feat(parser): add ability to parse arrays`.
- A scope MUST consist of a noun describing a section of the codebase surrounded by parenthesis, e.g., `fix(parser):`

## Miscellaneous

- You can use Vscode plugins to generate conventional commits.

## References

- [Official documentation](https://www.conventionalcommits.org/en/v1.0.0/#summary)
- [Commitlint](https://commitlint.js.org/#/guides-local-setup)

## Installing tools

### commitlint

```bash
npm init -y
npm install --save-dev @commitlint/{cli,config-conventional}
echo "module.exports = { extends: ['@commitlint/config-conventional'] };" > commitlint.config.js
```

Create a commitlint script in `package.json`

```bash
echo "hello world" | npm run commitlint
```

## To test

- How does it behave when using pull requests.
  - Like can I have multiple wips while developing the code and then a single pull request?
- If I have developed multiple features then should I split them into separate commits before pushing them?
- Check commitlint and commitzen
- Check release it
