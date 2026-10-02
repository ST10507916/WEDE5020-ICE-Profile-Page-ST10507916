# ICE Tasks 1 to 3 - My Responsive Profile Page

**Student:** Theolin Chetty
**Student Number:** ST10507916
**Module:** WEDE5020
**Task:** ICE Task 3 - Responsive Profile Page (continuation of ICE Tasks 1 and 2)

## What I Created

A single-page Profile Page (`index.html`) presenting a CV-style overview
of myself, including my profile photo, a personal description, my current
and previous studies, my work experience, the technologies and tools I use,
my technical skills and professional strengths, and a Contact section.

In ICE Task 1 the page was built with HTML only. In ICE Task 2 I continued
the same page, added an internal navigation menu and a contact form, and
used an external CSS stylesheet to create a consistent desktop design. In
ICE Task 3 I added CSS media queries so the same page adapts to tablet and
mobile screens (see the Responsive Design section at the end). All of the
original ICE Task 1 content has been kept, and the HTML is the same as in
ICE Task 2.

No CSS frameworks, JavaScript, website builders or templates were used, and
there is no inline CSS (no `style` attributes and no `<style>` block).

## Files in This Repository

- `index.html` - the Profile Page.
- `css/style.css` - the external stylesheet, including the responsive media queries at the end of the file (section 13), linked in the `<head>` with `<link rel="stylesheet" href="css/style.css">`.
- `images/profile.jpg` - my profile photograph from ICE Task 1 (moved out of the HTML into its own image file).
- `README.md` - this file.

## 1. CSS Techniques Used

- **Selectors**
  - *Element selectors* for styles that apply to every element of a type, such as `body`, `h1`, `h2`, `h3`, `p`, `a`, `img` and `footer`.
  - *Class selectors* for groups of related elements that share a look, such as `.card`, `.btn`, `.btn-primary`, `.section`, `.section-title`, `.tag-list` and `.form-group`.
  - *ID selectors* for unique elements that only appear once, such as `#main-nav` (the navigation bar), `#home` (the page header), `#profile-photo` and `#contact-form`.
  - *Pseudo-classes and pseudo-elements* such as `a:hover`, `:focus`, `:focus-visible`, `:last-child`, `::before`, `::after` and `::placeholder`.
- **Custom properties (CSS variables):** the colour palette, fonts, shadow and border radius are defined once in `:root` and reused, which keeps the design consistent.
- **Colours:** background colours for the page, alternating sections, navigation, cards, buttons and form fields, plus text, heading, link and border colours.
- **Typography:** `font-family`, `font-size`, `font-weight`, `line-height`, `letter-spacing`, `text-transform` and `text-align`.
- **Box model:** `margin`, `padding`, `border` and `box-sizing: border-box` so that padding and borders are included in an element's width.
- **Width:** `width` and `max-width` on the page container, the photograph, the introduction text and the form fields.
- **Borders and decoration:** `border`, `border-radius`, `box-shadow`, a `linear-gradient` background and small `transition` hover effects.
- **Flexbox and CSS Grid** for layout (see section 4).
- **Other:** `position: sticky` for the navigation, `scroll-behavior: smooth`, `scroll-margin-top`, `object-fit: cover` for the photo and CSS counters for the numbered strengths list.

## 2. Navigation

The navigation menu uses the semantic `<nav>` element (`<nav id="main-nav">`)
and contains an unordered list of links to the main sections of the page:

- Home
- About
- Education
- Experience
- Technologies
- Skills
- Contact

Each link uses an `href` that starts with `#` followed by the id of a section,
for example `<a href="#education">Education</a>`. The matching section has
the same value in its `id` attribute, for example
`<section id="education">`. When a visitor clicks the link, the browser jumps
to the element with that id, so the `id` acts as the anchor destination. The
links stay on the same page and do not open new pages. The "Home" link points
to `<header id="home">` at the top of the page.

The navigation bar uses `position: sticky` so it stays visible while the
visitor scrolls. `scroll-behavior: smooth` makes the jump scroll smoothly, and
`scroll-margin-top` on each section stops the sticky bar from covering the
section heading after a jump. Links have a background colour change on
`:hover`, and "Contact" is styled as a highlighted button.

## 3. Contact Form

The Contact section contains contact details (email, phone, LinkedIn and
location) next to a form built with these elements:

