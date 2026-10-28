# Wix implementation & import readiness

These pages are responsive design prototypes, not published Wix sites. Wix does not provide a generic one-click conversion of arbitrary static HTML into editable native Wix pages. The layouts can be recreated in Wix Editor / Wix Studio with native components, but they are not a Wix template file and cannot be imported as a finished native site by clicking once.

To support a future one-click workflow, `wix/site-manifest.json` records the bridal concepts, section order, theme tokens, media paths and CTA/form behavior in a structured format. This is an import source for a future Wix-connected importer—not a Wix-native import file by itself. A true one-click native import would require a Wix app/automation built against Wix’s supported APIs and authorized by the customer for their Wix site. No import button is shown on these portfolio pages.

## Suggested Wix build mapping

1. Create a full-width hero section with a two-column desktop layout: copy and CTA on one side, bridal image on the other. Stack the image above the copy on mobile.
2. Rebuild the story, details, and three-step journey as separate full-width sections. Use Wix containers / grids and native text elements; avoid fixed-width positioning.
3. Add a native Wix Form in the enquiry section. Ask for name, email, optional wedding date or season, and a note. Do not add a telephone field or WhatsApp action.
4. Point each CTA to the enquiry section anchor. Do not add a floating contact button.
5. Upload the matching `assets/img/bridal-*.jpg` image to Wix Media Manager and use it as the hero image. Keep the supplied alt text descriptive.
6. Set up language switching with Wix Multilingual for English, Bahasa Melayu and Chinese. The prototype's browser-translation widget is only for the static preview; use Wix's native language management on the actual Wix build.
7. Set mobile breakpoints and check the page at phone width: navigation, image crop, heading wraps, fields, buttons and footer should remain readable and tappable.

## Design system

Each concept keeps its own palette and fictional brand presentation. Reuse the shared section structure but preserve distinct imagery, voice and color styling for the Chinese Malaysian, Malay and Indian Malaysian concepts, plus the general, Kuala Lumpur, Johor and Penang concepts. All remain concept-only pages: keep the self-initiated / not paid client work footer disclosure, fictional-business caveat, and `noindex, follow` until replaced with approved real-business content.

Static previews are available at `/bridal-chinese/`, `/bridal-malay/`, `/bridal-indian/`, `/bridal-general/`, `/bridal-kl/`, `/bridal-johor/` and `/bridal-penang/`. Before publishing a real Wix site, replace concept details with the boutique's approved name, services, policies, availability and contact configuration; do not present fictional information as factual claims.
