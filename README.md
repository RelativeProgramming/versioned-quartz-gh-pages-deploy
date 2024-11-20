# Versioned Quartz GitHub Pages Deployment Action
GitHub Action for the deployment of versioned [Quartz](https://github.com/jackyzha0/quartz) sites to GitHub Pages.
This allows for the parallel hosting of sites for multiple versions of the same repository.
The hosted static sites are stored on a separate branch.

For the simpler, unversioned setup see [Quartz GitHub Pages Deployment Action](https://github.com/RelativeProgramming/quartz-gh-pages-deploy)

**Usage:**
See `action.yml` for parameters.

**Example Configuration:**
```yml
jobs:
  publish_job:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout repository
      uses: actions/checkout@v4

    - uses: RelativeProgramming/versioned-quartz-gh-pages-deploy@main
      with:
        quartz-version: v4.4.0
```
- documentation Markdown files are placed under `./docs/`
- modified `quartz.config.ts` is placed under `./docs/.quartz-config/`


**Tips:**
You can freely add or remove content from the `gh-pages` branch (or the one you configured via the `gh-pages-branch` input).
For Example: To redirect from the main page to the `current` page, just add a `index.html` with the follow content to the root directory of the `gh-pages` branch:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="refresh" content="0; url=./current/" />
    <title>Redirecting...</title>
  </head>
  <body>
    <p>
      If you are not redirected automatically,
      <a href="./current/">click here</a>.
    </p>
  </body>
</html>
```