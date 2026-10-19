# System Functions and Workflow
Always update for system functions and workflow.

## 1. System Overview
Mckanes Travel and Tours is a comprehensive travel and booking web platform providing domestic and international travelers with tailored experiences across the Philippines. The system serves as a unified hub for:
- Destination exploration and itinerary planning.
- Commercial flight reservations and partner deals.
- Provincial bus ticket purchasing and route scheduling.
- Hotel accommodations, vacation packages, and local tours.

## 2. Currently Implemented Functional Components

### A. Navigation & Brand Controller
- **File:** `C:\Antigravity files\Mckanes Travel and Tours\index.html` (Lines 33–55)
- **Functions:**
  - Provides centered navigation anchors (`HOME`, `ABOUT`, `PACKAGE`, `CONTACT`, `REVIEWS`) perfectly balanced between the left-aligned brand logo and the right container edge.
  - Implements responsive layout with clean, shadowless integration into the full-view hero section.

### B. Full-Screen Hero Experience & Interactive Controls
- **File:** `C:\Antigravity files\Mckanes Travel and Tours\index.html` (Lines 32–138)
- **Functions:**
  - **Full-Viewport Rendering:** Uses `min-h-screen` container sizing to ensure the user experiences a complete, unclipped landing screen above the fold with an exact 1.82:1 aspect ratio (`max-w-[1280px]`, `h-[540px] sm:h-[580px] md:h-[620px] lg:h-[670px]`).
  - **3D Overlapping Vehicle Showcase:** High-resolution transparent cutouts of the commercial airliner (`images/user_plane.png`) positioned at `left: 49.5%`, `top: 5.5%`, `width: 75%` with `rotate(1deg)` breakout, and tightly cropped red tour coach (`images/bus.png`) positioned at `left: -0.5%`, `bottom: 4%`, `width: 26.5%` anchored cleanly on the green hill with realistic drop shadows and no horizontal scrollbar overflow.
  - **Visual Journey Stepper:**
    - Step 1 (Active): Discover destinations.
    - Step 2: Select transit (Flight / Bus).
    - Step 3: Confirm packages and booking.
  - **Call to Action System:**
    - Primary Button: "Book A Trip Now" triggers direct navigation to booking interfaces.
    - Video Preview Trigger: Circular play button with micro-interaction hover scaling (`hover:scale-105`).
  - **Featured Teaser ("Awesome Places"):**
    - Bottom-right teaser card showcasing top destinations with an actionable "Know More" discovery link.
    - Dynamic image avatar stack showing preview thumbnails.
  - **Social Connectivity Strip:**
    - Floating pill container providing direct routing to official social media channels: Twitter, Instagram, Facebook, and TikTok.
  - **Partner Trust Network:**
    - Displays integrated aggregator and booking networks (Booking.com, Expedia, agoda, trivago) to reinforce traveler trust and security.

### C. Services & Transit Category Cards
- **Files:** [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html) (`#services`), [js/main.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/main.js)
- **Functions & Architecture:**
  - **3-Column Responsive Grid Layout:** Enclosed within `<div class="grid grid-cols-1 md:grid-cols-3 gap-8">` ensuring balanced, side-by-side card distribution on desktop and fluid collapse on mobile screens.
  - **Destination Exploration Card:** High-definition Palawan photograph (`&w=800&q=80`) directing users to curated Philippine vacation packages (`#packages`) via the "Find Now" CTA.
  - **Flight Ticketing Portal Card:** Features partner airline integration (Cebu Pacific) displaying the authentic Cebu Pacific aircraft photo (`images/cebu_pacific.jpg`, `object-position: center 55%`) with interactive hover animation. Intercepted by `requireAuthToBook('plane', event)` to prompt guest users to authenticate before entering ticketing.
  - **Bus Ticketing Portal Card:** Features partner provincial transit operator (Victory Liner) with high-definition coach photography (`&w=800&q=80`). Intercepted by `requireAuthToBook('bus', event)` ensuring booking session security.

### D. Asymmetrical Popular Destinations Engine
- **File:** `C:\Antigravity files\Mckanes Travel and Tours\index.html` (Lines 199–290)
- **Functions:**
  - **Spotlight Showcase:** Highlights premier destinations (Coron Island, Palawan) with detailed rating (`4.9 / 5.0`), location metadata, overview synopsis, and "Explore Destination" CTA.
  - **Quick-Browse Stack:** Three stacked destination cards enabling high-density browsing for secondary destinations:
    - White Beach (Boracay Island, Aklan) - Rating: 4.8
    - Waterfall Trails (Lazi, Siquijor) - Rating: 4.7
    - Cultural Landscapes (Banaue, Ifugao) - Rating: 4.5
  - **Navigation Anchors:** "Explore all destinations" link.

## 3. Planned Features & Workflow Roadmap

### Flow 1: Flight Booking Workflow
1. **Search Phase:** Selection of trip type (Round Trip, One Way, Multi-City), origin airport, destination airport, departure/return dates, passenger counts (Adults, Children, Infants), and cabin class.
2. **Flight Search Results:** Filterable list sorted by price, departure time, flight duration, and airline carrier.
3. **Passenger Details:** Guest information input, baggage add-ons, and seat preference.
4. **Payment & Ticketing:** Integration with payment providers (Credit Card, GCash, Maya, PayPal) and immediate issuance of e-ticket confirmation.

### Flow 2: Provincial Bus Ticketing Workflow
1. **Route Selection:** Origin bus terminal selection and arrival destination.
2. **Departure Selection:** Time slot selection and bus class (Standard Aircon, Deluxe, Executive Sleeper).
3. **Interactive Seat Selection:** Graphical seat map showing occupied, reserved, and available seats.
4. **Digital Boarding Pass:** Generation of QR code pass for mobile boarding.

### Flow 3: Tour Package & Custom Inquiry Workflow
1. Multi-day curated package catalog with itinerary timetables.
2. Direct booking and customized corporate/family travel inquiry submission.

### Flow 4: Reviews & Testimonials Engine
1. Customer rating and feedback submission module.
2. Filterable review archive sorted by verified traveler category (Solo, Couple, Family, Group).


### E. Interactive Bus Ticket Booking Module (`bus-booking.html`)
- **File:** `C:\Antigravity files\Mckanes Travel and Tours\bus-booking.html`
- **Implemented Functions:**
  - **Framed Compact Hero Banner & 2-Column Content Grid:** Employs the uncompressed master graphic (`images/bus_banner_exact.png`, 1024×190, ~5.39:1 aspect ratio) encased inside a framed container (`max-w-7xl mx-auto px-4 sm:px-6 pt-4 pb-1`) with rounded borders and subtle drop shadow (`rounded-2xl overflow-hidden shadow-md border border-blue-100 bg-[#3a8adc]`), matching the exact visual sizing, height, and framing of the domestic plane booking hero banner in `plane-booking.html` per user request (`media_1792202789066_9be0edef.png`). Seamlessly paired with the 2-column content grid (`max-w-7xl mx-auto px-4 sm:px-6 py-5 sm:py-6 relative z-20 pb-16`) where the Search / Filter Card (left 8 cols) and Trip Summary sidebar (right 4 cols) sit cleanly aligned directly beneath the hero card.
  - **Dynamic Route Search Engine:** 
    - Integrated Origin & Destination flex container (`lg:col-span-6`) with inline responsive swap button (left/right on desktop/tablet, up/down on mobile).
    - Integrated HTML5 Date picker (`lg:col-span-2`) with automated day-of-week calculation.
    - Day navigation buttons (`<` and `>`) that step departure dates forward and backward across the schedule.
    - Expanded Passenger selector (`lg:col-span-2`) with descriptive option labels ("1 Passenger", "2 Passengers" up to 5) and clean spacing, eliminating text collision and arrow overlap.
    - Reactive "Search Buses" trigger (`lg:col-span-2`) with search feedback state and filtered results counter.
  - **Live Operator Filtering & Trip Sorting:**
    - Instant filter pills by operator (`All Operators`, `Victory Liner`, `Genesis Transport`, `JoyBus`, `Partas`, `Philtranco`).
    - Multi-criteria sorting dropdown (`Departure Time`, `Price: Low to High`, `Price: High to Low`, `Duration`).
  - **Trip Selection State Management:**
    - Selecting any trip card dynamically highlights the card with a primary blue border and changes the button to "✓ Selected".
    - Automatically updates the **Trip Summary** sidebar with the operator name, service class, departure/arrival times, travel duration, per-passenger base fare, terminal fee, and calculated grand total.
  - **Dynamic Passenger Details & Seat Booking Modal:**
    - Triggered by clicking "Continue to Passenger Details →".
    - Dynamically generates passenger input cards for each passenger selected.
    - Interactive seat preference radio options (Window/Aisle).
    - Multi-channel payment method selector (GCash/Maya, Credit Card, Over-the-counter).
    - Instant digital ticket generation with printable e-ticket receipt, randomized official booking reference code, and traveler manifest.
  - **Seamless Navigation:** Integrated "Back to Home" links to return to [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html).


### F. Traveler Reviews & Social Proof Engine
- **File:** `C:\Antigravity files\Mckanes Travel and Tours\index.html` (Lines 299–465)
- **Functions:**
  - Displays verified user feedback across multiple transit and destination categories (Bus ticketing, regional discovery, multimodal booking).
  - Integrates 5-star rating presentation and traveler hometown verification.
  - Features real-time platform impact metrics:
    - 10+ Curated Domestic Destinations
    - 12,000+ Travelers Inspired
    - 4.9 Average Customer Satisfaction Rating
  - Navigation Anchor: Connected to the top navigation `REVIEWS` link for quick jumping.

### G. Kinetic Typography & Hero Micro-Interactions
- **File:** [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html) (Lines 105–175)
- **Functions:**
  - **Dynamic Floating Wave Typography:** Applied out-of-phase vertical oscillation keyframes (`floatWord1`, `floatWord2`, `floatWord3`) to headline words ("Experience", "The Magic", "Of Travel!"), creating an organic floating effect.
  - **Interactive Hover Elevate:** Each word responds to pointer hover with an elevated lift (`translateY(-6px) scale(1.02)`) and heightened drop shadow.
  - **Video Play Button Ripple:** Interactive pulse ring (`ripple-halo`) radiating outward behind the play button to draw traveler engagement.
  - **Authentic Airline Imagery:** Service Card 2 ("Book A Plane Ticket") updated to local authentic Cebu Pacific fleet aircraft (`images/cebu_pacific.jpg`).

### H. Persistent Sticky Header & Global Return Navigation
- **Files:** [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html) (Lines 105–130), [bus-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/bus-booking.html) (Lines 44–75)
- **Functions:**
  - **Always-Visible Top Header:** Positioned with `sticky top-0 z-50` directly under `<body>`, ensuring the header remains permanently visible while scrolling anywhere on the page.
  - **Dynamic Scroll Elevation:** JavaScript listener applies `shadow-md shadow-gray-200/50` and border highlights when scrolling past 20px offset.
  - **Instant Home Return:** Clicking `HOME` or the brand globe logo immediately triggers smooth scrolling to the top (`window.scrollTo({top: 0, behavior: 'smooth'})`) on the main page, and links back to `index.html` from `bus-booking.html`.
  - **Anchor Offset Compensation:** Configured `scroll-mt-24` on `#services`, `#destinations`, and `#reviews` sections so anchor jumps leave ample clearance below the sticky header.
  - **Comprehensive Footer & Contact Section:** Added a 4-column responsive footer (`#contact`) with brand story, social media channels, quick navigation, popular domestic destinations, customer support hotline, and 'Back to Top' return link.

