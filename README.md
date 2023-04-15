<p align="center"><img src="/assets/logo-text.svg" height="100" alt="minibar"></p>

<div align="center">

[![Continuous integration](https://github.com/jquery/typesense-minibar/actions/workflows/CI.yaml/badge.svg)](https://github.com/jquery/typesense-minibar/actions/workflows/CI.yaml?query=event%3Apush+branch%3Amain)
[![Test coverage](https://img.shields.io/badge/coverage-89%25-brightgreen.svg)](https://jquery.github.io/typesense-minibar/coverage/)
[![Tested with QUnit](https://img.shields.io/badge/tested_with-qunit-9c3493.svg)](https://qunitjs.com/)

</div>

**minibar** is a fast 2kB autocomplete search bar for [Typesense](https://typesense.org/). It is an alternative to typesense-docsearch.js, Algolia DocSearch, InstantSearch, autocomplete-js, and typesense-js.

## Features

* **Dependency-free**, vanilla JavaScript
* **Small size**, 2kB transfer size
* **Progressive enhancement**, works without JavaScript
* **Responsive**, mobile-first layout
* **Accessible**, keyboard navigation, arrow keys, close on `Esc` or outside click
* **Fast**, leverages preconnect (Resource Hints), LRU memory cache
* **Easy to install**, fully declarative via HTML (no-code setup!)

## Getting started

**[Demo](https://jquery.github.io/typesense-minibar/demo/)**

```html
<form role="search" class="tsmb-form"
      data-origin=""
      data-collection=""
      data-key="">
  <input type="search">
</form>
```

```html
<script defer type="module" src="typesense-minibar.js"></script>
<link rel="stylesheet" href="typesense-minibar.css">
```

## API

### Configuration

* ***data-origin*** (Required): Base URL to your Typesense server.

  Include the `https://` or `http://` protocol, and (if non-default) the port number.

  Example: `https://typesense.example.org`

* ***data-collection*** (Required): Which collection to query.

  Equal to the `"index_name"` in your `docsearch.config.json` file. If you index your websites
  with something other than [docsearch-scraper](https://github.com/typesense/typesense-docsearch-scraper),
  set this to the name of your Typesense collection ([Typesense API](https://typesense.org/docs/0.24.1/api/collections.html)).

  Example: `example_mine`

* ***data-key*** (Required): Search-only API key ([Typesense API](https://typesense.org/docs/0.24.1/api/api-keys.html#generate-scoped-search-key)).

  Example: `write000less000do000more0`

* [***data-slash***=true] (Optional): Focus the input field if the `/` slash key is pressed.

  When enabled, a `keydown` event listener is added to `document`. Key presses in `<input>` or `<textarea>` elements are safely ignored. If multiple search forms are initiatilised on the same page, the first has precedence.

  Set `data-slash="false"` to disable this feature.

* [***data-group***=false] (Optional): Group results under category headings.

  By default, search results are presented in a flat list, with the `lvl0` field
  interpreted as the page title, where `lvl0` typicaly selelects `h1`, `lvl1`
  selects `h2`, and so on.

  To group results under category headings, configure your [docsearch-scraper](https://github.com/typesense/typesense-docsearch-scraper)
  to have a `lvl0` selector that matches an element on your page that represents
  the multi-page group that a page belongs to, and `lvl1` would then instead
  select your `h1` page titles.

  Set `data-group="true"` to enable this feature.

## Compatibility

| typesense-minibar | typesense-server | typesense-docsearch-scraper
|--|--|--
| 1.0.x | >= 0.24 | 0.6.0.rc1 <!-- adds "group_by=url_without_anchor" -->

## Browser support

The below matrix describes support for the _enhanced_ JavaScript experience. The basic HTML experience, which falls back to submitting a form to DuckDuckGo, works in all known browsers (including IE 6, IE 5 for Mac, and Netscape Navigator).

| Browser | Policy | Version
|--|--|--
| Firefox | Current and previous version,<br>Current and previous ESR | Firefox 74+ (2020)
| Chrome | Last three years | Chrome 80+ (2020)
| Edge | Last three years | Edge 80+ (2020)
| Opera | Last three years | Opera 67+ (2020)
| Safari | Last three years | Safari 13.1 (2020)
| iOS | Last three years | iOS 13.4 (2020)

<sup>Notable feature requirements: ES6 syntax, ES2020 Optional chaining, ES2022 Async functions, DOM NodeList-forEach.</sup>

Practical implications:

| OS | Supported from | Running
|--|--|--
| Android | [Moto G4](https://en.wikipedia.org/wiki/Moto_G4) (2016) | Android 7.0 with Chrome 80+
| Android | [Samsung Galaxy S7](https://en.wikipedia.org/wiki/Samsung_Galaxy_S7) (2016) | Android 7.0 - 8.0
| Android | [Samsung Galaxy A5](https://en.wikipedia.org/wiki/Samsung_Galaxy_A5_(2016)) (2016) | Android 7.0
| Android | [Google Pixel 1](https://en.wikipedia.org/wiki/Pixel_(1st_generation)) (2016) | Android 7.0
| iOS | [iPhone 6S](https://en.wikipedia.org/wiki/IPhone_6S) (2015) | iOS 13.4 (2020) upto iOS 15 (2022)
| Linux | Debian 9 Stretch (2018) | [firefox-esr](https://packages.debian.org/oldoldstable/firefox-esr) (91)
| Linux | Debian 10 Stretch (2019) | [firefox-esr](https://packages.debian.org/oldstable/firefox-esr) (102), [chromium](https://packages.debian.org/oldstable/chromium) (90)
| Linux | Ubuntu 18.04 LTS (2018) | current [firefox](https://packages.ubuntu.com/bionic/firefox), current [chromium-browser](https://packages.ubuntu.com/bionic/chromium-browser)
| macOS | OS X 10.9 Mavericks (2013-2016) | Firefox 78 ESR (2020)<br>(Safari 7 default unsupported)
| macOS | OS X 10.13 Mavericks (2017-2020) | Firefox 78 ESR (2020), Chrome 80+<br>(Safari 11 default unsupported)
| macOS | OS X 10.15 Catalina (2019-2022) | Safari 13.1, Firefox 78 ESR (2020), Chrome 80+
| Windows | Windows 7 (2009) or later | current Edge, current Firefox

Notes:
* [Firefox release schedule](https://whattrainisitnow.com/calendar/)
* [iOS 16 dropped support](https://en.wikipedia.org/wiki/IOS_16#Supported_devices)
* [Google Chrome requires Android 7.0 and macOS 10.13](https://support.google.com/chrome/a/answer/7100626?hl=en)
* [Firefox 48 last to support OS X 10.6-10.8](https://www.mozilla.org/en-US/firefox/48.0/releasenotes/)
* [Firefox 78 last to support OS X 10.9-10.11](https://www.mozilla.org/en-US/firefox/78.0/releasenotes/)

## Feedback

For questions, bug reports, or feature requests, use the [Issue tracker](https://github.com/jquery/typesense-minibar/issues).
