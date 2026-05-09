---
name: deltek-brand-guidelines
description: Applies Deltek's official brand colors and typography to any sort of artifact that may benefit from having Deltek's look-and-feel. Use it when brand colors or style guidelines, visual formatting, or company design standards apply. Trigger this skill whenever the user mentions Deltek branding, corporate identity, visual design, brand compliance, or wants any output styled to match Deltek's brand guidelines.
license: Complete terms in LICENSE.txt
---

# Deltek Brand Styling

## Overview

To access Deltek's official brand identity and style resources, use this skill.

**Keywords**: branding, corporate identity, visual identity, post-processing, styling, brand colors, typography, Deltek brand, visual formatting, visual design, brand compliance

## Brand Guidelines

### Color Hierarchy

Deltek's colour palette is structured hierarchically. The primary accent represents the overarching brand and platform, while secondary accents symbolise project lifecycle stages.

#### Primary Accent

- **Deltek Marine Blue**: `#1742F5` / RGB(23, 66, 245) — Primary brand colour (PANTONE 2728C)

#### Text Colors

- **Rich Black**: `#00021D` / RGB(0, 2, 29) — Primary text on light backgrounds
- **Charcoal Gray**: `#3C454E` / RGB(60, 69, 78) — Secondary text
- **White**: `#FFFFFF` / RGB(255, 255, 255) — Text on dark backgrounds

**Contrast rule**: Dark text colours on light backgrounds; white text on dark backgrounds.

#### Secondary Accents — Project Lifecycle Colors

These should primarily symbolise content associated with lifecycle stages, or be used as subtle secondary accents.

- **Win Teal (Dark)**: `#00B6C3` / RGB(0, 182, 195)
- **Win Teal (Light)**: `#0BE9EB` / RGB(8, 233, 235)
- **Plan Magenta (Dark)**: `#C200CC` / RGB(194, 0, 204)
- **Plan Magenta (Light)**: `#FF5DF2` / RGB(255, 93, 242)
- **Execute Blue (Dark)**: `#1742F5` / RGB(23, 66, 245) — Same as Deltek Marine Blue
- **Execute Blue (Light)**: `#3B95FF` / RGB(56, 149, 255)
- **Analyze Purple (Dark)**: `#6D18F1` / RGB(109, 24, 241)
- **Analyze Purple (Light)**: `#7A62FF` / RGB(122, 98, 255)

#### Background Colors

- **White**: `#FCFDFF` / RGB(252, 253, 255) — Light backgrounds
- **Deltek Navy Blue**: `#070D63` / RGB(7, 13, 99) — Dark backgrounds
- **Deltek Marine Blue**: `#1742F5` / RGB(23, 66, 245) — Accent backgrounds

An optional multicolour gradient background (using lifecycle colours) can be used for dynamic accent backgrounds.

### Typography

Deltek uses the **Figtree** font family across all applications.

| Level            | Font    | Weight    | Size   |
|------------------|---------|-----------|--------|
| Display Headline | Figtree | ExtraBold | 108 pt |
| H1               | Figtree | Bold      | 60 pt  |
| H2               | Figtree | SemiBold  | 36 pt  |
| Subhead          | Figtree | ExtraBold | 18 pt  |
| Body             | Figtree | Regular   | 14 pt  |

**Typography rules:**
- Headlines can use accent colours; body copy should be black or grey
- Dark text on light backgrounds; white text on dark backgrounds
- Letter spacing should be compact at large font sizes and increase as font size decreases
- Line height (leading) should be relational to type size (e.g., 108 pt x 0.9 = ~100 pt line height for display; body text uses ~1.3x multiplier)

**Fallback fonts**: If Figtree is unavailable, use Arial (headings) or system sans-serif (body).

**Loading Figtree in web contexts**:
```html
<link href="https://fonts.googleapis.com/css2?family=Figtree:wght@400;600;700;800&display=swap" rel="stylesheet">
```

## Features

### Smart Font Application

- Applies Figtree ExtraBold/Bold to headings (24pt and larger)
- Applies Figtree Regular to body text
- Automatically falls back to Arial/sans-serif if Figtree is unavailable
- Preserves readability across all systems

### Text Styling

- Display/H1/H2 headings: Figtree Bold/SemiBold
- Subheads: Figtree ExtraBold at 18pt
- Body text: Figtree Regular at 14pt
- Smart colour selection based on background (dark text on light, white on dark)
- Preserves text hierarchy and formatting

### Shape and Accent Colors

- Non-text shapes use lifecycle accent colours
- Cycles through Teal, Magenta, Blue, and Purple accents
- Maintains visual interest while staying on-brand
- Primary accent (Marine Blue) should be dominant

## Technical Details

### Font Management

- Uses Google Fonts Figtree when available
- Provides automatic fallback to Arial (headings) and sans-serif (body)
- No font installation required for web — import from Google Fonts
- For PPTX/DOCX: check if Figtree is installed locally; fall back to Arial if not

### Color Application

- Uses RGB colour values for precise brand matching
- Applied via python-pptx's RGBColor class for presentations
- For CSS/HTML: use hex values from the palette above
- Maintains colour fidelity across different systems

### CSS Quick Reference

```css
:root {
  /* Primary */
  --deltek-marine-blue: #1742F5;

  /* Text */
  --deltek-rich-black: #00021D;
  --deltek-charcoal-gray: #3C454E;
  --deltek-white: #FFFFFF;

  /* Backgrounds */
  --deltek-bg-white: #FCFDFF;
  --deltek-navy-blue: #070D63;

  /* Lifecycle Accents */
  --deltek-win-teal-dark: #00B6C3;
  --deltek-win-teal-light: #0BE9EB;
  --deltek-plan-magenta-dark: #C200CC;
  --deltek-plan-magenta-light: #FF5DF2;
  --deltek-execute-blue-dark: #1742F5;
  --deltek-execute-blue-light: #3B95FF;
  --deltek-analyze-purple-dark: #6D18F1;
  --deltek-analyze-purple-light: #7A62FF;

  /* Typography */
  --font-family: 'Figtree', Arial, sans-serif;
}
```

### Python (python-pptx) Quick Reference

```python
from pptx.util import Pt
from pptx.dml.color import RGBColor

# Brand colours
DELTEK_MARINE_BLUE = RGBColor(23, 66, 245)
DELTEK_NAVY_BLUE = RGBColor(7, 13, 99)
DELTEK_RICH_BLACK = RGBColor(0, 2, 29)
DELTEK_CHARCOAL_GRAY = RGBColor(60, 69, 78)
DELTEK_WHITE = RGBColor(255, 255, 255)
DELTEK_BG_WHITE = RGBColor(252, 253, 255)

# Lifecycle accents
WIN_TEAL_DARK = RGBColor(0, 182, 195)
WIN_TEAL_LIGHT = RGBColor(8, 233, 235)
PLAN_MAGENTA_DARK = RGBColor(194, 0, 204)
PLAN_MAGENTA_LIGHT = RGBColor(255, 93, 242)
EXECUTE_BLUE_DARK = RGBColor(23, 66, 245)
EXECUTE_BLUE_LIGHT = RGBColor(56, 149, 255)
ANALYZE_PURPLE_DARK = RGBColor(109, 24, 241)
ANALYZE_PURPLE_LIGHT = RGBColor(122, 98, 255)

# Font settings
FONT_HEADING = 'Figtree'
FONT_BODY = 'Figtree'
FONT_FALLBACK = 'Arial'
```