### I. Hero Vehicle Kinematics & Kinetic Arrival Sequences
- **File:** [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html) (Lines 98–160, 225–235)
- **Functions:**
  - **Airliner Flight-In Entrance:** Commercial passenger airplane smoothly swoops in from the sky (`translate3d(260px, 115px, 0) scale(0.86) rotate(-2.5deg)`) on page load, gliding seamlessly into its headline breakout position over 1.9 seconds with hardware-accelerated cubic-bezier easing.
  - **Ambient Cruising Altitude:** After landing in position, the airplane transitions into an organic 6-second cruising drift (`@keyframes planeCruising`), gently banking and floating across the cloudscape.
  - **Coach Arrival & Suspension Brake Settle:** Red VIP tour coach accelerates onto the screen from `-240px` left over 1.7s, braking smoothly into its designated parking spot with realistic deceleration and suspension settle at `left: -0.5%; bottom: 4%`.

### J. Interactive 3-Slide Hero Stepper Carousel & HD Video Showcase Modal
- **File:** [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html) (Lines 220–280, 780–986)
- **Functions:**
  - **Clickable Stepper Tabs (`1`, `2`, `3`):** Converted static vertical numbers into interactive circular stepper controls with animated progress fill lines (`#step-track-0`, `#step-track-1`), 6px frosted halo outer rings, and active elevation states.
  - **Dynamic Multimodal Slide Transitions:**
    - Slide 1: All-in-One Philippine Travel showcasing both aircraft & VIP bus, with "Awesome Places" badge linking to `#destinations`.
    - Slide 2: Island Getaways focusing on authentic Cebu Pacific flights with airliner scaling to foreground and dimmed coach background.
    - Slide 3: Highland Express highlighting Baguio/Sagada/Vigan routes with red VIP bus foregrounding and direct CTA button to [bus-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/bus-booking.html).
  - **Automated 5-Second Motion Engine:** Configured exact 5.0-second auto-rotation cycle (`SLIDE_DURATION = 5000`) with smooth linear track fills (`animateProgressTracks`), reliable background progression without mouse-freeze locks, and instantaneous manual click reset.
  - **Full HD Tourism Video Modal:** Interactive popup player featuring official Philippine tourism footage with sound, glassmorphism modal backdrop, backdrop dismissal, and `Escape` key shortcut.

### K. Dedicated Interactive Plane Booking Engine (`plane-booking.html`)
- **Files:** [plane-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/plane-booking.html), [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html), [bus-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/bus-booking.html)
- **Functions:**
  - **Authentic Plane Booking Hero Header:** Integrated high-resolution banner (`images/plane_banner.png`) with "Book Your Plane Ticket" typography and Cebu Pacific Airbus A321neo fleet livery.
  - **Horizontal 3-Step Stepper Bar:** Visual progress flow (`1 Flight Details` -> `2 Passenger Information` -> `3 Review & Payment`) with smooth scrolling anchors, step completion checkmarks, and active state transitions.
  - **Interactive Flight Details Search Card:**
    - Dynamic Round-trip / One-way toggle updating return date opacity, leg tabs, and sidebar display.
    - Origin & Destination dropdowns (MNL, CEB, DVO, ILO, PPS, MPH, IAO) with animated `⇄` swap button, airport terminal subtext updates, and scenic destination photo synchronization.
    - Departure Date & Return Date pickers with calendar previews and automated return date adjustment.
    - Passenger quantity stepper counters for Adults, Children, and Infants with live passenger array synchronization and fare re-computation.
    - Cabin Class selector (`Economy`, `Premium Economy`, `Business Class`) with dynamic base fare multipliers.
  - **Dynamic Flight Results Catalog & Filter Engine:**
    - Dynamic search execution displaying available schedules for selected route with direct duration and amenity tags.
    - Airline filter pills (All Airlines, Cebu Pacific, Philippine Airlines, AirAsia) for instantaneous schedule filtering.
    - Sort controls (Cheapest, Earliest Departure, Fastest Flight).
    - Round-trip leg tabs (`tab-outbound` and `tab-inbound`) enabling independent outbound and return flight selection with completed check badges.
    - Interactive flight cards displaying airline code badges, equipment models, departure/arrival terminals, pricing, and active selection states.
  - **Dynamic Multi-Passenger Form & Add-ons Manager:**
    - Automatic generation of passenger profile cards matching traveler count, with Lead Passenger designation.
    - Passenger removal (`Remove ×`) functionality preserving lead traveler.
    - Interactive seat preference picker (`12A Window`, `12B Aisle`, `14A Window`, `14B Aisle`).
    - Baggage upgrade selection (20kg Included, 32kg Extra +₱450, 40kg Heavy +₱850).
    - Travel protection toggle (+₱280 per passenger) updating trip breakdown.
  - **Real-Time Synchronized Trip Summary Sidebar:**
    - Live destination scenic cover photo, route banner, and cabin tags.
    - Dynamic flight cards displaying selected departure and return airlines, flight numbers, aircraft, and departure/arrival times.
    - Transparent Fare Breakdown with base fare multiplier (`1x`, `2x`), taxes, baggage add-ons, insurance, and grand total.
  - **Multi-Channel Review & Payment Modal:**
    - State 1: E-Ticket preview card with live PNR, passenger manifest, route, seat, and interactive payment tabs (GCash, Maya, Card, OTC).
    - State 2: High-fidelity reservation simulation and seat assignment loader.
    - State 3: Confirmed booking screen with official dual-stub printable Boarding Pass (`#printable-boarding-pass`), barcode, QR code, one-click PNR clipboard copy, printable receipt (`window.print()`), and downloadable plain-text e-ticket receipt (`downloadTicketReceipt()`).

### L. Popular Destinations Interactive Showcase & Modals (`index.html`)
- **Files:** [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html) (`#destinations`, `#destination-modal`, `#all-destinations-modal`)
- **Functions:**
  - **Verified Asset Pipeline:** Replaced broken remote links and incorrect images with high-resolution local photography (`images/coron.jpg` Coron, `images/boracay.jpg` Boracay, `images/waterfall.jpg` Siquijor, `images/banaue.jpg` Banaue, `images/siargao.jpg` Siargao).
  - **Master-Detail Interactive Showcase (`selectDestination`):**
    - Clicking any destination card in the right stack or top quick selector pills dynamically updates the featured left card with smooth image cross-fade.
    - Synchronizes destination title, location, category tag, transportation method, season, rating, and description.
    - Real-time active border and badge highlights (`border-blue-600 bg-blue-50/70`, `Viewing Now` indicator) on selected items.
  - **Quick Filter Pills:** Four dedicated pills (`Coron Island`, `White Beach`, `Waterfall Trails`, `Cultural Landscapes`) for instant one-click switching.
  - **Comprehensive Destination Detail & Itinerary Modal (`openDestinationModal`):**
    - High-definition cover photo, star rating, verified review count, and full description.
    - Fast travel overview: Best season, recommended duration, and transportation routes.
    - Top attractions & experiences checklist.
    - Curated sample multi-day itinerary.
    - Action buttons linking directly into flight booking (`plane-booking.html`) or bus booking (`bus-booking.html`).
  - **All Destinations Directory Modal (`openAllDestinationsModal`):**
    - Directory displaying 8 top Philippine destinations across Luzon, Visayas, and Mindanao.
    - Category filtering: `All`, `Islands & Beaches`, `Highlands & Mountains`, and `Waterfalls & Eco-Trails`.
    - One-click `Preview` to switch the main showcase to that destination, and `Details ➔` to view the comprehensive itinerary guide.
  - **Modal Dismissal & Keyboard Controls:** Backdrop click to dismiss, close button, and global `Escape` key shortcut.

### M. Page-Wide Background Palette Harmonization (`index.html`)
- **Files:** [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html)
- **Functions:**
  - Standardized background canvas to unified `#f9fafb` (`bg-gray-50`) across the entire page, eliminating visual friction and abrupt color shifts between sections.
  - Adjusted sticky navigation header to `bg-gray-50/95` with backdrop blur and delicate border `border-gray-200/40`.
  - Converted Hero section from `bg-white` to `bg-gray-50`, seamlessly matching the organic corner cutout wrapper.
  - Aligned Popular Destinations (`#destinations`) and Traveler Reviews (`#reviews`) sections to `bg-gray-50` with subtle dividers `border-gray-200/50`.
  - Maintained pure white floating cards (`bg-white rounded-3xl shadow-sm border border-gray-100`) across all interactive modules for superior readability and elevation.

### N. Luminous Golden Boarding Pass Ticket Redesign (`plane-booking.html`)
- **Files:** [plane-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/plane-booking.html)
- **Functions:**
  - Redesigned flight cards from flat, heavy yellow rectangles into luxury Golden Boarding Pass tickets using a soft champagne gold gradient (`bg-gradient-to-b from-[#fff9e6] via-[#fef3cc] to-[#fae6a3]`), crisp border `border-[#e8ce85]`, and micro-elevation.
  - Implemented balanced 7-column layout (3 cols Origin, 1 col Center Flight Track, 3 cols Destination) preventing any horizontal text clipping, border overlaps, or crowded elements.
  - Formatted terminal tags concisely as `City Terminal` (e.g. `Manila Terminal 3`, `Cebu Terminal 1`) with departure/arrival plane icons and `max-w-[48%]` boundary protection.
  - Streamlined airline label in the header (`Cebu Pacific 5J 561`) alongside the `DEPARTURE` / `RETURN` indicator and emerald `Direct` badge.
  - Updated compact weekday date format (`Sat, Oct 15`) with prominent blue departure time (`text-blue-700`).
  - Synchronized the Official Boarding Pass card (`#printable-boarding-pass`) inside the Booking Confirmed modal with the matching 7-col golden ticket and vibrant airline badge.

### O. Organic Stepped S-Curve Hero Cutout & Dynamic Badge (`index.html`)
- **Files:** [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html) (`#hero-cutout-card`, `#hero-cutout-path`, `#hero-badge-link`, `#hero-badge-avatars`, `#hero-badge-title`, `#hero-badge-desc`)
- **Functions:**
  - Upgraded the bottom-right hero teaser card from a single quarter-circle box to the organic stepped S-curve dual-tier contour specified in the master Figma mockup.
  - Formatted container with scalable SVG geometry (`viewBox="0 0 440 170"`) adhering to an authentic 2.588:1 aspect ratio across responsive viewports (`w-[340px] h-[131px]`, `sm:w-[380px] sm:h-[147px]`, `lg:w-[440px] lg:h-[170px]`).
  - Implemented dual-path rendering:
    - **Cutout Path (`#f9fafb`):** Carves into the green landscape photo with a smooth tangent concave fillet at $y = 170$ eliminating any visible highway/road slivers, wrapping around the 58px radius pill cap, and sweeping up the organic Bezier S-curve with an exact 14px negative-space margin.
    - **Dynamic Badge Path (`#hero-cutout-path`):** Multi-tier card contour housing the "Know More ➔" link on the upper tier and destination avatar group on the lower pill tier, with rounded corners into the bottom and right edges.
  - Full compatibility with the 3-slide interactive stepper (`goToSlide`): dynamically transitions badge fill color between Slide 1 (`#4a6375`), Slide 2 (`#1e40af`), and Slide 3 (`#0d9488`).
  - Proportional tier centering: uses percentage coordinate positioning (`top-[16.5%] h-[31.8%] w-[37.5%]` upper wing; `top-[48.2%] bottom-0 pl-[18.5%]` lower pill) ensuring avatars and text remain centered with 23px vertical breathing room and zero bottom edge clipping across all screen sizes.
  - Preserved complete DOM semantic ID tree and responsive typography without layout shifts or text wrapping defects.

