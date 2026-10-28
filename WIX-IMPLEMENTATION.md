# Wix Studio recreation handoff

## Compatibility and delivery model

All seven bridal concepts are responsive static HTML/CSS references designed to be **manually rebuilt in Wix Studio** when a client requests a Wix site. Wix Studio is the target editor because its native sections, containers, grids, stacks, menus, repeaters, accordions, images and forms can reproduce the layouts. Each page has its own inline CSS and explicit component structure; there is no framework or app runtime.

This is **not** a one-click Wix deploy, Wix import file, or completed Wix implementation. No Wix-authorized importer has been built or verified. The static HTML is the visual source of truth; `wix/site-manifest.json` describes each separate shop concept, and `wix/design-spec.json` records route-by-route section order, source titles, asset paths and crop/alt text, inline CSS, theme values, form fields/options and responsive reference viewports. A Wix builder should recreate the source—not apply one shared template to all seven.

The intended acceptance criterion is a complete manual Wix Studio build whose appearance matches the corresponding source page 1:1 at the specified viewports. That fidelity is a target, not a claim that Wix has already been built or screenshot-verified.

## Seven deliberately different website systems

| Shop concept | Distinct design and information architecture |
| --- | --- |
| **Hong Yue Bridal · Chinese Malaysian** | Ceremony-editorial split hero; three-moment ribbon; framed story image; horizontal ritual timeline. Collections are organized around tea ceremony, modern change and reception; experience and family fitting pages focus on ritual planning and family questions. |
| **Seruni Bridal · Malay** | Calm centered composition with a tall arched portrait, generous whitespace and soft sage panels. Its gown page foregrounds modest silhouettes and preference notes; the experience page is comfort-led; the appointment page pairs the form with the detail image. |
| **Aaroh Bridal House · Indian Malaysian** | Image-first ruby hero and a three-stage event triad. Its collection and experience pages follow welcome, ceremony and reception moments; the appointment page includes a textile-detail image beside the form. |
| **Ever After Bridal · inclusive** | Asymmetric bento hero, inset secondary image and a style-chooser tile grid. Collections use comparison tiles; the guide covers fit, comfort, budget and questions; the enquiry page uses a broad, no-pressure planning layout. |
| **Atelier Kuala · Kuala Lumpur** | Dark editorial canvas, very large typographic masthead, full-width image and numbered index rows. The collection is a magazine-style lookbook; experience is a concise appointment sequence; enquiry is a minimal private-consultation layout. |
| **Rona Bridal Studio · Johor** | Warm practical hero with a tilted visit card, package-board rows and step cards. Collections compare illustrative wardrobe components; the experience page is a shared planning guide; the appointment form is paired with visit-planning information. |
| **Juniper & Lace · Penang** | Heritage-inspired archival frame, inset image, craft-note spread and material-detail grid. Its collection, experience and visit pages retain the framed/editorial language without claiming a real heritage address or craft provenance. |

These are materially different page structures and visual compositions, not seven palette swaps. The route-by-route structure and exact source rules are recorded in `wix/design-spec.json` and visible in each `bridal-*/` HTML page. Navigation is also intentionally varied across concepts: Chinese horizontal masthead, Malay centered links, Indian left rail, general bottom dock, Kuala Lumpur right rail, Johor native disclosure menu, and Penang two-tier tab strip. Preserve each treatment and its breakpoint behavior during manual recreation. The portfolio homepage uses live local homepage previews in browser-window frames rather than standalone bridal photographs.

## Manual 1:1 build procedure

1. Use `wix/design-spec.json` and the matching HTML route as the build sheet and final content reference. Preserve the exact page order, distinct navigation labels, source titles, supplied images, crop/focal positions, text and component proportions.
2. Build the same four routes—Home, Collections, Experience, Appointments—with Wix Studio native sections and containers. Recreate each concept’s own grid or stack hierarchy; do not flatten all concepts into the same layout.
3. Set the recorded palette and typography. The source uses Georgia/Times-style serif headings and Arial/Helvetica body text, with responsive sizes and spacing in the inline CSS. Translate the source breakpoint and fluid values into Wix Studio responsive settings.
4. Upload the exact supplied hero and detail images to Wix Media Manager. Match `object-fit: cover` and each source focal position; preserve descriptive alt text.
5. Use native Wix Forms with the exact source labels and concept-specific select options. Preserve name, email, optional date/season and note fields, and keep enquiry CTAs on the `#borang` anchor. Do not add phone fields or WhatsApp actions. The static concept form opens an email draft to `hello@jobshore.dpdns.org`; a commissioned Wix build must use the client-approved form destination and privacy configuration.
6. Replace the static preview’s Google translation widget with Wix Multilingual for English, Bahasa Melayu and Chinese. Do not embed the whole static page as a workaround for recreating the design.
7. Compare the Wix page with the source at **1440×900 desktop, 768×1024 tablet, and 390×844 mobile**. Check section order and height, grids, heading wraps, image crop, spacing, borders, colors, buttons, navigation, forms and footer. Adjust Wix breakpoints until the client-approved views match. Do not call the Wix implementation 1:1 until that comparison has been performed.

## Fictional content and public-contact rules

All shop names, areas, hours, product styles, sample prices, service scope and appointment terms are fictional placeholders for privacy and design demonstration. No real stock, availability, operating address or shop is represented. Keep every concept `noindex, follow` and retain the footer disclosure that the design is self-initiated, not paid client work. Public contact is `hello@jobshore.dpdns.org` only, and each footer must say **“Reka bentuk oleh Jobshore (M) Sdn Bhd”**. Do not add phone numbers, WhatsApp links or a Jobshore website link.

## Scope research (inspiration only)

The concepts use broad service patterns from Malaysian and Singapore bridal retail as scope references—not real businesses’ names, copy, photos, prices, policies or claims. Roundups are starting points, not authoritative rankings: [Malaysia bridal boutique guide](https://theweddingnotebook.com/inspire/fashion-and-beauty/best-bridal-boutique-in-kl-singapore) and [Singapore bridal boutique guide](https://theweddingnotebook.com/inspire/fashion-and-beauty/best-bridal-boutiques-in-singapore). Ten official Malaysian and Singapore bridal homepages were reviewed for category scope, content hierarchy and broad information-architecture patterns; the shortlist, takeaways and method limitations are recorded in [`BRIDAL-REFERENCE-RESEARCH.md`](BRIDAL-REFERENCE-RESEARCH.md). Roundups are discovery sources, not authoritative rankings, and this was not a screenshot-based visual benchmark. These references informed the breadth of the fictional concepts only.
