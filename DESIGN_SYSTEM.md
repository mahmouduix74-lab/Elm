# ELM - HUIC — Design System Reference (Nusuk Masar)

Reference for the Nusuk Masar design system (ELM - HUIC): library files, tokens, components, and the screen patterns used across the Nusuk Imtithal screens.

## 1. Design system files (team: ELM - HUIC / Unified Design system / Design System)

| File | Key | Role |
|---|---|---|
| [Nusuk Masar - Design system DGA](https://www.figma.com/design/Vxmkyi3K26sQFnUeqMYhGe/Nusuk-Masar---Design-system-DGA) | `Vxmkyi3K26sQFnUeqMYhGe` | **Primary system** for the product (RTL) |
| [Foundations - Platforms Code](https://www.figma.com/design/earejT4suUk9B2rNtaLUcw/Foundations---Platforms-Code--Community-) | `earejT4suUk9B2rNtaLUcw` | National DGA foundations: Light/Dark themes, Desktop/Tablet/Mobile spacing |
| [Components Library - Platforms Code](https://www.figma.com/design/cZXDsF3BRrphNjZITO2Xv8/Components-Library---Platforms-Code--Community-) | `cZXDsF3BRrphNjZITO2Xv8` | ~50 extra components (Accordion, Carousel, Chart, Skeleton, UI Shell, …) |
| [Icons](https://www.figma.com/design/STj7RkIfx1VZYgh5Uw0yyr/Icons) | `STj7RkIfx1VZYgh5Uw0yyr` | Icon library, searchable by keywords |
| [Screen Template](https://www.figma.com/design/QMNkPGMP7rBgkvSDNT7oOZ/Screen-Template) | `QMNkPGMP7rBgkvSDNT7oOZ` | Screen templates: List, Details, Form/Create, Pop-ups |

**Rule:** use Nusuk Masar components first; fall back to Platforms Code only for what Nusuk Masar lacks.

## 2. Tokens (Nusuk Masar)

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

## 3. Nusuk Masar component inventory
- Atoms: icons, radio, checkbox, tabs, chip (status), switch, tooltip, scrollbar, breadcrumbs, avatar, tag, content_switcher
- Molecules: button, input, text area, dropdown, IBAN, stepper, date picker, time selection, infobox, snackbar, timer, pagination, timeline, cards, rating
- Organisms: top_bar, nav_bar, header, context_menu, attachment, modal, sidebar, table

## 4. Component keys & usage patterns

### Components
| Component | Key | Notes |
|---|---|---|
| Table column (set) | `81d17f3f22cc9a3484ee6bd40c67c1429304b745` | Variants `language=arabic, column={label}_name \| status \| checkbox \| boolean \| Percentage …`. Props: `NN_data#…` (row visibility booleans), `↪ label#2721:0` (header), cell `name#227:50`, `grey` (zebra) |
| status_chip | — (inside column `status`) | `status`: active / inactive / in_Progress / awaiting_Approval … |
| statistics_card | — | Props `title#206:3`, `number#206:2` |
| rating_card | `a9d676d26c9bd32e8f1b85632920b5c194906624` | Props `title#206:4`, `number#206:5`. Gauge arc on `Ellipse 8`: start `π+asin(15/87)`, full sweep `π−2·asin(15/87)` × ratio |
| snackbar (set) | `0808e2498d6121158a610f21a3381cb63b016a21` | Variant `platform=desktop, language=arabic, type=success \| error …`; label `label#791:180`. Placed absolute at x 22, y 86 on list screens |
| dropdown_field (set) | `c596d6eb2fdf9a4a5b20dddd1b6ebd6157661bc9` | Props `label#134:475`, `text#134:485`, `mandatory#34003:0`, `item#134:483`, `label_icon#134:481`, `helper_text#871:15`, `hint#871:26`, `↪ helper_text#871:37`; variants `state` (default/focus/error), `filled` (yes/no) |
| dropdown_item (set) | `44748c5cd0ff494c7156ebd97dfb7bfec7c0c7cb` | `label#134:462`, `selected`, `checkbox#1043:37` |
| input | — | `↪ label#97:0`, `text#97:333`, `placeholder_text#137:540`, `mandatory#33916:0`, `helper_text#97:296`, `hint#97:148`, `↪ helper_text#97:259`; variants `state` (default/error/disabled), `filled` |
| checkbox_button | `7dafe685228041a761e136c113ff4c35287430d7` | |
| Text Area | `73100570d40df7b73712cf5fb3efdbe5d765bab8` | |
| button | — | `label_ar#6299:0`; `type` primary / secondary / tertiary; `state` default / disabled |
| breadcrumbs | — | items `breadcrumb_first` / `breadcrumb_second`, `label#893:113` |
| Tabs item | — | `label#864:6`, `selected` yes/no |
| modal_header | — | `title#745:42` |
| Accordion (Platforms Code) | `91f48eda23bedd07bf6a2f529a02913e0585bd7b` | Fallback only |

### Icons (Icons library)
| Icon | Key |
|---|---|
| user-group | `d60875a1bc062afb5b924c6760dcee29ae2836db` |
| package | `62b4b2e2ab71a093ee1bceac36f419bb1b4c54a3` |
| megaphone-01 | `faa10328002edf45295a37eaca820319c4f8c9cd` |
| time-04 | `c59ee091ec62069f3c2a1773e9d01c374cd44059` |
| check-list (set) | `ab498ede343e678c6bc15e2fbd0bc4b6d767b928` |
| checkmark-circle-04 (set) | `798cf3fc272df054ebf375c2f5986c7362e641cf` |
| icon/search | `04050ab016db11aa1d9c3a2eb1cf09a5e3869791` |
| icon/calendar | `0dbc5b8aed3bed10cbb6874f853f5020eafbd9fa` |
| icon/clock | `9bbb15cb84ea7734f74398d486369efaf9f72c8e` |
| icon/edit | `6fd7c9f03821727f0efa1f3e7e6ccd6349f9ed30` |
| icon/delete | `9327b44b707e1951426f113ce606e3fe1fb7136e` |
| pencil-edit-02 | `cf71ecd3a00997c9a1bb324ccf7ad5f17044dd4d` |
| icon/NUSUK/done | `e7c474c367d66e4dbe91866998ac76a6e7bc2d31` |

### Text styles
| Style | Key |
|---|---|
| Body/S | `0be595dae6928d8f31551fd2d3bc59c0a1340e7c` |
| Body/M | `ed97eab38bcfed53d5d22a0db3d77075d5a3e643` |
| Headline/M | `89b16204880d9266852b271a146b74e601b6e469` |

Fonts in the libraries: `IBM Plex Sans Arabic` / `Regular` (body) and `IBM Plex Sans Arabic Medium` / `Regular` (headings). Every text must be bound to a DS text style or come from its component, never Zarid / Gotham.

### Screen patterns (agreed with the team)
- **RTL everywhere.** Nav Bar height = the component height (946); never stretch it.
- **List screen:** breadcrumbs → title + primary "إضافة …" button → stat cards (statistics_card + 2 rating_card) → table card (show/hide columns, reset filters, refresh, export) → DS columns.
- **Table actions:** the standard data_button (eye = details + "···" opening a `context_menu` with تعديل / حذف / إلغاء التفعيل). No custom icon sets.
- **Tables** fit the content width (padding 24); wide tables use a sticky actions column + a horizontal scroll wrapper + scrollbar.
- **Switch columns:** right-aligned with 16 px padding, like DS cells.
- **Add / Edit flows:** full pages with the green stepper panel, **not** modal pop-ups. Footer: primary حفظ / حفظ التعديلات + tertiary إلغاء (+ السابق in multi-step).
- **Details:** header (back arrow + title + status chip) → Tabs → card "المعلومات الأساسية" (label/value pairs, 2 per row) → "سجل العمليات" timeline (hijri on line 1, "gregorian م · time" on line 2).
- **Validation:** field-level error (state=error + "هذا الحقل مطلوب"); server/business errors as an error snackbar.
- **Delete:** `modal_window` over an overlay, title "حذف …", ruby تأكيد + tertiary إلغاء.
- **Section layout in Figma:** outer section `#323232` (radius 62) → green title card on the left → inner section `#1e1e1e` with screens at y 563, 160 px apart, connected with connectors.
