# Oakland-Standard-Module

Whenever Generating any Code Through AI Model, add this Promptin starting  for model to strictly follow these practices.

# Prompt:

You are an Odoo module developer. When writing any module code, you must strictly follow all of the rules below without exception:

─────────────────────────────────────────

RULE 1 — NAMING CONVENTION (oe_ prefix)

─────────────────────────────────────────

Every field, method, view ID, action, menu, model, and any other technical identifier you create must start with the prefix oe_. This applies to:
  • Python field names       → oe_customer_id, oe_last_active_date
  • Method names             → def oe_compute_status(), def oe_get_report_data()
  • XML view IDs             → id="oe_view_customer_tree", id="oe_action_report"
  • Action and menu XML IDs  → id="oe_menu_main", id="oe_act_window_report"
  • Scheduled actions, server actions, ir.rule record IDs
Never use a plain name without the oe_ prefix for anything defined in this module.

─────────────────────────────────────────

RULE 2 — NON-INVASIVE CODE (no DB side-effects)

─────────────────────────────────────────

This module must not touch, modify, or interfere with any existing Odoo database flow, core model behavior, or standard business logic:
  • Do NOT override or extend any existing core method unless absolutely required; if you must inherit, only add new behavior — never change or remove existing behavior
  • Do NOT modify existing field values, default values, or constraints on core models
  • Do NOT add any onchange, compute, or constraint that alters the behavior of existing forms or records
  • All new functionality must be self-contained within the module's own models, views, and logic
  • The module must be fully removable without leaving any side-effect on the existing database or workflows

─────────────────────────────────────────

RULE 3 — README.md (always required)

─────────────────────────────────────────

Always create a README.md file in the root of the module. It must:
  • Be written in simple, non-technical language that any user can understand
  • Include a short description of what the module does and why it is useful
  • List all features and functionalities the module provides
  • Include basic usage instructions: how to install, configure, and use the module
  • Mention any dependencies or required Odoo version
  • Use clear headings, bullet points, and plain English — no developer jargon
  • Be properly formatted in Markdown
Do not skip or omit the README.md under any circumstances.

─────────────────────────────────────────

RULE 4 — NO COMMENTS IN CODE (zero comments)

─────────────────────────────────────────

Do not write any comments anywhere in any code file:
  • No inline comments        → # this is a comment
  • No docstrings             → """ ... """ or ''' ... '''
  • No XML comments           → 
  • No JS comments            → // ... or /* ... */
  • No TODO, FIXME, NOTE, or any annotation of any kind
Write clean, self-explanatory code using meaningful variable and method names. If something needs explanation, it belongs in README.md — not in the code.

─────────────────────────────────────────

These 4 rules are non-negotiable and apply to every file in every module you generate.

─────────────────────────────────────────
# Prompt for App Icon

____________________________________

# Standalone Cheque Printing

## Overview

Standalone Cheque Printing provides a complete cheque issuing workflow with a visual template designer.

The module lets users upload a cheque image, place fields using drag and drop, and print cheques with exact coordinates.

## Core Features

- Dedicated cheque template model with bank and account mapping.
- Physical cheque size setup (width and height in millimeters).
- Auto-generated paper format from cheque dimensions.
- Visual designer modal to place cheque fields:
  - Payee
  - Date
  - Amount
  - Amount words line 1
  - Amount words line 2
  - Account number
  - A/C Pay memo
- Cheque transaction model with status lifecycle:
  - Draft
  - Printed
  - Void
- Print and reprint actions from cheque form.
- Amount in words with smart line splitting.
- Auto-prefill partner balance and amount from open posted entries.
- Role-based access:
  - User own records group
  - Account manager full access

## Business Use Cases

- Print cheques on pre-printed stationery.
- Manage multiple banks with different cheque layouts.
- Keep a controlled register of printed and voided cheques.
- Reduce manual cheque writing errors through template positioning.

## Dependencies

- `base`
- `account`

## Menu Structure

- Standalone Cheque
  - Cheques
  - Templates

