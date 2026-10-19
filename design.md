# Design Details
Always update for website or app design details.

## 1. Project & Brand Identity
- **Project Name:** Mckanes Travel and Tours
- **Tagline:** Elevate Your Travel Journey / Experience The Magic Of Travel!
- **Brand Logo:** 
  - Dual-tone blue aesthetic: Globe icon (`#1a5b92`)
  - Primary text: **Mckanes** (`#1a5b92`, font-bold, text-xl)
  - Subtext: **TRAVEL & TOURS** (`#5ba4d6`, font-bold, tracking-wider, text-[9px])

## 2. Color Palette & Theme Tokens
- **Brand Navy / Primary Blue:** `#1a5b92` (Logo mark, brand title)
- **Brand Accent Cyan / Light Blue:** `#5ba4d6` (Logo subtitle, accents)
- **Call-to-Action Blue:** `#3b82f6` (Primary buttons, play button icon, link highlights)
- **CTA Hover Blue:** `#2563eb` / `#1d4ed8` (Interactive hover states)
- **Card / Cutout Accent Slate:** `#495e69` (Dark Slate Blue container for "Awesome Places" teaser)
- **Social Brand Blue:** `#1877f2` (Facebook circular icon background)
- **Backgrounds:**
  - Page Background: `#f9fafb` (Tailwind `gray-50`)
  - Hero & Header Container: `#ffffff` (Pure white)
  - Card Backgrounds: `#ffffff` with subtle borders (`border-gray-100`)
- **Text & Contrast:** 
  - Primary Headings: `#111827` (Tailwind `gray-900`)
  - Secondary / Body Text: `#4b5563` / `#6b7280` (Tailwind `gray-600` / `gray-500`)
  - Accent / Overlay Text: Pure White (`#ffffff`) with subtle text shadows

## 3. Typography & Styling
- **Font Family:** `'Poppins', sans-serif` loaded via Google Fonts CDN (`weights: 300, 400, 500, 600, 700, 800`).
- **Headings:**
  - Main Display Hero Headline: `text-6xl md:text-[5.5rem] font-bold leading-[1.1] tracking-tight`
  - Section Headings: `text-3xl font-bold` and `text-4xl font-extrabold tracking-tight`
  - Card Titles: `text-lg font-bold` and `text-xl font-bold`
- **Buttons & Tags:** Uppercase or Capitalized with `font-semibold` / `font-medium`, rounded pill shapes (`rounded-full`).

## 4. Section-by-Section Design Architecture

### A. Navigation Bar (`<nav>`)
- **Container:** `py-6 px-12 relative flex items-center justify-between bg-white z-50`
- **Left:** Brand logo with `fas fa-globe` icon and stacked brand title (`z-20`).
- **Center:** Navigation links (`HOME`, `ABOUT`, `PACKAGE`, `CONTACT`, `REVIEWS`) positioned in the exact horizontal center (`absolute inset-x-0 justify-center`) with `pointer-events-auto` for complete clickability.
- **Right:** Symmetrical spacer (`w-32`) to maintain balanced visual alignment across screen widths.
- **States:** Hover transition to `text-blue-600`. Seamless integration with hero (no shadow border).

### B. First Page Hero Section (Full View `min-h-screen`)
- **Wrapper:** `min-h-screen flex flex-col bg-white font-sans relative pb-10 overflow-x-clip` (with `body.overflow-x-hidden` eliminating horizontal scrollbars during 3D vehicle breakout).
- **Inner Frame:** `max-w-[1280px] mx-auto px-4 sm:px-6 relative flex flex-col justify-between`
- **Rounded Visual Container:**
  - Outer Frame: `relative w-full h-[540px] sm:h-[580px] md:h-[620px] lg:h-[670px]` maintaining the exact 1.82:1 aspect ratio of the reference mockup (`media_1792163300749_219b7f11.png`).
  - Background Card: `absolute inset-0 rounded-[2.8rem] lg:rounded-[3.2rem] overflow-hidden shadow-2xl bg-gray-300` with user-provided high-resolution mountain and cloud landscape photography (`images/hero_bg.jpg`).
- **Overlapping 3D Foreground Cutouts:**
  - **Passenger Airplane (`images/user_plane.png`):** Generated directly from the user-uploaded high-res passenger airliner image with aerodynamic contour preservation, fixed-range edge processing, and unmultiplied anti-aliased alpha matting. Positioned `absolute z-30` at `left: 49.5%`, `top: 5.5%`, `width: 75%`, `transform: rotate(1deg)` with `drop-shadow(0 20px 25px rgba(0,0,0,0.35))`. The nose tip aligns with the top of the word "Experience", while the right wing and rear fuselage break cleanly out past the card's right boundary.
  - **Tour Bus (`images/bus.png`):** Cropped tightly to its exact 296×507 bounding box. Positioned `absolute z-30` at `left: -0.5%`, `bottom: 4%`, `width: 26.5%` with `drop-shadow(0 15px 20px rgba(0,0,0,0.45))`. Perfectly anchored on the green hill in the lower-left corner with its rear bumper breaking out subtly past the card's left boundary and plenty of breathing room below the CTA button.
- **Vertical Stepper:**
  - Located on the left margin within the hero container.
  - Circle 1: `bg-white text-black font-bold shadow-md` (Active phase, aligned with "ELEVATE YOUR TRAVEL JOURNEY").
  - Vertical Line: `w-px h-16 lg:h-20 bg-white/60 my-1.5`.
  - Circle 2: `border border-white text-white backdrop-blur-sm` (aligned with "The Magic").
  - Vertical Line: `w-px h-16 lg:h-20 bg-white/60 my-1.5`.
  - Circle 3: `border border-white text-white backdrop-blur-sm` (aligned horizontally with the CTA button).
- **Hero Copy & Buttons:**
  - Tag: `ELEVATE YOUR TRAVEL JOURNEY` (`text-white tracking-[0.2em] font-semibold text-xs mb-3 uppercase drop-shadow-md anim-tag` with entrance slide-up and breathing letter-spacing tracking).
  - Headline (with out-of-phase floating wave keyframes and hover micro-interactions): 
    - Line 1: `<span class="text-white anim-line-1">Experience</span>` (`@keyframes floatWord1`, 4.8s floating cycle).
    - Line 2: `<span class="text-[#1a2332] anim-line-2">The Magic</span>` (`@keyframes floatWord2`, 5.2s floating cycle).
    - Line 3: `<span class="text-[#1a2332] anim-line-3">Of Travel!</span>` (`@keyframes floatWord3`, 4.6s floating cycle).
  - Primary CTA: Pill button `bg-[#2986fe] hover:bg-blue-600 text-white px-8 py-3.5 rounded-full font-semibold shadow-lg shadow-blue-500/30 hover:scale-[1.02] active:scale-95 transition`.
  - Secondary CTA: Play video circle `w-12 h-12 bg-white rounded-full shadow-lg hover:scale-110 active:scale-95` with `fas fa-play text-[#2986fe]` and an ambient radiating pulse ring (`rippleWave`).
- **"Awesome Places" Cutout Corner:**
  - Positioned bottom-right: Wrapped in an organic white concave frame (`pt-2.5 pl-2.5 rounded-tl-[3.5rem] z-20`).
  - Dark Slate Container: `w-[300px] sm:w-[330px] lg:w-[360px] h-[126px] lg:h-[138px] bg-[#4a6375] rounded-tl-[2.8rem] rounded-br-[2.8rem] p-4 lg:p-5 text-white flex flex-col justify-between shadow-inner`.
  - Header: Right-aligned `Know More <i class="fas fa-arrow-right"></i>` with `text-gray-900 font-bold`.
  - Avatar Group: 3 overlapping circular thumbnails (`w-10 h-10 lg:w-11 lg:h-11 rounded-full border-2 border-white -space-x-2.5 shadow-sm`).
  - Label: `Awesome Places` with subtitle `Discover The World / One At A Time!`.
- **Bottom Social & Partners Strip:**
  - Social Pill: `rounded-full px-6 py-2.5 bg-white border border-gray-100 shadow-sm flex items-center gap-5`. Includes "Follow" label, Twitter, Instagram, Facebook (`bg-[#1877f2]`), TikTok.
  - Partner Logos: Full-color vector logos for Booking.com, Expedia, agoda, and trivago.

### C. Services Section ("Explore the Philippines, Your Way!")
- **Files:** [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html) (`#services`), [js/main.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/main.js)
- **Grid Architecture:**
  - Enclosed within a responsive 3-column CSS Grid container: `<div class="grid grid-cols-1 md:grid-cols-3 gap-8">` nested in `max-w-7xl mx-auto`.
  - Guarantees balanced side-by-side card distribution across desktop (`md:grid-cols-3`) and tablet, collapsing into a natural single-column flow on mobile screens.
- **Card Styling:** `rounded-3xl shadow-sm border border-gray-100 hover:shadow-xl transition duration-300 overflow-hidden bg-white group`.
- **Card 1 (Find Your Destination):**
  - High-definition Palawan limestone coast photograph (`&w=800&q=80`) with smooth `group-hover:scale-105 transition duration-500`.
  - Blue circular marker badge (`fas fa-map-marker-alt`), dual-line header ("Find Your Destination"), introductory synopsis, and "Find Now" CTA linked directly to `#packages`.
- **Card 2 (Book A Plane Ticket):**
  - Authentic Cebu Pacific Airbus aircraft photograph (`images/cebu_pacific.jpg`, source `media_1792163997806_f54d3921.jpg`) with `object-position: center 55%` and `group-hover:scale-105 transition duration-500`.
  - Airline overlay badge ("Cebu Pacific"), circular flight glyph (`fas fa-plane`), and "Book Now" CTA with glowing blue drop shadow.
  - Intercepted by `requireAuthToBook('plane', event)` ensuring guest visitors trigger the `#auth-required-modal` before entering ticketing.
- **Card 3 (Book A Bus Ticket):**
  - High-definition provincial touring coach photograph (`&w=800&q=80`) with `group-hover:scale-105 transition duration-500`.
  - Operator badge overlay ("Victory Liner"), circular bus glyph (`fas fa-bus`), and "Book Now" CTA with glowing blue drop shadow.
  - Intercepted by `requireAuthToBook('bus', event)` ensuring guest visitors trigger the `#auth-required-modal` before entering ticketing.

### D. Popular Destinations Section (Asymmetrical Grid)
- **Header Row:** "Popular Destinations" title with "Explore all destinations" text link.
- **Left Featured Card (500px):**
  - Image: Coron Island, Palawan.
  - Overlays: Dark gradient (`from-black/80 via-black/40 to-transparent`).
  - Badge: Rating pill (`4.9` with star icon).
  - Copy: Description and "Explore Destination" button.
- **Right Stacked Cards (3x 1/3 height):**
  - Card 1: White Beach (Boracay Island, Aklan) - Rating: 4.8.
  - Card 2: Waterfall Trails (Lazi, Siquijor) - Rating: 4.7.
  - Card 3: Cultural Landscapes (Banaue, Ifugao) - Rating: 4.5.


### E. Bus Ticket Booking Interface (`bus-booking.html`)
- **Header Banner (Framed Compact Card - Exact Match to Plane Booking Hero):**
  - High-resolution framed hero graphic banner (`images/bus_banner_exact.png`, 1024×190 master resolution, ~5.39:1 aspect ratio).
  - Structured within `max-w-7xl mx-auto px-4 sm:px-6 pt-4 pb-1` matching the exact container width, margins, and card framing of [plane-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/plane-booking.html) as requested in user mockup `media_1792202789066_9be0edef.png`.
  - Inner card: `rounded-2xl overflow-hidden shadow-md border border-blue-100 bg-[#3a8adc]`.
  - Image element: `<img src="images/bus_banner_exact.png" class="w-full h-auto object-cover select-none">` preserving crisp aspect ratio without tall vertical bloat.
  - Fully frames "Book Your Bus Ticket" 3D typography ("Bus" in gradient cyan), highland mountain range, Daewoo bus windshield, Victory Liner coach side profile, and station canopy.
  - Screen-reader accessible headline (`alt="Book Your Bus Ticket - Mckanes Travel and Tours"`).
- **Main 2-Column Content Grid (`max-w-7xl mx-auto px-4 sm:px-6 py-5 sm:py-6 relative z-20 pb-16`):**
  - **Left Column (8 cols):**
    - Search & Filter Card (`bg-white rounded-2xl shadow-xl border border-gray-100 p-6`) neatly positioned below the framed hero card with trip switcher pills ("One-way" / "Round-trip"), unified Origin & Destination flex container (`lg:col-span-6`) with inline circular swap trigger, optimized "Departure" date picker (`lg:col-span-2`), spacious "Passengers" selector (`lg:col-span-2`) with descriptive labels ("1 Passenger", "2 Passengers"...) eliminating visual truncation and icon collision, and "Search Buses" CTA (`lg:col-span-2`).
    - Available Bus Trips section with day stepping navigator, operator filter pills, and interactive trip selection cards.
  - **Right Column (4 cols):**
    - Sticky `Trip Summary` sidebar card (`sticky top-6`) aligned horizontally with the Search Card, displaying destination thumbnail, selected route timetable, passenger details, fee breakdown, and checkout CTA.
- **Available Bus Trips Section (Left Column):**
  - Section title with date navigation chevrons (`< Sun, Oct 18, 2026 >`).
  - Operator filter pills: "All Operators" (active), "Victory Liner", "Genesis", "JoyBus", "Partas", "Philtranco".
  - Sort dropdown ("Departure Time", "Price", "Duration").
  - Trip list cards with operator logos, service class badges (Deluxe, Premium Deluxe, Executive), amenity icons (WiFi, Charging Port, Comfortable Seat), departure/arrival timetables with route line indicator, per-person pricing, and interactive "Select" / "Selected" buttons.
- **Trip Summary Sidebar (Right Column):**
  - Sticky summary card with destination preview photo (Manila → Baguio).
  - Selected trip schedule breakdown (Terminal origin/destination, duration).
  - Passenger details summary (1 Adult - Juan Dela Cruz).
  - Fare breakdown (Base Fare + ₱30 Terminal Fee = Total Amount).
  - Primary button: "Continue to Passenger Details →".
  - "Back to home" navigation link.
- **Passenger Booking Modal Form:**
  - Interactive popup modal containing traveler name inputs, email, mobile number, seat preference selector (12A, 12B, 14A, 14B), and payment selection (GCash/Maya, Credit Card, Over-the-counter).
  - Instant ticket confirmation view with booking reference code (`MCK-BUS-8492`).


### F. Traveler Reviews & Testimonials Section (`#reviews`)
- **Container:** `py-20 bg-gradient-to-b from-blue-50/40 via-sky-50/30 to-blue-50/60 px-8 relative overflow-hidden border-t border-gray-100`
- **Header Elements:**
  - Pill badge: `TRAVELER REVIEWS` (`bg-[#e0f2fe] text-[#0284c7] font-extrabold text-xs tracking-widest uppercase px-5 py-2 rounded-full`).
  - Headline: `WHAT OUR <span class="text-blue-600">TRAVELERS SAY</span>` (`text-3xl md:text-5xl font-extrabold text-gray-900 tracking-tight`).
  - Subtitle: Explanatory paragraph centered with `max-w-2xl mx-auto text-gray-500 text-sm md:text-base`.
  - Decorative SVG airplane flight path with looped dashed stroke and `fas fa-plane` icon in top-right.
