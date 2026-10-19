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
  - Cards are clones of the reference: two `rating_card_first` donut cards (by criticality, by read state)
    plus `statistics_card` for the total.
  - Done: details screen (NTF-05) for NTF-2026-000412, cloned from the green Details frame `4393:18164`.
    Tab «التفاصيل» is frame `4478:1113` with two info cards (بيانات المعتمر · البرنامج والتحرك; days shown as red
    text, no bar). Tab «سجل التحديثات» is frame `4478:14096`: the table is hidden and replaced (user request) by DS `historyTimeline`
    items (set key `c0af75b4…`, Type First/Middle/Last, «Show reason» for failures) — 000412 history: created by the system
    06:04 → sent to شركة الرحاب للعمرة (نافذة + بريد) 06:04 → SMS failed after 3 attempts 06:49 (reason «رقم الجوال المسجّل غير صالح»)
    → read by مهدي فاضل 09:12, all on 17/09/2026 · 06/04/1448; system rows use an initials avatar «ن».
    User decision: no cards for reason, company read status or delivery channels.
  - Done: delivery log (NTF-06), frame `4491:1446`, below the list. It is a clone of the list screen without cards,
    filters or explanatory text. Each row is one delivery attempt on one channel. Number and case repeat on every
    row with normal per-row zebra (user rejected grouping by notification).
    Columns: القناة (chip) · الوجهة · النتيجة (chip) · تاريخ إرسال الإشعار (real «17/09/2026 06:49», date and time
    in one cell, per HTML v6) · سبب الفشل · eye action. User removed المحاولة and kept سبب الفشل.
    HTML v6 also has merged rows, internal send references, full IDs and per-column filters; the user did NOT adopt these.
    Result chips: مُرسل `active`, ظهر `in_Progress`, قيد الإعادة `awaiting_Payment`, فشل نهائي `rejected`.
  - Page layout (set up by the user): one section per screen group (قائمة · سجل الإرسال · قواعد إشعارات التحركات).
    Put new frames inside the matching inner section.
  - Rules (NTF-01): two options in the rules section, with no case codes (ح-1…) and no cards under the table.
    - **A (table)** `4500:2233`: built from our table columns. Control cells are detached from the column
      template and hold DS Switch, dropdown (label=no), checkbox and input instances.
    - **B (cards)** `4502:2097`: accordion cards cloned from the add-role card `4204:40751`, with DS switch,
      dropdowns (label=yes), checkboxes and an input with helper text. Each open card ends with a footer:
      «حفظ» primary and «إلغاء» secondary on the bottom-left, and a tertiary «معاينة الإشعار» on the bottom-right.
      «استعادة الافتراضي» was dropped in B. There are no
      buttons in the title row (user decision).
    - Convention in this file: save/submit buttons sit at the bottom (primary on the left, tertiary link on the
      right). The title-row button slot is only for page actions such as «إنشاء إشعار».
    - DS keys: Switch `4515a13b…`, checkbox `7e286833…`, dropdown `97f9a18b…`, input `75cbda2e…`.
  - Rules: «N معلّقة» (pending count, `pend` in the HTML data) was removed from both options. Its meaning is unclear
    (ح-2 is instant yet shows 1 pending), so it's an open question for the business before it returns.
  - Delivery log: the user hid the actions column.
  - Permissions (NTF-02), section `4507:14631` (inner `4507:14632`). The user picked option 5 (two-list modal) out of
    three previews (`previews/mock-perm-option3/4/5.png`).
    - Screen `4507:14633` is a clone of rules A. Columns: حالة التحرك · مدراء حسابات الشركات (checkbox) ·
      شركة العمرة (checkbox) · مستخدم إضافي (DS Tag chips plus a secondary «+ إضافة» button).
    - Row «الدخول خارج نطاق البرنامج» is disabled with the description «معطّلة في قواعد الإشعارات».
    - «حفظ» and «إلغاء» sit at the bottom-left of the table card. There is no paginator or eye column.
    - Modal screen `4507:43874` has a 30% black overlay. Its `modal_window` `4507:44077` is cloned from the cancel
      modal `3573:57104`, and its two list panels are cloned from the add-receivers story `2056:114448/114514`
      (MOHU page). The panels are recolored green and use DS checkbox/button and IBM fonts.
    - Modal header/footer and the two panel headers are Nusuk Masar `modal_header` (`8b9e8bb8…`, title IBM Headline/M 22)
      and `modal_footer` (`d879015e…`); the old-library header (Zarid 28) made titles too big.
    - Data is realistic (users such as سارة العتيبي — وزارة الحج والعمرة, خالد الشهري — شركة دار الإيمان للعمرة, initials in avatars).
  - Page titles measured: green screens Zarid Serif 36/54 (≈ IBM 30), old brown Zarid Sans 40 (Headline/XL),
    Umrah Individuals list IBM Regular 28/54, details DS `Headline/XL` 32/56. DS `headerSection` uses Headline/L 24.
  - Permissions flow (user: design every case and modal as its own frame, in order left → right in `4507:14632`):
    1 default `4507:14633` (no save/cancel) · 2 after a change `4514:14906` (row الوفاة/شركة العمرة ticked, buttons shown)
    · 3 modal `4507:43874` (background has no buttons) · 4 after adding a user `4514:15340` (tag «سارة العتيبي» in row 1,
    buttons shown) · 5 saved `4514:15782` (buttons hidden, success `snackbar` at x24 y89, key `53c4f292…`,
    copied from the green «تم ارسال الاشعار بنجاح» screen `4387:41697`).
  - **Rule (user):** save/cancel appear only after the user changes something; every flow shows each state
    (default, changed, modal, result, success) as a separate frame.
  - Typography pass (user asked to fix all titles and fonts): every text on page `4461:6` is bound to a Nusuk Masar style.
    Page titles → `Desktop/Headline/L` 24/40 (the DS `headerSection` page-header size). Card/accordion titles →
    `Headline/S` 20. Modal titles → `Headline/M` 22 (from `modal_header`). Body text → matching `Body/*` or `Body/Bold/*`
    by size and weight. Left unstyled: breadcrumbs and date placeholders at 14 (no desktop 14 style), and the
    `statistics_card` number at 72. Style keys: Headline L `4459f615…`, S `0ca5b8a3…`, Body M `ed97eab3…`, Body S `0be595da…`,
    Body XS `3dc3e710…`, Body XS+ `d2fea3bb…`, Body L `cfa902de…`, Body XL `e93c2f27…`, Bold M `15b50610…`, Bold XS `3a21407a…`.
  - **Rule (user):** use real-looking data, not placeholders like «مستخدم 3» or «XX»; use DS components over old-library ones.
  - **Rule (user):** ignore brown entirely; always use primary green (SA600) for anything cloned from old screens.
    Tag set key `d0f3a464…`, icon/add `017f4710…`.
  - Selected tab needs an SA600 override on its label and indicator; the library default is brown.
  - Mapping: حرج → status_chip `rejected`, عالٍ → `awaiting_Payment`, متوسط → `active`,
    غير مقروء → `in_Progress`, مقروء → `draft` (chip text overridden).