- `<form>` - wraps all the fields.
- `<fieldset>` and `<legend>` - group the fields under the heading "Send Me a Message".
- `<label>` - a visible label for every field.
- `<input type="text">` - the visitor's name.
- `<input type="email">` - the visitor's email address. The `email` type lets the browser check the format.
- `<input type="text">` - a social media profile or other preferred contact method, such as LinkedIn, Instagram, X or a phone number.
- `<textarea>` - a multi-line box for the reason for contact / message.
- `<button type="submit">` and `<button type="reset">` - the form buttons.

**How labels are linked to fields:** each `<label>` has a `for` attribute
that matches the `id` of its input, for example `<label for="email">` and
`<input type="email" id="email">`. This means clicking the label puts the
cursor in the field, and screen readers read the label for that field.

**What the visitor can provide:** their name, email address, a social or
preferred contact detail, and a message explaining why they want to get in
touch. Name, email and message are marked as required with the `required`
attribute and a red asterisk.

**Buttons:** the **Submit** button (`type="submit"`) submits the form. The
browser first checks that the required fields are filled in and that the
email is valid. The **Reset Form** button (`type="reset"`) clears every field
back to empty so the visitor can start again. As this is an HTML/CSS exercise,
the form uses `action="#"` and does not actually send or store the data.

## 4. Layout

**Flexbox** is used for content that runs along one line (one direction):

- **Navigation bar** (`.nav-inner`, `.nav-list`) - places my name on the left and the links in a row on the right, with even gaps. Flexbox suits this because it is a single row of items.
- **Page header** (`.hero-inner`) - places the profile photo and the introduction text side by side and centres them vertically.
- **Buttons** (`.hero-actions`, `.form-actions`) - keeps the pairs of buttons in a row with a gap.
- **Technology tags** (`.tag-list`) - uses `flex-wrap: wrap` so the tags flow onto a new line when a row is full. Flexbox suits this because the tags are different widths.
- **Experience timeline** (`.timeline`) - stacks the job cards in a column with equal spacing.
- **Form fields** (`.form-group`) - stacks each label above its input.

**CSS Grid** is used for layouts with columns:

- **About section** (`.about-grid`) - a two-column grid (`2fr 1fr`) with the description on the left and the Quick Facts card on the right.
- **Education and Skills** (`.card-grid`) - two equal columns of cards (`repeat(2, 1fr)`), so matching cards line up in height.
- **Quick Facts** (`.facts`) - a small grid that lines the labels up in one column and the values in another.
- **Contact section** (`.contact-grid`) - contact details in a narrow column (`1fr`) and the form in a wider column (`2fr`).
- **Form rows** (`.form-row`) - puts Name and Email side by side.

I used Grid where content needed to line up in columns and Flexbox where
items only needed to sit in a row or a stack. The whole page sits inside a
centred container with a width of 1100px for a clear desktop layout.

## 5. Design Decisions

- **Colours:** dark slate (`#1e293b`) with a teal accent (`#0f766e`) on light grey and white backgrounds. I chose these because they look professional and calm, suit a web developer profile, and give strong contrast for readability. Teal is used only for important things (buttons, links, highlights) so they stand out. Sections alternate between two light backgrounds to separate them.
- **Typography:** Georgia (a serif font) for headings and Segoe UI / Arial (sans-serif fonts) for body text, navigation and form text. The mix gives headings character while keeping body text easy to read. Sizes drop clearly from the main heading (3.4rem) to section headings (2.1rem), subheadings (1.25rem) and body text (17px), with a comfortable `line-height` of 1.7. The footer text is centred with `text-align: center`.
- **Layout:** a centred container, a large introduction area with my photo, and content grouped into cards so each topic is easy to scan.
- **Spacing:** each section has 80px of padding at the top and bottom, cards have 30px of padding, and grids use a 30px gap. This keeps the page from feeling crowded without leaving too much empty space.
- **Navigation styling:** a dark bar that stays at the top, with light text, rounded hover backgrounds and a teal "Contact" button so it is clearly the main call to action.
- **Form styling:** labels sit above full-width fields. Fields have padding, rounded borders and a light background. A teal border and soft glow show which field is active, and an invalid email turns the border red. The primary Submit button is filled teal and the Reset button is an outline, so the two actions look different.
- **Profile photograph:** styled with a set `width` and `height`, `border-radius: 50%` to make it round, `padding` with a white background to create a ring, a teal `border`, a `margin`, a shadow and `object-fit: cover` so it is not stretched or distorted.