- **Review Cards (3-Column Responsive Grid):**
  - Card 1: Easy Booking Experience (5 stars, quote, Maria S., Manila, beach boat banner).
  - Card 2: Discovering New Places (5 stars, quote, Angela R., Laguna, island view banner).
  - Card 3: Convenient Travel Planning (5 stars, quote, Joshua M., Quezon City, mountain traveler banner).
  - Styling: `bg-white rounded-3xl p-6 shadow-sm border border-gray-100 hover:shadow-xl transition-all duration-300`.
- **Metrics & Stats Bar:**
  - Floating pill-container: `mt-16 bg-white/90 backdrop-blur-sm border border-blue-100/80 rounded-3xl p-8 max-w-4xl mx-auto grid grid-cols-1 md:grid-cols-3 gap-8 shadow-sm`.
  - Stat 1: `10+` Destinations to Explore with map pin icon.
  - Stat 2: `12K+` Travelers Inspired with user group icon.
  - Stat 3: `4.9` Average User Rating with star icon.

### 8. Sticky Navigation & Seamless Header Elevation
- **Structure:** Independent `<header id="main-header">` with `sticky top-0 z-50` placed as a direct child of `<body>` and sibling to the hero section.
- **Glassmorphism & Scroll Elevation:**
  - Base State: `bg-white/95 backdrop-blur-md border-b border-transparent transition-all duration-300`.
  - Scrolled State: JavaScript listener toggles `shadow-md shadow-gray-200/50 border-gray-100` when `window.scrollY > 20`.
- **Navigation Elements:**
  - Brand Logo: Globe icon with hover rotation and text link smoothly scrolling back to top.
  - Centered Nav Links: `HOME`, `ABOUT`, `PACKAGE`, `CONTACT`, `REVIEWS`.
  - Click Actions: `HOME` triggers `window.scrollTo({top: 0, behavior: 'smooth'})`; `ABOUT` points to `#services`; `PACKAGE` points to `#packages`; `REVIEWS` points to `#reviews`; `CONTACT` points to `#contact`.
  - Target Sections: Configured with `scroll-mt-24` ensuring sticky header never overlaps section titles upon anchor jumping.
- **Footer / Contact Section (`#contact`):**
  - Dark container (`bg-gray-900 text-white pt-16 pb-12 px-8 border-t border-gray-800 scroll-mt-24`) featuring brand description, social channel icons, quick link directories, top domestic destination links, direct contact lines (+63 02 8888-MCKANES, support@mckanestravel.ph), 24/7 service notice, and copyright bar with Back to Top link.

### 9. Hero Vehicle Motion & Kinetic Entrance Choreography
- **Commercial Airplane (`anim-hero-plane`):**
  - Flight Entrance Keyframe (`@keyframes planeFlyIn`): Begins at `translate3d(260px, 115px, 0) scale(0.86) rotate(-2.5deg)` with `opacity: 0`, climbing along its fuselage flight angle over 1.9s with cubic-bezier easing (`cubic-bezier(0.16, 1, 0.3, 1)`), smoothly banking and settling into `translate3d(0, 0, 0) scale(1) rotate(1deg)`.
  - Ambient Cruising Keyframe (`@keyframes planeCruising`): Runs continuously after entrance (6s cycle), drifting `-5px` horizontally and `-8px` vertically with a `+0.5deg` bank rotation to emulate cruising through the sky.
- **VIP Tour Coach (`anim-hero-bus`):**
  - Driving Entrance Keyframe (`@keyframes busDriveIn`): Begins at `translate3d(-240px, 8px, 0) scale(0.94)` with `opacity: 0`, driving forward along the grass roadway into its position at 1.7s (`cubic-bezier(0.2, 0.9, 0.3, 1)` with 0.15s offset delay), simulating vehicle brake deceleration and pneumatic suspension settling at `left: -0.5%; bottom: 4%`.

### 10. Interactive Hero Stepper Carousel & Philippine Tourism Video Showcase
- **Vertical Stepper Interaction (Steps 1, 2, 3):**
  - **Structure:** 3-step circular numbered indicator buttons (`#step-btn-0`, `#step-btn-1`, `#step-btn-2`) linked by vertical progress track connectors (`#step-track-0`, `#step-track-1`).
  - **Active State:** Solid white background (`bg-white text-black font-bold`), elevated with `shadow-lg shadow-white/30 ring-4 ring-white/20 scale-105`.
  - **Inactive State:** Semi-transparent outlined pills (`border border-white text-white font-semibold backdrop-blur-sm hover:bg-white/40 hover:scale-110`).
  - **Progress Fill Animation:** Vertical connector line heights dynamically animate (`height: 0%` to `100%`) reflecting current sequence progression.
- **Narrative 3-Slide Architecture:**
  - **Slide 1 (All-in-One Multimodal Travel):**
    - Headline: "Experience The Magic Of Travel!"
    - Eyebrow Tag: "ELEVATE YOUR TRAVEL JOURNEY"
    - CTA: "Book A Trip Now" (`#services`)
    - Cutout Badge: "Awesome Places", 3 destination avatars, background `#4a6375`
    - Vehicle Focus: Balanced perspective with both airliner (`left: 49.5%, top: 5.5%`) and red tour coach (`left: -0.5%, bottom: 4%`) fully active.
  - **Slide 2 (Domestic Flight Adventures):**
    - Headline: "Fly High Above The Island Skies!"
    - Eyebrow Tag: "AUTHENTIC CEBU PACIFIC & DOMESTIC FLIGHTS"
    - CTA: "Book A Plane Ticket" (`#services`)
    - Cutout Badge: "Island Getaways" (Boracay • Palawan • Siargao), background `#1e40af`
    - Vehicle Focus: Airliner banks forward with prominent scale (`scale(1.06)`) and deeper atmospheric drop shadow; bus opacity dims to `0.25` with `scale(0.92)`.
  - **Slide 3 (Highland Express Bus Trips):**
    - Headline: "Ride Across Scenic Mountain Highways!"
    - Eyebrow Tag: "COMFORTABLE HIGHLAND BUS TRIPS"
    - CTA: "Book Bus Ticket" ([bus-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/bus-booking.html))
    - Cutout Badge: "Highland Express" (Baguio • Sagada • Vigan), background `#0d9488`
    - Vehicle Focus: Red VIP coach pulls forward with prominent scale (`scale(1.1) translate(15px, -5px)`) and heavy road shadow; airplane opacity dims to `0.25`.
- **Timing & Ergonomics:**
  - Auto-rotation interval: Exactly 5.0 seconds per slide (`SLIDE_DURATION = 5000`) with smooth linear progress fill on connecting tracks (`#step-track-0`, `#step-track-1`).
  - Active Button Styling: Pure white circle (`bg-white text-black font-extrabold scale-105`) with a 6px frosted halo ring (`box-shadow: 0 0 0 6px rgba(255, 255, 255, 0.35), 0 4px 16px rgba(0, 0, 0, 0.25)`).
  - Inactive Button Styling: Frosted translucent circle (`border: 1.5px solid rgba(255, 255, 255, 0.85); background: rgba(255, 255, 255, 0.25); text-white font-bold backdrop-blur-sm`).
  - Uninterrupted Movement: Removed full-stage hover pausing so the 5-second automatic progression cycles reliably without getting stuck.
  - Manual Override: Clicking any step number (`1`, `2`, `3`) immediately switches to that slide and restarts the 5-second countdown.
- **Philippine Tourism Video Showcase Modal:**
  - Trigger: Circular Play Video button with pulsing ripple halo ring.
  - Modal Overlay (`#video-modal`): Fullscreen backdrop blur (`backdrop-blur-md bg-black/80 z-[100]`) with spring scaling modal window (`#video-modal-card`).
  - Player: Privacy-enhanced YouTube embed (`youtube-nocookie.com`) playing the official Philippine tourism 4K showcase.
  - Dismissal: Explicit close button (`x`), backdrop click outside dialog, and global `Escape` keyboard listener.

### 11. Dedicated Plane Booking UI Specification (Mockup Exact Match)
- **Files:** [plane-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/plane-booking.html)
- **Visual Design & Layout:**
  - **Hero Header Graphic (`images/plane_banner.png`):** Uncompressed 936×185 banner asset displaying "Book Your Plane Ticket" ("Plane" in cyan blue `#00b4d8`) alongside an authentic Cebu Pacific Airbus A321neo banking across a vivid Philippine sky and green mountain horizon.
  - **Checkout Stepper Bar:** Horizontal white progress bar directly below the banner with 3 numbered steps:
    - Step 1: `1` (solid blue `#0066f5` circle) "Flight Details" / "Search and select your flight".
    - Step 2: `2` (outlined gray circle) "Passenger Information" / "Enter traveler details".
    - Step 3: `3` (outlined gray circle) "Review & Payment" / "Confirm and complete booking".
  - **Two-Column Flight Booking Workspace (7 cols / 5 cols):**
    - **Card 1: Flight Details Search Card:**
      - Plane icon badge with "Flight Details" heading and subtitle.
      - Trip type toggle pills: `Round-trip` (active solid `#0066f5` button with sync icon) and `One-way` (outlined button with arrow icon).
      - Origin & Destination cards: Pin icon with Manila (MNL) / Ninoy Aquino Int'l on left, Cebu (CEB) / Mactan-Cebu Int'l on right, and a circular animated swap button (`⇄`) in the center.
      - Departure Date (`Oct 15, 2026`) and Return Date (`Oct 20, 2026`) input cards with calendar icons.
      - Passenger counters: Adults (1), Children (0), Infants (0) with `[-]` and `[+]` counter buttons.
      - Cabin Class dropdown: Economy (`fas fa-couch`), Premium Economy, and Business Class.
      - Full-width Search CTA: Solid blue `[ 🔍 Search Flights ]` button (`bg-[#0066f5]`).
    - **Card 2: Passenger Information (Step 2):**
      - Number 2 blue badge, title, and verification shield notice ("Use the same name as shown on your government-issued ID or passport").
      - Passenger 1 (Adult) fields: First Name (`Juan`), Middle Name (`Dela`), Last Name (`Cruz`), Date of Birth (`Jan 15, 1990`), Gender (`Male`), Nationality (`Philippines` with flag), Passport Number (`P1234567A`), Passport Expiry (`Jan 15, 2030`).
      - Contact Information: Email Address (`juan.delacruz@email.com`) with mail icon and Phone Number with `🇵🇭 +63 ▾ 912 345 6789`.
      - Bottom Actions: `< Back to Flight Details` and `Continue to Review ➔` button.
    - **Right Column: Your Trip Summary Sidebar:**
      - Clipboard icon, "Your Trip Summary", and right-aligned `Edit` link.
      - Scenic island landscape card featuring turquoise lagoons with a white capsule `[Round-trip]` pill in the bottom right, and a dark navy bottom bar: `Manila (MNL) ➔ Cebu (CEB) | Oct 15, 2026 – Oct 20, 2026 | 1 Adult | Economy`.
      - Flights breakdown:
        - Departure: Wed, Oct 15, 2026 • 08:00 AM MNL ➔ 09:15 AM CEB (1h 15m, Direct) • Philippine Airlines PR 1841.
        - Return: Mon, Oct 20, 2026 • 04:20 PM CEB ➔ 05:40 PM MNL (1h 20m, Direct) • Philippine Airlines PR 1846.
      - Passenger & Cabin Class summary (`1 Adult`, `Juan Dela Cruz`, `Economy`).
      - Estimated Fare Breakdown: Base Fare `₱2,850`, Taxes and Fees `₱620`, Baggage Allowance (20 kg) `Included` (green text), Total Amount `₱3,470` in large bold blue font.
      - Informational notice: "Instant e-ticket receipt and airline booking reference (PNR) issued immediately upon payment."
  - **Dynamic Flight Search Results Panel (`#flight-results-panel`):**
    - Dynamic route schedule header displaying departure date and destination airport info.
    - Airline filter pills: `All Airlines`, `Cebu Pacific`, `Philippine Airlines`, and `AirAsia` with real-time catalog filtering.
    - Sorting controls: `Cheapest Fare`, `Earliest Departure`, and `Fastest Flight`.
    - Flight Leg Tabs for Round-trips: Outbound (`MNL ➔ CEB`) and Inbound (`CEB ➔ MNL`) with checkmark indicator on completed legs.
    - Dynamic Flight Cards: Airline logo badges (yellow 5J, red PR, red Z2), flight numbers, aircraft equipment (Airbus A321neo, A321, A320), departure/arrival times, flight durations, direct route badges, baggage allowance pills, amenity tags, live pricing, and interactive Select buttons.
  - **Dynamic Multi-Passenger Generator & Add-ons (`#card-passenger-info`):**
    - Dynamic form generator rendering individual profile cards for each passenger based on Adults/Children counters.
    - Lead passenger badge indicator on Passenger 1.
    - Dynamic remove button (`Remove ×`) for passengers > 1.
    - Seat selection group: Interactive pills for `12A (Window)`, `12B (Aisle)`, `14A (Window)`, and `14B (Aisle)`.
    - Baggage upgrades: `20kg Standard (Included)`, `32kg Extra (+₱450)`, and `40kg Heavy (+₱850)`.
    - Comprehensive travel protection checkbox (+₱280 per passenger) with real-time fare row toggle.
  - **Multi-State Review & Payment Confirmation Modal (`#review-modal`):**
    - **State 1 (Review & Payment):**
      - E-Ticket preview card with live PNR booking locator (e.g., `MCK-5J561-8924`), passenger manifest, route, seat assignment, and baggage tags.
      - Payment method selector: GCash, Maya, Credit/Debit Card, and Over-the-counter (7-Eleven / Bayad Center).
      - Dynamic payment form fields with account/mobile input and card expiration/CVV formatting.
    - **State 2 (Processing Reservation):**
      - High-fidelity animated loading spinner and reservation simulation ("Allocating airline seat assignments & generating digital barcode...").
    - **State 3 (Confirmed E-Ticket & Boarding Pass):**
      - Success banner with confirmed PNR reference and one-click copy button.
      - Official printable Boarding Pass (`#printable-boarding-pass`) with dual-stub airline layout, barcode graphic, QR code verification, flight details, gate, terminal, and seat tags.
      - Actions: One-click `Print Boarding Pass` (`window.print()`), `Download E-Ticket` (formatted text receipt blob), and `Book Another Flight` reset flow.
  - **Print Layout Styles (`@media print`):**
    - High-contrast print optimization isolating `#printable-boarding-pass` and suppressing web headers, background panels, and control buttons during browser print preview.