- **UO side (company) of movement notifications**, from a second business HTML (`previews/uo/` renders). The user asked
  to redesign only the first 3 screens (list, details, critical modal) and keep them separate from the Backoffice work:
  outer section `4525:22509` «إشعارات التحركات — شركة العمرة (UO)» to the right of the Backoffice sections, inner `4525:22510`.
  - Reference: page `Notifications (UO and EA)` (`2003:73196`), UO list «إشعارات الوزارة» `2277:63585` with tabs
    التعاميم/الإنذارات/الاستدعاءات (brown, old). Movement notifications are a new 4th tab «إشعارات التحركات» (user agreed:
    tab only, no separate side-menu item; no case codes ج-1…; classification حرج/عادي as in the HTML).
  - Frames left → right: UO 1 list `4525:22511` (clone of our green list; page name «إشعارات التحركات» in title, breadcrumbs and nav —
    user renamed it from the reference's «إشعارات الوزارة»; tabs cloned from UO
    and the selected tab recolored SA600; cards follow the UO screens and the HTML: `statistics_card` total 12 + three DS `rating_card` gauges (key set `ed3d739e…`;
    arc = Ellipse 8 arcData from 3.4203 by 2.5836×ratio; الحرجة 5/12 ruby100, المقروءة 7/12 green, غير المقروءة 5/12 straw100) — not donuts; columns
    رقم · التصنيف · النوع · التاريخ (date+time) · الحالة · eye; unread rows use Body/Bold/M) · UO 2 details critical unread
    `4527:5190` (DS `infobox` error, key `f6df6b50…`; البيانات الأساسية 10 fields; تفاصيل الإشعار with notice text,
    pilgrims table built from request_no columns, «تم الاطلاع» primary + «تصدير قائمة المعتمرين») · UO 3 after
    acknowledge `4528:4255` (chip مقروء, fields المطّلع/وقت الاطلاع, success snackbar) · UO 4 normal unread
    `4528:4744` (2058, primary «تحديد كمقروء») · UO 5 locked critical modal `4528:5294` (no close X, «(1 من 2)»,
    over the UO list because no UO home screen exists).
  - Mapping: عادي → status_chip `active`; حرج → `rejected`; غير مقروء `in_Progress`; مقروء `draft`.
  - Not built (user decision): home ticker strip, daily entry/exit report, ministry read-tracking screen and send modal.
