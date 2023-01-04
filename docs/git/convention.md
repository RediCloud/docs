---
sidebar_position: 1
---

# Commit convention

We use [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) to standardize our commit messages.

## Commit message format

A commit message consists of a **type**, a **scope** and a **subject**:

```text
<type>(<scope>): <subject>
```

## Type

The type can be **one** of these types:

- **feat**: A new feature
- **fix:** A bug fix
- **build:** Build related changes (eg: gradle related/ adding external dependencies)
- **chore:** A code change that external user won't see (eg: change to .gitignore file or .prettierrc file)
- **docs:** Documentation related changes
- **refactor:** A code change that rename a parts of code like variable name or function name can also be used when updating dependencies to a newer major version
- **perf:** A code that improves performance
- **style:** A code that is related to styling
- **test:** Adding new test or making changes to existing test

## Scope

The scope is optional and can be used to indicate which part of the codebase the commit is related to. For example, if the commit is related to a Paper api, the scope can be `api-paper`.

## Subject

The subject contains a succinct description of the change:

- use the imperative, present tense: "change" not "changed" nor "changes"
- don't capitalize the first letter
- no dot (.) at the end

## Breaking change

If the commit has a breaking change, it should append a `!` after the type/scope.

If the breaking change is affects large amounts of code, it should also append a `BREAKING CHANGE:` in the body or footer.

A breaking change can be part of commits of any type.

## Body

The body is optional and can be used to provide a more detailed description of the change. It should include the motivation for the change and contrast this with previous behavior.

## Footer

The footer is optional and is used to reference issue tracker IDs.

---

## Examples

### Commit message with description and breaking change in body

```text
feat: allow provided config object to extend other configs

BREAKING CHANGE: `extends` key in config file is now used for extending other config files
```

### Commit message with a body and a footer

```text
fix: correct minor typos in code

see the issue for details on the typos fixed

closes issue #12
```