### 12. Popular Destinations Interactive Architecture & Modals
- **Files:** [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html) (`#destinations`, `#destination-modal`, `#all-destinations-modal`)
- **Visual Design & Assets:**
  - **Verified High-Fidelity Local Imagery:** Replaced broken remote URLs and mismatched images with verified local assets:
    - Coron Island: `images/coron.jpg` (authentic towering limestone karsts reflecting in crystal emerald waters).
    - White Beach: `images/boracay.jpg` (scenic tropical sunset with iconic paraw sailboats and coconut palms).
    - Waterfall Trails: `images/waterfall.jpg` (cascading mountain waterfalls and crystal swimming pools).
    - Cultural Landscapes: `images/banaue.jpg` (authentic UNESCO Banaue Rice Terraces with indigenous Ifugao culture).
  - **Two-Column Master-Detail Layout (7 cols / 5 cols):**
    - **Featured Showcase Card (Left):**
      - Responsive 520px card with dark vignette gradient, floating category tag, transportation method pill, rating badge, location pin, description, and dual action CTAs (`Explore Destination ➔` and direct booking link).
      - Smooth cross-fade transition on image, title, and metadata when switching destinations.
    - **Interactive Right-Hand Stack (Right):**
      - 3 interactive destination cards with hover elevation, image zoom, star badges, and active selection ring (`border-2 border-blue-600 bg-blue-50/70 shadow-md ring-2 ring-blue-500/20` and `● Viewing` badge).
  - **Quick Selector Pills:** Strip of clickable rounded pills (`Coron Island`, `White Beach`, `Waterfall Trails`, `Cultural Landscapes`) for instant one-click switching across all featured escapes.
- **Interactive Modals:**
  - **Destination Detail & Itinerary Modal (`#destination-modal`):**
    - Full-bleed hero banner with title, location, category badge, and rating.
    - Overview summary, Best Season to Visit, Recommended Stay duration, and Route Transport methods.
    - Top Highlights & Experiences checklist with blue checkmarks.
    - Sample multi-day travel itinerary.
    - Direct booking actions: `[ Book Flight Ticket ]` (deep-linked to `plane-booking.html`) and `[ Book Bus Ticket ]` (deep-linked to `bus-booking.html`).
  - **All Destinations Directory Modal (`#all-destinations-modal`):**
    - Triggered by `Explore all destinations ➔`.
    - 8 top Philippine destinations (Coron, Boracay, Siquijor, Banaue, Siargao, Bohol, Baguio, Mayon).
    - Category filter tabs (`All`, `🏝️ Beaches & Islands`, `⛰️ Highlands & Mountains`, `🌊 Waterfalls & Eco-Trails`).
    - One-click `Preview` action to set any destination active on the main page showcase and smooth-scroll to it, plus `Details ➔` to view the comprehensive itinerary guide.
  - **Global Ergonomics:** Backdrop blur dismiss, click-outside modal close, and `Escape` keyboard dismissal.

### 13. Unified Page-Wide Background Palette (`bg-gray-50` / `#f9fafb`)
- **Files:** [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html)
- **Palette Architecture:**
  - **Single Cohesive Canvas:** Harmonized background across the entire main page using the clean, soft `#f9fafb` (`bg-gray-50`) tone from the Services section (`#services`):
    - **Sticky Header (`#main-header`):** `bg-gray-50/95` with `backdrop-blur-md` and delicate border `border-gray-200/40`.
    - **Full Hero Section:** Converted from stark `bg-white` to `bg-gray-50`, seamlessly blending with the landscape stage and the organic corner cutout wrapper (`bg-gray-50`).
    - **Services Section (`#services`):** Maintained authentic `bg-gray-50` base.
    - **Popular Destinations Section (`#destinations`):** Converted from `bg-white` to `bg-gray-50` with subtle border `border-gray-200/50`.
    - **Traveler Reviews Section (`#reviews`):** Converted from multi-tone blue/sky gradient to unified `bg-gray-50` with subtle border `border-gray-200/50`.
  - **Elevated Card Contrast:** All interactive content containers (Services cards, Popular Destinations cards, Review cards, Stats bar) remain pure white (`bg-white rounded-3xl shadow-sm border border-gray-100`), ensuring sharp typographic contrast, crisp photography borders, and an uncluttered modern UI hierarchy.

### 14. Luminous Golden Boarding Pass Ticket Theme
- **Files:** [plane-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/plane-booking.html)
- **Visual Motif & Color Refinement:**
  - **Luminous Golden Gradient:** Soft champagne gold gradient (`bg-gradient-to-b from-[#fff9e6] via-[#fef3cc] to-[#fae6a3]`) providing warmth, luxury, and typographic clarity without the heavy, flat mustard look of solid saturated yellow.
  - **Border & Micro-Elevation:** Crisp golden border (`border-[#e8ce85]`) with soft diffused shadow `shadow-sm`, rounded-2xl corners, and safe interior padding preventing any text clipping.
- **Card Topology & Proportional 7-Column Layout:**
  - **Integrated Header:** Deep amber `DEPARTURE` / `RETURN` label with a blue capsule indicator dot, airline title (`#summary-airline-depart` / `#summary-airline-return`), and emerald `Direct` badge.
  - **Balanced 7-Col Route Grid:**
    - **Col 1–3 (Origin):** Left-aligned city label (`#summary-depart-city`), high-contrast airport code (`#depart-code-text`, `text-2xl font-black`), compact weekday date (`#summary-depart-date`, e.g., `Sat, Oct 15`), and departure time (`#depart-time-text`, `text-blue-700`).
    - **Col 4 (Center Flight Path):** Dashed flight trajectory line with a crisp 24px circular white center badge housing a tilted blue plane icon (`fas fa-plane text-blue-600 text-[10px] rotate-45`) with direct duration (`1h 15m`) underneath.
    - **Col 5–7 (Destination):** Right-aligned destination city (`#summary-dest-city`), airport code (`#dest-code-text`), arrival date (`#summary-arrive-date`), and arrival time (`#arrive-time-text`).
  - **Perforated Ticket Divider & Terminal Strip:** Delicate dashed divider (`border-dashed border-amber-900/15`) with clean, concise terminal tags (`Manila Terminal 3`, `Cebu Terminal 1`) featuring departure and arrival plane glyphs, bounded to `max-w-[48%]` to guarantee zero wrapping or edge collisions.
- **Integration Touchpoints:**
  1. **Sidebar Departure & Return Cards:** Live updating as the traveler configures dates and destinations.
  2. **Official Boarding Pass:** Matching 7-col golden flight card inside `#printable-boarding-pass` in the Booking Confirmed modal with vibrant golden airline header.
  3. **Checkout Review Ticket:** Luminous golden gradient timing strip in `#booking-review-modal`.

### 15. Organic Stepped S-Curve Hero Cutout & Badge Architecture
- **Files:** [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html)
- **Design Context & Origin:**
  - Implements the stepped organic contour from the master Figma design (`media_1791619354992_509223a5.png`) replacing the previous single-radius box with an authentic multi-tiered floating badge and seamless landscape cutout.
- **Mathematical Dual-Path Geometry:**
  - **Resolution & Aspect Ratio:** Scalable SVG container with `viewBox="0 0 440 170"` operating on an authentic 2.588:1 ratio across responsive breakpoints (`w-[340px] h-[131px]`, `sm:w-[380px] sm:h-[147px]`, `lg:w-[440px] lg:h-[170px]`).
  - **Uniform 14px Cutout Margin & Tangent Continuity:**
    1. **Bottom Tangent Fillet:** Starts tangentially along the hero landscape bottom line ($y = 170$) at $x = 25.5$ via a smooth concave arc (`A 28 28 0 0 0 53.01 136.79`), eliminating abrupt edge stops or visible highway pavement under the card.
    2. **Left Pill Cap:** Concentric semicircular arcs centered at $(110, 126)$. Outer cutout radius $R_o = 58$ (`A 58 58 0 0 1 110 68`), inner badge radius $R_i = 44$ (`A 44 44 0 0 1 110 82`), guaranteeing an exact 14px uniform negative-space margin around the 3 destination avatars.
    3. **Lower Tier Horizontal Edge:** Straight boundary along $y = 68$ (cutout) and $y = 82$ (badge), providing ample vertical clearance for the avatars and typography.
    4. **Stepped S-Curve Transition:** Organic cubic Bezier S-curve sweeping from lower tier to upper tier (`C 225 68, 235 14, 275 14` for outer cutout; `C 225 82, 235 28, 275 28` for inner badge), creating a relaxed, natural gradient without vertical distortion.
    5. **Tier Centering & Typography Alignment:**
       - **Upper Tier (`top-[16.5%] h-[31.8%] right-0 w-[37.5%]`):** Centers the "Know More ➔" link both vertically and horizontally within the upper wing, providing balanced padding on all sides.
       - **Lower Tier (`top-[48.2%] bottom-0 inset-x-0 pl-[18.5%]`):** Centers the 3 destination avatars (`w-10 h-10 lg:w-11 lg:h-11`) and "Awesome Places" copy vertically and horizontally within the 88px lower pill space, providing an equal 14px internal cushion from the pill arc and 23px vertical clearance above and below with zero bottom edge collision.
    6. **Rounded Corners & Clean Cutout:** Card features rounded corners ($R = 20$) into $(435, 48)$ and $(415, 170)$, while the outer `#f9fafb` cutout fills through to `(440, 170)`, ensuring no background landscape photo shows under or beside the badge.
- **Dual-Layer Rendering Model:**
  - **Layer 1 (Cutout Backdrop):** `<path d="..." fill="#f9fafb" />` carves into `#hero-bg-card` with page background `#f9fafb` (`bg-gray-50`), creating a natural negative-space pocket.
  - **Layer 2 (Inner Dynamic Badge):** `<path id="hero-cutout-path" d="..." fill="#4a6375" class="transition-colors duration-500" />` renders the dark slate card body.
- **Interactive Integration:**
  - Seamlessly hooked into `goToSlide(index)` slider controller: dynamically updates `cutoutPath.setAttribute('fill', slide.badgeBg)` with 500ms CSS transition across Slide 1 (`#4a6375`), Slide 2 (`#1e40af`), and Slide 3 (`#0d9488`).
  - Retains all semantic HTML element IDs (`#hero-cutout-path`, `#hero-cutout-card`, `#hero-badge-link`, `#hero-badge-link-text`, `#hero-badge-avatars`, `#hero-badge-title`, `#hero-badge-desc`).

### 16. Modular Asset Architecture (`css/`, `js/`, `data/`)
- **Root Directory:** [C:/Antigravity files/Mckanes Travel and Tours/](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/)
- **Architecture & Separation of Concerns:**
  - Decoupled all inline `<style>` and `<script>` blocks from HTML templates into organized subdirectories:
    - **`css/` Directory:** Dedicated stylesheets for animations, layouts, ticket prints, and UI components.
    - **`js/` Directory:** Dedicated client-side JavaScript controllers, interactive wizards, modal managers, and fare engines.
    - **`data/` Directory:** Clean JSON databases containing structured catalog data for destinations, flight schedules, and provincial bus trips.
- **Asset Manifest:**
  1. **Stylesheets (`css/`):**
     - [css/style.css](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/css/style.css): Custom keyframes (`@keyframes floatSlow`, `@keyframes vehicleBounce`, `@keyframes headlineWave`), perspective transformations, stepped S-curve styling, and scrollbar rules for [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html).
     - [css/plane-booking.css](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/css/plane-booking.css): Flight selection active states, date picker indicators, and `@media print` rules for the boarding pass in [plane-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/plane-booking.html).
     - [css/bus-booking.css](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/css/bus-booking.css): Date picker styling and responsive input definitions for [bus-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/bus-booking.html).
  2. **Scripts (`js/`):**
     - [js/main.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/main.js): Sticky header scroll elevations, 3-slide hero carousel controller (`goToSlide`), video modal controls, popular destinations showcase engine (`selectDestination`), and all-destinations directory modal.
     - [js/plane-booking.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/plane-booking.js): Airport mappings, domestic flight schedules, dynamic route filtering, seat selector matrix, passenger input generator, fare calculator, payment breakdown, and text receipt generator.
     - [js/bus-booking.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/bus-booking.js): Bus trip catalog (`TRIPS_DATA`), operator filtering, seat allocation, passenger modal, and booking confirmation generator.
  3. **Data Schemas (`data/`):**
     - [data/destinations.json](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/data/destinations.json): Structured JSON catalog of featured Philippine travel destinations with itineraries, ratings, and highlights.
     - [data/flights.json](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/data/flights.json): Domestic flight schedules and airport master data.
     - [data/bus-trips.json](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/data/bus-trips.json): Provincial bus schedules across victory liner, genesis, joybus, and partas.
- **Offline & `file:///` Protocol Resilience:**
  - JavaScript files bundle in-memory fallback datasets matching the external JSON files, ensuring 100% functionality when launched directly from Windows Explorer without triggering browser CORS cross-origin restrictions on local `fetch()`.

### 17. Curated Tour & Vacation Packages Architecture (`#packages`)
- **Files:** [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html), [js/main.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/main.js), [data/packages.json](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/data/packages.json), [css/style.css](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/css/style.css)
- **Navigation Integration:**
  - Configured navbar link `PACKAGE` to smoothly navigate to `<section id="packages">` (`scroll-mt-24`).
  - Added Vacation Packages direct anchor to footer quick links.
  - Linked from [bus-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/bus-booking.html) and [plane-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/plane-booking.html) top navigation back to `index.html#packages`.
- **Package Showcase Topology:**
  - **Header Block:** Emerald pill badge (`All-Inclusive Holiday Bundles`), bold dual-tone title (`Curated Tour & Vacation Packages`), and trust banner highlighting Best Price Guarantee, 24/7 Island Concierge, and Flexible Dates.
  - **Category Filter Tabs:** Interactive pills (`All Packages`, `🏖️ Beach & Islands`, `🌴 Island Hopping`, `🌲 Highland Escapes`, `🏄 Eco-Adventure`) with live re-rendering.
  - **Responsive 3-Column Card Matrix:**
    - High-res cover image with duration badge (`3D2N`, `4D3N`), transport mode badge (`✈️ Roundtrip Flights Included`, `🚌 Roundtrip Deluxe Bus Included`), rating pill, and promotion badge (`🔥 Best Seller`, `⭐ Top Rated`, `🌲 Highland Favorite`, `🏄 Adventure Pick`).
    - Destination location pin, package title, and resort partner subtitle.
    - Curated photography: Boracay sunset sailing (`images/boracay.jpg`), Coron limestone lagoon (`images/coron.jpg`), Banaue rice terraces (`images/banaue.jpg`), Siargao beach palm swing (`images/siargao.jpg`), Siquijor Cambugahay waterfall (`images/waterfall.jpg`), and Cebu Bohol natural wonders (`images/cebu_pacific.jpg`).
    - Curated highlights checklist with emerald checkmarks.
    - Pricing block featuring original strike-through price, discount badge (`Save 25%–29%`), prominent per-pax fare, and dual CTA buttons (`View Itinerary` and `Book Package ➔`).
  - **Custom Group Travel Banner:** Full-width gradient card (`from-blue-900 to-indigo-900`) catering to corporate retreats and custom family itineraries with inquiry link.
