# Design Guidelines: WhatsApp Booking System Landing Page

## Design Approach
**Reference-Based**: Modern SaaS landing pages (Framer, Typedream, Linear) with WhatsApp brand integration. Clean, conversion-focused, business-professional aesthetic prioritizing clarity and trust.

## Core Design Principles
- **Conversion-first**: Clear visual hierarchy guiding users to signup
- **Trust-building**: Professional polish that reassures small business owners
- **WhatsApp-aligned**: Leverage brand recognition without mimicking their app
- **Scannable**: Busy business owners should grasp value in seconds

## Typography System

**Font Family**: Inter (primary) with Poppins as alternative
- **Hero Headline**: font-bold, text-5xl (mobile: text-4xl) - punchy, clear
- **Subheadline**: font-normal, text-xl (mobile: text-lg) - breathing room
- **Section Headers**: font-semibold, text-3xl (mobile: text-2xl)
- **Body Text**: font-normal, text-base, leading-relaxed
- **Form Labels**: font-medium, text-sm, uppercase tracking-wide
- **CTA Buttons**: font-semibold, text-lg
- **Testimonials**: text-base italic (quote), text-sm font-medium (attribution)

## Layout & Spacing

**Spacing Primitives**: Tailwind units of 4, 6, 8, 12, 16, 20, 24 for consistency
- Section vertical padding: py-20 (desktop), py-12 (mobile)
- Component spacing: gap-8 or gap-12
- Form field spacing: space-y-6
- Button padding: px-8 py-4

**Container Strategy**:
- Max width: max-w-6xl mx-auto
- Form container: max-w-md mx-auto
- Testimonials: grid grid-cols-1 md:grid-cols-3 gap-8

## Component Library

### Hero Section (80vh minimum)
- **Layout**: Centered content with ample whitespace
- **Structure**: Headline + Subtext (max-w-3xl centered) + CTA button + trust indicator ("Join 200+ businesses automating bookings")
- **No hero image**: Focus on messaging clarity with subtle gradient background

### CTA Buttons
- **Primary**: WhatsApp green (#25D366) background, white text, rounded-lg (8px), shadow-lg
- **States**: Slight scale on hover (transform scale-105), deeper shadow
- **Size**: Generous padding (px-8 py-4), prominent text (text-lg)

### Signup Form (Modal/Slide-in)
- **Container**: White card with shadow-2xl, rounded-2xl, max-w-md
- **Fields**: Rounded-lg inputs, border-2 focus states, clean spacing
- **Layout**: Single column, full-width fields, stacked labels
- **Submit Button**: Full-width, same styling as primary CTA

### Testimonials Section
- **Layout**: 3-column grid (mobile: stacked)
- **Card Style**: Subtle border (border-2), rounded-xl, padding p-6
- **Structure**: Quote text + 5-star rating (green) + Name/Business Type
- **Placeholder content**: Use realistic business names (e.g., "Sarah's Salon", "FitCore Gym")

### Footer
- **Layout**: Centered content, py-12
- **Elements**: WhatsApp contact button (outlined green), social proof text, minimal legal links
- **WhatsApp Button**: Icon + "Chat on WhatsApp" text, outlined style with green border

## Visual Treatment

**Backgrounds**: 
- Hero: Subtle gradient (white to very light green tint)
- Sections: Alternating white and ultra-light gray (bg-gray-50)
- Form: White on semi-transparent overlay (when modal)

**Shadows**: 
- Cards/Testimonials: shadow-md
- Buttons: shadow-lg
- Form modal: shadow-2xl
- Hover states: Intensify shadow slightly

**Borders**: 
- Rounded corners throughout: rounded-lg (buttons/inputs), rounded-xl (cards), rounded-2xl (modals)
- Border width: border-2 for form fields, border for cards

## Images

**No large hero image needed**. This landing page prioritizes clarity of messaging over visual storytelling. The WhatsApp green accent and clean typography create sufficient visual interest.

**Optional**: Small icon/illustration elements in testimonials or as section dividers (keep minimal and functional).

## Responsive Behavior

- **Mobile-first**: Stack all multi-column layouts to single column
- **Breakpoints**: Focus on mobile (base) and desktop (md/lg)
- **Touch targets**: Minimum 44px height for all interactive elements
- **Form**: Full-screen on mobile for focus, modal on desktop

## Accessibility
- High contrast text (never gray on gray)
- Form field labels always visible
- Focus states clearly defined (ring-2 ring-green-500)
- Semantic HTML throughout