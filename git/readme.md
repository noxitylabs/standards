# Conventional Commits

A specification for adding human and machine-readable meaning to commit messages.

## Introduction

Conventional Commits is a standard that improves the readability and organization of commit history. It provides a set of rules and conventions for creating an easy-to-follow history of changes.

## Specification

### Commit Message Format

A commit message consists of a **header**, **body**, and **footer**.

**Header**: Contains a type, optional scope, and subject:

```<type>[optional scope]: <description>```


**Type**: Indicates the nature of the commit:

- `feat`: A new feature
- `fix`: A bug fix
- `docs`: Documentation only changes
- `style`: Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc)
- `refactor`: A code change that neither fixes a bug nor adds a feature
- `perf`: A code change that improves performance
- `test`: Adding missing tests or correcting existing tests
- `build`: Changes that affect the build system or external dependencies (example scopes: gulp, broccoli, npm)
- `ci`: Changes to our CI configuration files and scripts (example scopes: Travis, Circle, BrowserStack, SauceLabs)
- `chore`: Other changes that don't modify src or test files
- `revert`: Reverts a previous commit

**Scope**: Provides additional context about the commit, such as the affected module, package, or feature.

**Description**: A brief summary of the changes (max 50 characters).

### Examples

#### A new feature:

```feat(parser): add ability to parse arrays```

#### A bug fix:

```fix(header): fix typo in header```


### Body

The body includes a detailed explanation of the changes, reasons behind them, and any other relevant information.

Example:

```
feat(parser): add ability to parse arrays

This feature adds a new function to parse arrays, which helps in...
```


### Footer

The footer is optional and used to reference issues or breaking changes.

#### Referencing issues:

```
fix(parser): resolve issue with array parsing

Closes #123
```


#### Breaking changes:

```
feat(api): update API endpoints

BREAKING CHANGE: The API endpoints have been updated...
```


## Usage

Adopting Conventional Commits ensures a clear and systematic project history, making it easier to track changes and understand the project's evolution.

## Changelog

- Initial release of Conventional Commits documentation.

## Contribution

Feedback and contributions are welcome. Please follow the Conventional Commits specification when making commits to this project.

## License

MIT License.