- **Interactive Customizer & Booking Modal (`#package-booking-modal`):**
  - **Two-Column Master-Detail Layout:**
    - **Left Column (Overview & Itinerary):** Hero image, resort details, all-inclusive inclusions grid, and day-by-day expandable timeline.
    - **Right Column (Live Fare Calculator & Booking):**
      - Travel date input with validation.
      - Interactive guest counter (Adults, Children with 30% discount).
      - Multi-tier room selector with real-time price increments.
      - Optional activity add-ons (Scuba diving, cliff diving, travel insurance).
      - Instant dynamic price recalculation.
      - Lead traveler contact form.
  - **Instant Booking Confirmation & E-Voucher:**
    - Displays official booking reference (`MCK-PKG-XXXX-XXX`).
    - Renders official printable voucher with perforated border.
    - One-click print (`window.print()`) and downloadable plain-text voucher ticket (`downloadPackageVoucher()`).

### 18. User Authentication Modal & Persistent Session Architecture (`#auth-modal`)
- **Files:** [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html) (`#nav-auth-container`, `#auth-modal`, `#auth-toast`), [js/main.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/main.js)
- **Navbar Integration:**
  - Replaced former static layout spacer (`w-32`) with dynamic `#nav-auth-container` anchored at the right margin.
  - **Unauthenticated State:** High-contrast pill button (`Sign In`) with `fas fa-user-circle` icon and `shadow-blue-600/20` micro-elevation.
  - **Authenticated State:** Compact traveler profile pill with gradient avatar (`from-blue-600 to-indigo-500`), passenger name, and dropdown arrow triggering `#user-dropdown-panel`.
- **Modal Aesthetics & Layout (`#auth-modal-card`):**
  - **Backdrop & Geometry:** 24px rounded container (`rounded-3xl max-w-md w-full`) with `bg-black/60 backdrop-blur-sm`, subtle scale-in entrance, and `Escape` keyboard dismissal.
  - **Branded Header:** Official dual-line Mckanes logo with blue globe icon and circular close button.
  - **Dual-Mode Tab Switcher:** Segmented controller switching between **Sign In** and **Create Account** views with zero layout jitter.
  - **Social Authentication Suite:** Branded single-click authentication buttons for Google (multicolor G-icon), Facebook, and Apple ID.
  - **Form Topology:**
    - Icon-prefixed input fields for Email, Password, Full Name, and Mobile Number.
    - Interactive password visibility toggle eye button (`fas fa-eye` / `fas fa-eye-slash`).
    - "Remember Me" session toggle and "Forgot Password?" recovery simulation.
- **Client Session Engine & Toast Notifications:**
  - Persists authenticated user profiles in `localStorage` under `mckanes_user` with full persistence across page refreshes.
  - Dynamic user dropdown menu featuring:
    - User account identification header (`Signed In As: Juan Dela Cruz`).
    - Direct navigational anchors to My Booked Packages, Flight Tickets, and Bus Reservations.
    - One-click `Sign Out` action restoring default navbar state.
  - Non-blocking floating toast alert (`#auth-toast`) at bottom-right with slide-in animation and 3.8s auto-fade for status feedback.

### 19. About Us Showcase, Brand Identity & Core Pillars (`#about`)
- **Files:** [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html) (`#about`), [css/style.css](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/css/style.css) (`.font-script`, `.polaroid-frame`)
- **Visual Composition & Mockup Parity:**
  - Designed to achieve 100% pixel-level parity with the user's uploaded reference mockup (`media_1792245771833_992353dd.png`, `media_1792247211317_b15c70b0.png`).
  - Positioned in the final part of the page content, situated right after traveler reviews (`#reviews`) and immediately preceding the dark footer (`#contact`) with `id="about"` and `scroll-mt-20`.
- **Top Story Block:**
  - **Atmospheric Canvas:** Soft celestial gradient transition (`bg-gradient-to-b from-blue-50/50 via-white to-[#fbf8f2]`) with subtle vector world map silhouette watermark in the upper right quadrant.
  - **Tag & Cursive Brush Typography:**
    - Uppercase category tag: `ABOUT US` in deep navy (`#1e3a5f`) with `tracking-[0.28em]`.
    - Authentic cursive signature headline: `"Mckanes Travels and Tour."` rendered via Google Font `Caveat` (weights 600 & 700) with local cursive fallback (`Segoe Print`, `Brush Script MT`).
    - Subtitle: `"Your Journey, Our Priority"` in crisp modern sans-serif bold.
    - Narrative copy articulating Mckanes' commitment to memorable, hassle-free personalized travel packages and curated tour assistance.
  - **Airplane Flight Trail Doodle:**
    - Custom inline SVG depicting a playful curved dashed loop forming an organic heart motif, ending with a small stylized airplane silhouette soaring towards the photo collage.
  - **3-Polaroid Tilted Photo Collage (`.polaroid-frame`):**
    - **Card 1 (Left / Primary Anchor):** Tilted `-rotate-3`, featuring high-definition Coron/El Nido turquoise island lagoon with banca boat (`images/about_lagoon_hd.jpg`), white polaroid border with 40px bottom caption chin, and elevation drop shadow.
    - **Card 2 (Top Right):** Tilted `rotate-[4deg]`, featuring high-definition sunset airplane wing soaring above golden cloud layers (`images/about_plane_hd.jpg`).
    - **Card 3 (Bottom Right Overlapping):** Tilted `rotate-[7deg]`, overlapping both cards, featuring a high-definition adventurer overlooking scenic mountain peaks and misty horizons (`images/about_traveler_hd.jpg`).
    - **Handwritten Script Annotation:** Slanted handwritten cursive text (`"Explore"`, `"Discover"`, `"Create Memories"`, and an outlined heart `"♡"`) positioned beside the third polaroid card.
    - **Micro-Interactions:** Hovering on any polaroid gently untwists the card (`rotate-0 scale-105 translateY(-6px)`), amplifies shadow depth, and brings it to top z-index.
- **Middle Mission / Vision / Values Strip:**
  - **Warm Ivory Background:** Set in warm ivory/cream (`bg-[#fbf8f2]`) bounded by delicate top and bottom borders (`border-[#ede6d8]`).
  - **3-Column Symmetrical Layout:**
    - **Our Mission:** Deep navy circular glyph (`w-14 h-14 bg-[#132a4a] text-white`) with target dartboard icon (`fas fa-bullseye`) and mission copy delivering safe, reliable, and affordable travel services.
    - **Our Vision:** Deep navy circular glyph with vision icon (`fas fa-eye`) detailing aspirations as the leading and most trusted travel agency known for service quality and tourism innovation.
    - **Our Values:** Deep navy circular glyph with heart icon (`fas fa-heart`) accompanied by a structured checkmark list:
      1. Customer First (`fas fa-check`)
      2. Integrity (`fas fa-check`)
      3. Reliability (`fas fa-check`)
      4. Excellence (`fas fa-check`)
      5. Passion for Travel (`fas fa-check`)
- **Bottom "Why Choose Us" Strip:**
  - **Headline & Tag:** Uppercase tag `WHY CHOOSE US` and handwritten brush script title `"More Than Just a Trip"`, paired with narrative copy explaining the company's commitment beyond simple bookings.
  - **4 Feature Pillars:** Symmetrical horizontal cards featuring white circular icon containers with subtle drop shadow and hover scaling:
    1. **Customized Travel Packages:** Slanted plane icon (`fas fa-plane -rotate-45`) + "Tours designed to fit your interests and budget."
    2. **Safe & Reliable Travel:** Shield icon (`fas fa-shield-alt`) + "Your safety and comfort are always our priority."
    3. **Expert Travel Assistance:** Team gear icon (`fas fa-users-cog`) + "From booking to on-site support, we're with you."
    4. **Affordable Rates:** Price tag icon (`fas fa-tag rotate-45`) + "Great experiences don't have to be expensive."

### 20. Comprehensive Admin Operations Portal (`admin.html`)
- **Files:** [admin.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/admin.html), [js/admin.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/admin.js), [css/admin.css](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/css/admin.css)
- **Design Philosophy & Visual Layout:**
  - Modern, responsive SaaS operations console paired with agency branding (`Mckanes Travel and Tours`).
  - Dark Slate Fixed Sidebar (`w-72 bg-slate-900 border-r border-slate-800 text-white`) providing unified navigation across Operations, Customer Relations, and Agency Controls, with mobile drawer toggle and smooth slide animations.
  - Sticky Top Control Bar (`bg-white/95 backdrop-blur-md border-b border-gray-100 shadow-xs`) featuring global search input (`Ctrl + K` / `⌘K`) with live autocomplete popover, live digital clock, instant manual booking creator CTA, interactive notification center dropdown, and direct preview links to public engines (`plane-booking.html`, `bus-booking.html`, `index.html`).
- **Dashboard Topology & Analytics:**
  - **4 Top KPI Metric Cards:**
    1. Total Bookings Gross: `₱4,829,450` (+14.8% vs last month).
    2. Total Active Bookings: `1,284` (642 Flights, 418 Buses, 224 Vacation Packages).
    3. Passengers Served: `3,890 Pax` (98.4% on-time departure rate).
    4. Traveler Satisfaction: `4.9 / 5.0` based on 1,420+ verified customer reviews.
  - **Dynamic Revenue Trajectory Chart:** Monthly bar graph (Jan–Oct 2026) visualizing seasonal tourism cycles, highlighting April summer peak and October festival surge (`₱820K`).
  - **Service Share Distribution:** Clean progress bars breaking down category volume (Domestic Flights 48%, Vacation Packages 32%, Provincial Buses 20%).
  - **Recent Transactions Feed:** Real-time table displaying recent bookings with status pills and direct modal view triggers.
- **Enterprise Bookings Management Engine (`#tab-bookings`):**
  - **Interactive 1-Click Status Popover:** Replaced blind status cycling with an intuitive dropdown popover on each booking badge allowing direct 1-click status transitions (`Confirmed`, `Pending`, `Completed`, `Cancelled`) with instant recalculations and toast feedback.
  - **Multi-Column Sorting:** Header click sorting for `Booking Ref`, `Lead Passenger`, `Travel Date`, `Total Amount`, and `Status` with dynamic ascending/descending chevron indicators.
  - **Configurable Pagination:** Page navigation controls with selectable page size (`5`, `8`, `15`, `All`), direct page number buttons, previous/next shortcuts, and record range indicator.
  - **Quick Status Filter Chips:** Real-time filter pills with live record counter badges (`All`, `Confirmed`, `Pending`, `Completed`, `Cancelled`).
  - **Bulk Action Operations Bar:** Master checkbox and individual row selectors revealing a floating bottom action pill (`N Selected`, `Mark Confirmed`, `Mark Cancelled`, `Export Selected CSV`, `Delete Selected`) with instant mass-update routines.
  - **Instant Search with Clear Button:** Filter by reference code, passenger name, email, or destination route with instantaneous `✕` clear control.
- **Multi-Tab Operational Suites:**
  - **Tab 1: Dashboard (`#tab-dashboard`):** Real-time analytics, KPIs, chart breakdowns, and rapid actions.
  - **Tab 2: Bookings Manager (`#tab-bookings`):** Master directory table with dynamic search, service filter pills, status dropdown, quick status toggle, e-ticket view modal, and CSV export.
  - **Tab 3: Tour Packages (`#tab-packages`):** Visual card matrix of 6 curated Philippine holiday bundles with capacity progress bars, active toggles, and inline price modifier.
  - **Tab 4: Fleet & Schedules (`#tab-fleet`):** Sub-tabbed dispatch tables for provincial bus lines and domestic commercial flights.
  - **Tab 5: Travelers & VIPs (`#tab-customers`):** Customer table displaying loyalty tiers (Platinum VIP, Gold, Silver), trips taken, and lifetime spend.
  - **Tab 6: Inquiries Inbox (`#tab-inquiries`):** Central feed for customer inquiries submitted via `#contact`, with interactive reply modal, status progression (`Pending` ➔ `Replied` ➔ `Resolved`), and direct mailto links.
  - **Tab 7: Promo Vouchers (`#tab-promos`):** Coupon catalog with redemption counts, min spend, expiry date, and new code generator form.
  - **Tab 8: Agency Settings (`#tab-settings`):** Official DOT accreditation credentials, bus terminal fee parameters, VAT rates, agency metadata form persistence, and local database backup/reset tools.
- **Interactive Modals & Dialogs:**
  - **E-Ticket Manifest Modal:** Formatted printable digital receipt displaying official booking reference, lead traveler, itinerary, seat numbers, fee breakdown, and print action (`@media print`).
  - **Edit Booking Modal:** Comprehensive form allowing operations staff to modify traveler names, phone, email, travel dates, seat numbers, and total fare.
  - **Manual Reservation Creator Modal:** Form for administrative booking entry (walk-ins, phone reservations).
  - **Inquiry Reply Modal:** Dedicated response modal for customer support to draft replies, copy mailto links, and auto-resolve inquiries.
- **Offline Resilience & Data Persistence:**
  - Fully offline-ready with default factory seed data and instant `localStorage` synchronization across all updates, deletions, and additions.
- **Admin Authentication Gate & Staff Security Protocol (`#admin-auth-screen`):**
  - **Full-Screen Security Barrier:** Fixed glassmorphism modal barrier (`fixed inset-0 z-[100] bg-slate-950/95 backdrop-blur-md`) blocking unauthorized inspection or access to operational records.
  - **Authorized Credentials:**
    - **User / Username:** `Mckanes@123` (case-tolerant validation)
    - **Password:** `chibiba` (trimmed, case-tolerant validation matching `chibiba` or `Chibiba`)
  - **Display State Guarantee:**
    - Enforced `#admin-auth-screen.hidden { display: none !important; visibility: hidden !important; opacity: 0 !important; pointer-events: none !important; }` in `css/admin.css`.
    - Script explicitly clears `.flex`, adds `.hidden`, and injects `style.setProperty('display', 'none', 'important')` on successful unlock.
  - **Interactive Features:**
    - Streamlined, minimalist brand header focusing directly on portal typography and operational status badge.
    - Live error feedback with shake physics (`.shake-error`) and red input border highlights on invalid submissions.
    - Password visibility toggle (`fas fa-eye` / `fas fa-eye-slash`).
    - Instant 1-Click "Apply" button in staff helper card (`autofillAdminCredentials(true)`) executing immediate credential pre-fill and console unlock.
    - Floating toast notifications elevated to `z-[120]` for clean visibility above modals and auth gates.
    - "Remember this session on this computer" checkbox utilizing local device persistence.
  - **Session Management & Console Lock:**
    - Dedicated sidebar "Lock Portal" action and top-bar lock icon clearing `mckanes_admin_logged_in` and returning to the sign-in barrier with instant feedback.
    - Cross-platform integration: Entering `Mckanes@123` / `chibiba` into the main website (`index.html`) auth modal verifies the admin, updates the user navbar badge to `Staff`, and redirects directly to `admin.html`.

