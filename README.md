# Customized JSON Resume Theme: GitHub

🖼️ This is a tweaked version of the [GitHub theme](https://github.com/mathieudutour/jsonresume-theme-github). Tweaked to fit my design preferences. Published on NPM and GitHub Registry.

## Notable Changes

* Added sections for speaking and articles
* Style changes

## Prerequisites

To build and start the local server, it needs to use the cli command, which is custom cli I tweaked.

`npm i @anthonyjdella/customized-resume-cli`

## How to Start

`npm run start`

## How to Change

* `resume.handlebars` is the order of the resume.
* `style.scss` is the styling
* To make changes to the PDF/printable version, make changes in the `@print` section of `style.scss`
* Change version number in `package.json`
* Deploy the changes via `npm publish --access public`
* To see changes from `resume.anthonydellavecchia.com` you need to go to the [registry project](https://github.com/anthonyjdella/customized-registry-functions), then cd into `functions`, run `npm i` and `npm update`, then `firebase deploy`.

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
