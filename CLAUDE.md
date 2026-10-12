# Elm — ELM HUIC design work

This repo holds context for design work on ELM - HUIC products (Nusuk / Umrah Individuals).
The work happens in Figma through the Figma MCP; this file carries the context between sessions.

## Figma access

- The Figma connector must be signed in as **mabdalkhalek** (mabdalkhalek@ntgclarity.com), who is a guest
  in the **ELM - HUIC** organization. Check with `whoami` at the start of a session.
- The Figma MCP needs **edit** access to a file even to read it — view-only sharing is not enough.
- `get_variable_defs` needs a frame/node ID, not a page ID. Page-level `get_metadata` on large pages
  overflows; list top-level children instead, or read tokens with a read-only `use_figma` script.
- Before any `use_figma` call, load the figma-use skill (`skill://figma/figma-use/SKILL.md` resource).

## Design system files (team: ELM - HUIC / Unified Design system / Design System)

| File | Key | Role |
|---|---|---|
| [Nusuk Masar - Design system DGA](https://www.figma.com/design/Vxmkyi3K26sQFnUeqMYhGe/Nusuk-Masar---Design-system-DGA) | `Vxmkyi3K26sQFnUeqMYhGe` | **Primary system** for the product (RTL) |
| [Foundations - Platforms Code](https://www.figma.com/design/earejT4suUk9B2rNtaLUcw/Foundations---Platforms-Code--Community-) | `earejT4suUk9B2rNtaLUcw` | National DGA foundations: Light/Dark themes, Desktop/Tablet/Mobile spacing |
| [Components Library - Platforms Code](https://www.figma.com/design/cZXDsF3BRrphNjZITO2Xv8/Components-Library---Platforms-Code--Community-) | `cZXDsF3BRrphNjZITO2Xv8` | ~50 extra components (Accordion, Carousel, Chart, Skeleton, UI Shell, …) |
| [Icons](https://www.figma.com/design/STj7RkIfx1VZYgh5Uw0yyr/Icons) | `STj7RkIfx1VZYgh5Uw0yyr` | Icon library, searchable by keywords |
| [Screen Template](https://www.figma.com/design/QMNkPGMP7rBgkvSDNT7oOZ/Screen-Template) | `QMNkPGMP7rBgkvSDNT7oOZ` | Screen templates: List, Details, Form/Create, Pop-ups |

All four libraries are published and reachable through `search_design_system`.

**Rule:** use Nusuk Masar components first; fall back to Platforms Code only for what Nusuk Masar lacks.

## Working file

- [Umrah Individuals](https://www.figma.com/design/NqiN77UdmU29qbrcIADqHl/Umrah-Individuals--?node-id=5756-118027) — key `NqiN77UdmU29qbrcIADqHl`, edit access confirmed.
- Page `مفوض الوزارة - تحسينات` (node `5756:118027`): two groups — **الباقة الشاملة** and **الباقة المخصصة** (section `6131:18571`).
  Each flow is its own section with a ticket number (e.g. 172376, 172388) and holds 4–5 Desktop screens:
  list → details → confirmation modal → result. Flows cover stopping/activating packages for OTA, by country,
  by nationality and by days, plus booking management and the travel-agents list.
- **Rule:** this is the team's shared file. Put new designs in a new section or page; only touch existing
  screens when explicitly asked.

## Notifications file

- [Notifications](https://www.figma.com/design/T2j2zyxa8w6V2ZwknThcDq/Notifications) — key `T2j2zyxa8w6V2ZwknThcDq`, edit access confirmed.
- Pages: `Notification - add role` · `Notifications (MOHU)` · `Notifications (Backoffice)` · `Notifications (UO and EA)` ·
  `Notification General` · `Notification Management`. Brown screens are the old palette; the green **Notifications**
  section on the Backoffice page (157033 / 157039, e.g. frame `4387:24000`) is the reference for the current system.
- Page `إشعارات التحركات (Backoffice)` (`4461:6`) holds the **movement-notifications** work, built from a business HTML
  prototype (NTF-01 rules, NTF-02 permissions, NTF-04 list, NTF-05 details, NTF-06 delivery log).
  - Done: list screen, frame `4461:8`. Nav: الإشعارات › إشعارات التحركات › قائمة الإشعارات.
  - Local component `movement_counter_card` (`4464:910`) for the criticality / unread counters.
  - Mapping: حرج → status_chip `rejected`, عالٍ → `awaiting_Payment`, متوسط → `active`,
    غير مقروء → `in_Progress`, مقروء → `draft` (chip text overridden).
- Screen conventions: 1440 wide, `nav_bar` 268 on the right, `top_bar`, breadcrumbs + title, cards row, table card.
  Wide tables are allowed to overflow to the left of the frame (the team's way of showing horizontal scroll).
- Font gotchas: `statistics_card` numbers, `status_chip` defaults and `items_number` use **Gotham**, and some titles use
  **29LT Zarid Serif**. Neither font is available to the plugin API, so set `fontName` to IBM Plex Sans Arabic
  before editing that text, or apply a DS text style.

## Tokens (Nusuk Masar)

### Colors
| Group | Values |
|---|---|
| Green (primary) | SA25 `#f7fdf9` · SA50 `#f3fcf6` · SA100 `#dff6e7` · SA200 `#b8eacb` · SA300 `#88d8ad` · SA400 `#54c08a` · SA500 `#25935f` · **SA600 `#1b8354` (Primary)** · SA700 `#166a45` · SA800 `#14573a` · SA900 `#104631` · SA950 `#092a1e` |
| Neutral | white `#ffffff` · surface/neutral10 `#fafafa` · 20 `#f0f0f1` · 30 `#dadbdc` · 40 `#bfc2c4` · 60 `#7e8387` · 80 `#484d51` · 100 `#23282d` · 200 `#15181b` |
| Mint (success) | 20 `#ecf8f5` · 30 `#ceece5` · 40 `#afe0d4` · 60 `#8ed4c2` · 80 `#5dc1a8` · 100 `#3cb496` · 200 `#2a7e69` · 250 `#256e5c` |
| Ruby (error) | 20 `#fceded` · 30 `#f8d9d9` · 40 `#f1b7b7` · 60 `#ec9999` · 80 `#e46d6d` · 100 `#c41a1a` · 200 `#9b3737` · 250 `#873030` |
| Straw (warning) | 20 `#fef8f0` · 30 `#fcf2e2` · 40 `#f9e4c0` · 60 `#f6d9a6` · 80 `#f3c880` · 100 `#f0bd66` · 200 `#a88447` · 250 `#92733e` |
| Info | 25 `#f5faff` · 50 `#eff8ff` · 100 `#d1e9ff` · 200 `#b2ddff` · 300 `#84caff` · 400 `#53b1fd` · 500 `#2e90fa` · 600 `#1570ef` · 700 `#175cd3` · 800 `#1849a9` · 900 `#194185` · 950 `#102a56` |

Gradients: SA600→SA500 (90°), SA700→SA600 (45°), SA950→SA600 (45°), SA800→SA600 (90°), SA800→SA700 (26.5°), SA900→SA600 (45°).

### Semantic tokens
- Text: `text_Primary` = neutral200, `text_Invert` = white. Surface: `surface_Primary` = surface.
- Button: Default SA600 · Hover SA700 · Focus SA600 · Press SA900.
- Border: Default neutral40 · Hover SA400 · Focus SA700 · Press SA600 · Disabled neutral20 · Error ruby100.

### Spacing (4-based)
Primitives: half 4 · 1=8 · 2=12 · 3=16 · 4=20 · 5=24 · 6=28 · 7=32 · 8=36 · 9=40 · 10=44 · 11=48 · 12=56 · 13=64 · 14=80.
Tokens: None 0 · Half 4 · XS 8 · S 12 · M 16 · L 20 · XL 24 · 2XL 32 · 3XL 40.

### Radius
XS 4 · S 8 · **M 12** · L 16 · XL 24 · 2XL 32 · Max 200.

### Typography — IBM Plex Sans Arabic
Headings use Medium, body uses Regular. Desktop scale (size/line-height):
- Hero XL 44/120% · Hero L 38/120%
- Headline XL 32/56 · L 24/40 · M 22/36 · S 20/28 · XS 16/24
- Body XL 20/30 · L 18/27 · M 16/24 · S 15/22 · XS+ 13/20 · XS 12/20 · XXS 11/20
- Body Bold (Medium) L 18/24 · M 16/24 · S 15/22 · XS+ 13/20 · XS 12/20 · XXS 11/16

Tablet and Mobile have their own scales (`RWD/Tablet/...`, `RWD/Mobile/...`), e.g. Mobile Hero XL 36, Headline L 22/36, Body M 15/22.

### Shadows
- shadow_top `0 8 24 rgba(35,40,45,.04)` · shadow_bottom `0 -8 24 rgba(35,40,45,.04)`
- shadow_tile_default `0 4 24 rgba(35,40,45,.04)` · shadow_tile_selected `0 4 24 rgba(180,145,100,.08)`
- shadow_info / success / wraning / error: `0 2 12` at 16% of Info / mint100 / straw100 / ruby100.

### Known inconsistencies in the source file
- `RWD/Mobile/Body/Bold/L` uses **29LT Zarid Sans** instead of IBM Plex Sans Arabic (likely a mistake).
- `neutral10` and `surface` share the same value (`#fafafa`).
- Effect style is misspelled `shadow_wraning`.

## Nusuk Masar component inventory
- Atoms: icons, radio, checkbox, tabs, chip (status), switch, tooltip, scrollbar, breadcrumbs, avatar, tag, content_switcher
- Molecules: button, input, text area, dropdown, IBAN, stepper, date picker, time selection, infobox, snackbar, timer, pagination, timeline, cards, rating
- Organisms: top_bar, nav_bar, header, context_menu, attachment, modal, sidebar, table