### P. Modular Codebase & Decoupled Asset Pipeline
- **Directory Structure:**
  - `css/`: Standalone stylesheets containing keyframe animations, component themes, date input rules, and print media blocks.
    - [css/style.css](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/css/style.css): Main landing page animation keyframes, hero perspective, and stepped S-curve card styles.
    - [css/plane-booking.css](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/css/plane-booking.css): Flight selection active indicators, date pickers, and `@media print` rules for the boarding pass.
    - [css/bus-booking.css](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/css/bus-booking.css): Form input formatting and calendar picker styling.
  - `js/`: Client-side controllers and business logic engines.
    - [js/main.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/main.js): Sticky header scroll elevations, 3-slide hero carousel controller (`goToSlide`), video modal controls, popular destinations showcase engine (`selectDestination`), and all-destinations directory modal.
    - [js/plane-booking.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/plane-booking.js): Airport mappings, domestic flight schedules, dynamic route filtering, seat selector matrix, passenger input generator, fare calculator, payment breakdown, and text receipt generator.
    - [js/bus-booking.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/bus-booking.js): Bus trip catalog (`TRIPS_DATA`), operator filtering, seat allocation, passenger modal, and booking confirmation generator.
  - `data/`: Clean JSON databases for external integration and backend compatibility.
    - [data/destinations.json](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/data/destinations.json): Structured JSON array of 4 top featured Philippine travel destinations with full itineraries, highlights, and ratings.
    - [data/flights.json](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/data/flights.json): Domestic flight schedules and airport master data.
    - [data/bus-trips.json](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/data/bus-trips.json): Provincial bus schedules across victory liner, genesis, joybus, and partas.
- **Verification & Integrity:**
  - Zero syntax errors verified via Node.js v24 (`node --check`).
  - All JSON files verified as valid data schemas (`JSON.parse`).
  - Seamless offline execution on `file:///` protocol preserved.

### Q. Interactive Vacation & Tour Packages System (`#packages`)
- **Files:** [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html) (`#packages`, `#package-booking-modal`), [js/main.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/main.js), [data/packages.json](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/data/packages.json)
- **Functions:**
  - **Dynamic Package Catalog (`renderPackageCards`):** Renders interactive cards featuring authentic Philippine vacation bundles:
    1. Boracay Ultimate Tropical Retreat (3D2N, Flights + Henann Resort + Island Hopping + Sunset Sail, ₱8,499, featuring `images/boracay.jpg` sunset paraw sailing).
    2. Coron & Palawan Island Odyssey (4D3N, Flights + Bayside Eco-Resort + Kayangan Lake + Twin Lagoon, ₱11,999, featuring `images/coron.jpg` limestone karsts).
    3. Baguio & Banaue Highland Heritage Expedition (3D2N, Deluxe Coach + Camp John Hay Lodge + Terraces Trek, ₱5,899).
    4. Siargao Surf, Lagoon & Island Explorer (4D3N, Flights + Kermit Eco-Villa + Cloud 9 Surf + Sugba Lagoon, ₱13,499, featuring `images/siargao.jpg` tropical beach palm swing).
    5. Siquijor Enchanted Waterfalls & Coastal Haven (3D2N, Flights + Fastcraft + Coco Grove Resort + Cambugahay Falls, ₱7,999).
    6. Cebu & Bohol Twin Island Wonder Vacation (4D3N, Flights + Fast Ferry + Oslob Whale Shark + Chocolate Hills, ₱12,750).
  - **Real-Time Category Filtering (`filterPackages`):** Instant category filtering across All, Beach & Islands, Island Hopping, Highland Escapes, and Eco-Adventure.
  - **Comprehensive Itinerary & Customizer Modal (`openPackageModal`):**
    - High-definition destination imagery, duration badges, and transport tags.
    - Day-by-Day expandable itinerary timeline.
    - All-inclusive inclusions checklist with visual indicators.
    - Interactive Guest Counter: Adults and Children (with 30% discount applied automatically).
    - Multi-Tier Accommodation Selector: Standard Deluxe, Premier Beachfront Suite, and Luxury Pool Villa with dynamic per-night calculations.
    - Trip Enhancement Add-ons: Scuba diving, cliff diving, and travel insurance with instant live total calculation.
  - **Instant Reservation & Voucher Generation (`handlePackageBookingSubmit`):**
    - Form validation for traveler credentials and travel dates.
    - Generates unique reference code `MCK-PKG-XXXX-XXX`.
    - Renders official printable voucher with perforated border.
    - Downloadable plain-text voucher ticket (`downloadPackageVoucher`) and print support (`window.print()`).

### R. User Authentication & Profile Session Management (`#auth-modal`)
- **Files:** [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html) (`#nav-auth-container`, `#auth-modal`, `#auth-toast`), [js/main.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/main.js)
- **Functions:**
  - **Dynamic Authentication Trigger (`openAuthModal` / `closeAuthModal`):**
    - Seamless popup triggered via top navbar "Sign In" button or programmatic events.
    - Backdrop blur and centered card with scale animation.
  - **Dual-Mode Tab Switching (`switchAuthTab`):**
    - Instant tab switching between "Sign In" and "Create Account" without page reloading.
  - **Social SSO Simulation (`handleSocialAuth`):**
    - One-click sign-in options for Google, Facebook, and Apple ID with automatic traveler profile creation.
  - **Sign In Validation (`handleSignInSubmit`):**
    - Validates email and password, extracts user display name, generates avatar initials, and stores session in `localStorage`.
  - **Registration Validation (`handleSignUpSubmit`):**
    - Full client validation with matching password verification, telephone recording, and terms agreement check.
  - **Password Visibility Toggle (`togglePasswordVisibility`):**
    - Interactive eye icon to inspect or hide password inputs.
  - **Forgot Password Handler (`handleForgotPassword`):**
    - Instant password reset prompt with feedback notification.
  - **Persistent Navbar Rendering (`renderAuthNav`):**
    - Checks for active session upon page load.
    - Dynamically swaps between "Sign In" CTA and active user profile button with dropdown menu.
  - **Interactive User Dropdown Menu (`toggleUserDropdown`):**
    - Displays traveler name and email, quick links to Vacation Packages, Flights, and Buses, plus a one-click Sign Out action.
  - **Toast Notification Engine (`showAuthToast`):**
    - Displays non-blocking success, error, or info feedback pills with auto-dismiss timers.

### S. Brand Identity, About Us Showcase & Core Pillars (`#about`)
- **Files:** [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html) (`#about`), [css/style.css](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/css/style.css)
- **Functions & Visual Components:**
  - **Section Placement & Navigation Integration:**
    - Positioned in the final part of the page content between Traveler Reviews (`#reviews`) and Footer (`#contact`).
    - Top navigation `ABOUT` link smoothly scrolls directly to `href="#about"` (`scroll-mt-20`) from anywhere on the page.
    - Updated cross-page links in `bus-booking.html` (`index.html#about`) and footer quick links (`#about`).
  - **Hero Story Showcase:**
    - Displays authentic handwritten brush cursive typography for `"Mckanes Travels and Tour."` via Google Font `Caveat`.
    - Features company mission subtitle `"Your Journey, Our Priority"` and full brand storytelling paragraph.
    - Includes inline flight loop SVG depicting dashed heart path with an airborne plane icon.
  - **Dynamic 3-Polaroid Interactive Collage:**
    - Features 3 tilted photo frames showcasing high-definition Coron island lagoon (`images/about_lagoon_hd.jpg`), sunset flight wing (`images/about_plane_hd.jpg`), and mountain summit explorer (`images/about_traveler_hd.jpg`).
    - Hand-drawn script annotation: `"Explore"`, `"Discover"`, `"Create Memories ♡"`.
    - Interactive 3D hover physics: untwists angle (`rotate-0`), scales up (`scale-105`), lifts (`translateY(-6px)`), and deepens shadow.
  - **Triple Pillar Mission, Vision & Values Strip:**
    - Warm ivory backdrop (`#fbf8f2`) with 3 distinct glyph badges:
      - **Mission Badge:** Target icon (`fas fa-bullseye`) explaining dedication to safe, reliable, and accessible travel.
      - **Vision Badge:** Eye icon (`fas fa-eye`) highlighting the goal to become the top trusted travel agency in tourism.
      - **Values Badge:** Heart icon (`fas fa-heart`) with interactive 5-point checkmark list (Customer First, Integrity, Reliability, Excellence, Passion for Travel).
  - **Why Choose Us Feature Pillars:**
    - Headline `"More Than Just a Trip"` with dedicated brand promise copy.
    - 4 hover-responsive circular feature modules:
      1. Customized Travel Packages (`fas fa-plane`).
      2. Safe & Reliable Travel (`fas fa-shield-alt`).
      3. Expert Travel Assistance (`fas fa-users-cog`).
      4. Affordable Rates (`fas fa-tag`).

### T. Complete Admin Operations Portal & Central Management Engine (`admin.html`)
- **Files:** [admin.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/admin.html), [js/admin.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/admin.js), [css/admin.css](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/css/admin.css)
- **Functions & Modules:**
  - **Live Executive Dashboard (`#tab-dashboard`):**
    - Dynamic KPI calculation: Total Revenue (`₱4,829,450`), Total Bookings (`1,284`), Passengers Served (`3,890`), and Customer Satisfaction rating (`4.9/5.0`).
    - Dynamic revenue trend bar chart for 2026 and visual transit share distribution bars.
    - Live feed of latest booking transactions with status tags and detail inspect actions.
  - **Enterprise Bookings Manager (`#tab-bookings`):**
    - **1-Click Status Popover:** Interactive dropdown on each booking row badge to transition directly between `Confirmed`, `Pending`, `Completed`, and `Cancelled` with instant stats recalculation and toast feedback.
    - **Multi-Column Sorting:** Sort by `Booking Ref`, `Lead Passenger`, `Travel Date`, `Total Amount`, or `Status` (ascending/descending toggle with indicator chevrons).
    - **Configurable Pagination:** Page navigation controls (`5 | 8 | 15 | All` rows per page), dynamic page numbers, previous/next shortcuts, and record counter.
    - **Quick Status Filter Chips:** Filter bar with live record counter badges (`All`, `Confirmed`, `Pending`, `Completed`, `Cancelled`).
    - **Bulk Action Operations Bar:** Row selection with master checkbox and floating bottom action bar for bulk status modification, bulk CSV export, and bulk deletion.
    - **Live Search & Instant Clear:** Search by reference, passenger, email, route, or operator with instantaneous `✕` clear button.
    - **Edit Booking Modal:** Ability to update passenger name, email, phone, date, seat, and amount directly.
    - **E-Ticket Passenger Manifest:** Printable modal view with `@media print` layout for on-counter ticketing.
    - **Manual Booking Generation:** Quick modal form for counter walk-ins and telephone reservations.
    - **CSV Export Engine:** Generates clean, downloadable `mckanes_bookings_YYYY-MM-DD.csv` spreadsheets.
  - **Global Header Operations Bar:**
    - Live digital clock syncing with local time.
    - Global quick search with real-time dropdown autocomplete across reservations, tour packages, and VIP travelers.
    - Interactive Notification Center with unread badge counter and "Mark all read" function.
    - Quick shortcut button to "+ New Booking" and deep links to public flight and bus engines.
  - **Tour Packages Inventory Manager (`#tab-packages`):**
    - Live capacity meter displaying booked slots vs limit per package.
    - Active/Paused package availability toggle.
    - Interactive pricing prompt to update package base rate per passenger.
  - **Fleet & Schedule Dispatcher (`#tab-fleet`):**
    - Sub-tabbed directory for active Provincial Bus Lines and Domestic Commercial Flight routes.
  - **Traveler & VIP Customer Directory (`#tab-customers`):**
    - Comprehensive directory displaying loyalty tier classification, completed trips, and total spend.
  - **Customer Inquiries Desk (`#tab-inquiries`):**
    - Central inbox for messages received via the public site contact form with reply modal, status progression (`Pending` ➔ `Replied` ➔ `Resolved`), and direct mailto links.
  - **Promo Codes & Campaign Manager (`#tab-promos`):**
    - Active promo vouchers catalog with redemption tracking and new promo code generation form.
  - **Agency Settings & Database Utilities (`#tab-settings`):**
    - Official licensing credentials, fee parameters, agency contact form persistence in `localStorage`, and local database backup/reset utilities.
  - **Admin Authentication & Staff Security Gate (`#admin-auth-screen`):**
    - Secure modal login gate blocking unauthorized access to operational data with streamlined typography and status badge.
    - Authorized Staff Credentials:
      - **User:** `Mckanes@123` (case-tolerant)
      - **Password:** `chibiba` (trimmed, case-tolerant matching `chibiba` or `Chibiba`)
    - Visibility & Layout Reliability: Enforced with `#admin-auth-screen.hidden { display: none !important; ... }` and JavaScript `.style.setProperty('display', 'none', 'important')` to prevent flex layout conflicts from blocking access.
    - Live error banner with `.shake-error` animation on incorrect inputs.
    - Password visibility toggle (`fas fa-eye` / `fas fa-eye-slash`).
    - One-click "Apply" credential helper button (`autofillAdminCredentials(true)`) for instant prefill and console unlock.
    - Floating toast notifications elevated to `z-[120]` for clean readability above all overlays.
    - Persistent session state via `mckanes_admin_logged_in` and `mckanes_admin_session`.
    - Instant Console Lock / Sign Out controls in sidebar and header.
    - Cross-platform integration: logging in with `Mckanes@123` / `chibiba` on `index.html` marks user as `Staff` and auto-redirects to `admin.html`.
  - **Cross-Platform Integration:**
    - Deep-linked from public navbar user profile dropdown (`js/main.js`), footer Quick Links (`index.html`), and header bars of `bus-booking.html` and `plane-booking.html`.

