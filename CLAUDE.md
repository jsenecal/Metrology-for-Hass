# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Metrology for Home Assistant is a collection of themes bringing Metro and Fluent design language (Microsoft Windows 10/11 style) to Home Assistant. It provides multiple color variants (Red, Blue, Green, Orange, Purple, Slate) with light and dark modes, plus custom Segoe UI typography.

This is a maintained fork of [Madelena/Metrology-for-Hass](https://github.com/Madelena/Metrology-for-Hass) with updates for Home Assistant 2025.5+ and 2025.8+ compatibility.

**Minimum requirement:** Home Assistant 2025.5+

## Architecture

**Single Theme File**: All theme definitions live in `/themes/metro.yaml`. This file uses YAML anchors extensively for DRY color definitions. Structure:
- Common base colors and HA 2025.5+ font variables (anchors at top)
- HA 2025.8+ neutral color palette
- Light/dark mode definitions
- 6 color variant themes, each with Fluent (Win11) and Metro (Win10) styles
- Each theme includes its own `ha-color-primary-*` palette (05-95 scale)

**Typography**: Font files in `/www/*.ttf` with `@font-face` definitions in `/www/style.css`

**No Build System**: This is a static configuration package. No dependencies, no build process.

## Validation

GitHub Actions validate on push/PR:
- **HACS Action**: Validates theme structure for Home Assistant Community Store compatibility
- **hassfest**: Home Assistant's official theme validator

To validate locally, push changes and check GitHub Actions results.

## Key Files

- `/themes/metro.yaml` - Main theme file (edit this for theme changes)
- `/www/style.css` - Font face definitions
- `/hacs.json` - HACS community registration config

## Theme Structure Conventions

When editing `metro.yaml`:
- Define reusable colors as YAML anchors at the top (e.g., `primary-color: &primary-color "#ff0000"`)
- Reference anchors with `*anchor-name`
- Maintain consistency across all 12 theme variants (6 colors × 2 styles)
- Theme CSS variables follow Home Assistant and Material Design conventions
- Support for Mushroom cards and Browser Mod custom properties is included

**HA 2025.x Compatibility:**
- Each theme must include `ha-color-primary-*` palette (05, 10, 20, 30, 40, 50, 60, 70, 80, 90, 95)
- The `-40` value should match the theme's `primary-color`
- Common base includes `ha-font-family-*`, `ha-font-size-*`, `ha-font-weight-*` variables
- Common base includes `ha-color-neutral-*` grayscale palette

## Code Style

- No trailing whitespace
- YAML indentation: 2 spaces
- Maintain existing anchor/reference patterns for color definitions