- **New shell (user, 2026-10-15):** all movement-notification frames (Backoffice + UO) now use the new library
  `Nav Bar` (set key from instance `4557:5715`, main `bd13124e…`, State=Expanded, built with slots) and the new
  `top_bar` (main `a06b2c4e…`, the user's reference instance `4556:80534`). Top bar breadcrumb product reads «العمرة»
  (user: not «الحج»). Nav content: Section «عام» → «الصفحة الرئيسية» (home-01 icon) · «الإشعارات» (notification-02
  icon, State=Selected, 2nd Level=Yes) → 2nd level «إشعارات التحركات» (3rd Level=Yes, Selected) with 3rd level
  قائمة الإشعارات · سجل الإرسال · قواعد الإشعارات · صلاحيات الاستقبال (current page Selected) and 2nd level
  «قائمة الإشعارات»; other sections hidden. UO frames: «الإشعارات» → «إشعارات التحركات» only (3rd Level=No, Selected).
  Nav is resized to the frame height and kept under modal overlays. Slot children (2nd/3rd level items) are edited in place.
  The `star` and `drag-drop-vertical` icons on nav items are hidden on every frame (user decision).
- **Settings stepper flow (user, 2026-10-15):** entry is the button «اعدادات اشعارات التحركات» (`4579:88592`) on the
  user's list frame `4579:87714`. Section `4582:9724` «إعدادات إشعارات التحركات — Stepper» (x4800 y2300). Built on the
  user's stepper template `4572:17557` (green `stepper` panel on the right, `top_bar` version=stepper with headline
  «إعدادات إشعارات التحركات», infobox, content, «Buttons» row). Two steps only (user): 1 قواعد الإشعارات `4586:12055`
  = the rules A table `4500:2233` (no paginator, overflows left like other wide tables; «التالي» + «إلغاء» link) ·
  2 صلاحيات الاستقبال `4586:13144` = the permissions table `4507:14633` (its footer hidden; «حفظ» + «السابق») ·
  2b `4586:14015` «+ إضافة» opens the side window (Side Panel `4572:27907` from `4572:27643`, 800 wide from the left,
  30% overlay, two-list picker, «إضافة» + «إلغاء») · 2c `4586:79602` user added (tag «سارة العتيبي» in row 1) ·
  3 success `4583:12791` (list + snackbar «تم حفظ إعدادات إشعارات التحركات بنجاح»). No review step (user: save directly).
