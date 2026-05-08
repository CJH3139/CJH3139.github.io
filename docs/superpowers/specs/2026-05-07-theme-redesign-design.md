# Theme Redesign — Design Spec
**Date:** 2026-05-07  
**File:** `index.html`

## Summary

Replace the green + circles theme with an electric blue + blocky/angular aesthetic. No circular shapes anywhere. Retain all existing content and structure.

## Color Changes

| Variable | Before | After |
|---|---|---|
| Accent | `#4ade80` (green) | `#38bdf8` (electric blue) |
| Accent dim | `#16a34a` | `#0284c7` |
| Accent glow | `rgba(74,222,128,0.25)` | `rgba(56,189,248,0.25)` |
| Background grid | green-tinted | blue-tinted |
| Ambient glows | green | blue |

The "available" badge keeps green (`#4ade80`) as a deliberate accent — it reads as a status color, not a theme color.

## Shape Changes

All `border-radius` values set to `0`. No exceptions.

| Element | Before | After |
|---|---|---|
| Avatar | Circle (50%) + spinning ring | Removed entirely |
| Badge dot | Circle (50%) | Square (0px) |
| Skill icon containers | Rounded (9px) | Sharp (0px) + left blue border |
| Cards | Rounded (12px) | Sharp (0px) + left blue border |
| Buttons | Rounded (8px) | Sharp (0px) + bottom 3px shadow |
| Contact box | Rounded (16px) | Sharp (0px) + left 3px blue border |
| Link cards | Rounded (12px) | Sharp (0px) + left blue border |
| Discord pill | Rounded (8px) | Sharp (0px) |

## Avatar

Removed from hero entirely. No replacement element.

## Hero Section

- Badge: green "available" (lowercase) with green square dot — keeps green as a status indicator
- Subtitle: removed "Building scripts and systems to power Minecraft communities." line
- Remaining subtitle: "**Minecraft Java & Skript Developer** · Server Owner" only
- Hero quote and CTAs unchanged

## Card Styling

All cards (skill cards, link cards, contact box) get:
- `border-left: 2px solid #38bdf8` (3px on contact box)
- `border-radius: 0`
- Hover: `box-shadow: 4px 4px 0 rgba(56,189,248,0.08)` instead of glow

## Buttons

- Primary (was `.btn-green`): blue fill, `border-bottom: 3px solid #0284c7` for a blocky 3D press effect
- Ghost: sharp corners, same structure as before but blue hover tint

## Background

- Pixel grid: blue-tinted (`rgba(56,189,248,0.025)`)
- Ambient radial glows: blue-tinted

## Nav

- Logo font and size unchanged (VT323, electric blue)
- Nav link style: uppercase, slightly spaced letters

## Out of Scope

- No layout changes
- No content changes beyond hero subtitle removal
- No new sections
- No font changes
