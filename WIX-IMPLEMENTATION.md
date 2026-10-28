# Wix implementation & import readiness

These are responsive static-HTML design prototypes—not published Wix sites and not a one-click Wix deploy. The goal is that a Wix Studio builder can manually recreate each complete site with a 1:1 visual target, using the source pages and the detailed handoff below. No Wix-authorized importer has been implemented or tested, and the manifest is not a Wix-native import file.

`wix/site-manifest.json` records each concept’s routes, navigation, scope, palette, media, and form behavior. `wix/design-spec.json` is the fidelity handoff: it records the exact source route order, page titles, palette tokens, layout-specific CSS rules, image assets, and reference viewports. The HTML/CSS in each `bridal-*/` folder remains the visual source of truth. A manual Wix build must preserve each page’s structure and design—not replace the seven sites with one template or a merely recolored theme.

## 1:1 visual recreation target

A complete Wix Studio rebuild should match the corresponding static site at the reference widths in `wix/design-spec.json`: desktop 1440×900, tablet 768×1024, and mobile 390×844. The spec also includes each page’s actual section order, content titles, theme tokens, image assets and crop rules, plus layout-specific CSS declarations. Match the complete four-page site—not only its homepage hero.

Use the static HTML as the source for exact copy and component order. In Wix Studio, recreate those sections with native sections, containers, grid/stack layouts, menus, repeaters, accordions, images and forms. Set the recorded colors and fonts, reproduce column proportions and spacing at each breakpoint, and choose the same supplied image with the same crop/position. Keep each concept’s distinct navigation and page titles. Replace the preview’s translation widget with Wix Multilingual and the demo mailto form with a native Wix Form configured for the approved real client contact when a real business commissions the site.

For sign-off, compare the Wix build side-by-side with the corresponding static page at all three reference widths. Check section heights/order, text wrapping, image focal point, spacing, colors, borders, buttons, navigation, form fields and footer. Adjust Wix breakpoints and values until the comparison matches. Do not claim a Wix site has achieved 1:1 fidelity until it has actually been built and checked; the current repository contains the reconstruction specification, not a published/verified Wix implementation.

## Suggested Wix build mapping

1. Use the matching concept’s layout direction rather than forcing all seven into one template: Chinese editorial split hero; Malay centered, arched-image composition; Indian image-first asymmetric hero; general inclusive modular layout; Kuala Lumpur oversized city-atelier typography; Johor rounded, welcoming composition; Penang framed heritage-inspired composition.
2. Rebuild the exact route-specific section sequence recorded for that concept in `wix/design-spec.json`; use Wix containers / grids and native text elements rather than fixed-width positioning.
3. Add a native Wix Form in the enquiry section. Match the concept-specific select label and options, plus name, email, optional wedding date or season, and note. Do not add a telephone field or WhatsApp action.
4. Point each enquiry CTA to the form anchor. Do not add a floating contact button.
5. Upload the matching `assets/img/bridal-*.jpg` hero image and `assets/img/bridal-*-detail.jpg` close-up image to Wix Media Manager. Preserve the supplied alt text and source crop. All sample shop details, product names and prices are fictional and must be replaced with verified information before publishing a real shop.
6. Set up language switching with Wix Multilingual for English, Bahasa Melayu and Chinese. The prototype's browser-translation widget is only for the static preview; use Wix's native language management on the actual Wix build.
7. Set Wix Studio breakpoints to reproduce the 760px source breakpoint and compare at the desktop, tablet and mobile reference sizes. Check image crop, heading wraps, fields, buttons, navigation and footer.

## Design system

Each concept has its own fictional brand, navigation, page titles, enquiry choices, service scope and editorial composition—not merely a separate color palette. Preserve the distinctions: Chinese ceremony wardrobe; Malay modest styling; Indian multi-event outfit planning; inclusive silhouette discovery; a curated Kuala Lumpur atelier; a Johor one-stop package concept; and a Penang detail-led studio. These are original demonstrations of possible shop scope, not claims about real businesses. All remain concept-only pages: keep the self-initiated / not paid client work disclosure, fictional-business caveat, and `noindex, follow` until replaced with approved real-business content.

## Scope research (inspiration only)

The concept briefs use broad service patterns visible in Malaysian and Singapore bridal retail—not real businesses’ names, copy, photos, prices, policies or claims. Roundups are starting points for research, not an authoritative ranking: [Malaysia bridal boutique guide](https://theweddingnotebook.com/inspire/fashion-and-beauty/best-bridal-boutique-in-kl-singapore) and [Singapore bridal boutique guide](https://theweddingnotebook.com/inspire/fashion-and-beauty/best-bridal-boutiques-in-singapore). Official examples reviewed include [Liang Yuan](https://www.liangyuan.com.my/) for specialist traditional Chinese wear and rental/custom-made paths, [The Proposal](https://www.theproposal.com.sg/) for designer-led rental/purchase and bespoke eveningwear/cheongsam, [The Aurora Wedding](https://theaurorawedding.com/) for one-stop wedding package scope, and [Gelly Wee](https://gellywee.com/) and [Dressaville](https://www.dressaville.com/) for curated collections, appointments and rental/package information. These references informed the breadth of the fictional concepts only; no real operating details are presented as belonging to the mock shops.

Static previews are available at `/bridal-chinese/`, `/bridal-malay/`, `/bridal-indian/`, `/bridal-general/`, `/bridal-kl/`, `/bridal-johor/` and `/bridal-penang/`. Before publishing a real Wix site, replace concept details with the boutique's approved name, services, policies, availability and contact configuration; do not present fictional information as factual claims.