### 21. Client Booking Authentication Gate & Pop-up Modal (`#auth-required-modal`)
- **Files:** [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html), [js/main.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/main.js), [js/bus-booking.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/bus-booking.js), [js/plane-booking.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/plane-booking.js)
- **Design Objective:** Ensure travelers cannot complete bookings or enter ticketing engines unauthenticated without seeing a clear, friendly, and branded reminder prompt.
- **Visual Modal Topology (`#auth-required-modal`):**
  - Ambient dark overlay backdrop (`bg-black/70 backdrop-blur-sm fixed inset-0 z-50`).
  - Rounded white card container (`rounded-3xl max-w-md shadow-2xl border border-gray-100 scale-95 -> scale-100 transition`).
  - Amber padlock icon badge (`bg-amber-50 text-amber-600 border border-amber-200`) with uppercase "Account Verification" header.
  - Contextual banner highlighting the user's intended booking action (e.g. *Flight Reservation Requires Sign In*, *Bus Ticket Booking Requires Sign In*, or *Vacation Package Requires Sign In*).
  - 3 traveler value propositions:
    1. Instant digital E-Ticket & Boarding Pass delivery.
    2. Real-time SMS & email trip schedule alerts.
    3. Official PNR reservation code saved directly to traveler profile.
  - Primary CTA: **"Sign In to Continue Booking"** (`bg-blue-600 hover:bg-blue-700 text-white font-extrabold`).
  - Secondary CTA: **"Create New Traveler Account"** (`border border-gray-200 hover:bg-gray-50 text-gray-700`).
  - Footer actions: Staff login deep link and "Cancel & Browse More" dismissal.
- **Workflow & Interception Points:**
  - **Service Cards (Homepage):** Clicking "Book A Plane Ticket" or "Book A Bus Ticket" without an active session triggers the modal rather than navigating away unauthenticated.
  - **Vacation Packages:** Clicking "Book Package ➔" or switching to the booking tab in the package modal intercepts unauthenticated guests.
  - **Continuation Memory:** Remembers the client's destination (`pendingBookingRedirect`). As soon as sign-in or registration succeeds, automatically navigates the client straight to their selected engine or package checkout.
  - **Standalone Engine Safety:** Directly accessing `bus-booking.html` or `plane-booking.html` checks session upon checkout submission, preventing orphan or unverified ticket issues.

### 22. Client-Admin Real-Time Synchronization & Customer Directory Suite (`#tab-customers`, `#view-customer-modal`, `#customer-form-modal`)
- **Files:** [admin.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/admin.html), [js/admin.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/admin.js), [js/main.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/main.js), [js/plane-booking.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/plane-booking.js), [js/bus-booking.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/bus-booking.js)
- **Design Objective:** Provide real-time visibility into customer account activations, sign-in activity, and reservation manifests within the Admin Operations Portal, alongside full CRM inspection, filtering, editing, and export capabilities.
- **Visual & Component Topology (`#tab-customers`):**
  - **Live Metrics Cards Grid:** 4-column metric row:
    1. *Total Registered Clients:* Aggregate count of active client accounts (`#cust-stat-total`).
    2. *Online / Active Now:* Real-time count of currently active sessions with a pulsating green radar ping (`#cust-stat-online`, `.animate-ping`).
    3. *VIP Loyalty Members:* Count of Platinum and Gold VIP tier accounts (`#cust-stat-vip`).
    4. *Total Lifetime Spend:* Aggregate revenue generated by registered clients (`#cust-stat-spend`).
  - **Search & Filter Command Bar:**
    - Live search input querying client ID, full name, email, phone number, and city.
    - Tier filter dropdown (`All Tiers`, `Platinum VIP`, `Gold VIP`, `Silver`, `Bronze`).
    - Status filter dropdown (`All Statuses`, `Online / Active`, `Active`, `Standard`).
    - Sort selector (`Recently Active`, `Highest Lifetime Spend`, `Most Trips Booked`, `Client Name A-Z`).
    - One-click "Reset" filter action.
    - Primary actions: "Export Directory CSV" and "Register New Client" CTA button.
  - **Directory Data Table:** 8 structured columns:
    - *Client ID:* Monospace badge format (`CUST-001`, `CUST-002`).
    - *Traveler Profile:* Circular avatar with gradient initials (`from-blue-600 to-indigo-600`), traveler name, and online beacon indicator.
    - *Contact Details:* Formatted email address and direct phone contact.
    - *Loyalty Tier:* Color-coded pill badges (`Platinum VIP` purple/indigo, `Gold VIP` amber, `Silver` slate, `Bronze` stone).
    - *Trips Completed:* Bold numeric trip counter with calendar icon.
    - *Total Lifetime Spend:* Formatted Philippine Peso (`₱XX,XXX`) lifetime billing sum.
    - *Last Active:* Humanized relative timestamp (e.g. `Online Now`, `5m ago`, `2h ago`).
    - *Manage Actions:* Interactive action buttons:
      - 👁️ **View:** Inspect full client dossier, trip manifest, and CRM notes.
      - ✏️ **Edit:** Modify client details, loyalty tier, or contact info.
      - 🗑️ **Delete:** Safely remove client record with confirmation safeguard.
- **Client Profile Dossier Modal (`#view-customer-modal`):**
  - Ambient backdrop overlay (`bg-black/60 backdrop-blur-sm z-50`).
  - Gradient header with traveler name, initials avatar, email, phone, location, and live status badge.
  - Quick action: Direct `mailto:` email button.
  - 3 Lifetime Metric stat tiles: *Trips Completed*, *Total Spend (₱)*, and *Sign-In Sessions*.
  - *Booking History Manifest:* Dynamically aggregates all confirmed flight, bus, and vacation package reservations linked to the client's email/name from `mckanes_admin_bookings`.
  - *Admin CRM Operational Notes:* Editable textarea for confidential notes, VIP preferences, and operational reminders with instant persistence.
- **Customer Form Modal (`#customer-form-modal`):**
  - Dynamic dual-mode modal (Register New Client / Edit Traveler Profile).
  - Validated fields: Full Name, Email Address, Contact Phone, City/Location, Loyalty Tier, Account Status, Trips Completed, Total Spend, and Internal Notes.
  - Form validation with instant feedback toasts.
- **Cross-Tab Real-Time Sync Architecture:**
  - Employs HTML5 `storage` events (`window.addEventListener('storage', ...)`).
  - Any client signing in, registering, or booking across any browser tab instantaneously updates the Admin Portal's tables, metric counters, and operational notifications without requiring a page reload.

### 23. Mock Accounts Purge & Chibiba Admin Persistence
- **Files:** [admin.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/admin.html), [js/admin.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/admin.js), [js/main.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/main.js)
- **Objective:** Eliminate all mock/placeholder customer profiles (`Juan Dela Cruz`, `Maria Santos`, `Roberto Lim`, `Dr. Angela Reyes`, `Joshua Mendoza`, `Patricia Gomez`, `Kenneth Bautista`) while preserving and elevating the primary staff administrator account (`Mckanes@123` / `chibiba`).
- **Admin Identity & Credentials:**
  - *Primary Staff User:* `Mckanes@123` (or `chibiba`)
  - *Password:* `chibiba`
  - *Display Name:* `Mckanes Admin (Chibiba)` (`#admin-user-display-name`)
  - *Display Role:* `Mckanes@123 (Operations Director)` (`#admin-user-display-role`)
  - *Avatar Badge:* Gradient `CH` initials avatar
- **Customer Directory State:**
  - Retains exclusively the authorized `ADMIN-01` profile (`Mckanes Admin (Chibiba)`) in `DEFAULT_CUSTOMERS`.
  - Self-healing purge mechanism automatically removes legacy mock accounts from browser `localStorage` on boot.
  - Leaves the customer table ready for live traveler sign-ins and reservations without mock clutter.

### 24. Streamlined Authentication Modal (Social Accounts Removal)
- **Files:** [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html), [js/main.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/main.js)
- **Design Objective:** Present a clean, distraction-free authentication experience by removing third-party demo social logins ("Continue with Google", "Facebook", "Apple ID") and the "or email" separator.
- **Visual Modal Topology (`#modal-auth`):**
  - Ambient backdrop with smooth entrance scaling (`max-w-md bg-white rounded-3xl shadow-2xl`).
  - Streamlined header with agency typography and close control.
  - Dual Tab Switcher (`Sign In` vs `Create Account`).
  - Direct form presentation: The sign-in and registration forms render immediately below the tab switcher with no external social buttons cluttering the view.

### 25. Complete Bookings Purge, Dynamic Dashboard & Client Accounts Management Suite
- **Files:** [admin.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/admin.html), [js/admin.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/admin.js), [js/main.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/main.js)
- **Design Objective:** Provide a completely clean operational environment in the Admin Operations Portal where mock bookings and inquiries are purged, live dashboard KPIs calculate exclusively from authentic client activity, and the administrator possesses comprehensive management capabilities over client accounts, passwords, and session statuses.
- **Visual & Component Topology:**
  - **Clean Slate Bookings Directory (`#tab-bookings`):**
    - `DEFAULT_BOOKINGS` emptied (`[]`). All 12 legacy mock bookings (`MCK-FL-2891`, `MCK-BUS-8492`, etc.) purged from memory and browser `localStorage`.
    - Automated startup purge filter cleans out any legacy mock booking seeds from browser storage upon load.
    - Zero-state placeholder displays informative message when no bookings have been placed yet.
  - **Clean Slate Inquiries Directory (`#tab-inquiries`):**
    - `DEFAULT_INQUIRIES` emptied (`[]`). All 4 legacy mock inquiries purged from memory and browser storage.
  - **Dynamic Real-Time Dashboard Overview (`#tab-dashboard`):**
    - Removed arbitrary artificial metric baselines (`+ 4250000` revenue, `+ 1272` bookings, `+ 3820` pax).
    - KPIs dynamically aggregate confirmed and completed bookings directly from `mckanes_admin_bookings`.
    - Recent bookings feed displays authentic live transactions with a dedicated zero-state empty container when no bookings exist.
  - **Central Client Accounts Repository (`mckanes_registered_accounts`):**
    - Public website registration on [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html) stores client credentials (name, email, phone, password, address, loyalty tier) and synchronizes to `mckanes_admin_customers`.
    - Client authentication verifies supplied credentials against `mckanes_registered_accounts`. Rejects incorrect passwords and non-existent emails with actionable error toasts.
    - Preserves primary staff bypass for `Mckanes@123` / `chibiba` with password `chibiba`.
    - Client sign-out marks session status to `Offline` across both account repositories.
  - **Full Admin Customer & Account Management (`#tab-customers`):**
    - **Password Inspection & Editing:** `#view-customer-modal` displays the client's registered account password in a secure monospace token (`#view-cust-password`).
    - **Profile & Password Modification:** `#customer-form-modal` includes an Account Password input (`#cust-form-password`) allowing staff to update or reset client passwords, and an expanded status dropdown (`Online`, `Offline`, `Active`, `Standard`, `Suspended`).
    - **Live Status Filtering:** `#cust-status-filter` supports filtering by `All Statuses`, `Online Now`, `Offline`, `Active`, `Standard`, and `Suspended`.
    - **Directory & Account Removal:** Deleting a customer removes both their customer profile in `mckanes_admin_customers` and their authentication credentials in `mckanes_registered_accounts`, automatically terminating any active session.



### 26. Bookings Master Directory Zero-State, Mock Heuristic Purge & Filter Toggle Architecture
- **Files:** [admin.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/admin.html), [js/admin.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/admin.js), [js/main.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/main.js)
- **Design Objective:** Eliminate any residual mock bookings in local browser storage, initialize static HTML counters to pure zero baselines, make filter chips interactive and toggleable, and furnish administrators with an immediate 1-click test data purging tool.
- **Visual & Component Topology:**
  - **Zero-Base Initial Counter Chips:**
    - Static HTML filter buttons in `#tab-bookings` are initialized to zero count badges (`All Bookings (0)`, `Confirmed (0)`, `Pending (0)`, `Completed (0)`, `Cancelled (0)`), eliminating flashing of legacy test counts (`12, 8, 2, 1, 1`) prior to hydration.
    - Record counters initialize cleanly to `0 Records` and `Showing 0 reservations`.
  - **Toggleable Status Filter Chips:**
    - `filterBookings(type, val)` evaluates whether the selected status filter chip is already active. If active, clicking it again resets the filter to `'all'`, providing natural toggle interactivity.
  - **Multi-Vector Residual Mock Purge Engine:**
    - `isMockBooking(booking)` evaluates booking reference ID against 22 known legacy mock codes (`MCK-FL-2891` through `MCK-BUS-8519`), customer email against 23 legacy mock email patterns, and customer name against 20 known mock names.
    - Self-healing purge runs on `DOMContentLoaded` and `getBookings()` across `admin.js` and `main.js`, stripping any legacy records that were modified (e.g. set to 'Cancelled') from `localStorage`.
  - **Administrator 1-Click Clear Data Button:**
    - Positioned adjacent to "Export CSV" and "+ New Booking" in the toolbar as `#btn-clear-bookings`.
    - Invokes `clearAllTestBookings()`, which prompts for confirmation, cleanses `mckanes_admin_bookings`, resets active filters, and updates all counters and metrics immediately.
  - **Dynamic Contextual Empty States:**
    - If total bookings are 0, renders a friendly zero-state illustration encouraging staff to place their first reservation via `+ Create First Booking`.
    - If active filters yield 0 results, renders a clear filter mismatch illustration with a `Reset All Filters` button.


### 27. Dedicated Client Authentication UI & Clean Design Topology
- **Files:** [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html), [js/main.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/main.js)
- **Design Objective:** Provide an immaculate, professional customer login modal on the public website that exclusively displays client-relevant inputs (`Email Address` and `Password`) without leaking administrative usernames or internal test hints.
- **Visual & Component Topology:**
  - **Email Address Field:** Labeled `Email Address`, featuring an envelope icon (`fas fa-envelope`), placeholder `you@example.com`, `inputmode="email"`, and `autocomplete="email"`.
  - **Password Field:** Labeled `Password`, featuring standard placeholder `Enter your password`, toggleable visibility eye icon, and `autocomplete="current-password"`.
  - **Portal Navigation:** Clean transition link `Admin Portal Sign In →` routing authorized personnel to `admin.html` without presenting administrative credentials in plain sight.


### 28. Real-Time Client Presence Heartbeat & Cross-Window Synchronization Topology
- **Files:** [admin.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/admin.html), [js/admin.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/admin.js), [js/main.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/main.js)
- **Design Objective:** Provide immediate, high-fidelity online presence detection across client and admin interfaces using local event streams and heartbeat mechanisms without requiring external server dependencies.
- **Visual & Component Topology:**
  - **Live Sync Badge:** The Traveler Customer Directory features a prominent `Live Sync Active` pill in the header, visually indicating active cross-window event monitoring.
  - **Online Status Indicator:** The `ONLINE / ACTIVE NOW` metric card aggregates all profiles currently identified as active by `isCustomerOnline()`. Individual rows render a radiant emerald pulse badge (`● Active`) next to traveler names.
  - **Presence Pulse Heartbeat:** `initClientPresenceHeartbeat()` sends regular 45-second pings and interaction-triggered signals to browser storage, guaranteeing accurate real-time metrics across open tabs and windows.


### 29. Public Gateway Client Privacy & Admin Interface Isolation
- **Files:** [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html), [plane-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/plane-booking.html), [bus-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/bus-booking.html)
- **Design Objective:** Establish total separation of concerns between public customer touchpoints and internal operations portals, removing any visual breadcrumbs leading to administrative tools.
- **Visual & Component Topology:**
  - **Clean Sign-In Card:** The customer authentication modal strictly contains Sign In / Create Account forms with no bottom administrative shortcuts.
  - **Uncluttered Navigation:** Flight and bus booking navigation headers exclusively feature branding and "Back to Home".
  - **Pure Consumer Footer:** Footer navigation contains exclusively customer-facing service and destination links.


