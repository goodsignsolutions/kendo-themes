# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This project extends the open source [kendo-themes](https://github.com/telerik/kendo-themes) repo with custom themes (swatches) and a custom build task for copying the compiled CSS and swatch JSON files to the GoodSign.Portal project.

Always use the branch that matches the Kendo version used in GoodSign.Portal (e.g. `gs-2025.3.812` for Kendo version 2025.3.812).

## Commands

### Setup
```sh
npm ci
```


### Build
```sh
npm run sass:dist         # Compile and minify all themes for distribution
npm run sass:dist:copy    # Compile, minify, then copy output to KENDO_COPY_TARGET
```

### Cleanup
```sh
npm run clean             # Reset Nx cache and remove all node_modules
npm run clean:dist        # Remove dist/ from all packages
```

## Architecture



### Swatch system

Swatches are JSON files in `lib/swatches/` that override theme variables. The `.env` file controls which swatches get copied where:

```
KENDO_COPY_TARGET=d:/repos/goodsignsolutions/goodsign/src/GoodSign.Portal/Content/kendo/sass
KENDO_COPY_SWATCHES=fluent-main-gs,fluent-main-dark-gs
```

Run `npm run sass:dist:copy` to build and push output to the copy target.