### U. Client Booking Authentication Gate & Pop-up Modal (`#auth-required-modal`)
- **Files:** [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html), [js/main.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/main.js), [js/bus-booking.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/bus-booking.js), [js/plane-booking.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/plane-booking.js)
- **Features & Logic:**
  - **Booking Gate Requirement:** Prevents clients from booking tickets or entering ticketing workflows without an authenticated session (`mckanes_user`).
  - **Interception Pop-up (`#auth-required-modal`):**
    - Contextual alert highlighting specific booking target (Flight, Bus, or Vacation Package).
    - Explains 3 key benefits: Digital Boarding Pass / E-Ticket delivery, live schedule updates, and PNR profile tracking.
    - One-click trigger for Sign In or Account Creation.
  - **Destination Preservation (`pendingBookingRedirect`):**
    - Stores the client's intended destination prior to sign-in.
    - Upon successful login or registration, automatically resumes and forwards the user to their chosen reservation engine (`plane-booking.html`, `bus-booking.html`, or package modal).
  - **Comprehensive Safety Across Standalone Booking Engines:**
    - `bus-booking.js` and `plane-booking.js` verify session at checkout submission, ensuring 100% data integrity and account ownership for all reservations.

### V. Client-Admin Real-Time Synchronization & Customer Management Suite (`#tab-customers`)
- **Files:** [admin.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/admin.html), [js/admin.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/admin.js), [js/main.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/main.js), [js/plane-booking.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/plane-booking.js), [js/bus-booking.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/bus-booking.js)
- **Features & Capabilities:**
  - **Live Client Activity Synchronization:**
    - Whenever a client signs in (`handleSignInSubmit`), signs up (`handleSignUpSubmit`), or uses social demo auth (`handleSocialAuth`) on `index.html`, their account is instantaneously updated or created in the central admin directory (`mckanes_admin_customers`).
    - Stamped with real-time metadata: `lastActive`, status set to `Online`, and `loginCount` incremented.
    - Automated staff alert dispatched to `mckanes_admin_notifications` announcing traveler presence.
    - Client sign-out (`handleSignOut`) marks the status back to `Standard`.
  - **Real-Time Cross-Tab Reactivity:**
    - Utilizes HTML5 `storage` event listeners (`window.addEventListener('storage', ...)`).
    - If the Admin Operations Portal is open in another tab or monitor, customer listings, online counter badges, and notification center items update instantly without manual page refreshing.
  - **End-to-End Reservation Revenue & Metric Linking:**
    - Across all 3 booking engines (Vacation Packages in `main.js`, Flight Reservations in `plane-booking.js`, and Bus Tickets in `bus-booking.js`):
      - Saves the booking record into `mckanes_admin_bookings`.
      - Locates the client by email or full name in `mckanes_admin_customers` and automatically increments `trips` (+1), adds the transaction value to `totalSpend`, updates `lastActive`, and automatically recalculates loyalty tiers (`Silver` at ₱10,000, `Gold VIP` at ₱25,000, and `Platinum VIP` at ₱60,000).
      - Posts immediate booking notifications to the admin activity feed.
  - **Admin Customer CRM & Directory Management:**
    - **Live Dashboard Cards:** Real-time counters for *Total Clients*, *Online / Active Now* (with animated pulse beacon), *VIP Members*, and *Lifetime Spend*.
    - **Advanced Search & Filtering:** Real-time full-text search across Client ID, Name, Email, Phone, and City, plus multi-criteria filters for Loyalty Tier and Activity Status.
    - **Dynamic Sorting:** Sort by Recently Active, Total Spend, Most Trips, or Alphabetical Name.
    - **Customer Inspection Dossier (`#view-customer-modal`):**
      - Inspect full traveler contact details, location, and lifetime statistics.
      - Dynamic reservation manifest displaying all flights, buses, and vacation packages booked under that traveler's account.
      - Admin confidential notes box with immediate local persistence.
      - 1-Click `mailto:` communication action.
    - **Customer Form Management (`#customer-form-modal`):**
      - Register walk-in clients directly through the admin portal.
      - Edit existing client details, loyalty tiers, trip counts, or spending records.
    - **Directory Export (`exportCustomersCsv`):**
      - One-click CSV export generating a downloadable spreadsheet manifest of all registered travelers.
    - **Account Safeguards (`deleteCustomer`):**
      - Confirmation dialog protecting client records from accidental deletion.

### W. Mock Accounts Purge & Chibiba Admin Persistence
- **Files:** [admin.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/admin.html), [js/admin.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/admin.js), [js/main.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/main.js)
- **Features & Capabilities:**
  - **Complete Removal of Mock Customer Accounts:**
    - Purged all 7 mock accounts (`Juan Dela Cruz`, `Maria Santos`, `Roberto Lim`, `Dr. Angela Reyes`, `Joshua Mendoza`, `Patricia Gomez`, `Kenneth Bautista`) from `DEFAULT_CUSTOMERS`.
    - Added automated self-cleaning startup routines in both `admin.js` and `main.js` that detect and purge old mock account artifacts from `localStorage` (`mckanes_admin_customers` and `mckanes_user`).
  - **Preservation of Chibiba Admin Account:**
    - Kept the primary authorized administrator profile `ADMIN-01` (`Mckanes Admin (Chibiba)`) with username `Mckanes@123` and password `chibiba`.
    - Updated login validation to allow entering either `Mckanes@123` or `chibiba` as username, with password `chibiba`.
    - Updated sidebar admin badge to `CH` avatar initials with title `Mckanes Admin (Chibiba)` (`Operations Director`).
    - Clean slate customer directory prepared for live client accounts.

### X. Streamlined Authentication Modal (Social Accounts Removal)
- **Files:** [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html), [js/main.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/main.js)
- **Features & Logic:**
  - **Social Logins Removal:** Removed third-party social auth buttons ("Continue with Google", "Facebook", "Apple ID") and the intermediate "or email" divider from `#modal-auth`.
  - **Focused Credentials Access:** Users directly authenticate with their email address and password, or administrator ID (`Mckanes@123` or `chibiba`), eliminating mock social demo interactions.
  - **Clean Tab Transitions:** Instant switching between `Sign In` and `Create Account` without layout shifting or social button clutter.

### Y. Complete Bookings Purge, Dynamic Dashboard & Client Accounts Suite
- **Files:** [admin.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/admin.html), [js/admin.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/admin.js), [js/main.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/main.js)
- **Features & Capabilities:**
  - **Complete Purge of Fake Mock Bookings:**
    - Purged all 12 hardcoded/seeded bookings from `DEFAULT_BOOKINGS` in `js/admin.js`.
    - Implemented self-cleaning startup routines in `getBookings()` and `DOMContentLoaded` in both `admin.js` and `main.js` that detect and strip legacy mock booking IDs (`MCK-FL-2891`, `MCK-BUS-8492`, `MCK-PKG-4819`, etc.) from browser `localStorage` (`mckanes_admin_bookings`).
    - The Bookings Master Directory starts completely clean and dynamically populates only with real bookings made on `index.html` (packages), `plane-booking.html` (flights), `bus-booking.html` (buses), or created by Admin via "+ New Booking".
  - **Complete Purge of Fake Mock Inquiries:**
    - Purged `DEFAULT_INQUIRIES` in `js/admin.js` and cleared stale entries from `localStorage` (`mckanes_admin_inquiries`).
  - **Dynamic Real-Time Dashboard Metrics:**
    - Replaced hardcoded KPI additions (`+ 4250000`, `+ 1272`, `+ 3820`) in `renderDashboard()`.
    - Total Revenue, Total Bookings, and Total Passengers are calculated directly from confirmed bookings with clean zero-state display.
    - Recent bookings feed displays an empty state card when no bookings exist.
  - **Client Accounts Database & Password Verification (`mckanes_registered_accounts`):**
    - Client Sign Up on [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html): Enforces password length check (>=4 chars), checks email duplication against `mckanes_registered_accounts`, saves full account with password, creates customer profile in `mckanes_admin_customers`, and logs user in.
    - Client Sign In on [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html): Authenticates entered email and password against `mckanes_registered_accounts` (or `mckanes_admin_customers`). Rejects invalid credentials with clear toast alerts.
    - Admin Credentials Bypass: Retains `Mckanes@123` or `chibiba` with password `chibiba` to launch admin console.
    - Client Sign Out: Marks client status as `Offline` across both `mckanes_admin_customers` and `mckanes_registered_accounts`.
  - **Full Admin Control Over Logins & Accounts (`#tab-customers`):**
    - **View Password:** `#view-customer-modal` includes an Account Password row (`#view-cust-password`) displaying the registered client's password.
    - **Edit Password & Status:** `#customer-form-modal` includes an Account Password field (`#cust-form-password`) and expanded status options (`Online`, `Offline`, `Active`, `Standard`, `Suspended`). Modifying a client updates both `mckanes_admin_customers` and `mckanes_registered_accounts`.
    - **Account Deletion:** Deleting a customer in `#tab-customers` cleans out their record in both directories and clears their session if currently signed in.
    - **Filter by Status:** Filter by `Online Now`, `Offline`, `Active`, `Standard`, or `Suspended`.