### 30. Customer Profile Dropdown Topology & Role Separation
- **Files:** [js/main.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/main.js)
- **Design Objective:** Ensure registered travelers have a clean, consumer-appropriate account menu without access to administrative tools or confusing staff designations.
- **Visual & Component Topology:**
  - **Traveler Profile Button:** Displays traveler's initials and first name in standard neutral typography with a gentle blue-indigo avatar.
  - **Account Dropdown Panel:**
    - User Identity Header: Displays customer full name and email in standard text.
    - Consumer Navigation Links: Links directly to booking modules (`Vacation Packages`, `Flight Tickets`, `Bus Tickets`).
    - Session Control: Direct `Sign Out` button with red accent.


### 31. Dynamic Boarding Pass & Route Synchronization Architecture
- **Files:** [plane-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/plane-booking.html), [js/plane-booking.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/plane-booking.js)
- **Design Objective:** Eliminate hardcoded airport code discrepancies between route selectors and flight summary tickets by binding atomic state updates to both departure and return boarding cards.
- **Visual & Component Topology:**
  - **Departure Flight Card:** Displays origin airport code in bold 24px typography (`#depart-code-text`), city title (`#summary-depart-city`), destination code (`#dest-code-text`), and destination city (`#summary-dest-city`).
  - **Return Flight Card:** Displays inverse destination code (`#return-depart-code-text`) routing back to origin code (`#return-dest-code-text`).
  - **Terminal Strip:** Displays dynamic terminal designations (`${city} ${terminal}`) for both outbound and inbound legs.


### 32. Custom Modal Dialog Architecture (Zero Native Browser Popups)
- **Files:** [admin.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/admin.html), [js/admin.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/admin.js), [plane-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/plane-booking.html), [js/plane-booking.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/plane-booking.js), [bus-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/bus-booking.html), [js/bus-booking.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/bus-booking.js)
- **Design Objective:** Replace unstyled, browser-native popup dialogues (`confirm()`, `alert()`, `prompt()`) with integrated, theme-consistent Tailwind dialog cards featuring smooth backdrop blur, entry animations, context-sensitive icon badges, and keyboard shortcuts.
- **Visual & Component Topology:**
  - **Backdrop & Layering:** Deep semi-transparent overlay (`fixed inset-0 z-[115] bg-slate-950/70 backdrop-blur-xs`) establishing strict visual hierarchy over all dashboards and forms.
  - **Dialog Card Anatomy (`#admin-confirm-box`, `#plane-notice-box`, `#bus-notice-box`):**
    - Geometry: `rounded-3xl max-w-md w-full overflow-hidden shadow-2xl border border-gray-100`.
    - Animation: Entry transition from `scale-95 opacity-0` to `scale-100 opacity-100` in 200ms with spring physics.
    - Status Badge: Central 64x64px soft badge (`w-16 h-16 rounded-2xl border text-2xl shadow-xs`) color-coded per action type (Rose for Lock/Delete/Purge, Amber for Warning, Blue for Informational/Rates).
    - Typography: 18px font-black title (`text-gray-900`) and 12px relaxed message (`text-gray-600 leading-relaxed`).
    - Inline Prompt Input Container: Hidden by default, toggled on for interactive value updates (e.g. package rate editing) with focus rings (`focus:ring-2 focus:ring-blue-100`).
    - Action Footer: Clean border-separated bottom strip with secondary button (neutral gray border) and primary action button (vibrant filled button with soft shadow).
  - **Accessibility & Interaction:**
    - `Escape` key dismisses modal and resolves promise with `false` or `null`.
    - `Enter` key confirms current dialog action.
    - Clicking the backdrop dismisses the dialog safely.


### 33. Date Picker Component Topology & Interactive State Design
- **Files:** [plane-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/plane-booking.html), [js/plane-booking.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/plane-booking.js)
- **Design Objective:** Create a high-conversion date selection card matching premier airline portals (Cebu Pacific, Singapore Airlines), resolving invisible layer input issues and redundant iconography.
- **Visual & Component Topology:**
  - **Outer Card Wrapper (`#depart-date-container`, `#return-date-container`):**
    - Geometry: `border border-gray-200 rounded-xl p-3 relative cursor-pointer group bg-white`.
    - Hover / Active Micro-Interactions: `hover:border-blue-400 hover:bg-blue-50/20 active:scale-[0.99] transition`.
  - **Information Hierarchy:**
    - Label Header: `text-[10px] font-bold text-gray-400 uppercase tracking-wider block mb-1`.
    - Left Lead Icon: `far fa-calendar-alt text-blue-600 text-sm group-hover:scale-110 transition-transform`.
    - Main Date String: `text-xs sm:text-sm font-bold text-gray-900 block leading-tight` (e.g. `Oct 15, 2026`).
    - Subtitle Day-of-Week: `text-[10px] text-gray-500 font-medium block leading-tight mt-0.5` (e.g. `Thursday`).
    - Right Trailing Indicator: Clean chevron dropdown indicator (`fas fa-chevron-down text-gray-400 text-[10px] group-hover:text-blue-500 transition-colors`) creating visual parity with Origin and Destination dropdown cards.
  - **One-Way Inactive State:**
    - Card opacity dimmed (`opacity-50 bg-gray-50/60`), main label rendered as "No Return Flight", and subtitle as "One-way trip (Click to add return)" for zero user ambiguity.


### 34. Destination Scenic Photography & Dynamic Visual Architecture
- **Files:** [plane-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/plane-booking.html), [js/plane-booking.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/plane-booking.js), [bus-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/bus-booking.html), [js/bus-booking.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/bus-booking.js)
- **Visual Design Objectives:**
  - Eliminate mismatched, generic imagery (e.g. limestone karsts when Cebu is selected) in favor of authentic, destination-specific landscape photography.
  - Deliver dynamic, instant visual feedback in the Trip Summary sidebar when travelers modify flight or bus locations.
- **Component Anatomy & Visual Tokens:**
  - **Flight Destination Banner Card (`#summary-dest-img` container):**
    - Geometry: `relative h-28 w-full overflow-hidden bg-slate-800 rounded-t-xl`.
    - Image Layer: `w-full h-full object-cover group-hover:scale-105 transition-all duration-500`.
    - Destination Tag Pill (`#summary-dest-tag`): Floating top-left pill (`absolute top-2.5 left-2.5 bg-black/60 backdrop-blur-md text-white text-[10px] font-bold px-2.5 py-0.5 rounded-full border border-white/20 flex items-center gap-1 shadow-sm`) with a vibrant amber map pin (`fas fa-map-marker-alt text-amber-400 text-[9px]`) identifying the destination locality.
    - Trip Type Pill (`#summary-trip-pill`): Floating bottom-right pill (`absolute bottom-2.5 right-2.5 bg-white text-blue-600 font-extrabold text-[10px] px-3 py-1 rounded-full shadow-md`).
    - Lower Route Bar: Navy overlay (`bg-[#112437] p-3 text-white`) showcasing route arrow and trip itinerary metadata.
  - **Local High-Resolution Asset Catalog (`images/`):**
    - `cebu.jpg`: Bantayan Island white beach and crystal waters for Cebu (`CEB`).
    - `boracay.jpg`: Iconic sunset paraw sailing along White Beach for Boracay (`MPH`).
    - `siargao.jpg`: Surfing shoreline, coral reef, and palm swing for Siargao (`IAO`).
    - `coron.jpg`: Towering limestone karsts and emerald lagoons for Palawan (`PPS`).
    - `davao.jpg`: Sweeping golden sands and crashing surf of Dahican for Davao (`DVO`).
    - `manila.jpg`: Golden harbor sunset over Manila Bay for Manila (`MNL`).
    - `iloilo.jpg`: Islas de Gigantes rock formations and turquoise waters for Iloilo (`ILO`).
    - `baguio.jpg`: Mountain pine landscape for Baguio City bus trips.
    - `vigan.jpg`: Historic Calle Crisologo cobblestones for Vigan bus trips.
    - `la_union.jpg`: Famous San Juan surf shoreline for La Union bus trips.
    - `batangas.jpg`: Matuod beach sunset for Batangas bus trips.


### 35. Luxury Executive Lock Screen Topology & Component Architecture
- **Files:** [admin.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/admin.html), [js/admin.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/admin.js), [css/admin.css](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/css/admin.css)
- **Design Philosophy:** Transform the admin login gate from an isolated flat slate box into a high-security executive flight operations control room with luxury glassmorphism, depth, and enterprise tactile cues.
- **Visual & Component Topology:**
  - **Atmospheric Environment Layering:**
    - Background stage: Atmospheric blurred Philippine landscape (`images/hero_bg.jpg`) veiled in deep navy/slate vignettes (`from-[#050914] via-[#091122]/95 to-[#060b18]`).
    - Matrix overlay: Delicate 28px dot matrix (`bg-[radial-gradient(#60a5fa_1px,transparent_1px)]`).
    - Luminous glow orbs: 500px multi-directional diffuse gradient orbs (`bg-blue-600/25`, `bg-indigo-600/20`, `bg-sky-500/10`) establishing ambient depth.
  - **Frosted Glassmorphism Console Card (`#admin-login-card`):**
    - Outer envelope: `max-w-[460px] bg-slate-900/85 backdrop-blur-2xl border border-white/10 rounded-3xl overflow-hidden shadow-[0_25px_60px_-15px_rgba(0,0,0,0.85),0_0_50px_rgba(37,99,235,0.2)]`.
    - Top edge beacon: 1px luminous horizontal light beam (`h-1 bg-gradient-to-r from-transparent via-blue-500 to-transparent`).
  - **Emblem & Status Pill:**
    - Shield badge: 64x64px rounded-2xl gradient shield with soft blur halo, inner border, and mini amber padlock indicator.
    - Status pill: Dark capsule (`bg-slate-800/90 border border-slate-700/80`) with live pulsing amber radar dot (`status-pulse`).
  - **Executive Staff Keycard Module:**
    - Replaces raw debug credentials with a tactile executive badge:
      - `CH` golden initials avatar for Chibiba with `Director` status pill.
      - Masked credential placeholder (`Mckanes@123 • ••••••••`).
      - Lightning quick-action CTA (`[ ⚡ 1-Click Unlock ]`) triggering instant credential injection and seamless portal unlocking.
    - Security footer: Cryptographic assurance badge (`TLS 1.3 • 256-Bit`) alongside high-contrast return link to public site.


### 36. Vacation Package Destination Photography & Visual Cohesion Topology
- **Files:** [data/packages.json](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/data/packages.json), [js/main.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/main.js), [js/admin.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/admin.js), [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html)
- **Visual Design Architecture:**
  - **Thematic Visual Harmony:** Align vacation package cards with scenic leisure destinations rather than transit vehicles. The "Cebu & Bohol Twin Island Wonder Vacation" card displays a sun-drenched tropical seascape (`images/cebu_bohol.jpg`) highlighting turquoise shallows, an overwater boardwalk, and traditional banca boats.
  - **Transit vs Package Semantic Separation:**
    - Services Section: Card 2 explicitly represents flight booking and utilizes `images/cebu_plane.jpg` centered with `object-position: center 55%` for clear airline recognition.
    - Packages Section: Package card showcases destination beauty (`images/cebu_bohol.jpg`) with duration badges, price tags, and attraction highlights.
  - **Asset Topology (`images/`):**
    - `cebu_bohol.jpg` (451 KB): Scenic tropical boardwalk and banca boat photograph.
    - `cebu_pacific.jpg` (451 KB): Mirrored asset for backward-compatible client cache resolution.
    - `cebu_plane.jpg` (141 KB): Preserved commercial airliner visual for flight booking service card.


### 37. Flight Operations Radar & Command Center Lock Screen Background Architecture
- **Files:** [admin.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/admin.html), [js/admin.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/admin.js), [css/admin.css](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/css/admin.css)
- **Visual Design Philosophy:** Elevate the lock screen from an isolated dark card into a comprehensive, high-security executive flight operations control room with atmospheric depth, live telemetry, and aviation graphics.
- **Component & Layer Topology:**
  - **Layer 0 (Solid Anti-Bleed Base):** `#admin-auth-screen` styled with `bg-[#030712]` providing absolute opacity and zero dashboard bleed.
  - **Layer 1 (Cinematic Horizon):** `images/about_plane_hd.jpg` at `opacity-40 mix-blend-luminosity brightness-90 contrast-125` bathed in dark midnight gradients.
  - **Layer 2 (Flight Radar Vectors):** Fullscreen SVG with rotating radar sweep line (`.radar-sweep-beam`), gradient flight arcs (`.flight-path-pulse`), airport waypoints (`MNL`, `CEB`, `DVO`, `MPH`, `PPS`), and an active aircraft beacon.
  - **Layer 3 (Ambient Light Orbs):** Quad-point multi-spectrum gradient orbs (amber-500/12, blue-600/20, indigo-600/25, sky-500/12) creating vibrant backlight depth.
  - **Layer 4 (Telemetry HUD Chrome):** Top operational control bar with Mckanes Global Operations title, active radar status, gateway coordinates (`14.5086° N, 121.0194° E`), and live ticking PST clock (`#admin-lock-clock`). Bottom dispatch status ticker with encryption and audit notices.
  - **Layer 5 (Operations Console Card):** Central frosted glassmorphism card (`#admin-login-card`) floating seamlessly with deep drop shadows.


### 38. Admin Portal Secure Gate Typography & Footer Simplification
- **Files:** [admin.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/admin.html)
- **Design Decisions:**
  - **Eradication of Visual Debug Shortcuts:** Removed the bottom credential helper badge and 1-Click Unlock button.
  - **Compact Luxury Proportions:** Reducing card height by removing the credential helper allows the central frosted glass card to sit comfortably within any viewport without requiring vertical scrolling.
  - **Minimalist Security Footer:** Preserved the TLS 1.3 encryption indicator in a sleek, semi-transparent obsidian basebar.


### 39. Standalone Admin Operations Security Portal & Perimeter Containment
- **Files:** [admin.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/admin.html)
- **Visual Design Decisions:**
  - **Elimination of Public Website Anchor:** Removed the `Return to Public Website` hyperlink from the locked portal footer to present a unified, enterprise-grade authentication screen with no public consumer escape paths.
  - **Centered Cryptographic Compliance Pill:** Re-centered the security badge (`Authorized Personnel Only • TLS 1.3 • 256-Bit Encrypted Gate`) at the bottom of the card with micro-shield iconography and subdued slate typography.
  - **Closed Navigation Loop:** Formatted all internal header branding to link strictly within the admin management portal (`admin.html`).


