
# Browsers

## Chromium

The [keyboard shortcuts](https://developer.chrome.com/docs/devtools/shortcuts) for Chromium's DevTools provide a good survey of the features available.

### Visbug

[Visbug](https://chromewebstore.google.com/detail/visbug/cdockenadnadldjbbgcallicgledbeoc) is a Chrome extension that allows you to more easily grok the DOM. You can do things like measure distances between elements, change colors, save changes to page. You can test the extension's features in [visbug.web.app](https://visbug.web.app/)

## Firefox

An overview of the Firefox DevTools feature set can be found in their docs on [shortcut keys](https://firefox-source-docs.mozilla.org/devtools-user/keyboard_shortcuts/index.html#keyboard-shortcuts-opening-and-closing-tools).

# VSCode

## Extensions

If an extension is found in the `.vscode/recommended.json`, we've tested that it's generally compatible with other extensions in that file.

### Frontend

|            name |          key           | description                                                      |
| --------------: | :--------------------: | :--------------------------------------------------------------- |
| prettier-vscode | esbenp.prettier-vscode | Autoformats html, css/scss/less, javascript/json, markdown, yaml |
|   vscode-eslint | dbaeumer.vscode-eslint | Cleans code, catches simple mistakes and adds missing semicolons |
|     vscode-yaml |   redhat.vscode-yaml   | Quickly checks the format of Jekyll's `_config.yml` for you      |
|          liquid | sissel.shopify-liquid  |                                                                  |

- `vscode-yaml` may require configuring the [Jekyll YAML schema](https://json.schemastore.org/jekyll), but it should autodownload once it's set.
- `vscode-thunder-client`: allows you to test making requests to API's. It may be helpful when working on automation later.

#### Liquid

[Liquid extension](https://github.com/panoply/vscode-liquid)

A `.liquidrc` file needs to be present and a generator can be found in the command pallette. The engine should be set to `standard`.

To make the liquid extension work, see [the response on this post](https://talk.jekyllrb.com/t/jekyll-liquid-visual-studio-code/5531/6)

#### YAML

To enable parsing of YAML for Jekyll and Docker Compose, your `.vscode/extensions.json` file should contain at least `yaml.schemas`.

The schema association for a YAML file can be set in a file-local variable. See [Associating Schemas](https://marketplace.visualstudio.com/items?itemName=redhat.vscode-yaml).

```json
{
  "yaml.format.enable": true,
  "yaml.format.singleQuote": null,
  "yaml.format.bracketSpacing": true,
  "yaml.format.proseWrap": "preserve",
  "yaml.format.printWidth": 80,
  "yaml.validate": true,
  "yaml.hover": true,
  "yaml.completion": true,
  "yaml.schemas": {
    "https://json.schemastore.org/jekyll": "site/_config.yml",
    "https://raw.githubusercontent.com/compose-spec/compose-spec/master/schema/compose-spec.json": "/docker-compose.*.yml"
  },
  "yaml.customTags": null,
  "yaml.maxItemsComputed": 5000
}
```

### Git

- Gitlens is an alternative to git-graph, but is more likely to impact performance. When GitLens is used, the other four extensions below should be disabled or deleted.
- With `vscode-pull-request-github`, you can manage the Github project from VSCode to create or respond to pull requests and issues.

|      name |           key           | description                                                              |
| --------: | :---------------------: | :----------------------------------------------------------------------- |
| git-graph |   mhutchie.git-graph    | Shows git history to help you navigate branches and check changesets     |
|  gitstash |    arturock.gitstash    | Quickly "stash" and "unstash" changes to pull updates or change branches |
| git-blame | solomonkinard.git-blame | Shows where a line of code came from and what's in the same commit       |
|  gitpatch |   paragdiwan.gitpatch   | Advanced tool for contributing to projects with email-based workflows    |

Other Git Extensions

- I you're new to git: `git-graph`, `gitstash` and perhaps `gitignore` may be useful
- `vscode-conventional-commits` may be helpful to format commits (IDK)
- `vscode-gitweblinks` can help to quickly communicate about code

### Docs

The `manpages` extension allows you to open docs from `man` for entries it finds in your `MANPATH`.

### Future Extensions

#### Tailwind CSS

+ bradlc.vscode-tailwindcss
+ csstools.postcss

## Web development

### Emmet

EmmetCSS is included by default. It allows you to type abbreviated CSS selectors and have them expand into DOM. It also works for XML.

- How to use [Emmet HTML/CSS Snippets](https://code.visualstudio.com/docs/editor/emmet)
- [Emmet Cheatsheet](https://docs.emmet.io/cheat-sheet/): altogether a great reference for HTML5 and CSS3. The cheatsheet includes information on flexbox, but not CSS3 grids.

### Completion and Documentation

All the Web Development LSP should just work (HTML/CSS/JS), but may require some
configuration.

### Formatting and Linting

The `prettier` and `eslint` extensions are particularly helpfu, but may require running `npm install -g $pkg`. They mainly make pull requests much smaller and and simpler, especially for javascript. Extremely helpful, but if these tools aren't working in your environment, it's not worthwhile in this project.

Combining them may require [prettier-eslint](https://www.npmjs.com/package/prettier-eslint). It would be simpler to just disable eslint, especially if you're not writing javascript.

#### Prettier

To use prettier to format HTML with Liquid outside of VSCode, you'll need to run
`npm install --save-dev @shopify/prettier-plugin-liquid` and set the following
in `.prettierrc`.

```yaml
# -*- mode: yaml -*-
---
plugins:
  - "@shopify/prettier-plugin-liquid"
overrides:
  - files: "*.html"
    options:
      parser: "liquid-html"
```