### Z. Bookings Master Directory Zero-State, Mock Heuristic Purge & Filter Toggle Engine
- **Files:** [admin.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/admin.html), [js/admin.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/admin.js), [js/main.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/main.js)
- **Features & Capabilities:**
  - **Comprehensive Multi-Vector Mock Purge Engine:**
    - Eradicates all 12 legacy seed mock bookings (`MCK-FL-2891`, `MCK-BUS-8492`, `MCK-PKG-1049`, `MCK-BUS-8504`, `MCK-FL-2895`, `MCK-PKG-1052`, `MCK-BUS-8510`, `MCK-FL-2899`, `MCK-PKG-1055`, `MCK-FL-2902`, `MCK-BUS-8515`, `MCK-BUS-8519`, and their variants) regardless of status (`Cancelled`, `Confirmed`, etc.).
    - Implements triple-attribute matching (`ALL_MOCK_BOOKING_IDS`, `ALL_MOCK_EMAILS`, `ALL_MOCK_NAMES`, and `isMockBooking()`).
    - Automatically cleanses browser `localStorage` on page load in both admin console and client storefront.
  - **Interactive Status Filter Chip Toggles:**
    - Quick status filter chips (`All Bookings`, `Confirmed`, `Pending Payment`, `Completed`, `Cancelled`) support toggle behavior: clicking an active status filter chip switches back to `all`, making filter manipulation fluid and intuitive.
  - **Accurate Zero-Base Counter Badges:**
    - Quick counter chips initialize to `0` in static HTML and update dynamically based on authentic user bookings.
    - Filter record counter displays accurate count (`0 Records`) with proper singular/plural grammar.
    - Pagination summary indicates exact range or `Showing 0 reservations`.
  - **Instant One-Click "Clear Data" Button:**
    - Added `#btn-clear-bookings` (`clearAllTestBookings()`) in the directory toolbar next to "Export CSV" and "+ New Booking".
    - Allows administrators to wipe all test bookings with a confirmation modal, instantly zeroing all metrics.
  - **Context-Aware Dynamic Empty States:**
    - Differentiates between zero overall records (prompts admin to create their first reservation) versus zero filter results (provides a 1-click button to reset all active filters).


### AA. Dedicated Client Sign-In Interface Refinement
- **Files:** [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html), [js/main.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/main.js)
- **Features & Capabilities:**
  - **Strictly Client-Facing Sign-In Modal:**
    - Field label rendered strictly as `Email Address` (omitting admin credentials references).
    - Email field adorned with `fas fa-envelope` icon and standard `you@example.com` placeholder.
    - Added `inputmode="email"` and `autocomplete="email"` for enhanced mobile keyboard and autofill UX.
    - Password field placeholder set to clean `Enter your password` with `autocomplete="current-password"`, removing administrative hints (`e.g. chibiba`).
    - Admin portal footer link refined to `Admin Portal Sign In →`.
  - **Robust Multi-Identifier Staff Authentication:**
    - Retains background administrator access for `Mckanes@123`, `chibiba`, `admin@mckanes.com`, and `chibiba@mckanes.com` without exposing admin hints to public visitors.


### BB. Real-Time Client Presence Heartbeat & Live Activity Engine
- **Files:** [admin.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/admin.html), [js/admin.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/admin.js), [js/main.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/main.js)
- **Features & Capabilities:**
  - **Live Client Activity Heartbeat:**
    - Background pulse (`initClientPresenceHeartbeat()`) executes every 45 seconds while visitors are active on the site, updating `lastActive` timestamps and maintaining live `Online` presence.
    - Interaction-driven pulses (listening to `click`, `scroll`, and `keydown`, throttled to once per 30s) ensure active browsing immediately registers in the admin console.
    - Visibility change listener immediately reconnects presence when the client returns to their browser tab.
  - **Precision Online/Offline Evaluation (`isCustomerOnline`):**
    - Strictly honors `Offline` and `Suspended` states, preventing disconnected users from appearing as active.
    - Evaluates active sessions within a 30-minute threshold, automatically rendering the green `● Active` badge and incrementing the `ONLINE / ACTIVE NOW` counter.
  - **Auto-Refreshing Admin Directory:**
    - 15-second background tick in `admin.js` re-evaluates presence and updates relative timestamps (`Active just now`, `6m ago`, etc.) in real time without page reloads.


### CC. Complete Client Privacy & Admin Portal Isolation
- **Files:** [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html), [plane-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/plane-booking.html), [bus-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/bus-booking.html)
- **Features & Capabilities:**
  - **Zero Public Admin Visibility:**
    - Stripped all public links to `admin.html` across navigation headers, footers, booking authorization gates, and authentication modals.
    - Public visitors strictly interact with traveler registration and booking systems without any visual cues indicating the existence or location of the administrative gateway.
  - **Seamless Staff Access:**
    - Authorized personnel can still log into `admin.html` either by accessing the administrative URL directly or by entering staff credentials (`Mckanes@123` / `chibiba`) on the public sign-in form, which seamlessly unlocks and redirects to the console.


### DD. Customer Profile Experience & Administrative Privilege Barrier
- **Files:** [js/main.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/main.js)
- **Features & Capabilities:**
  - **Strict Customer Non-Privilege Enforcement:**
    - Any traveler account logged in through [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html) is strictly granted standard customer status (`isAdmin: false`).
    - The top navbar profile dropdown contains exclusively traveler services (`Vacation Packages`, `Flight Tickets`, `Bus Tickets`, and `Sign Out`).
    - Administrative operations links, "Staff" tags, and shield icons are completely removed from the customer dropdown menu.


### EE. Dynamic Flight Ticket Route Synchronization Engine
- **Files:** [plane-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/plane-booking.html), [js/plane-booking.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/plane-booking.js)
- **Features & Capabilities:**
  - **Full Dual-Leg Ticket Code Synchronization:**
    - Selecting an origin (e.g. `Puerto Princesa (PPS)`) and destination (e.g. `Boracay/Caticlan (MPH)`) immediately updates all visual elements on the golden boarding pass cards:
      - Departure Flight Ticket: Origin code (`#depart-code-text`), origin city (`#summary-depart-city`), departure terminal (`#depart-terminal-text`), destination code (`#dest-code-text`), destination city (`#summary-dest-city`), arrival terminal (`#arrive-terminal-text`).
      - Return Flight Ticket: Inbound origin code (`#return-depart-code-text`), destination code (`#return-dest-code-text`), inbound cities, and terminals.
  - **Contextual Schedule & Modal Previews:**
    - Synchronizes the Trip Summary header, route image thumbnail, Step 3 Review Modal ticket preview, and the Final Electronic Boarding Pass modal with the exact selected airport codes.


### FF. Custom Confirmation & Modal Dialog Architecture (Zero Native Popups)
- **Files:** [admin.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/admin.html), [js/admin.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/admin.js), [plane-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/plane-booking.html), [js/plane-booking.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/plane-booking.js), [bus-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/bus-booking.html), [js/bus-booking.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/bus-booking.js)
- **Features & Capabilities:**
  - **Complete Elimination of Browser Native Dialogs:**
    - Eradicated all browser-native `confirm()`, `alert()`, and `prompt()` popups across the entire application.
  - **Admin Operations Custom Modal (`#admin-confirm-modal`):**
    - High-elevation (`z-[115]`) backdrop blur overlay with animated scale-in card transitions (`scale-95 opacity-0` -> `scale-100 opacity-100`).
    - Configurable icon badges (lock, trash, database, exclamation, tag), title, message, cancel, and action buttons.
    - Integrated optional input prompt field for updating package rates inline without browser prompts.
    - Keyboard accessibility: `Escape` key dismisses modal; `Enter` key confirms action.
    - Backdrop click-outside listener automatically resolves as false.
    - Powers Admin Logout (`logoutAdmin()`), Bulk Deletion (`bulkDelete()`), Single Reservation Deletion (`deleteBooking()`), Test Bookings Purge (`clearAllTestBookings()`), Package Rate Editing (`editPackagePrice()`), Client Directory Removal (`deleteCustomer()`), and Factory Database Reset (`resetLocalDatabase()`).
  - **Ticketing & Booking Notice Modals (`#plane-notice-modal`, `#bus-notice-modal`):**
    - Modern, styled modal popups for airport selection warnings (same origin and destination) and guest booking authorization prompts ("Sign In Now" / "Stay on Page").


### GG. Optimized Flight Date Picker Engine
- **Files:** [plane-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/plane-booking.html), [js/plane-booking.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/plane-booking.js)
- **Features & Capabilities:**
  - **Click-Anywhere Interactive Card Activation:**
    - Wrapped Departure Date and Return Date in tactile card containers (`#depart-date-container`, `#return-date-container`) invoking `triggerDatePicker()`.
    - Leverages modern `input.showPicker()` API to instantly summon the calendar popup from any click coordinate across the card.
  - **Timezone-Safe Local Parsing:**
    - Utilizes `parseLocalDate()` to eliminate UTC midnight discrepancies, ensuring selected dates never shift by one day in negative UTC offsets.
  - **Dynamic Multi-Level Synchronization:**
    - Updates date strings, day-of-week subtitles (`#depart-day-display`, `#return-day-display`), trip summary manifest badges, flight card legs, search results schedule subtitles, and boarding pass modal previews.
  - **Smart Round-Trip & One-Way Management:**
    - When one-way is active, dimming the return date card with an informative "No return flight (Click to add return)" state; clicking automatically re-enables round-trip and opens the calendar.
    - Automatic `min` date bounding clamping return date to departure date and departure date to today's date.


### HH. Place-Specific Scenic Photography Engine for Flight and Bus Bookings
- **Files:** [plane-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/plane-booking.html), [js/plane-booking.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/plane-booking.js), [bus-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/bus-booking.html), [js/bus-booking.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/bus-booking.js)
- **Features & Capabilities:**
  - **Authentic, High-Resolution Destination Photography Pipeline:**
    - Replaced generic and duplicate stock images with authentic local photography corresponding directly to each specific airport and destination:
      - `CEB` (Cebu): Bantayan Island white beach, crystal turquoise water, and traditional outrigger boats (`images/cebu.jpg`).
      - `MPH` (Boracay / Caticlan): World-renowned White Beach sunset with silhouette paraw sailboats (`images/boracay.jpg`).
      - `IAO` (Siargao): Siargao surfing coastline with leaning coconut palm swing and coral reef (`images/siargao.jpg`).
      - `PPS` (Puerto Princesa / Palawan): Iconic Coron towering karst limestone cliffs and emerald lagoons (`images/coron.jpg`).
      - `DVO` (Davao): Dahican sweeping golden beach, emerald surf, and coastal mountain horizons (`images/davao.jpg`).
      - `MNL` (Manila): Historic Manila Bay golden sunset with maritime vessels and harbor reflections (`images/manila.jpg`).
      - `ILO` (Iloilo): Islas de Gigantes turquoise lagoon, carved rock formations, and coconut palms (`images/iloilo.jpg`).
  - **Dynamic Route & Location Synchronization:**
    - Changing destination airport dropdown (`#dest-select`) or swapping route origins and destinations (`swapAirports()`) dynamically swaps the card image (`#summary-dest-img`), alt accessibility description, and destination pill badge (`#summary-dest-tag`).
    - Integrated smooth CSS opacity transitions ensuring fluid visual handoffs as destination images change.
    - Added resilient offline-first architecture with high-resolution CDN fallback links (`DEST_ONLINE_FALLBACKS`) if relative paths ever disconnect.
  - **Provincial Bus Trip Image Dynamism:**
    - Mapped provincial destinations (`Baguio City`, `Vigan`, `La Union`, `Sagada`, `Batangas Pier`, `Manila`) to authentic scenic assets (`images/baguio.jpg`, `images/vigan.jpg`, `images/la_union.jpg`, `images/banaue.jpg`, `images/batangas.jpg`, `images/manila.jpg`) inside `BUS_DEST_IMAGES`.
    - Automatically updates `#summary-img` whenever destination selection changes in the dropdown or via origin/destination swap.


