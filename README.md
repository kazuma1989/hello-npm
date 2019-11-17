# hello-npm

For my personal training

## Getting started

npx from npm:

```bash
npx @kazuma1989/hello-npm
# Hello npm!
```

npx from GitHub:

```bash
npx kazuma1989/hello-npm#master
# Hello npm!
```

## Publish to npm

First, update the version of the package (major|minor|patch):

```bash
npm version patch
```

Or you can change the version field in `package.json` manually.

Then publish:

```bash
npm publish
```

You will get an email from npm when success.

# What I learned

- Sign in before publishing.  
  Sign up via the npm website and run `npm adduser` in CLI terminal.
- Files to publish are not necessarily versioned by Git.
- Scoped packages (like `@scopename/xxx`) are **private** by default.  
  Use `npm publish --access public` command for the first time.  
  For following publish commands, the access option can be omitted.
- Scope name is reserved for each user or organization.  
  I could not publish `@k/hello-npm` (npm returns 401) because I am _@kazuma1989_.
- Local files are all published.  
  Write the `.npmignore` file carefully or follow the pattern in which paths are ignored by default.  
  I usually use a `._*` pattern for my local files without publishing or versioning.  
  Detail: http://npm.github.io/publishing-pkgs-docs/publishing/the-npmignore-file.html
