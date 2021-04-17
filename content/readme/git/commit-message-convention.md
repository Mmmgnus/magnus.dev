---
title: "Commit message convention"
date: 2020-03-12T19:48:22+02:00
draft: true
---

There is a [convention for GIT commits](https://www.conventionalcommits.org/) that seems to be used by a bunch of people on the internet. The convention originally comes from the [Git patches guidelines](https://git.kernel.org/pub/scm/git/git.git/tree/Documentation/SubmittingPatches?id=HEAD)

The benefits of this kind of convention is:
- Easy to read list of commit.
- Possible to autogenerate the changelog.

The format of the convention is:
```
<type>(<scope>): <subject>

<body>

<footer(s)>
```

Example:
```
feat(sign-in): Add reset password functionality

New button added on the sign-in component to reset the password.

BREAKING CHANGE: Adding label to a Button component is done by adding it to the body of the button and not via the label attribute.
```

The first line of the commit message should be a short description (50 characters)

## Type
- `fix`: Bug fixes (not build fixes)
- `build`: Build related changes (npm, webpack, gulp)
- `ci`: Continues integration related changes
- `docs`: Documentation changes
- `feat`: A new feature
- `perf`: Performance related changes
- `refactor`: A code change that neither fixes a bug or adds a feature
- `style`: Code style related changes that not affect the meaning of the code (missing semi-colons, white-space)
- `test`: Test related changes.

We can add a `!` to the end of the type to signal that the commit contain a breaking change.

## Scope *(optional)*
The scope is useful to signal what part of the code base that has changed.

## Subject
Short description starting with a lower-case letter. And remember, keep it short, first line has a soft limit of 50 characters.

- Uses the imperative, present tense: "change" not "changed" or "changes"
- Don't end the subject with a period (.)

## Body
- Uses the imperative, present tense: "change" not "changed" or "changes"
- Include motivation for the change, and contrasts its implementation with previous behaviour
- The body should explain the problem the change is trying to solve.
- Justify the way the change solves the problem, i.e Why the result with the change is better.
- Try to make sure the explanation can be understood without external resources.

## Footer(s) *(optional)*
Some flavour of the convention uses a *footer* at the bottom to notify that a breaking change was made in the commit.

```
BREAKING CHANGE: 
```


## Why use the imperative, present tense?
I may seen strange to write in the imperative, present tense; "change", "remove", "fix". Git is a distributed versioning control system, so changes to our code base can come from different places. If you think of your commits as commands/instructions instead of log entries; "remove unused code" vs "removed unused code".

As the creator of the commit, it makes more sense to write down that you did. But from the other side, the person who may apply the commit, is more interested in what the commit will do when we apply it.

This is also the way Git itself generate messages; "Merge", "Rebase".

## Links
- https://dev.to/i5han3/git-commit-message-convention-that-you-can-follow-1709
- http://karma-runner.github.io/1.0/dev/git-commit-msg.html
- https://365git.tumblr.com/post/3308646748/writing-git-commit-messages
- https://git.kernel.org/pub/scm/git/git.git/tree/Documentation/SubmittingPatches?id=HEAD
- https://github.com/fteem/git-semantic-commits
- https://www.conventionalcommits.org/
- https://github.com/angular/angular/blob/22b96b9/CONTRIBUTING.md#-commit-message-guidelines