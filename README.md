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
npx kazuma1989/hello-npm
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

### With npm

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

### With GitHub

- You can use packages directly from GitHub without publishing to npm!  
  Use `npm install username/repo-name` format to reference the default branch or `npm install username/repo-name#branch` to specify some branch.
  - But sub directories are not referenced this way.  
    The above commands just downloads the tarball from the URL which is resolved from GitHub repo name, so without a URL from which we can download sub directories it is impossible to use sub directories (like Babel packages) as packages.
- **npx** has an escape hatch where we can use sub directories like packages.  
  In `package.json` the `bin` field may have multiple keys, so specify sub commands to point to binaries in sub directories, and call the sub commands with `npx -p username/repo-name sub-command`.
- GitHub Gist can also be used as a package.  
  Even though Gist cannot have directory structures, the `dependencies` field in `package.json` works well!