### 40. Vacation Package Real-Time Admin Synchronization & Dynamic Client Reflection Architecture
- **Files:** [admin.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/admin.html), [js/admin.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/admin.js), [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html), [js/main.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/main.js)
- **Visual & Component Topology:**
  - **Admin Package Edit Suite (`#package-edit-modal`):**
    - High-elevation glassmorphism overlay (`bg-slate-900/60 backdrop-blur-xs z-50`).
    - Obsidian dark header with tropical palm iconography (`fa-umbrella-beach text-blue-400`), modal title, subtitle notice, and smooth close trigger.
    - Two-tier price control panel highlighted in soft cobalt (`bg-blue-50/70 border-blue-100/80`) featuring prominent Philippine Peso currency indicators (`₱`), client-facing rate inputs, and original strike-through fields.
    - Operational status dropdown with clear state options (`Active (Open for Clients)` vs `Paused (Seasonal Pause / Full)`).
    - Capacity and booked slots numeric steppers.
    - High-contrast primary submission button: `Save & Reflect on Main Page`.
  - **Client Package Card Dynamics (`#packages-cards-grid`):**
    - *Live Price Display:* Dynamically formats client rates with `toLocaleString()` (`₱X,XXX / person`).
    - *Original Strikethrough & Auto-Calculated Savings:* Renders the strike-through original rate with green discount pill (`Save X%`) auto-computed from `((originalPrice - basePrice) / originalPrice) * 100`.
    - *Seasonal Hold State:* When paused by administration, replaces the top badge with an amber `⏸ Temporarily Paused` indicator and substitutes the booking button with an amber `Paused` status button.
  - **Real-Time Storage Event Bus:**
    - Leverages HTML5 `window.addEventListener('storage', ...)` and custom `packageDataUpdated` events.
    - Updates across separate tabs or windows instantly without triggering full page reloads or layout jumps.


### 41. Flight Booking Passenger Information Card Visual Simplification & Sticky Summary Priority
- **Files:** [plane-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/plane-booking.html), [js/plane-booking.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/plane-booking.js)
- **Visual Design Decisions:**
  - **Elimination of Duplicate Lower Navigation Strip:**
    - Removed the footer bar (`.mt-6.pt-4.border-t`) at the bottom of the passenger details card which previously housed `< Back to Flight Details` and a secondary `Continue to Review ->` button.
  - **Single Strong Call to Action:**
    - By concentrating the primary forward progression on the sticky right sidebar (`Your Trip Summary`), visual hierarchy is preserved. The traveler reviews their selected flights, seat selections, and live fare breakdown before naturally triggering review confirmation.
  - **Balanced Asymmetric Grid Spacing:**
    - The left-hand 7-column passenger card now aligns naturally with the sticky 5-column summary card without trailing action bars, creating clean visual margins and preventing card bottom heaviness.

### 42. Admin Live Booking Alert Banner, Synthesized Chime, & Dynamic Transaction Highlighting
- **Files:** [admin.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/admin.html), [js/admin.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/admin.js), [plane-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/plane-booking.html), [js/plane-booking.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/plane-booking.js), [bus-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/bus-booking.html), [js/bus-booking.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/bus-booking.js)
- **Visual & Auditory Architecture:**
  - **Top-Right Real-Time Booking Alert Banner (`#admin-live-booking-alert`):**
    - High-elevation floating toast card (`fixed top-6 right-6 z-[130]`) with luxury frosted obsidian finish (`bg-gradient-to-r from-slate-950 via-slate-900 to-slate-950 backdrop-blur-md`).
    - Luminous emerald border with glow shadow (`border-2 border-emerald-500/50 shadow-emerald-500/20 shadow-xl`).
    - Live radar ping beacon (`w-2 h-2 rounded-full bg-emerald-400 animate-ping`).
    - High-contrast typography: Bold white customer identity, slate-300 route/service description, and bold emerald fare pill.
    - Interactive "View Details →" button opening complete transaction modal, and manual dismiss "✕".
  - **Zero-Dependency Synthesized Audio Chime (`playBookingChime()`):**
    - Generates a pristine ascending two-tone acoustic chime (D5: 587Hz to A5: 880Hz) via the native Web Audio API (`window.AudioContext`), operating with 0kB disk overhead and 0 external network requests.
  - **Recent Booking Transactions Highlighting (`#dashboard-recent-tbody`):**
    - Newly placed booking rows automatically receive an animated emerald gradient highlight (`bg-gradient-to-r from-emerald-50/70 via-teal-50/30 to-transparent`) and a bold left indicator stripe (`border-l-4 border-l-emerald-500`).
    - Glowing badge: `<span class="bg-emerald-500 text-white font-black text-[9px] px-1.5 py-0.5 rounded uppercase tracking-wider"><i class="fas fa-sparkles text-[7px]"></i> New</span>`.
  - **Traveler Profile Dynamic Data Binding:**
    - Replaced all legacy placeholder names and emails with automatic session binding (`getSignedInTraveler()`), ensuring booking manifests and digital tickets show authentic traveler names, emails, and phone numbers.

### 43. Executive E-Ticket Manifest Modal Architecture & Viewability Design
- **Files:** [admin.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/admin.html), [js/admin.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/admin.js)
- **Visual & Structural System:**
  - **Modal Shell & Dimensional Hierarchy:**
    - Container class: `max-w-3xl w-full max-h-[92vh] flex flex-col bg-white rounded-3xl overflow-hidden shadow-2xl border border-slate-700/30`.
    - Modal Header: Obsidian navy bar (`bg-slate-900 text-white p-5 sm:p-6 border-b border-slate-800 flex flex-col sm:flex-row justify-between items-start sm:items-center gap-4 flex-shrink-0`).
    - Decoupled Controls: Custom status selector with chevron badge and dedicated circular close button (`w-9 h-9 rounded-xl bg-slate-800/80 hover:bg-rose-500/20 text-slate-400 hover:text-rose-300`).
  - **Lead Traveler Card (`#modal-booking-customer`):**
    - High-contrast card with blue gradient initials avatar (`bg-gradient-to-tr from-blue-600 to-indigo-600 w-12 h-12 rounded-2xl text-white font-black`).
    - Integrated metadata pills: `Lead Traveler` chip (`text-[10px] font-extrabold text-blue-700 bg-blue-100/80 px-2 py-0.5 rounded-md`) and dynamic passenger count badge.
    - Clickable email (`mailto:`) and telephone (`tel:`) anchors with SVG font icons.
  - **Bifurcated 2-Column Manifest Grid:**
    - **Route Column:** Displays service route (`Manila (MNL) ➔ Cebu (CEB)`), operating airline/bus carrier, and calendar travel date.
    - **Inclusions Column:** Displays seat allocation pill (`12A (Window)`), cabin class (`Economy Class`), and baggage specifications (`20kg Checked + 7kg Hand-carry Included`).
  - **Operational Admin Directives Suite:**
    - Replaces single-line input with full-width `<textarea id="modal-booking-notes" rows="3">`, guaranteeing unclipped visibility for lengthy PNRs, baggage tags, and client special instructions.
    - 4 quick-insert tags: `+ VIP`, `+ Baggage OK`, `+ Priority`, `+ Assistance`.
    - Action CTA: `Save Notes` button with instant admin toast feedback.
  - **Financial Summary Box:**
    - Soft tinted gradient card (`from-blue-50/70 via-indigo-50/40 to-slate-50 border-blue-100`).
    - Payment channel pill (`GCash`, `Online/Counter`), verified badge, and bold high-contrast total (`text-2xl sm:text-3xl font-black text-blue-700`).
  - **Executive Manifest Action Strip:**
    - Dark slate `Print Official E-Ticket` button (`bg-slate-900 hover:bg-slate-800`).
    - `Copy Details` clipboard export tool.
    - `Edit Reservation` direct modal transition.
    - `Close` secondary button.

### 44. Authenticated Traveler Account Identity Pill & Pre-fill Verification Banner Design
- **Files:** [bus-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/bus-booking.html), [js/bus-booking.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/bus-booking.js), [plane-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/plane-booking.html), [js/plane-booking.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/plane-booking.js)
- **Visual & Structural Architecture:**
  - **Account Linked & Pre-fill Verification Banner (`#modal-account-sync-banner`, `#plane-account-sync-banner`):**
    - Container: `mb-4 p-3.5 rounded-2xl bg-gradient-to-r from-blue-50 to-indigo-50/60 border border-blue-200/80 flex items-center justify-between gap-3 text-xs shadow-2xs`.
    - Avatar Badge: `w-8 h-8 rounded-xl bg-gradient-to-tr from-blue-600 to-indigo-600 text-white font-black text-xs flex items-center justify-center shadow-xs flex-shrink-0`.
    - User Identity: Bold slate-900 traveler name accompanied by a `text-[9px] bg-blue-100 text-blue-700 font-extrabold px-1.5 py-0.5 rounded-md uppercase tracking-wider` chip.
    - Contact Subtitle: High-contrast email and phone display (`text-[11px] text-gray-500 mt-0.5`).
    - Status Indicator: `text-[10px] font-bold text-emerald-700 bg-emerald-100/90 border border-emerald-300 px-2.5 py-0.5 rounded-full inline-flex items-center gap-1 flex-shrink-0` with checkmark icon.
  - **Header Active Account Identity Pill (`#bus-nav-account-pill`, `#plane-nav-account-pill`):**
    - Clean rounded-full container (`flex items-center gap-2 bg-gray-50 border border-gray-200/90 py-1 px-3 rounded-full text-xs shadow-2xs`).
    - Circular avatar (`w-6 h-6 rounded-full bg-gradient-to-tr from-blue-600 to-indigo-600 text-white font-bold flex items-center justify-center text-[10px]`).
    - Profile Name & Status Chip: Bold traveler name with `text-[9px] bg-emerald-100 text-emerald-700 font-extrabold px-1.5 py-0.2 rounded-full uppercase hidden md:inline` badge.
  - **Seamless Interactive Data Binding:**
### 45. Floating Status Dropdown Portal & Viewport-Aware Smart Positioning Design
- **Files:** [admin.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/admin.html), [js/admin.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/admin.js)
- **Visual Design & Positioning Architecture:**
  - **Global Portal Isolation (`#global-status-dropdown`):**
    - High-elevation glassmorphism popover (`fixed z-[9999] bg-white/95 backdrop-blur-md rounded-2xl shadow-2xl border border-gray-200/90 py-2 w-52 ring-1 ring-black/5 select-none`).
    - Mounted directly as a top-level child of `<body>`, completely breaking free from table `.overflow-x-auto` or card `.overflow-hidden` clipping contexts.
  - **Executive Header Bar:**
    - Clean uppercase title `UPDATE STATUS` paired with a high-contrast booking reference badge (`text-[9px] font-mono font-extrabold text-blue-600 bg-blue-50 px-1.5 py-0.5 rounded border border-blue-100`).
  - **Tactile Status Choice Buttons:**
    - Option cards (`w-full flex items-center justify-between px-3 py-2 text-xs font-bold rounded-xl transition text-left cursor-pointer group`):
      - **Confirmed:** Emerald dot (`bg-emerald-500 shadow-xs shadow-emerald-500/50`), emerald label, hover tint `hover:bg-emerald-50`.
      - **Pending Payment:** Amber dot (`bg-amber-500 shadow-xs shadow-amber-500/50`), amber label, hover tint `hover:bg-amber-50`.
      - **Completed:** Blue dot (`bg-blue-500 shadow-xs shadow-blue-500/50`), blue label, hover tint `hover:bg-blue-50`.
      - **Cancelled:** Rose dot (`bg-rose-500 shadow-xs shadow-rose-500/50`), rose label, hover tint `hover:bg-rose-50`.
    - Active status row is highlighted with `bg-slate-100 font-black` and an unhidden `.status-check-icon` (`fas fa-check`).
  - **Dynamic Viewport-Aware Auto-Flip Coordinate Math:**
    - Horizontal: Aligns with the left edge of the clicked status pill, with boundary clamping ensuring the dropdown never overflows off-screen: `left = Math.max(12, Math.min(window.innerWidth - dropWidth - 12, rect.left))`.
    - Vertical: Computes `spaceBelow = window.innerHeight - rect.bottom`. If `spaceBelow < 200px` (or near viewport bottom), flips **UPWARDS** (`top = rect.top - dropHeight - 6`); otherwise opens **DOWNWARDS** (`top = rect.bottom + 6`).
  - **Table Breathing Room:**
    - Enhanced table container with `min-h-[220px]`, maintaining executive balance even when the directory displays only 1 reservation.

