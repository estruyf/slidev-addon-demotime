# slidev-addon-demotime

[![NPM version](https://img.shields.io/npm/v/slidev-addon-demotime?color=3AB9D4&label=)](https://www.npmjs.com/package/slidev-addon-demotime)

Slidev component to integrate with [Demo Time](https://demotime.elio.dev) a Visual Studio Code extension to simplify coding demos.

## Installation

```bash
npm install slidev-addon-demotime
```

Declare the addon in your front matter of the `slidex.md` file:

```md
---
addons:
  - slidev-addon-demotime
---
```

## Usage

```md
---
clicks: 1 // Define the click count
---

# Slide 1

This slide triggers the first demo after **1** click.

<vscode-action
    click="1"
    id="demo1" />
```

> **Important**: The `clicks` property in the frontmatter is required, otherwise the slide will not trigger the demo.

## Options

- `click`: The number of clicks to trigger the demo.
- `id`: The demo ID to trigger.
- `port`: The port where the Demo Time server is running. Default is `3710`.
- `host`: The host where the Demo Time server is running. Default is `http://localhost`.
- `image`: The image to show in the slide. Default is the Demo Time logo.
