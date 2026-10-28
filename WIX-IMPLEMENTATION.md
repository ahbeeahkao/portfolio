# Wix implementation & import readiness

These pages are responsive design prototypes, not published Wix sites. Wix does not provide a generic one-click conversion of arbitrary static HTML into editable native Wix pages. The layouts can be recreated in Wix Editor / Wix Studio with native components, but they are not a Wix template file and cannot be imported as a finished native site by clicking once.

`wix/site-manifest.json` records the seven separate concepts, their distinct navigation labels and scope, four-page routes, theme tokens, media paths and CTA/form behavior. Home-page section order varies by concept; the handoff is an import source for a future Wix-connected importer, not a Wix-native import file by itself. A true one-click native import would require a Wix app/automation built against Wix’s supported APIs and authorized by the customer for their Wix site. No import button is shown on these portfolio pages.

## Suggested Wix build mapping

1. Use the matching concept’s layout direction rather than forcing all seven into one template: Chinese editorial split hero; Malay centered, arched-image composition; Indian image-first asymmetric hero; general inclusive modular layout; Kuala Lumpur oversized city-atelier typography; Johor rounded, welcoming composition; Penang framed heritage-inspired composition. Adapt each responsively for mobile.
2. Rebuild each concept’s own page sequence and featured service scope as separate sections. Use Wix containers / grids and native text elements; avoid fixed-width positioning.
3. Add a native Wix Form in the enquiry section. Ask for name, email, optional wedding date or season, and a note. Do not add a telephone field or WhatsApp action.
4. Point each CTA to the enquiry section anchor. Do not add a floating contact button.
5. Upload the matching `assets/img/bridal-*.jpg` hero image and `assets/img/bridal-*-detail.jpg` close-up image to Wix Media Manager. Keep each supplied alt text descriptive. All sample shop details, product names and prices are fictional and must be replaced with verified information before publishing a real shop.
6. Set up language switching with Wix Multilingual for English, Bahasa Melayu and Chinese. The prototype's browser-translation widget is only for the static preview; use Wix's native language management on the actual Wix build.
7. Set mobile breakpoints and check the page at phone width: navigation, image crop, heading wraps, fields, buttons and footer should remain readable and tappable.

## Design system

Each concept has its own fictional brand, navigation, page titles, enquiry choices, service scope and editorial composition—not merely a separate color palette. Preserve the distinctions: Chinese ceremony wardrobe; Malay modest styling; Indian multi-event outfit planning; inclusive silhouette discovery; a curated Kuala Lumpur atelier; a Johor one-stop package concept; and a Penang detail-led studio. These are original demonstrations of possible shop scope, not claims about real businesses. All remain concept-only pages: keep the self-initiated / not paid client work disclosure, fictional-business caveat, and `noindex, follow` until replaced with approved real-business content.

## Scope research (inspiration only)

The concept briefs use broad service patterns visible in Malaysian and Singapore bridal retail—not real businesses’ names, copy, photos, prices, policies or claims. Roundups are starting points for research, not an authoritative ranking: [Malaysia bridal boutique guide](https://theweddingnotebook.com/inspire/fashion-and-beauty/best-bridal-boutique-in-kl-singapore) and [Singapore bridal boutique guide](https://theweddingnotebook.com/inspire/fashion-and-beauty/best-bridal-boutiques-in-singapore). Official examples reviewed include [Liang Yuan](https://www.liangyuan.com.my/) for specialist traditional Chinese wear and rental/custom-made paths, [The Proposal](https://www.theproposal.com.sg/) for designer-led rental/purchase and bespoke eveningwear/cheongsam, [The Aurora Wedding](https://theaurorawedding.com/) for one-stop wedding package scope, and [Gelly Wee](https://gellywee.com/) and [Dressaville](https://www.dressaville.com/) for curated collections, appointments and rental/package information. These references informed the breadth of the fictional concepts only; no real operating details are presented as belonging to the mock shops.

Static previews are available at `/bridal-chinese/`, `/bridal-malay/`, `/bridal-indian/`, `/bridal-general/`, `/bridal-kl/`, `/bridal-johor/` and `/bridal-penang/`. Before publishing a real Wix site, replace concept details with the boutique's approved name, services, policies, availability and contact configuration; do not present fictional information as factual claims.
