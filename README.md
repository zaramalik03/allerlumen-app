# AllerLumen

AllerLumen gives severe allergy families and individuals a community-driven dining tool that helps them freely find safe foods and trustworthy restaurants wherever they are — and feel confident in what they eat.

# Link

- Live app: https://allerlumen.lovable.app 
- Feedback form: https://docs.google.com/forms/d/e/1FAIpQLScXj0TwHu6K4G-FjXq5q-ix2a6jDfxz1TUfo0AER_bfP1EvIQ/viewform?usp=header

# The problem it solves

Dining out with severe allergies means hours of calling kitchens, worrying about cross-contact, and hoping staff actually understand. AllerLumen replaces that guesswork with community-reported safety detail, a personal allergen profile applied everywhere automatically, and a quick menu check.

# How it works

1. Create an account and pick your allergies once (allergen, severity, optional diet and cuisine preferences).
2. Browse places — restaurants are filtered and ordered by your profile. No re-selecting allergens on any page.
3. Rate and review — 1–5 hearts plus visited status, allergen-friendly variety, trained staff, written allergen menu, concerns, and a yes/no recommendation.
4. Add a place that isn't listed yet, with the allergen-friendly details you know.
5. Menu Check — paste a menu or upload a photo/PDF and get a per-item verdict: likely safe, confirm with staff, or contains your allergens, with evidence and a call-ahead script.
6. Dashboard — your account details, allergies, rated places, and membership (coming soon).

# Tech stack

## Frontend

- Framework: TanStack Start v1 (React 19, full-stack, SSR/SSG)
- Build tool: Vite 8
- Language: TypeScript 5.8
- Styling: Tailwind CSS v4 (native CSS theme tokens, no config file)
- UI primitives: Radix UI + shadcn-style components, lucide-react icons
- Data fetching: TanStack Query v5 with route loaders
- Forms: react-hook-form + zod validation
- Maps: Mapbox GL JS (interactive places map, geocoding)
- Installable: PWA (vite-plugin-pwa, manifest, service worker, offline shell)
- Mobile-first: single-column layouts, bottom tab navigation

## Backend & data

- Database & auth: Supabase (Postgres, email/password auth, row-level security)
- Server logic: TanStack server functions, bearer-token middleware
- AI: OpenAI/GPT-6-Astra (through Lovable) for menu text, photo and PDF analysis
- Privacy: owner-only allergy profiles; reviews publicly readable with no reviewer names

## Python analysis service (services/menu-analyzer)

- Layer 1: Postgres allergen ingredient dictionary (whole-word, plural-aware)
- Layer 2: spaCy ingredient extraction (noun chunks, lemmas)
- Layer 3: Hugging Face zero-shot classification — can only escalate risk, never clear it
- Guidance: extractive "Know Before You Go" worker, public restaurant websites only, sources attributed

# Safety notices

Every analysis result carries a notice that it is guidance only — always inform your server of your restrictions and confirm preparation methods in person. Public safety, privacy and terms pages are linked from the footer on every screen.

# Status

Pilot stage. Community reviews and place contributions are live; the Python analysis service is ready to deploy and the app falls back to built-in AI until it is hosted.

AllerLumen — eat with confidence.


