# QA Report: Yasmin Raygada

**Date:** 2026-02-11
**URL:** https://cofoundy.github.io/portfolio-yasmin-raygada/
**Status:** FAIL

## Data Validation
- [x] Name matches source (Sheet: "Yasmin Raygada", Page: "Yasmin Raygada")
- [x] Email matches source (Sheet: "yasportsolutions@gmail.com", Page: same)
- [x] Title consistent with source (Form: "Account Manager" + "Google Ads and LSA expert", Page: "Google Ads Specialist & Account Manager")
- [x] Companies from CV (YaSOLUTIONS from form, United Rentals, Tight Line Marketing, Peru Pacifico S.A. all in CV)
- [x] Dates from CV (all date ranges match CV entries)
- [!] Possible embellishment: "Google Ads Certified Professional", "Microsoft Dynamics CRM Certification", and "LSA Specialist Training" listed as education achievements but CV does not mention these as formal certifications — only as skills/experience

## Clean Deploy
- [x] No watermarks or "Powered by" text
- [x] No "Lorem ipsum" or placeholder text
- [x] No "undefined" or "null" visible in content
- [x] No template branding visible
- [ ] **FAIL** — Footer shows Twitter (X) and GitHub icons with no href (ghost links from template not conditionally rendered)
- [ ] **FAIL** — Hero has programming-symbol background pattern (</>, =>, [], etc.) — wrong for a Google Ads / marketing professional

## Language
- [ ] **FAIL** — Client requested English ("Pueden hacer mi version en Ingles?") but UI is in Spanish: nav labels "Sobre Mi", "Proyectos", "Experiencia", "Educacion"; footer "Todos los derechos reservados"; `<html lang="es">`
- [x] Content body (aboutMe, experience bullets) is in English

## Technical
- [x] Page loads (HTTP 200)
- [x] CSS loads (HTTP 200 for _astro/index.B57cf2Ov.css)
- [x] Favicon loads (HTTP 200, favicon.svg with "YR" initials in #00A5A8)
- [x] Profile image loads (HTTP 200, profile.svg — SVG avatar with "YR" initials, no photo used per "sin foto" note)
- [x] astro.config.mjs has correct site + base configuration
- [!] Console errors: Chrome MCP unavailable during QA — could not verify
- [!] Screenshots: Chrome MCP unavailable during QA — no visual evidence captured

## Project Links
- [!] All 3 project cards have href="#" with clickable arrow icons that imply external links — misleading UX

## Issues Found (ordered by severity)

### CRITICAL
1. **Language mismatch**: Client explicitly requested English. Navigation labels ("Sobre Mi", "Proyectos", "Experiencia", "Educacion"), footer text ("Todos los derechos reservados"), and `<html lang="es">` are all in Spanish. Must be changed to English equivalents ("About Me", "Projects", "Experience", "Education", "All rights reserved") and `<html lang="en">`.

2. **Ghost social icons in footer**: Twitter (X) and GitHub icons render in footer as `<a>` elements with no `href` attribute because `siteConfig.social.twitter` and `siteConfig.social.github` are undefined. Footer.astro lacks conditional rendering for these links. Known template bug.

### MINOR
3. **Programming symbols in hero background**: SVG pattern includes code symbols (`</>`, `=>`, `[]`, `()`, `::`, `==`, `++`, `;`) which are developer-oriented. Inappropriate for a Google Ads Specialist / marketing professional. Should use marketing-relevant decorative elements or neutral geometric patterns.

4. **Project links are "#"**: All 3 project cards link to `#` but display an arrow icon suggesting they are external links. Either remove the arrow/link behavior or add actual URLs.

5. **Education embellishments**: "Google Ads Certified Professional", "Microsoft Dynamics CRM Certification", and "LSA Specialist Training" are listed as education achievements but are not confirmed in the CV as formal certifications. The CV says she is a "high level user" of MS Dynamics, not certified. Risk of misrepresentation.

## Evidence
- Chrome MCP server was unavailable — no screenshots captured
- All checks performed via curl HTTP requests and HTML content analysis
