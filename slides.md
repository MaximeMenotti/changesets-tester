---
# try also 'default' to start simple
theme: default
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://cover.sli.dev?3
# some information about your slides, markdown enabled
title: Changesets
info: |
  ## Changesets simple presentation

  Learn more on [github](https://github.com/changesets/changesets)
# apply any unocss classes to the current slide
class: text-center
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# https://sli.dev/guide/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations#slide-transitions
transition: slide-left
# enable MDC Syntax: https://sli.dev/guide/syntax#mdc-syntax
mdc: true
---

# Changesets

A release facilitator?

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Press Space for next page <carbon:arrow-right class="inline"/>
  </span>
</div>

<div class="abs-br m-6 flex gap-2">
  <a href="https://github.com/slidevjs/slidev" target="_blank" alt="GitHub" title="Open in GitHub"
    class="text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
</div>

---
layout: quote
transition: fade-out
---

# What is Changesets?

A tool to manage versioning and changelogs with a focus on multi-package repositories

> The `changesets` workflow is designed to help when people are making changes, all the way through to publishing. It lets contributors declare how their changes should be released, then we automate updating package versions, and changelogs, and publishing new versions of packages based on the provided information.

---
layout: image-right
image: https://cover.sli.dev?1
transition: slide-up
---

# Installation

Has any npm package: 

```shell
npm install @changesets/cli && npx changeset init
```
or

```shell
yarn add @changesets/cli && yarn changeset init
```
<br/>

And init the needed `.changesets` folder by running: 

```shell
yarn changeset init
```

<br/>

<span v-mark.red="1">Important</span>: you need to define a base version in your package.json file to work properly.


---
layout: center
image: https://cover.sli.dev?2
---


# Add changesets

Once you have done all you changes, you can ask changesets to generate changes metadata:

````md magic-move
```shell
➜ yarn changeset
yarn run v1.22.19
🦋  What kind of change is this for changesets-tester? (current version is 0.1.0) … 
❯ patch
  minor
  major
```


```shell {4-6}
➜ yarn changeset
yarn run v1.22.19
🦋  What kind of change is this for changesets-tester? (current version is 0.1.0) · minor
🦋  Please enter a summary for this change (this will be in the changelogs).
🦋    (submit empty line to open external editor)
🦋  Summary › add base slide 
```

```shell {8-10}
➜ yarn changeset 
yarn run v1.22.19
🦋  What kind of change is this for changesets-tester? (current version is 0.1.0) · minor
🦋  Please enter a summary for this change (this will be in the changelogs).
🦋    (submit empty line to open external editor)
🦋  Summary · add base slide
🦋  
🦋  === Summary of changesets ===
🦋  minor:  changesets-tester
🦋  
🦋  Is this your desired changeset? (Y/n) › true
```

```shell {10-12}
➜ yarn changeset
yarn run v1.22.19
🦋  What kind of change is this for changesets-tester? (current version is 0.1.0) · minor
🦋  Please enter a summary for this change (this will be in the changelogs).
🦋    (submit empty line to open external editor)
🦋  Summary · add base slide
🦋  
🦋  === Summary of changesets ===
🦋  minor:  changesets-tester
🦋  
🦋  Is this your desired changeset? (Y/n) · true
🦋  Changeset added! - you can now commit it
🦋  
🦋  If you want to modify or expand on the changeset summary, you can find it here
🦋  info /Users/mac-MMENOT19/Sites/changesets-tester/.changeset/large-items-invite.md
```

````
---
level: 2
---

# Create a new version

```shell
➜ yarn changeset version
```

This will:

- Compile all changesets to add to the `CHANGELOG.md`
- Create a new version using semver depending on changes
- Update the version in `package.json`

<br/> 

---
level: 2
---

# Changelog sample 

```md
# changesets-tester

## 0.2.0

### Minor Changes

- 9cd5249: add base slide

### Patch Changes

- 9cd5249: add slides for version
```

---

# Changeset bot

<img v-click.hide="1" class="mx-auto h-98" src="https://user-images.githubusercontent.com/11481355/66183943-dc418680-e6bd-11e9-998d-e43f90a974bd.png" />

<img v-click class="mx-auto h-98" src="https://user-images.githubusercontent.com/11481355/66184229-cf716280-e6be-11e9-950e-0f64a31dbf15.png" />

[Learn more](https://github.com/apps/changeset-bot)

<style>
  .slidev-vclick-hidden {
    display: none;
  }
  </style>


---

# Changeset CI

<div class="flex gap-8">

Their is a way to automate version generation by using provided Github action. This will create a PR running `yarn changesets version` and can also have a publish function that can be trigger on merge.


<img class="w-3/5 rounded shadow-xl" src="/ci.png" />
</div>