### II. Luxury Executive Lock Screen for Admin Operations Portal
- **Files:** [admin.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/admin.html), [js/admin.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/admin.js), [css/admin.css](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/css/admin.css)
- **Features & Capabilities:**
  - **Ambient Travel Stage & Cyber Grid Backdrop:**
    - Replaces the plain black screen with a layered, luxury ambient setting featuring a subtle blurred scenic Philippine backdrop (`images/hero_bg.jpg`), deep navy gradient vignettes (`from-[#050914] via-[#091122]/95 to-[#060b18]`), cyber dot matrix overlay, and multi-tone illuminated gradient orbs.
  - **Frosted Glassmorphism Console (`#admin-login-card`):**
    - High-elevation glass card (`bg-slate-900/85 backdrop-blur-2xl border border-white/10`) with top luminous accent light line and deep ambient glow shadow.
  - **Security Emblem & Status Pill:**
    - 3D security shield icon badge with glowing blur halo and amber locked status icon.
    - Real-time pulse indicator badge: `● CONSOLE LOCKED • ENCRYPTED GATE`.
  - **Ergonomic Staff Authentication Form:**
    - Clean micro-labeled inputs (`Staff Identity`, `Security Key`) with focus rings and tactile icons.
    - Interactive password reveal toggle button (`#admin-login-pass-icon`).
    - Luminous gradient unlock CTA (`#admin-login-submit-btn`) with active spring physics.
  - **Executive Smart Keycard Module:**
    - Eliminates raw debug text in favor of an executive NFC-style smart keycard:
      - `CH` executive avatar and `Director` verified badge for Chibiba.
      - Masked credential indicator (`Mckanes@123 • ••••••••`).
      - Interactive `[ ⚡ 1-Click Unlock ]` button that automatically fills credentials and unlocks the operations console instantly.
    - Security encryption notice (`TLS 1.3 • 256-Bit`) alongside a streamlined "Return to Public Website" navigation link.


### JJ. Cebu & Bohol Scenic Destination Package Visuals & Flight Service Asset Separation
- **Files:** [data/packages.json](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/data/packages.json), [js/main.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/main.js), [js/admin.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/admin.js), [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html)
- **Features & Capabilities:**
  - **Authentic Island Boardwalk & Banca Photography:**
    - Replaced the commercial airplane tarmac photo previously shown on the "Cebu & Bohol Twin Island Wonder Vacation" card with a high-resolution, picturesque tropical photograph (`images/cebu_bohol.jpg`) capturing a wooden pier boardwalk, thatched gazebo hut, crystalline turquoise waters, and traditional Philippine outrigger banca boat.
  - **Flight Service Card Image Preservation:**
    - Dedicated the original commercial Cebu Pacific airplane asset to `images/cebu_plane.jpg`, specifically maintaining the aviation theme for the "Book A Plane Ticket" card in the primary Services directory on `index.html`.
  - **Resilient Multi-Store Backward Compatibility:**
    - Injected the new scenic boardwalk photograph simultaneously into `images/cebu_bohol.jpg` and `images/cebu_pacific.jpg`.
    - Synchronized package catalogs across static JSON (`data/packages.json`), client-side package registry (`js/main.js`), and admin master directory (`js/admin.js`), ensuring unified visuals whether rendered directly or dynamically from localStorage.


### KK. Admin Lock Screen Flight Operations Radar Background & Anti-Bleed Isolation
- **Files:** [admin.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/admin.html), [js/admin.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/admin.js), [css/admin.css](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/css/admin.css)
- **Features & Capabilities:**
  - **100% Anti-Bleed Dashboard Isolation:**
    - Enforced an opaque base container (`bg-[#030712]`) on `#admin-auth-screen`, completely preventing the underlying dashboard, charts, tables, and KPIs from ghosting or bleeding through when the operations console is locked.
  - **Cinematic High-Altitude Flight Horizon:**
    - Showcases an evocative golden hour airplane wing soaring above cloud decks (`images/about_plane_hd.jpg`), veiled in midnight sapphire and deep obsidian gradients with subtle luminous ambient lighting.
  - **Interactive Flight Radar & Airspace Trajectory Network:**
    - Features a precision SVG airspace network displaying rotating radar sweep beams (`@keyframes radarSweep`), glowing flight corridor paths (`@keyframes flightPulse`), and waypoint beacons for Manila (`MNL`), Cebu (`CEB`), Davao (`DVO`), Boracay (`MPH`), and Palawan (`PPS`).
  - **Real-Time Philippine Standard Time (PST UTC+8) Live Clock:**
    - Displays a real-time live digital clock in the top telemetry HUD bar synchronized every second with `Asia/Manila` time.
  - **Corporate Operations Telemetry HUD Chrome:**
    - Integrates a top operational control bar and bottom dispatch ticker indicating system encryption, air traffic status, station security identifiers, and session auditing.


### LL. Elimination of 1-Click Unlock Shortcut & Strict Admin Credential Gating
- **Files:** [admin.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/admin.html), [js/admin.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/admin.js)
- **Features & Capabilities:**
  - **Removal of 1-Click Unlock Keycard:**
    - Eradicated the demo credentials display card and `[ ⚡ 1-Click Unlock ]` button from the modal footer, ensuring unauthorized observers cannot bypass the password gate with a single click.
  - **Removal of Auto-Fill Trigger:**
    - Removed the "Auto-Fill" shortcut link above the password input, enforcing authentic manual credential authentication.
  - **Streamlined Security Footer:**
    - Cleaned up the modal base to only feature the essential public website return link and the cryptographic `TLS 1.3 • 256-Bit` security badge.


### MM. Complete Isolation of Admin Operations Portal (Public Website Links Eradication)
- **Files:** [admin.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/admin.html)
- **Features & Capabilities:**
  - **Removal of Public Navigation from Lock Screen:**
    - Completely removed the "Return to Public Website" anchor link from `#admin-login-card`, ensuring the administrative entrance functions as an isolated, secure enterprise terminal without exposed back-navigation.
  - **Centered Security Badge:**
    - Re-aligned the security compliance badge (`Authorized Personnel Only • TLS 1.3 • 256-Bit Encrypted Gate`) to a clean, centered layout in the modal base.
  - **Admin Internal Navigation Consistency:**
    - Set the top sidebar logo to link directly within the operational portal (`admin.html`), preventing accidental redirects away from active flight and tour administration.


### NN. Real-Time Tour Package Synchronization Between Admin Console and Public Client Portal
- **Files:** [admin.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/admin.html), [js/admin.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/admin.js), [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html), [js/main.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/main.js)
- **Features & Capabilities:**
  - **Full Executive Package Edit Suite (`#package-edit-modal`):**
    - Provides administrative operators with comprehensive package configuration in `admin.html`:
      - Package Title (`#edit-pkg-name`)
      - Destination Location (`#edit-pkg-dest`)
      - Duration (`#edit-pkg-duration`)
      - Base Rate per Pax in Philippine Peso (`#edit-pkg-price`)
      - Original Strike-Through Price (`#edit-pkg-original-price`)
      - Operational Booking Status (`Active (Open for Clients)` vs `Paused (Seasonal Pause / Full)`)
      - Booked Slots Meter (`#edit-pkg-booked` / `#edit-pkg-capacity`)
  - **Schema & ID Dual Normalization:**
    - Normalizes minor naming discrepancies between admin mock identifiers and client package keys via `altId` mapping (`banaue-heritage` ➔ `baguio-banaue`, `siargao-surf` ➔ `siargao-adventure`, `siquijor-mystique` ➔ `siquijor-haven`, `cebu-bohol-wonders` ➔ `cebu-bohol`).
    - Synchronizes dual properties `pkg.price` and `pkg.basePrice` across both stores.
  - **Dynamic Client Reflection Engine (`getClientVacationPackages()`):**
    - Retrieves persisted admin updates from `localStorage.getItem('mckanes_admin_packages')` and seamlessly overlays updated prices, names, durations, destinations, and availability onto the client-facing catalog (`VACATION_PACKAGES`).
    - Automatically recalculates dynamic discount badges (`Save X%`) according to revised base and original prices.
  - **Responsive State Indicators & Booking Protection:**
    - Renders an amber `⏸ Temporarily Paused` badge and switches the primary booking action to a dedicated `Paused` status button whenever an administrator pauses a tour package, preventing unauthorized checkout while keeping itinerary details accessible.
  - **Live Cross-Tab & Cross-Window Synchronization:**
    - Binds window `storage` and `packageDataUpdated` listeners in `js/main.js`. Editing or pausing any vacation package in the Admin Portal instantaneously updates the client-facing grid on `index.html#packages` across separate tabs or windows without requiring a page reload.


### OO. Passenger Form Layout Streamlining & Redundant Navigation Bar Eradication
- **Files:** [plane-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/plane-booking.html), [js/plane-booking.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/plane-booking.js)
- **Features & Capabilities:**
  - **Removal of Redundant Passenger Card Bottom Strip:**
    - Eradicated the duplicate action bar situated at the base of `#card-passenger-info` containing the `< Back to Flight Details` link and auxiliary `Continue to Review ->` button.
  - **Clean Form Boundary:**
    - Allowed the passenger input card to terminate cleanly after the contact information fields and dynamic validation warning alert.
  - **Unified Checkout CTA:**
    - Funnels travelers exclusively to the primary `Continue to Review ➔` button in the sticky Trip Summary sidebar (`Your Trip Summary`), eliminating duplicate click targets and reinforcing consistent user flow across flight checkout.

### PP. Dynamic Traveler Identity, Accurate Fare Recording, and Real-Time Admin Booking Pop-Up
- **Files:** [plane-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/plane-booking.html), [js/plane-booking.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/plane-booking.js), [bus-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/bus-booking.html), [js/bus-booking.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/bus-booking.js), [admin.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/admin.html), [js/admin.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/admin.js)
- **Features & Capabilities:**
  - **Real-Time Cross-Tab Live Booking Alert Banner (`#admin-live-booking-alert`):**
    - High-visibility frosted alert card sliding into the top-right viewport of `admin.html` immediately upon booking creation in any client tab/window.
    - Displays pulsing live reservation beacon (`animate-ping`), traveler name, email, route/service description, total transaction amount, and direct "View Details →" modal trigger.
    - Synthesizes a crisp, two-tone audio alert chime (`playBookingChime()`) using Web Audio API without external audio file dependencies.
  - **Recent Booking Transactions Highlighting:**
    - The top recent booking row in `#dashboard-recent-tbody` renders with an emerald highlight gradient (`bg-gradient-to-r from-emerald-50/70 via-teal-50/30 to-transparent`), bold left accent border (`border-l-4 border-l-emerald-500`), and animated "NEW" pill badge (`bg-emerald-500 text-white`).
    - Displays traveler name, contact email, phone number, flight/bus/tour badge, exact amount, and operational status.
  - **Dynamic Traveler Identity Resolution & Pre-Filling:**
    - Automatically populates lead passenger first name, last name, email, and mobile number from `localStorage.getItem('mckanes_user')` on page load.
    - Removed hardcoded "Juan Cruz" and placeholder contact values from HTML forms in `plane-booking.html` and `bus-booking.html`.
    - Live-updates summary card traveler tags and digital boarding pass/ticket passenger lines upon keystroke.
  - **Outer-Scoped Fare Calculation & Zero-Fare Auto-Repair:**
    - Corrected variable scoping in `js/plane-booking.js`, guaranteeing `recordFlightBookingToAdmin()` always records the calculated fare (e.g. `₱3,470`).
    - Implemented self-healing sanitizer in `js/admin.js` (`getBookings()`) converting any historical `₱0` test records to standard route fares.

