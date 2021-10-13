# Customized JSON Resume Theme: GitHub

🖼️ This is a slightly tweaked version of the [GitHub theme](https://github.com/mathieudutour/jsonresume-theme-github). Tweaked to fit my design preferences. Published on NPM and GitHub Registry.

<details>
  <summary>Click to expand README.md of the source repository!</summary>


## JSON Resume Theme Github

A JSON Resume theme looking like a GitHub profile.

_Inspired by [@nataliemarleny](https://twitter.com/nataliemarleny). Built using [Primer](https://primer.style/css)._

## Preview

The theme can be previewed at [https://mathieudutour.github.io/jsonresume-theme-github](https://mathieudutour.github.io/jsonresume-theme-github).

## Getting Started

Checkout [https://jsonresume.org/getting-started/](https://jsonresume.org/getting-started/).

There are some addition to the JSON Resume schema in order to control the "pinned" stuff.
You can add `"pinned": true` to any `work`, `volunteer`, `award`, `publications`, `education`, or `projects`.

### Automatically publish your resume

Create a new repository with 2 files:

- `resume.json`: your JSON resume.
- `.github/workflows/publish_resume.yml`:

  ```yaml
  name: "Publish Resume"
  on:
    push:
      branches:
        - master

  jobs:
    publish_resume:
      runs-on: ubuntu-latest
      steps:
        - uses: actions/checkout@v1
        - uses: actions/setup-node@v1

        - name: Install the dependencies
          run: npm install resume-cli jsonresume-theme-github

        - name: Build the resume
          run: ./node_modules/.bin/resume export public/index.html --theme github

        - name: Deploy
          uses: peaceiris/actions-gh-pages@v3
          with:
            github_token: ${{ secrets.GITHUB_TOKEN }}
            publish_dir: ./public
  ```

## License

MIT
  
  </details>
