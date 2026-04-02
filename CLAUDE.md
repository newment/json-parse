# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A collection of browser-based developer utility tools. All pages are pure HTML/CSS/JavaScript with no build step required — open any HTML file directly in a browser.

## Architecture

**Shell Pattern**: `index.html` is the main shell with sidebar navigation that loads other tools in an iframe. Each tool page is also independently viewable by opening it directly.

**File Structure**:
- `index.html` — Main shell with sidebar navigation
- `sidebar-component.js` — Reusable sidebar component with theming (default/dark/light)
- `json-format.html` — JSON formatter with collapsible tree view
- `json-escape.html` — JSON escape/unescape/compress
- `text-compare.html` — Text diff using LCS algorithm
- `timestamp.html` — Timestamp (ms/s) ↔ datetime converter
- `url-encode.html` — URL component/full encode/decode
- `base64.html` — Base64 encode/decode with file support
- `assets/` — Static assets (favicon)

## Tools

### JSON Formatter (json-format.html)
- Parses and visualizes JSON in a collapsible tree structure
- Color-coded syntax (keys, strings, numbers, booleans, null)
- Debounced auto-parsing on input (300ms)
- Ctrl+Enter to manually trigger parsing

### JSON Escape (json-escape.html)
- Compress JSON (remove whitespace)
- Escape text for JSON use
- Unescape JSON-escaped text
- Swap input/output and reprocess
- Auto-compresses valid JSON on input

### Text Compare (text-compare.html)
- Line-by-line diff using LCS algorithm
- Options: ignore spaces, ignore case, show line numbers
- Visual diff highlighting (added/removed/unchanged)
- Stats summary (added, removed, unchanged lines)

### Timestamp Converter (timestamp.html)
- Current time display with live updating
- Convert ms or second timestamps to datetime
- Convert datetime to both ms and second timestamps
- Auto-detects 10-digit vs 13-digit timestamps

### URL Encoder (url-encode.html)
- URL Encode / Decode (encodeURI / decodeURI)
- Component Encode (encodeURIComponent) for query params
- Full URL Encode for complete URL strings
- Auto-processes on input with 500ms debounce

### Base64 (base64.html)
- Encode text to Base64
- Decode Base64 to text
- File to Base64 (drag or select, outputs data URL)
- Auto-detects input type and processes accordingly

## Shared UI Patterns

- Two-panel layout (input left, output right) on desktop; stacked on mobile
- Primary accent color: `#667eea`
- Buttons: `.btn-primary`, `.btn-secondary`, `.btn-success`, `.btn-danger`
- Monospace fonts for code/timestamps (Monaco, Menlo, Courier New)
- Empty states with emoji icons
- Debounced auto-processing on input fields

## Development

No build step. To run locally:
```bash
# Open directly in browser
open index.html

# Or serve with any static server
python3 -m http.server 8000
```

## Design Notes

- Responsive breakpoints at 768px and 968px
- Mobile layout switches sidebar to horizontal top nav
- All CSS is inline within each HTML file
- No external JS dependencies (except Google Fonts CDN)