- **Review comments (ahmedsherif, 2026-10-18) on the list `4579:98322`** (now in section `4579:93770`, page renamed
  «إشعارات التحركات-Movement Notifications»). Comments are read through the Figma REST API (`api.figma.com` is allowed in the
  environment; header `X-Figma-Token`). Open items: merge the list with سجل الإرسال + «prioritize the columns» (a reply on the
  same thread, region comment under the frame), «use pie charts to gather all data» (cards), «sub-status» (حالة التحرك column).
  - Done steps 1+2 (user: result, reason and date stay in the main table): new frame `4614:18`
    «Movement Notifications / List — v2 (دمج سجل الإرسال)» at x699 y1700 in `4579:93770` (section height extended).
    Columns right → left: رقم الإشعار 110 · الأهمية 100 · حالة التحرك 240 · المعتمر 220 · شركة العمرة 240 · قنوات الإرسال 150
    · نتيجة الإرسال 130 (status_chip: مُرسل active, فشل جزئي awaiting_Payment, قيد الإعادة in_Progress, فشل نهائي rejected)
    · سبب الفشل 250 · تاريخ الإرسال 180 · حالة القراءة 120 (renamed from حالة الإشعار) · eye. Removed البرنامج, الجنسية and the
    hidden وقت/تاريخ الإشعار columns. New columns are clones of the delivery-log columns (`4491:2489/2602/2528`) with
    08–10_data turned off. Table overflows left (team convention). Preview `previews/merged-list/A-default.png`.
  - Follow-up (user): removed قنوات الإرسال; الأهمية is the only main status (status_chip); نتيجة الإرسال and حالة القراءة
    use the DS data_item `type=sub-status` (text + dot; dot colours: مُرسل mint100, فشل جزئي straw100, قيد الإعادة info500,
    فشل نهائي ruby100, غير مقروء info500, مقروء neutral60). Per-channel detail shown two ways (user: build both):
    A default `4614:18` · B hover `4616:18` (x2539): DS `tooltip` (set `1ff8f7cb…`, desktop/arabic/down, width locked 200) over
    row 000412 «فشل جزئي — 2 من 3 قنوات», وصل إلى نافذة/بريد, لم يصل إلى SMS + reason · C expanded `4616:22196` (x4379):
    table_body split into row_expanded_top / expanded_details panel (SA25 fill, mini table cloned from delivery-log columns:
    القناة · المستلم · النتيجة · تاريخ إرسال الإشعار · سبب الفشل, 3 rows for 000412) / rows_rest; arrow-down-01 chevrons
    (row 1 rotated up) left of each send result. Previews `previews/merged-list/A-default.png`, `B-hover-tooltip.png`,
    `C-expanded-row.png`. The user edited the cards in v2 meanwhile (now total 7 + two donuts) — leave them.
  - Pattern search (user asked where hover/expand exist): tooltips exist only on charts (green «View List» `4387:24000`/`4393:15632`,
    «Reception / Company») and on a disabled checkbox in Umrah «Tafweej / Request Tafweej / step 135» (`176:60877`, DS tooltip
    direction=up, «لا يمكن التعديل في هذة الخطوة»). No expandable table row anywhere: not in the files, not in Nusuk Masar
    (`columns`/`column`), not in Platforms Code (`Table Row` has only Hovered/Selected). **User chose B (hover).**
    B `4616:18` renamed «List v2 — B (المعتمد)…»: row 1 cells + 01_data_button filled with Nusuk `Colors/Green/SA 50`
    (`2f5bf0c4…`) as the hovered row, Icons `touch-09` hand cursor on «فشل جزئي», tooltip kept on top. C renamed
    «(بديل غير معتمد)» and left in place.
  - **Details tab reworked (comments «think about adding side section…», «move it down»; user-approved mock
    `previews/details-side/mock-*`):** in `4478:1113` the cards sit in `details_row (70/30)` = side card
    `notification_summary (side)` `4626:22085` (clone of the user's side box `4593:100919`, 340 wide, same height as
    بيانات المعتمر 355) + `details_main` (cards 760, inner fixed 728 frames set to FILL). Side content: حالة التحرك «ثبوت التخلف»
    · alert chip ruby20/ruby40 + circle_warning «تجاوز مدة البقاء النظامية بـ 7 أيام» (97 − 90) · pair (right → left)
    نتيجة الإرسال «● فشل جزئي / وصل لـ 2 من 3 قنوات» and حالة القراءة «● مقروء / مهدي فاضل · 09:12» (dots straw100 /
    neutral60, sub text Body/XS+ neutral60) · تاريخ الإشعار «06/04/1448هـ - 17/09/2026م» + «الساعة 06:04 ص» (same format as
    the side box). Title keeps only the الأهمية chip «حرج»; the «مقروء» chip is hidden here and in the timeline tab
    `4478:14096` (header kept identical). User: no side card on سجل التحديثات. Frame grown to 1117 (nav resized).
    Send result made explicit (user picked option B of `mock-3-send-result-options.png`; A tooltip-only, C extra card):
    side card now = حالة التحرك · alert · نتيجة الإرسال full width [DS `subtatus_chip` «فشل جزئي» (dot = status_dots frame
    fill straw100) + «وصل لـ 2 من 3 قنوات»] + `channels` row (Icons `checkmark-circle-02` SA600 «نافذة» «بريد», `circle_warning`
    ruby100 «رسالة نصية» in ruby text — both icons already used in the side box) · pair حالة القراءة (DS `subtatus_chip` «مقروء»,
    dot neutral60, «مهدي فاضل · 09:12») | تاريخ الإشعار «17/09/2026م» + «06/04/1448هـ». The manual dots were replaced by the DS
    chip (same one the title used). Height still 355 = بيانات المعتمر. Hover state = separate frame `4629:22024` below the
    details frame: DS tooltip (desktop/arabic/down) «رسالة نصية — لم تصل» + recipient, reason, attempts, `touch-09` cursor.
    Open: list v2 shows 000412 as «غير مقروء» while details/timeline say read by مهدي فاضل 09:12 (pre-existing mismatch).
  - Next (not done): sub-status in حالة التحرك (needs the business list of sub-statuses), cards → pie charts (current cards
    contradict: totals 12 vs 7, critical 5/12 vs 2, read 7/12 vs 3).