## 6. Learning Reflection

**A CSS concept I understand better:** the box model. I now understand how
`padding` adds space inside an element, `border` goes around the padding, and
`margin` adds space outside it. `box-sizing: border-box` made widths much
easier to control because padding and borders no longer make an element
wider than the width I set.

**A CSS concept that was challenging:** making the navigation stay at the top
of the page. Once the bar was sticky, clicking a link jumped to the section
but the section heading ended up hidden underneath the bar.

**How I solved it:** I researched the problem and added `scroll-margin-top`
to each section, set to the same height as the navigation bar. This tells
the browser to stop slightly above the section, so the heading is visible
below the bar. I also found that when I opened `index.html` directly from
inside the zip file, the CSS and photo did not load. This taught me that the
stylesheet and image are linked with relative paths (`css/style.css` and
`images/profile.jpg`), so the files and folders must stay together.

**A new HTML feature I added:** the contact form. It uses `<form>`,
`<fieldset>`, `<legend>`, `<label>`, different `<input>` types, a
`<textarea>` and Submit and Reset `<button>` elements. I also added `id`
attributes to each section so the new `<nav>` links can use them as anchor
destinations.

---

## ICE Task 3 - Responsive Design

### Why responsive design matters

People visit websites on many screen sizes. A recruiter or client may open my
profile on a phone, where there is far less horizontal space than on a
desktop. Without responsive CSS, my desktop layout made the navigation run off
the side of the screen and forced the visitor to scroll sideways, and the
multi-column grids squeezed text into narrow columns. Responsive design keeps
the same content and visual style, but rearranges and resizes it so the page
stays readable and easy to use on any device.

### 1. Media Queries

All responsive rules are at the end of `css/style.css` in section 13. I used
four media queries. Each uses `max-width`, so its rules apply only when the
browser window is that width or narrower. They are ordered from widest to
narrowest, so a phone gets the tablet rules first and then the mobile rules
on top of them.

| Media query | Target | What it is used for |
|---|---|---|
| `@media (max-width: 1100px)` | Small laptops, large tablets in landscape | Reduces the navigation link padding and gaps so the name and all seven links still fit on one line. |
| `@media (max-width: 900px)` | Tablets | Moves the navigation links onto a second row under my name, and changes the About and Contact sections from two columns to one. Reduces the photo, heading and spacing sizes. |
| `@media (max-width: 600px)` | Mobile phones | Changes the whole page to a single column, stacks the photo above the introduction, turns the navigation into a 3-column grid of buttons, stacks the form fields and buttons, and reduces sizes and spacing. |
| `@media (max-width: 360px)` | Very small phones | Changes the navigation grid to 2 columns so longer words like "Technologies" fit, and makes the main heading and photo slightly smaller. |

I chose these widths by testing my own page. I narrowed the browser window
until something broke (for example, the navigation overflowing at about
790px) and added a breakpoint just above that point.

### 2. Layout Changes

- **Navigation (`.nav-inner`, `.nav-list`):** on desktop, my name and the links sit in one Flexbox row. On tablets, `flex-direction` changes to `column` so the name is on top and the links wrap (`flex-wrap: wrap`) in a centred row underneath. On phones, the link list changes from Flexbox to a CSS Grid with `grid-template-columns: repeat(3, 1fr)`, so the links become evenly sized buttons, and the Contact button spans the full width with `grid-column: 1 / -1`. On very small phones the grid uses 2 columns.
- **Sticky navigation:** on phones I changed `#main-nav` from `position: sticky` to `position: static`. Three rows of links stuck to the top would cover a large part of a small screen, so on phones the menu stays at the top of the page and the footer "Back to top" link returns the visitor to it.
- **Page header (`.hero-inner`):** on desktop and tablet, the photo and introduction sit side by side. On phones, `flex-direction` changes to `column` and `text-align: center` is applied, so the photo sits above the centred text. The two header buttons also stack and stretch to full width.
- **About (`.about-grid`):** changes from two columns (`2fr 1fr`) to one column (`1fr`) on tablets, so the Quick Facts card moves below the description.
- **Education and Skills (`.card-grid`):** stay in two columns on tablets, where there is still enough room, and change to one column on phones.
- **Contact (`.contact-grid`):** changes from two columns (`1fr 2fr`) to one column on tablets, so the contact details card sits above the form.
- **Contact form rows (`.form-row`):** Name and Email change from side by side to stacked on phones. The Submit and Reset buttons change from a row to a full-width column (`flex-direction: column`).
- **Experience timeline:** the left padding and the position of the timeline line and dots are reduced on phones so the job cards get more width.