## Step-by-Step User Guide

### 1) Create cheque template

1. Open `Standalone Cheque -> Templates`.
2. Click `New`.
3. Enter template name.
4. Select bank.
5. Enter account number.
6. Set cheque width and height (mm).
7. Set font size.
8. Upload cheque image (for designer reference).
9. Save.

### 2) Configure field positions

1. From template form, click `Configure` or `Open Designer`.
2. In designer modal, choose a field from dropdown.
3. Click `Add Field`.
4. Drag field to required position on cheque image.
5. Repeat for all required fields.
6. Click `Save Positions`.
7. Close modal.

### 3) Create cheque

1. Open `Standalone Cheque -> Cheques`.
2. Click `New`.
3. Select template.
4. Enter cheque number.
5. Set cheque date.
6. Select payee.
7. Verify amount and balance.
8. Optional: set payment voucher number.
9. Optional: enable/disable A/C Pay memo.
10. Save.

### 4) Print cheque

1. Open cheque in Draft.
2. Click `Print Cheque`.
3. State changes to `Printed`.
4. Print output uses template coordinates and cheque paper format.

### 5) Reprint, void, reset

- Use `Reprint` when cheque is already printed.
- Use `Void` to cancel a cheque.
- Use `Reset to Draft` for printed cheque corrections.

## Test Plan

### Scenario A: Template creation

1. Create a template with valid bank and size.
2. Save.
3. Expected:
   - Template saved.
   - Paper format linked automatically.

### Scenario B: Designer save

1. Open designer for template.
2. Place at least 3 fields.
3. Click save.
4. Re-open designer.
5. Expected:
   - Field positions persist.

### Scenario C: Cheque draft to printed

1. Create cheque in Draft.
2. Click `Print Cheque`.
3. Expected:
   - Report opens.
   - State changes to `Printed`.

### Scenario D: Void flow

1. Open a printed cheque.
2. Click `Void`.
3. Expected:
   - State becomes `Void`.
   - Print action blocked for void cheque.

### Scenario E: Amount words

1. Create cheque with different amounts.
2. Save.
3. Expected:
   - Amount words line 1 and line 2 computed.
   - Split respects max chars.

### Scenario F: Access security

1. Login with user in own-record group.
2. Create cheque.
3. Login with another own-record user.
4. Expected:
   - Cannot see first user cheques.
5. Login as account manager.
6. Expected:
   - Can see all cheques.

## Known Operational Notes

- Designer coordinates are stored in millimeters.
- The cheque image is for visual alignment only and is not printed as background.
- For accurate printing, test with printer-specific settings and paper feed calibration.

____________________________________________
# Prompt For Banner.gif

____________________

A 6-second seamlessly looping animated hero banner for an Odoo 
business module called "Stock Exception Guard" — a sales/inventory 
control module that prevents overselling and adds manager approval 
workflow for stock shortages.

DIMENSIONS:
- Exact width: 750 pixels
- Exact height: 375 pixels  
- Aspect ratio: 2:1 (horizontal banner)
- Render at 1500x750 first, then export/resize to 750x375 for 
  maximum text crispness

COLOR PALETTE (Odoo Standard):
- Primary brand: Odoo Purple #714B67
- Deep accent: #875A7B (richer purple)
- Success/approve: #00A09D (Odoo teal)
- Warning/exception: #F0AD4E (amber)
- Background light: #F8F9FA
- Text on dark: #FFFFFF
- Text on light: #2C2C2C
- Subtle dividers: rgba(255,255,255,0.15)

LAYOUT (modern UI/UX, 60/40 split):
- LEFT 60% (0-450px): Text/messaging zone on dark purple background
- RIGHT 40% (450-750px): Visual illustration zone with light 
  off-white background, separated by a soft diagonal or curved 
  divider for visual interest (not a hard vertical line)
- Safe padding: 40px from all edges, no critical content in outer 
  20px margin
- Vertical alignment: all key elements optically centered on the 
  375px height

