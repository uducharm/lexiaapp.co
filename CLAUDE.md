# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**Ilena** is a human-centered AI writing companion designed for serious songwriters and lyricists.
Rather than generating lyrics automatically, Ilena enhances the creative process by providing intelligent feedback on rhythm, structure, tone, and language — while preserving full author control.

The product addresses a core tension in modern creative tools: automation versus authorship. Ilena positions itself clearly on the side of authorship. AI assists, but never replaces the writer.

Built as a cloud-native SaaS platform, Ilena offers:
- Real-time rhythm and syllable analysis
- Rhyme suggestions (perfect, near, and slant)
- Grammar and language refinement
- Style feedback and structural insights
- Secure cloud storage for works-in-progress

The platform targets independent lyricists, semi-professional songwriters, and creative professionals seeking a disciplined yet supportive writing environment.

Ilena’s differentiation lies in its philosophy:

> Precision over automation.
> 
> Craft over content generation.
> 
> Assistance without replacement.

The long-term vision is to establish Ilena as the reference AI companion for serious songwriters — a tool that strengthens creative autonomy rather than diluting it.

## Deployment

No build step required. The site is a single `index.html` file served directly by GitHub Pages. Push to `main` to deploy.

## Architecture

**Single-file site:** All HTML, CSS, and layout lives in `index.html` (~770 lines). There is no JavaScript, no external stylesheets, and no build tooling.

**Key design tokens (CSS variables in `index.html`):**
- Primary accent: `#7c5cfc` (purple)
- Dark background theme
- Typography uses `clamp()` for fluid scaling

**Assets:**
- `assets/ilena.png` — logo
- `assets/favicon.ico` / `assets/ilena.ico` — favicons
- `BrandBook.md` — brand guidelines (reference before making visual changes)

## Content Structure

Sections in `index.html` (in order): Hero → Problem → Features → How It Works → Credibility → Pricing → Tech Stack → Footer.

Pricing tiers: Free, Pro, Studio.

## Conventions

- All styling is inline within `index.html` via a `<style>` block — do not create separate `.css` files unless the user requests it.
- `robots.txt` intentionally blocks all crawlers (`Disallow: /`) — this is by design for the beta period.
- The `.gitignore` contains Java/Helm/Skaffold entries inherited from a template; these can be ignored.

## Urls
- `https://www.ilena.app` --> domain
- domain + /[locale]/ --> locale
- domain + /[locale]/[flowname] --> flow
  - create --> create flow
  - login --> login flow
  - app --> app flow
- `https://www.ilena.app/[locale]/app` --> baseurl for app
- `https://www.ilena.app/[locale]/app/invoicing` --> invoicing microservice
- `https://www.ilena.app/[locale]/app/profiles` --> profiles microservice
- `https://www.ilena.app/[locale]/app/notification` --> notification microservice

## 📖 Ilena — Core Terminology Glossary
### Artist

Definition:

An individual user of Ilena who creates written works (lyrics, poems, or other structured text).

Notes:
- An Artist owns their Projects and Works.
- An Artist may belong to one or multiple Studios.
- In database terms: primary account entity.

### Studio

Definition:

A collaborative space where multiple Artists can work together on shared Projects.

Notes:
- Studios are designed for bands, co-writers, or creative teams.
- A Studio can contain multiple Projects.
- Artists within a Studio have role-based permissions (owner, editor, viewer).
- A Studio does not own Works directly — it owns Projects.

### Project

Definition:

A container that groups related Works under a common creative goal.

Examples:
- An album
- An EP
- A songwriting session
- A thematic collection

Notes:
- A Project belongs to either an Artist (personal) or a Studio (collaborative).
- A Project can contain multiple Works.
- Projects help organize creative intent.

### Work

Definition:

A single creative artifact authored within Ilena.

Examples:
- A song
- A poem
- A draft version of lyrics

Notes:
- A Work belongs to one Project.
- A Work can have multiple Versions.
- A Work is the atomic creative unit in the system.