### QQ. Executive E-Ticket Manifest Modal Enhancement & 100% Viewability Optimization
- **Files:** [admin.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/admin.html), [js/admin.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/admin.js), [plane-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/plane-booking.html), [js/plane-booking.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/plane-booking.js), [bus-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/bus-booking.html), [js/bus-booking.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/bus-booking.js)
- **Features & Capabilities:**
  - **Expanded Executive Layout Dimensions:**
    - Replaced the cramped `max-w-lg` container with an executive wide `max-w-3xl w-full max-h-[92vh] flex flex-col` modal box, allowing travelers, flight operations, seat allocations, baggage, and billing to be viewed comprehensively at a single glance without claustrophobic scrolling.
  - **Non-Overlapping Flex Header Architecture:**
    - Decoupled the status selection dropdown from the circular close (`✕`) button into clean flexbox siblings, completely eliminating the visual obstruction and click conflict present in legacy versions.
    - Added dynamic status theme styling (emerald for Confirmed, amber for Pending, blue for Completed, rose for Cancelled).
    - Resolved missing "Booked on " timestamp with formatted date/time strings (`Oct 18, 2026, 10:45 PM`) and automatic self-healing fallback for legacy records.
  - **High-Visibility Lead Traveler Dossier Card:**
    - Features a 2-letter uppercase initials circular badge (`JC`, `MS`), Lead Traveler role badge, dynamic passenger count pill (`1 Passenger` / `X Passengers`), and clickable `mailto:` and `tel:` links with icons.
  - **2-Column Itinerary & Inclusions Manifest Grid:**
    - **Column 1 (Journey & Carrier Route):** Service title, carrier name, origin/destination route arrow, and scheduled travel date.
    - **Column 2 (Seating, Cabin & Baggage Inclusions):** Seat assignment chip (`12A (Window)`), cabin tier (`Economy Class`), and baggage allowances (`20kg Checked + 7kg Hand-carry Included`).
  - **Full-Width Multi-Line Operational Directives Textarea:**
    - Replaced the single-line truncated `<input>` with a 3-row expandable `<textarea id="modal-booking-notes">` displaying complete PNRs, booking codes, and staff directives with zero clipping.
    - Equipped with one-click quick tag buttons (`+ VIP`, `+ Baggage OK`, `+ Priority`, `+ Assistance`) and a dedicated `Save Notes` button with instant admin toast confirmation.
  - **Financial Settlement Box & Verified Transaction Stamp:**
    - Formatted payment breakdown with payment channel tag (`GCASH`, `ONLINE / COUNTER`), emerald verified badge, and bold high-contrast total amount (`₱3,470`).
  - **Integrated Executive Action Strip:**
    - `Print Official E-Ticket`: Triggers clean print-ready manifest styling via `window.print()`.
    - `Copy Details`: Formats and copies a complete plain-text manifest directly to system clipboard.
    - `Edit Reservation`: Seamlessly transitions to the Edit Booking dialog.
    - `Close`: Gracefully dismisses the modal.

### RR. Authenticated Traveler Account Dynamic Pre-Fill & Modal Synchronization Engine
- **Files:** [bus-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/bus-booking.html), [js/bus-booking.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/bus-booking.js), [plane-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/plane-booking.html), [js/plane-booking.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/plane-booking.js)
- **Features & Capabilities:**
  - **Comprehensive Account Session Resolution Hierarchy:**
    - Intelligently queries multiple storage layers to resolve the authenticated traveler:
      1. `mckanes_user` (active client or administrative session).
      2. `mckanes_admin_session` (authenticated admin director session).
      3. `mckanes_registered_accounts` (client accounts repository with online status matching).
      4. `mckanes_admin_customers` (central CRM database).
      5. Primary verified enterprise profile: `Chibiba Mckanes` (`chibiba@mckanes.com`, `+63 917 123 4567`).
  - **Automated Placeholder Sanitization:**
    - Automatically purges legacy dummy placeholder values ("Juan Dela Cruz", "juan.delacruz@email.com", "+63 912 345 6789") from `localStorage`, replacing them with authentic authenticated account credentials.
  - **Modal Open Dynamic Field Synchronization:**
    - Re-executes session extraction on every modal trigger (`openPassengerModal()`), guaranteeing that newly logged-in accounts immediately pre-fill Passenger 1 First Name, Last Name, Email, and Mobile Number without requiring manual retyping or page reload.
  - **Account Linked & Pre-filled Verification Banner:**
    - Renders `#modal-account-sync-banner` inside the passenger modal with the user's avatar circle, verified account name, email, phone number, and a green `Auto-Filled` pill badge.
    - Renders `#plane-account-sync-banner` in the flight booking passenger section confirming account synchronization.
  - **Top Navigation Active Account Badges:**
    - Displays `#bus-nav-account-pill` and `#plane-nav-account-pill` in top headers with the traveler's avatar initials and full name matching the UX pattern of `index.html`.
 
 
### SS. Global Floating Status Dropdown Portal with Viewport-Aware Smart Auto-Flip
- **Files:** [admin.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/admin.html), [js/admin.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/admin.js)
- **Features & Capabilities:**
  - **Absolute Overflow-Clipping Immunity:**
    - Replaced table cell inline popovers with a global floating dropdown portal (`#global-status-dropdown`) mounted directly to `<body>` at `z-[9999]`.
    - Immune to CSS container clipping (`overflow-x: auto`, `overflow-hidden`), guaranteeing that all status options are 100% visible regardless of table height or row position.
  - **Smart Viewport-Aware Auto-Flip:**
    - Calculates trigger button bounding box (`getBoundingClientRect()`).
    - If distance to viewport bottom is `< 200px` (or when clicking the last row/near screen bottom), automatically flips **UPWARDS** above the trigger pill; otherwise opens **DOWNWARDS**.
    - Clamps horizontal positioning with safe window padding.
  - **Visual Status Manifest & Dynamic Checkmark Indicators:**
    - Displays the active booking reference code in an executive header chip (`#global-status-dropdown-ref`).
    - Highlights the currently active status (`Confirmed`, `Pending`, `Completed`, `Cancelled`) with background fill and checkmark icon (`.status-check-icon`).
  - **Seamless Keyboard & Pointer Accessibility:**
    - Closes immediately on outside click, window scroll, table horizontal scroll, window resize, or `Escape` key press.
    - Selecting an option updates booking records in `localStorage`, refreshes table and dashboard feeds, and triggers instant admin toast confirmation.