TYPOGRAPHY (readability-first):
- Main title "Stock Exception Guard": bold modern sans-serif 
  (Inter, Poppins, or similar geometric sans), size 32px, color 
  white #FFFFFF, letter-spacing tight, line-height 1.1
- Tagline "Smart approval workflow for stock shortages": regular 
  weight, size 15px, color #E5D8E0 (soft lavender-white for 
  hierarchy), letter-spacing slightly relaxed
- Optional micro-label above title "ODOO MODULE" or "FOR SALES 
  TEAMS": uppercase, 11px, letter-spacing 2px, color #00A09D (teal 
  accent)
- All text must be sharp, antialiased, and pass WCAG AA contrast 
  on the purple background

BACKGROUND:
- Left side: solid Odoo purple #714B67 with a subtle radial 
  gradient toward #875A7B in the upper-left for depth
- Right side: clean #F8F9FA with very faint geometric grid pattern 
  (5% opacity) suggesting "inventory / warehouse"
- Two or three slow-floating soft purple circles (8% opacity) 
  drifting diagonally on the left side for ambient motion
- Smooth curved divider between left and right zones, with a thin 
  teal accent line (#00A09D, 2px) tracing along the curve

ILLUSTRATION (right side, flat 2D style):
- Center of right zone: a stylized stack of 3 inventory boxes 
  drawn with thin purple outlines on white
- One box has a small red/amber warning badge (exclamation mark) 
  in the top corner — representing the shortage exception
- Above the boxes: a floating shield icon (in Odoo purple) with 
  a checkmark inside — representing the "Guard" approval
- Small arrow connectors or dotted lines suggesting the workflow 
  between boxes and shield
- All illustration elements use 2px stroke weight, flat colors, 
  no gradients on the icons themselves

ANIMATION SEQUENCE (6 seconds, perfect loop):
- 0.0s-0.3s: Background fades in from black, ambient circles 
  begin their slow drift (continuous throughout)
- 0.3s-1.0s: Micro-label "ODOO MODULE" types in character by 
  character (teal); main title "Stock Exception Guard" slides 
  up from below with fade-in (ease-out)
- 1.0s-1.5s: Tagline fades in below the title with slight 
  upward motion
- 1.5s-2.5s: On the right, three inventory boxes scale in one 
  by one with a subtle bounce (stagger 200ms between each)
- 2.5s-3.2s: A small warning badge pops in on one of the boxes 
  with a soft pulse animation (representing "shortage detected")
- 3.2s-4.2s: The shield-with-checkmark icon scales in from above 
  the boxes with a smooth ease-out, then glows softly once in 
  teal #00A09D (representing "approved")
- 4.2s-5.0s: A thin teal connection line draws itself from the 
  shield to the warning badge, completing the "guard approves 
  exception" visual story
- 5.0s-5.7s: All elements hold steady; subtle breathing animation 
  on the shield (scale 1.0 to 1.03 and back)
- 5.7s-6.0s: Smooth crossfade back to opening frame for seamless 
  loop (no harsh cut)

MOTION PRINCIPLES:
- All easing: cubic-bezier(0.4, 0.0, 0.2, 1) — Material Design 
  standard ease
- Frame rate: 30fps minimum
- No jittery or robotic movements
- Subtle parallax: ambient circles move slower than foreground 
  elements
- Every animation has a clear purpose (no decorative motion for 
  its own sake)

STYLE RULES:
- Clean flat 2D motion graphics, NO 3D, NO photorealism
- NO human faces, NO stock photos
- Premium enterprise SaaS aesthetic — think Stripe, Linear, 
  Notion meets Odoo's brand
- Generous whitespace, balanced composition
- Every element must remain crisp and readable when displayed 
  at 750x375 actual pixel size
- No text smaller than 11px
- No critical visual element smaller than 24x24px

OUTPUT:
- Format: looping MP4 (preferred) or optimized GIF
- Final delivered resolution: exactly 750x375 pixels
- File size target: under 2MB for GIF, under 4MB for MP4
- Loop must be perfectly seamless (last frame matches first frame)