### 3. Dimension Changes

| Element | Desktop | Tablet (900px) | Mobile (600px) | Very small (360px) |
|---|---|---|---|---|
| Container side padding | 32px | 28px | 18px | 18px |
| Profile photo (`#profile-photo`) width and height | 240px | 190px | 160px | 140px |
| Profile photo padding / margin | 6px / 10px right | 6px / 10px right | 5px / 0 | 5px / 0 |
| Page header padding (`#home`) | 90px top and bottom | 64px | 44px top, 48px bottom | 44px / 48px |
| Section padding (`.section`) | 80px top and bottom | 64px | 48px | 48px |
| Card padding (`.card`) | 30px | 26px | 20px | 20px |
| Card grid gap | 30px | 22px | 18px | 18px |
| Header gap between photo and text | 60px | 44px (from 1100px) | 24px | 24px |
| Nav bar height | 72px fixed | `height: auto` (grows to fit) | auto | auto |
| Technology tag padding | 10px 20px | 10px 20px | 7px 14px | 7px 14px |
| Form buttons width | Natural width | Natural width | `width: 100%` | `width: 100%` |
| `.hero-summary` max-width | 560px | 560px | 100% | 100% |

The photo keeps `object-fit: cover` and `border-radius: 50%` at every size,
so it shrinks but is never stretched or distorted.

### 4. Typography Changes

Yes. I reduced text sizes step by step as the screen gets smaller, while
keeping body text at a comfortable reading size.

| Text | Desktop | Tablet (900px) | Mobile (600px) | Very small (360px) |
|---|---|---|---|---|
| Body text | 17px | 16px | 16px | 16px |
| Main heading (`#home h1`) | 3.4rem | 2.8rem | 2.3rem | 2rem |
| Section headings (`.section-title`) | 2.1rem | 1.85rem | 1.6rem | 1.6rem |
| Subheadings (`h3`) | 1.25rem | 1.25rem | 1.15rem | 1.15rem |
| Role line (`.hero-role`) | 1.25rem | 1.1rem | 1.05rem | 1.05rem |
| About paragraph | 1.1rem | 1.1rem | 1rem | 1rem |
| Navigation links | 0.95rem | 0.9rem | 0.9rem | 0.9rem |
| Form legend | 1.5rem | 1.5rem | 1.3rem | 1.3rem |
| Form field text | 1rem | 1rem | 16px | 16px |
| Technology tags | 17px (inherited from body) | 16px (inherited from body) | 0.9rem | 0.9rem |

I did not go below 16px for body text or form fields. Keeping form fields at
16px also stops phones (especially iPhones) from automatically zooming in
when a visitor taps a field. The navigation links on phones got extra
padding (10px top and bottom) so they are easier to tap with a finger.

The colour scheme, borders, backgrounds, shadows, accent bars, tick and
number list markers, and the photo ring are unchanged at every screen size.
Only layout, sizes and spacing change.

### 5. Testing

- I used my browser's developer tools (Device Toolbar / Responsive Design Mode, opened with F12 then Ctrl + Shift + M) to view the page at different widths, and I also resized the browser window by hand to watch where the layout started to break.
- I tested these sizes:
  - **Desktop:** 1440 x 900
  - **Small laptop / tablet landscape:** 1024 x 768
  - **Tablet:** 768 x 1024 (for example, an iPad)
  - **Mobile:** 390 x 844 (for example, an iPhone 14)
  - **Very small phone:** 320 x 640
- At each size I checked that:
  - the page had no horizontal scrollbar and nothing ran off the right edge
  - every navigation link was visible, could be clicked and scrolled to the correct section, with the section heading visible and not hidden under the menu
  - the profile photo stayed round and in proportion
  - text was readable without zooming
  - the contact form fields fitted the screen and the Submit and Reset buttons were easy to reach
- I checked that the desktop version looked the same as it did in ICE Task 2.
- **A problem I found while testing:** on phones, the navigation links overlapped the top of my profile photo. This happened because in ICE Task 2 I gave the navigation bar a fixed `height` of 72px, and the wrapped links needed more space than that. I fixed it by setting `height: auto` on `.nav-inner` in the tablet media query, so the bar grows to fit its contents.
