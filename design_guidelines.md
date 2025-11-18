# GLOWFEED Design Guidelines

## Design Approach
**Reference-Based Hybrid:** Drawing from Instagram's social features, TikTok's video-first feed, and Shopify's commerce interface. This platform balances entertainment (video feed) with utility (shopping, earnings dashboards), requiring both visual appeal and functional clarity.

## Color System
**Primary Colors (User-Specified):**
- Navy Header: #3e5a80
- Green Accents: #3a7e34 (profile borders, CTA buttons, UPDATE button, POST button)

**Supporting Palette:**
- White: #FFFFFF (backgrounds, cards)
- Light Gray: #F5F5F5 (secondary backgrounds)
- Dark Gray: #1A1A1A (primary text)
- Medium Gray: #666666 (secondary text)
- Border Gray: #E0E0E0 (dividers, card borders)
- Success Green: #10B981 (success states)
- Error Red: #EF4444 (validation errors)
- Discount Badge: #FF6B35 (discount percentage badges)

## Typography
**Font Family:** Inter (Google Fonts) for clean, modern readability across UI and content

**Hierarchy:**
- H1 (Page Titles): 32px/bold (mobile: 24px)
- H2 (Section Headers): 24px/semibold (mobile: 20px)
- H3 (Card Titles, Shop Names): 18px/semibold
- Body (Post Captions, Descriptions): 16px/regular
- Small (Metadata, Timestamps): 14px/regular
- Tiny (Labels, Badges): 12px/medium

## Layout System
**Spacing Primitives:** Use Tailwind units of 2, 4, 6, and 8 for consistency
- Tight spacing: p-2, m-2
- Standard spacing: p-4, gap-4
- Section spacing: py-6, px-6
- Large spacing: py-8, px-8

**Container Strategy:**
- Full-width: Video feed, header
- Constrained: max-w-7xl for shop grids, discount deals
- Narrow: max-w-2xl for forms, profile content

**Grid Systems:**
- Product Grid: grid-cols-2 md:grid-cols-3 lg:grid-cols-4
- Video Feed: Single column, full-width on mobile
- Order Dashboard: grid-cols-1 md:grid-cols-2

## Component Library

### Navigation
**Navy Header (#3e5a80):**
- Fixed top position, white text, logo left, auth buttons right
- Mobile: Hamburger menu, logo centered
- Height: 64px with px-4 horizontal padding
- Icons: White with hover:opacity-80

### Profile Components
**Profile Photo:**
- Circular with 4px solid border (#3a7e34 green)
- Sizes: 128px (profile page), 48px (post creator), 32px (comments)
- Upload button overlays bottom-right corner

**Profile Card:**
- White background, rounded-lg, p-6
- Center-aligned photo, name (H2), username (gray, @username), bio (body text)
- Followers count: Bold number + "Followers" label
- Green UPDATE button: Full-width, rounded-lg, py-3

### Video Feed (TikTok-Inspired)
**Post Card:**
- Full-width container, mb-4
- Creator info bar: Photo (32px) + username + timestamp, bg-white, px-4, py-2
- Video player: Aspect ratio 9:16, auto-play muted, tap-to-unmute
- Interaction bar (bottom overlay): Like/Comment/Share icons, white with drop shadow
- Caption: bg-white, px-4, py-3, below video
- Product link: "Shop Now" button (green), inline with caption if present

### Shopping Components
**Shop Header:**
- Banner image: aspect-ratio 21:9, max-h-48
- Shop info overlay: Name (H2), description (body), semi-transparent dark gradient background
- "CREATE SHOP & EARN" CTA: Large, prominent, green button if no shop exists

**Product Card:**
- White background, rounded-lg, shadow-sm
- Product image: aspect-ratio 1:1, object-cover
- Content padding: p-4
- Name: H3, truncate after 2 lines
- Price display: Original (strikethrough if discount), Final (bold, green if discounted)
- Discount badge: Circular, orange (#FF6B35), top-right corner, "X% OFF"

**Add Product Form:**
- White card, p-6, rounded-lg
- Media upload: Dashed border, 200px height, center icon + text
- Text inputs: Full-width, border, rounded, p-3
- Discount section: 
  - Dropdown: "No Discount" / "Yes" (required)
  - Conditional: If "Yes", show percentage input (0-100)
  - Live preview: Original price (strikethrough) → Final price (green, bold)

### Order & Earnings
**Order Modal:**
- Centered overlay, max-w-md
- White card with close button
- Form inputs: Stacked, labeled, required asterisks
- Submit button: Green, full-width, py-3

**Dashboard Cards:**
- Grid layout (2 columns on desktop)
- White cards, p-6, rounded-lg, shadow
- Stat display: Large number (H1), label below (small text)
- Status badges: Colored pills (pending: yellow, completed: green)

**Shopkeeper Dashboard:**
- Table layout with order rows
- Columns: Order ID, Customer, Product, Quantity, Status
- Action buttons: "Ship" (blue), "Mark Delivered" (green)
- Mobile: Stack as cards with all info visible

### Discount Deals Page
**Hero Section:**
- Gradient background (navy to dark navy), py-8
- Title: "Top Discount Deals" (H1, white)
- Subtitle: "Updated hourly • Highest discounts first" (white, opacity-80)

**Deals Grid:**
- grid-cols-2 md:grid-cols-3 lg:grid-cols-4
- Ranking badges: #1 gold, #2 silver (top-left)
- Discount badge: Circular, orange, top-right
- Product card structure same as shopping

### Modals & Feedback
**Success Modal:**
- Centered, max-w-sm
- Green checkmark icon (large)
- Message (H3)
- "Got it" button (green)

**Loading States:**
- Skeleton screens for feed (gray animated bars)
- Spinner for form submissions

## Responsive Behavior
**Breakpoints:**
- Mobile: < 768px (single column, stacked)
- Tablet: 768px - 1024px (2 columns for products)
- Desktop: > 1024px (full grid layouts)

**Mobile Priorities:**
- Video feed: Full-screen vertical scroll
- Navigation: Bottom tab bar for Home/Shop/Profile
- Forms: Full-width inputs, larger touch targets (min 48px height)
- Product grid: 2 columns maximum

## Images
**Profile Photos:** User-uploaded, cropped to square, green border
**Product Images:** User-uploaded, optimized for 1:1 display, sharp quality
**Shop Banners:** User-uploaded, 21:9 aspect ratio, inspirational store imagery
**Video Thumbnails:** Auto-generated from first frame

No large hero images needed - the video feed IS the hero experience.

## Interactions
**Minimal Animations:**
- Button hover: Subtle opacity change (0.9)
- Card hover: Slight shadow increase
- Pull-to-refresh: Native mobile spinner
- Auto-scroll: Smooth scroll behavior

**No hover/active states for buttons on images** - rely on button component's native states.

## Accessibility
- ARIA labels for icon buttons
- Focus states: 2px blue outline
- Contrast ratio: Minimum 4.5:1 for text
- Touch targets: Minimum 48x48px
- Alt text required for all images