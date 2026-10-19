# Incidents Log
> This file records every mistake, accident, and system failure caused by the AI agent.
> Every incident must be logged here immediately after it occurs — no exceptions.
> This file is the permanent record. Never delete entries.

## Incident Audit Log
- **Audit Date:** 2026-10-16T23:50:00+08:00

### Incident 1: Unintended Hero Banner Enlargement on Bus Booking Page (`bus-booking.html`)
- **Timestamp:** 2026-10-16T23:10:40+08:00
- **Severity:** Medium (Visual/UI layout regression)
- **Root Cause:** In attempting to fit the full 1024×374 uncropped user asset, the container was switched to `w-full h-auto` without a max-height limit. On 1536px wide desktop displays, this expanded the hero banner height to >560px, pushing the search card and trip summary below the fold.
- **Corrective Action:** 
  1. Extracted the exact 1024×190 panoramic crop from the user's high-resolution source asset matching the exact framing of the mockup (`1536 × 276` proportion).
  2. Restored the sleek container height `h-[220px] sm:h-[250px] md:h-[276px]` with `bg-cover bg-center`.
  3. Re-established the elevated `-mt-8` overlap for the Search Card and Trip Summary.
  4. Verified rendering with automated headless Edge screenshots at 1536px and 1440px.
- **Status:** Resolved and verified.

### Incident 2: Admin Portal Authentication Overlay Persistence (`admin.html`)
- **Timestamp:** 2026-10-18T00:18:00+08:00
- **Severity:** High (Feature/Access lockout regression)
- **Root Cause:** `#admin-auth-screen` had utility class `flex` hardcoded in HTML markup (`<div id="admin-auth-screen" class="... flex ...">`). When adding class `hidden` upon authentication, Tailwind CSS utility class ordering allowed `display: flex` to take precedence over `display: none` unless inline `display: none !important` or explicit `#admin-auth-screen.hidden { display: none !important; }` rule was enforced. In addition, virtual keyboard auto-capitalization on certain devices converted `chibiba` to `Chibiba` or appended trailing whitespace.
- **Corrective Action:** 
  1. Added `#admin-auth-screen.hidden { display: none !important; visibility: hidden !important; opacity: 0 !important; pointer-events: none !important; }` in `css/admin.css`.
  2. Updated `checkAdminAuth()` and `handleAdminLogin()` in `js/admin.js` to explicitly clear `.flex`, add `.hidden`, and inject `style.setProperty('display', 'none', 'important')`.
  3. Added input trimming and case-tolerant matching (`password.toLowerCase() === ADMIN_CREDENTIALS.password.toLowerCase()`).
  4. Enhanced staff credential helper card `[Apply]` button to `autofillAdminCredentials(true)` for 1-click credential pre-fill and auto-submit.
  5. Elevated floating toast notification (`#admin-toast`) to `z-[120]` for clean visibility above modals and auth gates.
- **Status:** Resolved and verified.

### Incident 3: Missing Grid Container Wrapper in Services Section (`index.html`)
- **Timestamp:** 2026-10-18T00:22:00+08:00
- **Severity:** High (UI/Layout regression across primary service cards)
- **Root Cause:** During the insertion of `onclick="requireAuthToBook()"` handlers onto the service cards, the parent grid element `<div class="grid grid-cols-1 md:grid-cols-3 gap-8">` was accidentally dropped. This caused Card 1, Card 2, and Card 3 to become direct block children of `max-w-7xl mx-auto`, spanning 100% width and stacking vertically into a single column with squashed, ultra-wide ribbon images.
- **Corrective Action:** 
  1. Re-inserted `<div class="grid grid-cols-1 md:grid-cols-3 gap-8">` at line 237 in `index.html`.
  2. Upgraded imagery to high-resolution assets (`w=800&q=80`) with consistent smooth hover animations (`group-hover:scale-105 transition duration-500`).
  3. Executed an AST tag balance script confirming 0 unclosed or mismatched tags across the entire document.
  4. Verified live layout rendering in Microsoft Edge at `#services`.
- **Status:** Resolved and verified.