### 46. Cloudflare Pages Production Architecture & Edge CDN Delivery Design
- **Production Host:** [Cloudflare Pages](https://pages.cloudflare.com)
- **Primary Domain:** `https://mckanes-travel.pages.dev`
- **Infrastructure Architecture:**
  - **Edge-First Static Asset Pipeline:**
    - All 69 compiled files (HTML5 markup, CSS utility sheets, client/admin JavaScript controllers, JSON catalog seeds, and optimized imagery) are deployed across Cloudflare's Anycast edge network.
    - Zero server-side runtime overhead ensures sub-50ms Time To First Byte (TTFB) globally.
  - **High-Fidelity Media Delivery:**
    - Scenic destination imagery (`cebu.jpg`, `boracay.jpg`, `siargao.jpg`, `coron.jpg`, `davao.jpg`, `manila.jpg`, `iloilo.jpg`) served directly with HTTP/2 multiplexing, aggressive edge cache-control, and automatic WebP/AVIF transformation where supported.
  - **Security & Access Containment:**
    - Global HTTPS certificate provisioned automatically via Cloudflare Universal SSL (ECDSA + RSA).
    - Hardened HTTP headers, TLS 1.3 protocol enforcement, and automatic HTTP-to-HTTPS upgrade.
 
### 47. Client Vacation Package Modal Account Sync Banner & Admin Reflection Design
- **Files:** [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html), [js/main.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/main.js), [admin.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/admin.html), [js/admin.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/admin.js)
- **Visual Design & Architectural Patterns:**
  - **Account Linked Verification Banner (`#pkg-account-sync-banner`):**
    - Container: `mb-4 p-3 rounded-2xl bg-gradient-to-r from-blue-50 to-indigo-50/60 border border-blue-200/80 flex items-center justify-between gap-3 text-xs shadow-2xs`.
    - Profile Initials Avatar (`#pkg-account-sync-avatar`): `w-8 h-8 rounded-xl bg-gradient-to-tr from-blue-600 to-indigo-600 text-white font-black text-xs flex items-center justify-center shadow-xs flex-shrink-0`.
    - Account Identity: Bold slate-900 traveler name accompanied by an account sync indicator pill.
    - Status Badge: `text-[10px] font-bold text-emerald-700 bg-emerald-100/90 border border-emerald-300 px-2 py-0.5 rounded-full inline-flex items-center gap-1 flex-shrink-0` with `fa-shield-check` icon.
  - **Clean Voucher Layout:**
    - Voucher Reference (`#voucher-ref-code`): `font-mono font-black text-blue-600 tracking-wider`.
    - Lead Traveler Display (`#voucher-lead-name`): Dynamically populated from lead form inputs or active session, completely replacing legacy dummy Juan Dela Cruz.
  - **Admin Operations Bookings Integration:**
    - Package Service Badge: `<span class="text-[9px] bg-emerald-50 text-emerald-700 border border-emerald-200 px-1.5 py-0.2 rounded font-extrabold uppercase">Package</span>` with `fa-umbrella-beach text-emerald-500` icon.
    - Dashboard Notification Highlight: Top recent booking row rendered with `bg-gradient-to-r from-emerald-50/70 via-teal-50/30 to-transparent border-l-4 border-l-emerald-500` and animated `NEW` badge.

### 48. Single-Page Print Layout & Typography Specifications for All Ticket Types
- **Files:** [css/plane-booking.css](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/css/plane-booking.css), [css/bus-booking.css](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/css/bus-booking.css), [css/admin.css](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/css/admin.css), [css/style.css](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/css/style.css)
- **Visual Design & Print Grid System:**
  - **Universal Page Constraint:**
    - Standard page bounds: `@page { size: portrait; margin: 8mm 10mm; }`.
    - Body height normalization: `html, body { max-height: 100vh !important; overflow: hidden !important; }`.
    - Total suppression of interactive/chrome elements: `header, nav, main, footer, button, .no-print { display: none !important; height: 0 !important; }`.
  - **Airline Boarding Pass Typography & Spacing:**
    - Maximum width: `max-w-[560px]` centered horizontally (`margin: 0 auto`).
    - Border: `2px solid #0f172a` with rounded perimeter `border-radius: 14px`.
    - Header: Golden gradient `bg-gradient-to-r from-amber-400 via-yellow-400 to-amber-300` with high-contrast navy typography.
    - Route Box: High-contrast origin/destination airport codes (24pt font-black) with dashed trajectory vector.
    - Scannable Footer: Code 128 barcode simulation typography paired with high-resolution vector QR code.
  - **Bus Transit E-Ticket Layout:**
    - Maximum width: `max-w-[500px]` centered horizontally with dark slate perimeter border.
    - Carrier badge: Amber bus icon emblem with bold operator and transit class subtitle.
    - Split itinerary columns: Departure date/time and assigned seats highlighted in bold color accents.
  - **Admin E-Ticket Manifest Layout:**
    - Maximum width: `max-w-[650px]` with dark slate header banner.
    - Formatted lead passenger card, carrier route grid, verified billing summary, and staff directive notes.
    - Interactive textarea controls, tag pills, and action bars suppressed during print.
  - **Vacation Package Voucher Layout:**
    - Maximum width: `max-w-[560px]` with dashed security perimeter border.
    - Two-column reservation specifications (package, resort, lead traveler, travel date, guests, total price).

### 49. Fluid Responsive Header & Non-Overlapping Nav Action Design
- **Files:** [bus-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/bus-booking.html), [plane-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/plane-booking.html), [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html)
- **Visual Design & Architectural Layout:**
  - **Fluid 3-Part Flexbox Hierarchy:**
    - Navbar Container: `max-w-7xl mx-auto py-3.5 px-4 sm:px-6 flex items-center justify-between gap-4`.
    - Left Identity Anchor: Logo with `flex-shrink-0` ensuring zero compression.
    - Middle Navigation Center: `hidden lg:flex items-center justify-center gap-5 xl:gap-7 flex-1 mx-2 sm:mx-4`. Links occupy only the remaining dynamic width between logo and actions.
    - Right Action Island: `flex items-center gap-2.5 sm:gap-3 flex-shrink-0`.
  - **Account Status Indicator Ergonomics:**
    - Status Container: `flex items-center gap-2 bg-gray-50 border border-gray-200/90 py-1 px-2.5 sm:px-3 rounded-full text-xs shadow-2xs flex-shrink-0`.
    - Avatar: `w-6 h-6 rounded-full bg-gradient-to-tr from-blue-600 to-indigo-600 text-white font-bold flex items-center justify-center text-[10px]`.
    - Traveler Name: Truncated at `max-w-[120px]` with `truncate` ellipsis.
    - Activity Dot: Emerald `w-2 h-2 rounded-full bg-emerald-500 animate-pulse`.
    - Status Badge: `text-[9px] bg-emerald-100 text-emerald-700 font-extrabold px-1.5 py-0.2 rounded-full uppercase hidden 2xl:inline`.
  - **High-Contrast Contact Anchor:**
    - Visual Weight: `font-bold text-blue-700 hover:text-blue-600 transition` ensuring instant readability against white and blurred glass navigation backdrops.

### 50. Pixel-Perfect Stepper Grid Alignment & 1:1 Card Parity
- **Files:** [plane-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/plane-booking.html)
- **Visual Design & Architectural Grid Alignment:**
  - **1:1 Card Parity Structure:**
    - Wrapper: `<section class="w-full max-w-7xl mx-auto px-4 sm:px-6 mt-3">`.
    - Inner Card: `<div class="bg-white rounded-2xl border border-gray-200/90 shadow-xs py-3 px-5 sm:px-8 flex items-center justify-between">`.
    - Replaced full-bleed 100vw strip with an executive floating card that matches the hero banner card (`rounded-2xl`, border, shadow, and side margins) with 100% width and coordinate parity.
  - **Inner Grid Alignment & Framing:**
    - Internalized padding: `px-5 sm:px-8` ensures Step 1, Step 2, and Step 3 are gracefully framed within the card boundaries, eliminating any spillage past the banner's outer edges.
    - Preserves consistent `#f8fafc` backdrop on the left and right, harmonizing the visual vertical flow from header to hero banner, stepper card, booking grid, and footer.















### 51. Split-Screen Dual Role Gateway Architecture & Art Integration
- **Files:** [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html), [home.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/home.html), [admin.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/admin.html)
- **Visual Design & Architectural Layout:**
  - **Split-Screen Viewport Geometry:**
    - Desktop: `h-screen overflow-hidden flex flex-col md:flex-row w-full` dividing the screen into two balanced 50% interactive panels.
    - Mobile: Graceful transition to stacked vertical cards with auto-scroll and thumb-friendly touch targets.
  - **Chromatic Palette Matching User Artwork:**
    - Admin Card: Royal Blue gradient `bg-gradient-to-b from-[#014eae] via-[#0156c0] to-[#013f92]` representing executive authority and operations.
    - Client Card: Royal Sky Blue gradient `bg-gradient-to-b from-[#0057c7] via-[#004eb2] to-[#003882]` representing leisure, travel, and vacation exploration.
    - Typography: Bold white sans-serif headings (`text-4xl md:text-5xl font-black tracking-tight text-white drop-shadow-md`) with high-contrast subtitles.
  - **Micro-Interactions & Hover Dynamics:**
    - Card-wide hover trigger: `hover:brightness-105 transition-all duration-300 cursor-pointer`.
    - Float animation on characters: `transition-transform duration-500 group-hover:scale-105 group-hover:-translate-y-2`.
    - Action buttons: Pure white pill buttons (`bg-white text-blue-900 font-bold px-8 py-3.5 rounded-full shadow-lg hover:shadow-xl hover:bg-blue-50 active:scale-95 transition-all duration-200`) with arrow iconography.
  - **Floating Brand Header & Central Divider:**
    - Centered top pill: Glassmorphism badge (`bg-white/10 backdrop-blur-md border border-white/20 rounded-full px-4 py-1.5`) featuring Mckanes globe emblem.
    - Central "OR" badge: Circular divider badge (`w-12 h-12 rounded-full bg-white shadow-xl text-blue-900 font-black text-sm flex items-center justify-center`) placed at the exact 50% horizontal seam.


### 52. Authenticated Gateway Security State & Quick Credential Ergonomics
- **Files:** [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html), [admin.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/admin.html)
- **Visual Design & Architectural Layout:**
  - **Guaranteed Locked Screen Presentation:**
    - Root screen `#admin-auth-screen` renders in full-bleed viewport `fixed inset-0 z-[100] bg-[#030712] flex flex-col justify-between items-center p-4 sm:p-6`.
    - Features atmospheric flight horizon backdrop (`images/about_plane_hd.jpg`), air traffic radar sweeps, glowing waypoint coordinates, and real-time PST clock telemetry HUD.
  - **Security Card Ergonomics:**
    - Glassmorphism container `#admin-login-card` (`bg-slate-900/85 backdrop-blur-2xl border border-white/10 rounded-3xl`).
    - Luminous accent line and gold lock emblem badge (`fas fa-lock text-amber-400`).
    - Clean empty password input with eye toggle icon and subtle focus glow.
  - **Quick Demo Fill Pill:**
    - Subtly positioned below the primary "Unlock Admin Console" submit button: `text-[11px] text-slate-400 hover:text-sky-300 py-1 px-3 rounded-lg bg-slate-800/40 hover:bg-slate-800/80 border border-slate-700/50`.
    - Features gold key icon (`fas fa-key text-amber-400`) and high-legibility monospace username/password tags (`Mckanes@123` / `chibiba`).


### 53. Unauthenticated Guest Header Architecture & Client Sign In Modal Trigger
- **Files:** [home.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/home.html), [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html), [plane-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/plane-booking.html), [bus-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/bus-booking.html)
- **Visual Design & Architectural Layout:**
  - **Coordinated Guest Navigation Structure:**
    - `#nav-auth-container` in `home.html` harmoniously balances two prominent action pills in guest mode:
      1. White/gray `Role Portal` switcher pill with blue gear icon.
      2. Vibrant royal blue `Sign In` button (`bg-blue-600 hover:bg-blue-700 text-white font-bold rounded-full shadow-md`).
  - **Unauthenticated Booking Pill Consistency:**
    - In `plane-booking.html` and `bus-booking.html`, guest navigation pills render neutral slate avatars (`GT`, `bg-gradient-to-tr from-slate-500 to-slate-700`), `Guest Traveler` typography, and static gray status indicator dots (`bg-slate-300`), eliminating premature profile flashes.
  - **Automated Client Auth Dialog Ergonomics:**
    - Triggered `#auth-modal` appears with smooth cubic-bezier scale (`scale-95` to `scale-100`) and backdrop blur `bg-black/60 backdrop-blur-sm`.
    - Features discrete `Quick Demo Fill` pill (`julie@gmail.com` / `password123`) styled with `bg-gray-50 hover:bg-blue-50 border border-gray-200 text-gray-500` for effortless client identity evaluation.

### 54. Role Selection Gateway Streamlined Button Anatomy & Clean Hierarchy
- **Files:** [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html)
- **Visual Design & Architectural Layout:**
  - **Minimalist Call-To-Action Layout:**
    - Streamlined the bottom CTA block on both sides of the gateway, removing repetitive instructional prompts (`Click anywhere on this side to enter`) to produce an elegant, uncluttered presentation.
    - Action buttons (`Admin Login` and `Enter Main Page`) now command clean visual hierarchy centered beneath character graphics.
  - **Symmetrical Vertical Spacing:**
    - Retained balanced vertical rhythm with `flex flex-col items-center`, preserving glassmorphism pill styling (`bg-white/15 hover:bg-white text-white hover:text-blue-900 border border-white/30 backdrop-blur-md shadow-xl`).
  - **Seamless Interactive Affordance:**
    - Full-card clickable zones (`cursor-pointer group`) remain fully operational, maintaining card hover dynamics (`hover:brightness-105`, character lifts) without requiring visible instructional text prompts.

### 55. Main Page Instant Gateway Refresh Redirection Mechanics
- **Files:** [home.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/home.html), [js/main.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/main.js)
- **Visual Design & Architectural Layout:**
  - **Synchronous Lifecycle Interception:**
    - Placed inside `<head>` of `home.html` immediately after `<title>`, ensuring page refresh triggers redirect immediately before any layout engine execution or paint passes.
  - **Visual Continuity & Zero Page Flicker:**
    - Utilizing `location.replace('index.html')` prevents blank white page flashes or half-rendered sections, seamlessly returning the user directly to the split-screen gateway cards.
  - **Session State Cleansing:**
    - Returning to `index.html` triggers gateway session purges, ensuring both the Admin console and Client portal present clean, unauthenticated entry states.

### 56. Main Page Header Composition & Role Pill Elimination
- **Files:** [home.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/home.html), [js/main.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/main.js)
- **Visual Design & Architectural Layout:**
  - **Balanced Top Navigation Bar:**
    - Purged the `Role Portal` auxiliary pill button from `#nav-auth-container`, reducing visual noise in the header.
    - The right-hand action container now showcases a singular, prominent action: the vibrant blue `Sign In` button (`bg-blue-600 hover:bg-blue-700 text-white font-bold rounded-full shadow-md shadow-blue-600/20`) for guests, or the elegant round avatar pill (`TR`) for signed-in travelers.
  - **Sleek Horizontal Hierarchy:**
    - Creates generous negative space separating centered navigation items (`HOME`, `ABOUT`, `PACKAGE`, `CONTACT`, `REVIEWS`) from the account trigger, preventing visual crowding on laptops and tablets.

### 57. Client Sign-In Modal Keep Me Signed In Micro-Interactions
- **Files:** [home.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/home.html), [js/main.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/main.js)
- **Visual Design & Architectural Layout:**
  - **Dynamic Input Lighting & Tactile Feedback:**
    - Toggling the "Keep me signed in" checkbox triggers a gentle soft blue focus transition (`bg-blue-50/60`) on the Email Address textbox `#signin-email`, visually signaling that the account's Gmail address has been populated.
  - **Predictable Form Ergonomics:**
    - Seamlessly eliminates user friction by pairing checkbox states with input population, guaranteeing that checking "Keep me signed in" renders the registered traveler's Gmail directly into the textbox.

### 58. Curated Tour Packages Operations Interface & Place Creation Modal Architecture
- **Files:** [admin.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/admin.html), [js/admin.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/admin.js), [home.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/home.html), [js/main.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/main.js)
- **Visual Design & Architectural Layout:**
  - **Executive Inventory Header & Status Counter:**
    - Features an emerald-pill status badge (`#packages-count-badge`) and royal blue action button (`bg-blue-600 hover:bg-blue-700 shadow-blue-500/20 active:scale-95`) commanding visual precedence in `#tab-packages`.
  - **High-Density Modal Form Ergonomics (`#add-package-modal`):**
    - Styled with deep slate header (`bg-slate-900 text-white`), clean 2-column input grids, soft blue pricing highlight container (`bg-blue-50/70 border-blue-100/80`), and full mobile responsiveness (`max-h-[92vh] overflow-y-auto`).
  - **Visual Preset Image Grid & Real-Time Thumbnail Preview:**
    - 12 rounded image thumbnails (`h-14 rounded-xl`) with active blue borders and ring glow, complemented by a live 40x40px square preview box (`#add-pkg-image-preview`) with fallback error handling.
  - **Synchronous Catalog Hydration & Client Card Harmony:**
    - Seamlessly transforms raw admin package objects into rich client travel cards matching the typography, gradients, ratings, badges, and modal structures of the public catalog.

### 59. Find Your Destination Card Navigation Alignment & Viewport Scrolling
- **Files:** [home.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/home.html)
- **Visual Design & Architectural Layout:**
  - **Contextual Visual Routing:**
    - Aligned the "Find Your Destination" card with the immediately adjacent "Popular Destinations" showcase, creating a cohesive visual and logical progression from service discovery to island exploration.
  - **Optimal Viewport Framing:**
    - Bound navigation targets to `#destinations` with `scroll-mt-24` top margin compensation, guaranteeing that the section's badges, title ("Popular Destinations"), and quick destination selector pills align cleanly below the fixed frosted navigation header.