### TT. Cloudflare Pages Production Deployment & Global CDN Edge Hosting
- **Production Host:** [Cloudflare Pages](https://pages.cloudflare.com)
- **Live Production URL:** [https://mckanes-travel.pages.dev](https://mckanes-travel.pages.dev)
- **Features & Capabilities:**
  - **Worldwide Anycast Edge Delivery:**
    - Deployed to Cloudflare's ultra-low latency global network across 330+ cities worldwide.
    - All 69 static assets cached and served from edge locations with 0ms cold starts.
  - **Full Automated SSL/TLS Encryption:**
    - Zero-configuration HTTPS using modern TLS 1.3 cryptographic suites and automatic HTTP-to-HTTPS redirect.
  - **Independent Routing Architecture:**
    - Clean top-level routing across all platform modules:
      - Main Public Portal: `/` & `/index.html`
      - Flight Reservation Engine: `/plane-booking.html`
      - Bus Ticketing System: `/bus-booking.html`
      - Administrative Operations Console: `/admin.html`
  - **Asset Optimization:**
    - Brotli & Gzip compression enabled automatically on edge.
    - High-resolution photography, Web Audio sound generators, and SVG vectors delivered with HTTP/2 and HTTP/3 multiplexing.
 
### UU. Vacation Package Client Booking Engine & Real-Time Admin Synchronization
- **Files:** [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html), [js/main.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/main.js), [admin.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/admin.html), [js/admin.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/admin.js)
- **Features & Capabilities:**
  - **Account Identity & Pre-fill Engine:**
    - Resolves active traveler identity (`getSignedInTravelerForPackage()`) across active client session, admin session, registered accounts repository, and customer records.
    - Automatically pre-fills Lead Traveler First Name, Last Name, Email, and Phone number.
    - Displays `#pkg-account-sync-banner` with traveler avatar initials, full name, contact details, and a green `Verified` pill badge.
  - **Frictionless Booking & Guest Onboarding:**
    - Removes blocking gates for guests; automatically provisions and stores user profile on booking submission without data loss.
    - Generates standardized reference code `BK-PKG-XXXXXX`.
  - **Full Lifecycle Admin Operations Synchronization:**
    - **Bookings Master Directory:** Records the booking into `mckanes_admin_bookings` with ISO `createdAt`, passenger counts, selected room tier, add-ons, computed fare, and `Confirmed` status. Protected from mock purging by explicit `BK-PKG-` whitelist in `isMockBooking()`.
    - **Dashboard Live Alert & Recent Transactions:** Top recent transaction row features animated `NEW` badge and emerald highlight. Triggers live chime alert on open admin dashboards.
    - **Tour Packages Capacity Meter:** Automatically increments `booked` and `bookedSlots` in `mckanes_admin_packages`, dynamically updating progress bar and booked percentage.
    - **Traveler Customer Directory:** Automatically links reservation to traveler profile, increments lifetime trip count, updates total spend, and advances loyalty tier (`Platinum VIP`, `Gold VIP`, `Silver`, `Bronze`).
    - **E-Voucher & Offline Document Generation:** Populates voucher card with real customer name, reference code, travel dates, and guests summary with one-click TXT download (`downloadPackageVoucher()`).

### VV. Guaranteed 1-Page Official Ticket & Boarding Pass Print Architecture
- **Files:** [plane-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/plane-booking.html), [bus-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/bus-booking.html), [admin.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/admin.html), [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html), [css/plane-booking.css](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/css/plane-booking.css), [css/bus-booking.css](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/css/bus-booking.css), [css/admin.css](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/css/admin.css), [css/style.css](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/css/style.css)
- **Features & Capabilities:**
  - **Zero Page Spillover Standard:**
    - Standardized `@page { size: portrait; margin: 8mm 10mm; }` ensuring clean margins on both A4 and US Letter printers.
    - Set `html, body { max-height: 100vh !important; overflow: hidden !important; }` in `@media print` to eliminate extra blank pages.
    - Applied `page-break-inside: avoid !important; break-inside: avoid !important; page-break-after: avoid !important;` to all printable ticket containers.
  - **Flight Boarding Pass Print Optimization (`#printable-boarding-pass`):**
    - Collapses all website navigation, hero, search cards, and footer with `display: none !important;`.
    - Centers the airline boarding pass card with official PNR badge, flight details, passenger name, seat assignment, and scannable barcode.
  - **Bus Transit E-Ticket Print Optimization (`#printable-bus-ticket`):**
    - Isolates the official transit ticket card with operator badge, route codes, departure timestamp, assigned seat, payment receipt, and transit barcode.
  - **Admin E-Ticket Manifest Print Optimization (`#booking-details-modal`):**
    - Suppresses the entire operations dashboard (`main`, `aside`, topbar) during print.
    - Formats the executive manifest into a compact single-page layout with verified transaction details and staff directives.
  - **Vacation Package Voucher Print Optimization (`#printable-package-voucher`):**
    - Isolates the vacation package voucher with resort accommodation, travel dates, guest count, and presentation notice.

### WW. Non-Colliding Responsive Flex Navbar Architecture
- **Files:** [bus-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/bus-booking.html), [plane-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/plane-booking.html), [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html)
- **Features & Capabilities:**
  - **Collision-Proof 3-Column Flexbox Layout:**
    - Replaced unconstrained `absolute inset-x-0` link positioning with a native 3-column flex container:
      1. Brand Identity (`flex-shrink-0`): Locks Mckanes globe icon and typography to the left boundary.
      2. Centered Navigation Links (`flex-1 mx-2 sm:mx-4 hidden lg:flex items-center justify-center`): Dynamically bounds the navigation links to the exact available space between logo and actions, preventing physical layout overlap regardless of screen width.
      3. Action Area (`flex-shrink-0 flex items-center gap-2.5 sm:gap-3`): Houses the traveler account status pill and navigation buttons.
  - **Dynamic Account Pill Responsive Adaptation:**
    - Active account pills (`#bus-nav-account-pill`, `#plane-nav-account-pill`) feature truncated traveler name (`max-w-[120px]`), pulsing green indicator dot, and responsive `hidden 2xl:inline` badge visibility.
    - Prevents horizontal expansion from encroaching upon adjacent navigation items on viewports from 1024px to 1440px.
  - **Enhanced Visual Prominence for Contact Link:**
    - High-visibility styling on `CONTACT` link with `font-bold text-blue-700` and smooth hover transitions.

### XX. Checkout Stepper 1:1 Card Alignment to Hero Banner Image
- **Files:** [plane-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/plane-booking.html)
- **Features & Capabilities:**
  - **1:1 Card Architecture Parity:**
    - Converted checkout stepper into a matching executive card: `<section class="w-full max-w-7xl mx-auto px-4 sm:px-6 mt-3">` enclosing `<div class="bg-white rounded-2xl border border-gray-200/90 shadow-xs py-3 px-5 sm:px-8 flex items-center justify-between">`.
    - Matches the hero graphic banner card (`rounded-2xl`, border, shadow, and `#f8fafc` outer margins) with 100% width and coordinate parity.
  - **Coordinated Grid Guide Rails:**
    - Unifies horizontal grid geometry across:
      - Top Navigation: `<nav class="max-w-7xl mx-auto py-3.5 px-4 sm:px-6 ...">`
      - Hero Graphic Banner: `<section class="... max-w-7xl mx-auto px-4 sm:px-6 ...">`
      - Stepper Card: `<section class="... max-w-7xl mx-auto px-4 sm:px-6 ...">`
      - Main Content Grid: `<main class="max-w-7xl mx-auto px-4 sm:px-6 ...">`
      - Footer: `<div class="max-w-7xl mx-auto px-4 sm:px-6 ...">`
  - **Clean Framing & Inset Breathing Room:**
    - Step 1 `(1) Flight Details`, Step 2 `(2) Passenger Information`, and Step 3 `(3) Review & Payment` are framed within the card with `px-5 sm:px-8`, eliminating visual overflow past the banner's outer boundaries.















### XXI. Dual-Portal Role Selection Gateway (Admin / Client Dynamic Routing)
- **Files:** [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html), [home.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/home.html), [admin.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/admin.html), [plane-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/plane-booking.html), [bus-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/bus-booking.html)
- **Features & Capabilities:**
  - **Dynamic Split-Screen Entry Architecture:**
    - Established `index.html` as the initial landing role selection gateway based directly on user mockup (`media_1792384934391_0a349057.png`).
    - Visitors landing on site root `/` or `index.html` are presented with two distinct interactive portal cards:
      1. **Admin Portal (Left Card):** Deep royal blue `#0156c0` gradient styling, executive character illustration (`role_admin_2x.png`), operational copy, and "Admin Login" action button directing to `admin.html`.
      2. **Client Portal (Right Card):** Royal sky blue `#004eb2` gradient styling, traveler character illustration (`role_client_2x.png`), vacation booking copy, and "Enter Main Page" action button directing to `home.html`.
  - **Preserved Main Travel Portal (`home.html`):**
    - The complete public booking portal is preserved at `home.html` with full fidelity: multi-modal flight and bus booking, vacation package modals, real-time admin sync, customer review carousels, and contact sections.
  - **Bidirectional Cross-Page Shortcuts:**
    - Integrated "Role Portal" / "Switch Role" pills in the headers of `home.html`, `plane-booking.html`, and `bus-booking.html`.
    - Added quick-access links ("Role Gateway" and "Public Site") in the `admin.html` sidebar and login screen footer, ensuring intuitive role switching without URL bar tampering.
  - **High-DPI Retina Graphic Assets:**
    - Extracted and upscaled transparent character assets `role_admin_2x.png` and `role_client_2x.png` with Lanczos resampling, delivering crisp 2x resolution on Retina and 4K displays.


### XXII. Gateway Security Isolation & Forced Admin Authentication Protocol
- **Files:** [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html), [admin.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/admin.html), [js/admin.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/admin.js)
- **Features & Capabilities:**
  - **Decoupled Gateway Session State:**
    - Visiting the public Role Selection Gateway (`index.html`) automatically resets persistent admin authentication tokens (`mckanes_admin_logged_in` and `mckanes_admin_session`) to guarantee that selecting the Admin role always requires affirmative authentication.
  - **Explicit Login Flow (`action=login`):**
    - Clicking "Admin Login" or the Admin card triggers `navigateToAdmin(event)`, sanitizing storage and routing to `admin.html?action=login`.
    - `checkAdminAuth()` in `admin.js` intercepts the login query parameter or gateway referrer, suppressing auto-login and enforcing active presentation of the luxury `#admin-auth-screen`.
  - **Password Field Sanitization:**
    - Password inputs are wiped blank upon screen display, preventing stale cached passwords from auto-submitting.
  - **Console Lockdown on Role Switch:**
    - Clicking "Role Gateway" or "Switch Role" in `admin.html` triggers `goToRoleGateway()`, securely locking the administrative console before navigating to the role selector.
  - **One-Click Staff Demo Credentials:**
    - Features a discreet "Quick Demo Fill" pill (`Mckanes@123` / `chibiba`) on the login screen for rapid staff verification.


### XXIII. Client Role Gateway Decoupling & Prompted Sign In Protocol
- **Files:** [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html), [home.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/home.html), [js/main.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/main.js), [plane-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/plane-booking.html), [bus-booking.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/bus-booking.html)
- **Features & Capabilities:**
  - **Client Gateway Session Decoupling:**
    - Visiting the Role Selection Gateway (`index.html`) resets lingering client authentication tokens (`mckanes_user`) from `localStorage` and `sessionStorage`, ensuring selecting the Client portal never defaults to an already signed-in state.
  - **Prompted Sign In on Arrival (`home.html?action=login`):**
    - Clicking "Client" / "Enter Main Page" routes with `action=login`. `checkClientAuthTrigger()` validates the parameter, renders the top navigation in clean guest mode (`[Role Portal] [Sign In]`), and automatically pops up the `#auth-modal` client authentication dialog with email/password and registration tabs.
  - **Non-Polluting Traveler Sessions:**
    - Refactored `getSignedInTraveler()` in `plane-booking.js` and `getSignedInUserForBus()` in `bus-booking.js` to only read stored users and never fabricate artificial account records, preserving true unauthenticated guest states.
  - **Quick Demo Traveler Pill:**
    - Integrated a one-click sample credentials button (`julie@gmail.com` / `password123`) in the client authentication modal for instant traveler testing.

### XXIV. Role Selection Gateway Minimalist Action Hierarchy & Subtext Removal
- **Files:** [index.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/index.html)
- **Features & Capabilities:**
  - **Clean Action Button Hierarchy:**
    - Removed extraneous instructional text prompts (`Click anywhere on this side to enter`) beneath both the Admin ("Admin Login") and Client ("Enter Main Page") action buttons per user preference.
    - Simplified CTA containers to sleek `<div class="relative z-10 flex flex-col items-center">` wrappers, maximizing card breathing room and visual focus.
  - **Retained Full-Card Responsive Navigation:**
    - Preserved responsive card click areas (`navigateToAdmin(event)` and `navigateToClient(event)`) so clicking either side of the viewport or tapping the distinct pill buttons seamlessly routes visitors to their target destination.

### XXV. Main Page Browser Refresh Role Gateway Redirection Engine
- **Files:** [home.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/home.html), [js/main.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/main.js)
- **Features & Capabilities:**
  - **Zero-Latency Reload Interception:**
    - Embedded synchronous performance detection in `<head>` of `home.html` evaluating `performance.getEntriesByType('navigation')[0].type === 'reload'` and `performance.navigation.type === 1`.
    - Automatically intercepts browser refresh actions (F5, browser reload button, Ctrl+R, mobile pull-down) and redirects directly to the Role Selection Gateway (`index.html`).
  - **Flicker-Free Viewport Transition:**
    - Employs `window.location.replace('index.html')` prior to CSS and DOM parsing, preventing layout flash and unnecessary asset fetching.
  - **Discrimination Between Navigation & Reload:**
    - Normal incoming navigations from `index.html` or internal application links maintain `type: 'navigate'`, loading the public travel portal seamlessly without premature gateway redirects.

### XXVI. Main Page Header Streamlining & Role Portal Pill Removal
- **Files:** [home.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/home.html), [js/main.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/main.js)
- **Features & Capabilities:**
  - **Uncluttered Navigation Action Strip:**
    - Removed the redundant `Role Portal` switcher pill button (`media_1792393961834_d55c26f5.png`) from the top sticky header on `home.html`.
    - Visitors returning to the Role Gateway do so intuitively via page refresh or direct URL navigation, keeping the navigation bar clean and focused strictly on travel brand links and user authentication.

### XXVII. Keep Me Signed In Gmail Auto-Populate Engine
- **Files:** [home.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/home.html), [js/main.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/main.js)
- **Features & Capabilities:**
  - **Dynamic Checkbox Toggle Population:**
    - Checking the "Keep me signed in" checkbox (`#signin-remember`) immediately populates the traveler's Gmail address (`julie@gmail.com` or previously remembered client email) and password into the sign-in form.
    - Unchecking the box clears the credentials and removes the saved token, providing clear, tactile user control.
  - **Modal Open Credential Recall:**
    - Opening the authentication modal in sign-in mode automatically checks the preference and seeds the Gmail address, eliminating empty form states when the checkbox is active.

### XXVIII. Admin Tour Packages & Places Creation Engine with Real-Time Client Synchronization
- **Files:** [admin.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/admin.html), [js/admin.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/admin.js), [js/main.js](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/js/main.js), [home.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/home.html)
- **Features & Capabilities:**
  - **Interactive "+ Add New Place / Package" Header Action:**
    - Integrated high-prominence action button in the `#tab-packages` header of `admin.html` paired with dynamic counter badge (`#packages-count-badge`) displaying live active holiday bundles and total inventory.
  - **Comprehensive Add Place / Package Modal (`#add-package-modal`):**
    - Dialog allows operations staff to configure destination title, location, category (Island, Beach, Highland, Adventure), duration (e.g. `3D2N`, `4D3N`), transit mode, rate per pax, original price, capacity slots, hotel partner, and overview.
  - **12-Destination Preset Scenic Cover Chooser:**
    - Features a 12-thumbnail visual picker (Batanes, Palawan, Siargao, Baguio, Davao, Iloilo, La Union, Vigan, Batangas, Siquijor, Boracay, Bohol) alongside a custom image URL input with real-time thumbnail preview.
  - **Full Client Synthesis & Real-Time Sync:**
    - Automatically builds day-by-day itineraries, inclusion checklists, deluxe room tiers, and optional add-ons so newly created destinations immediately render on `home.html`, respond to category filters, open full itinerary modals, and accept verified bookings.
  - **Package Deletion & Lifecycle Management:**
    - Integrated `deletePackage(id)` with styled confirmation modal and pause/activate status toggling.

### XXIX. Find Your Destination Direct Navigation to Popular Destinations Showcase
- **Files:** [home.html](file:///C:/Antigravity%20files/Mckanes%20Travel%20and%20Tours/home.html)
- **Features & Capabilities:**
  - **Targeted Section Navigation:**
    - The "Find Your Destination" exploration card's "Find Now" call-to-action button links directly to `#destinations` (the interactive "Popular Destinations" showcase).
  - **Full-Card Interactive Clickability:**
    - Tapping or clicking anywhere on the "Find Your Destination" card initiates smooth programmatic scrolling down to the Popular Destinations section, matching the UX patterns of the companion Flight and Bus booking cards.


