# Design System Documentation: The Guardian Pulse

## 1. Overview & Creative North Star
The "Guardian Pulse" is the creative North Star for this design system. In emergency situations, users experience cognitive tunneling and high stress. Our mission is to provide an interface that acts as a steady, authoritative hand. We move beyond "utility" into "Editorial Urgency"—a style that combines the high-contrast clarity of a premium news broadsheet with the tactile, layered responsiveness of modern Android hardware.

By utilizing intentional asymmetry, oversized display typography, and a "Tonal Stack" instead of traditional lines, we create a signature experience that feels both high-end and life-saving. We avoid the "template" look by treating the screen as a fluid canvas where critical information is elevated through depth and light, rather than boxes and borders.

## 2. Colors & Surface Architecture
Our palette is rooted in Material Design logic but executed with editorial sophistication. We use color not just for branding, but as a functional tool to guide the eye through chaos.

### The "No-Line" Rule
**Strict Mandate:** Designers are prohibited from using 1px solid borders to define sections. Layout boundaries must be established through:
1.  **Background Shifts:** Placing a `surface_container_low` card against a `surface` background.
2.  **Tonal Transitions:** Using the `surface_container` hierarchy to denote nesting.
3.  **Negative Space:** Utilizing the spacing scale to create psychological separation.

### Surface Hierarchy & Nesting
Treat the UI as a physical stack of materials. 
- **Base Layer:** `surface` (#fcf9f8) for the main application background.
- **Sectioning:** Use `surface_container_low` (#f6f3f2) for large content blocks.
- **Interactive Elements:** Use `surface_container_highest` (#e5e2e1) for cards that require immediate user focus.
- **Nesting:** To create a "nested" feel, an inner component should always be one step higher or lower in the `surface_container` tier than its parent, creating natural depth.

### The "Glass & Gradient" Rule
To elevate the "Emergency Red" (#af101a) beyond a flat hex code:
- **Signature Gradients:** Apply a subtle linear gradient from `primary` (#af101a) to `primary_container` (#d32f2f) on the main SOS button. This creates a "glowing" effect that feels urgent and alive.
- **Glassmorphism:** Use `surface_container_lowest` at 80% opacity with a 20px `backdrop-filter: blur()` for floating navigation bars or critical status overlays. This ensures the user never feels disconnected from the map or content beneath.

## 3. Typography: The Editorial Voice
We utilize **Inter** to deliver a hierarchy that prioritizes rapid scanning. In an emergency, every millisecond counts.

*   **Display (lg, md, sm):** Used for "Hero" metrics like ETA or distance (e.g., "4 MINS"). Use these to break the grid—large, bold, and unapologetic.
*   **Headline (lg, md, sm):** Used for critical instructions (e.g., "Apply pressure to the wound"). These are the "Command" level of the app.
*   **Title (lg, md, sm):** Used for card headings and section titles.
*   **Body (lg, md, sm):** Used for descriptive text. Maintain a line height of 1.5x for maximum legibility in high-vibration environments (like a moving ambulance).
*   **Label (md, sm):** Used for micro-copy and metadata.

**Visual Identity Tip:** Use `headline-lg` in `on_background` (#1b1c1c) to create high-contrast anchors on the page. Let the typography do the heavy lifting of the layout.

## 4. Elevation & Depth
We eschew traditional "drop shadows" in favor of **Tonal Layering** and **Ambient Light**.

### The Layering Principle
Depth is achieved by stacking `surface-container` tiers. A card using `surface_container_lowest` (#ffffff) sitting on a `surface_container_low` (#f6f3f2) background creates a sophisticated, soft lift without the "muddy" look of standard shadows.

### Ambient Shadows
When a floating effect is mandatory (e.g., the primary SOS action):
- **Blur:** 32px to 48px.
- **Opacity:** 4% to 8%.
- **Color:** Use a tinted shadow. Instead of pure black, use `on_surface` (#1b1c1c). This mimics natural light and keeps the UI looking premium.

### The "Ghost Border" Fallback
If a border is required for accessibility (e.g., high-sunlight rural use):
- **Constraint:** Use `outline_variant` (#e4beba) at **15% opacity**. It should be a suggestion of a line, not a hard barrier.

## 5. Components

### The SOS Hero Button
- **Shape:** `full` (9999px) or `xl` (1.5rem) roundedness.
- **Color:** Gradient of `primary` to `primary_container`.
- **Interaction:** Large tap target (minimum 80x80dp for one-handed rural use).

### Action Cards
- **Rounding:** Always `xl` (1.5rem) to feel approachable and modern.
- **Content:** Forbid the use of divider lines. Separate "Call Police" from "Call Ambulance" using `24px` of vertical white space and a subtle background shift to `surface_container_high`.

### Input Fields
- **Height:** Minimum 64dp to accommodate stressed, imprecise finger taps.
- **State:** Active states should use a `secondary` (#005faf) "Ghost Border" to signal focus without cluttering the screen.

### Status Chips
- **Style:** Use `secondary_container` (#54a0fe) for positive statuses and `error_container` (#ffdad6) for critical alerts. 
- **Typography:** Always use `label-md` in All-Caps with 0.5px letter spacing for an authoritative, "official" feel.

## 6. Do's and Don'ts

### Do:
*   **DO** use oversized typography to create a clear visual hierarchy.
*   **DO** leverage the `xl` (1.5rem) corner radius for all primary containers to maintain the "Soft Minimalism" aesthetic.
*   **DO** ensure all touch targets are at least 48x48dp (ideally 56dp+) for rural users who may be using the app with one hand while moving.
*   **DO** use `surface_bright` to highlight the most important action on a screen.

### Don't:
*   **DON'T** use 1px dividers. If you need to separate items in a list, use a 8px-16px gap or a subtle tonal shift.
*   **DON'T** use standard grey shadows. They look "cheap." Always use low-opacity, tinted ambient light.
*   **DON'T** crowd the screen. In an emergency, white space is a functional tool that reduces cognitive load.
*   **DON'T** use high-contrast borders. They create "visual noise" that slows down information processing.