- **Rule (user):** copy how the existing screens are built (clone their cards, table header, columns, and
  placeholders such as YYYY/MM/DD dates). Don't invent new patterns straight from the design-system library.
- Screen conventions: 1440 wide, `nav_bar` 268 on the right, `top_bar`, breadcrumbs + title, cards row, table card.
  Wide tables are allowed to overflow to the left of the frame (the team's way of showing horizontal scroll).
- Fonts: screens mix in **Gotham** (numbers, dates, paginator, `statistics_card`, `items_number`), **29LT Zarid**
  (titles, some top-bar labels) and **Inter** (donut tooltips). None of them are available to the plugin API.
  - **Rule (user):** convert any non-IBM text to IBM Plex Sans Arabic at a size that looks the same.
  - Measured: Arabic IBM is about 22% larger than Zarid, so use ×0.82 (Zarid 20 → IBM 16, Zarid Serif title
    36/54 → IBM Medium 30/54). Gotham digits and Latin text keep the same size in IBM.
  - Book/Regular → `IBM Plex Sans Arabic` Regular; Medium → `IBM Plex Sans Arabic Medium` Regular.

## Transport Information Center homepage (DGA review)

- File `cAMY504gWaSItUzw4yJevl` («Untitled»), frame `1:16870` «homepage» 1440×2827 (the user's link said 1-18455): public site of مركز معلومات النقل
  (النقابة العامة للسيارات). Built mostly with **Components Library - Platforms Code** (Nav Header, Header Menu Item,
  Button, Card, Featured icon, Tag, Accordion, Pagination, Link) and its text styles (Display/Text …) and «Themes» variables.
- User asked (2026-10-17) whether a 100% DGA-compliant version is possible and what to fix first. Audit findings:
  no gov masthead (`Second Nav Header`) and a custom footer frame instead of the DGA `Footer` component; accessibility
  tools text hidden; ~1,110 unbound colours (1,084 are the gold #9e925f decorative pattern; also #000/#1a1a1a text,
  #074d31 footer, #f8f7f5); 4 fills bound to a «Delete» variable collection; 6 hidden stray layers at the frame root
  (old hero, «نبذة وخبرات» in «The Year of The Camel»); hidden «12 reviews» ratings and «عنوان مجموعة» footer placeholders;
  Swap Placeholder instances and a crypto icon (huobi-token) in cards; 44 groups; an image named «ChatGPT Image…»;
  copy typos (خدامتنا، المصليين، منشأت، الاسئلة، kashida stretching) and mixed digits; footer «2026 © 2024».
- **DGA v2 built (user: «خد بالك من الارقام»):** frame `8:315` «homepage — DGA v2», 1640 to the right of the original
  (main column `8:316`, gap 0). Hidden layers deleted. Previews: `previews/dga-homepage/1-before.png`, `2-dga-v2.png`.
  - Grid: DGA Foundations `Grid desktop` style (key `147991e9…`): 12 columns, gutter 24, margin 112, content 1216
    (1 column ≈ 79.3; 3 columns = 286; 6 columns = 596).
  - Stack: masthead `Second Nav Header` RTL=Yes Gray (40, instance `9:22863`, date «17-أكتوبر-2026») → Nav Header 1440×72
    (padding 112) → **Hero `9:22936` 1440×640 full-bleed**, radius 0, padding 64/112, content aligned to the bottom
    (image + gradient overlay absolute 1440×640). 40 + 72 + 640 = 752, so the next section shows inside a 900px viewport.
    Hero content 1216 = two 6-column halves (596 + 24 + 596); title column gap 24 (was 22).
  - Sections: padding 64/112, radius 0, no gap between sections. About `8:1476` white (two halves of 596; image card
    `8:1481` text 32 from the edges), Services `8:1500` neutral-50 (4 cards × 286 + 3 × 24 = 1216, equal heights),
    FAQ `8:1516` white (gold 6% fill removed).
  - **Footer = DGA `Footer` instance** `12:6666` (set `aa4c5b3f…`, RTL=True, Dark green, 600+; fill `background-SA-Flag`),
    padding 112, Content FILL 1216. Old custom footer deleted. Groups (right → left): روابط سريعة (nav items) · خدماتنا
    (the 4 services) · تواصل معنا (phone, email, address) · المساعدة والدعم (الأسئلة الشائعة, الدعم الفني, خريطة الموقع);
    5th placeholder group hidden. Social group renamed «تابعنا» with X / LinkedIn / YouTube / Instagram icons; accessibility
    tools = view / zoom-in-area / zoom-out-area. Bottom links: تواصل معنا · الدعم الفني · الأسئلة الشائعة · خريطة الموقع.
    Caption «جميع الحقوق محفوظة لمركز معلومات النقل © 2026».
  - Footer logos: nested `Logo Placeholder` instances are locked at 98×42 (size can't be overridden), so the real lockup
    was split into two local components on the page (`12:7117` مركز معلومات النقل, `12:7119` النقابة العامة للسيارات;
    cropped image fills) and swapped in. Vision 2030 has no third slot, so it is not shown.
  - Tip: set `figma.skipInvisibleInstanceChildren=false` before reaching hidden instance sublayers by id.
- **Before/after board** (user asked for it): section `16:749` «قبل وبعد — توافق الصفحة الرئيسية مع DGA» at y3400 under both frames.
  Snapshots of the original and v2 (after-snapshot `18:1743`, refresh it if v2 changes), 12 numbered pins (red = before, green = after)
  and a 13-row table «الفروقات بالترتيب» (`16:2175`) with قبل/بعد per item. The user rearranged it (before on the left).
  Preview `previews/dga-homepage/3-before-after.png`.
- **2026-10-17 later:** the user deleted the standalone frames `1:16870` (original) and `8:315` (v2) from the page. The board copies
  are now the working frames: «قبل» `16:754`, «بعد» `18:1743` (main column `18:1744`). Work on `18:1743` directly.
  - Added DGA **`Digital Stamp`** (set `3ea85c5e…`, RTL=Yes Opened=no, 1440×32, padding 112) above the Second Nav Header —
    this is the «موقع حكومي رسمي تابع لحكومة المملكة العربية السعودية — كيف تتحقق» bar. Its link was 4.32:1 on #f3f4f6, so it
    is overridden to `Text/text-primary-sa-flag` (#14573a, 7.78:1). Second Nav Header padding set to 112 too.
  - Colour audit: every solid fill/stroke is bound to DGA «Themes» variables (only the flag inside Digital Stamp keeps its own
    colours). Gradient stops bound via `boundVariables.color` on stops: hero overlay alpha-black-0 → alpha-black-80; About
    card overlay alpha-black-0 → background-primary at layer opacity 0.86. Contrast measured from pixels: all hero text ≥ AA
    (title 60px worst 4.48, needs 3; body ≥ 7.2).
  - Board table «الفروقات بالترتيب — من أعلى الصفحة لأسفل» rebuilt in page order (14 numbered rows + one «عام» row);
    pins renumbered to match (1 stamp, 2 top bar, 3 nav, 4 hero, 5 hero title, 6 hero spacing, 7 stats, 8 grid, 9 icon,
    10 services section, 11 services title, 12 cards, 13 FAQ, 14 footer).
  - **Header padding (user: «في بادينج كبير من الناحيتين»):** Digital Stamp, Second Nav Header and Nav Header are back to the
    DGA component default padding 32 (all three aligned). Page sections stay on the 112/1216 grid.
  - User: «انا عايز زي الكمبوننت اللي موجود في dga» → all DGA instances (Digital Stamp, Second Nav Header, Nav Header, Footer)
    use their main component's padding/spacing (32; footer Content max 1280). Only content overrides remain (real texts,
    logos, icons) plus the «كيف تتحقق» link colour (text-primary-sa-flag, for AA contrast).
  - The user deleted board items «عنوان الهيرو والزرار», «أيقونة كفاءة تشغيلية» and the «عام» row (with their pins). Remaining
    12 items renumbered 1–12: stamp · top bar · nav · hero · hero spacing · hero stats · grid · services section ·
    services title · cards · FAQ · footer. Useful tokens: Link/link-primary-visited `4d2b021f…`,
    text-primary-sa-flag `b3519ee6…`, alpha-black-0 `32ccf4a8…`, alpha-black-80 `ffd636ba…`, icon-default `e041e3f2…`.
  - Removed: gold pattern (1,133 vectors), #f8f7f5 dots, hidden pagination, hidden footer nav links, Swap Placeholders.
  - Copy: استكشف خدماتنا · نظام نقل المصلين · منشآت · الأسئلة الشائعة · التزام بالأنظمة · «نقود مستقبل النقل» (no kashida/ellipsis)
    · stats 98% / 100% / 24/7 · «جميع الحقوق محفوظة لمركز معلومات النقل © 2026». Crypto icon → `chart-increase`.
  - Tokens: in the Platforms Code theme `Text/text-primary` is **brand green**. Neutral titles use `Text/text-display`, paragraphs
    `Text/text-primary-paragraph`, neutral icons `Icon/icon-default` (`e041e3f2…`), image borders `Border/border-neutral-secondary`.

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
