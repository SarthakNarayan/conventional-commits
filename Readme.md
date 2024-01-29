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

## References

- [Official documentation](https://www.conventionalcommits.org/en/v1.0.0/#summary)
- [Commitlint](https://commitlint.js.org/#/guides-local-setup)
- [Commitizen](https://www.npmjs.com/package/commitizen#making-your-repo-commitizen-friendly)
- https://davipon.hashnode.dev/add-commitlint-commitizen-standard-version-and-husky-to-sveltekit-project#heading-commitizenhttpsgithubcomcommitizencz-cli

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

- It is mostly used by CI tools and precommit hooks

### Commitizen

```bash
sudo npm install commitizen -g
commitizen init cz-conventional-changelog --save-dev --save-exact
```

### Standard version

```bash
npm install -D standard-version
```

Add a script to `package.json` for running standard-version.

```bash
npm run release -- --first-release # for first release
npm run release # subsequent releases
npm run release -- --no-verify # prevent git hooks being run at the commit step
```

## Miscellaneous

- You can use Vscode plugins to generate conventional commits.
- If I have developed multiple features then should I split them into separate commits before pushing them?
  - Yes. So suppose you have made any documentation releated changes to readme and some code related changes then they should be different commits.
- If you use branches to develop features then:
  - If you plan to squash the commits then ensure that the squashed commit has a meaningful summary that follows the conventional commits pattern. This means while developing in a branch commit messages need not follow conventional commits pattern.
  - If you just merge the commits as is then ensure that all the commits follow the conventional commits pattern.
