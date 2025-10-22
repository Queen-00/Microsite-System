<!--
  Cyber README — Next.js Microsite Template (one-file, no assets)
  Mobile-friendly, GitHub-safe. No side scrolling, no giant code fence.
  Typing banners use readme-typing-svg (image-based).
-->

<!-- Gradient Title (SVG; GitHub-safe) -->
<p align="center">
  <svg width="100%" height="70" viewBox="0 0 1200 70" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="Next.js Microsite Setup (TypeScript Template)">
    <defs>
      <linearGradient id="titleGradient" x1="0" x2="1">
        <stop offset="0%" stop-color="#8A2BE2"/>
        <stop offset="50%" stop-color="#FF00CC"/>
        <stop offset="100%" stop-color="#00E5FF"/>
      </linearGradient>
      <filter id="titleGlow"><feGaussianBlur stdDeviation="2"/></filter>
    </defs>
    <text x="50%" y="48" text-anchor="middle" font-size="30" font-family="Segoe UI, Ubuntu, Roboto, Helvetica, Arial, sans-serif" font-weight="800" fill="url(#titleGradient)" filter="url(#titleGlow)">
      Next.js Microsite Setup (TypeScript Template)
    </text>
  </svg>
</p>

<!-- Typing subtitle -->
<p align="center">
  <img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=700&size=16&duration=2600&pause=900&center=true&vCenter=true&width=640&color=8A2BE2&lines=%F0%9F%92%A1+Next.js+15+App+Router;%F0%9F%93%9A+Copy%2FPaste+page.tsx+stubs;%F0%9F%9A%80+Build+internal+sub-sites+fast" alt="typing-subtitle" />
</p>

<!-- Badges (split across lines for mobile) -->
<p align="center">
  <a href="#folder-structure"><img src="https://img.shields.io/badge/Next.js-15-000000?logo=nextdotjs" alt="Next.js 15"></a>
  <a href="#page-templates-typescript"><img src="https://img.shields.io/badge/React-19-20232a?logo=react" alt="React 19"></a>
  <a href="#language--compatibility"><img src="https://img.shields.io/badge/TypeScript-5.x-3178c6?logo=typescript&logoColor=white" alt="TS 5.x"></a>
</p>
<p align="center">
  <img src="https://img.shields.io/badge/App_Router-Enabled-8A2BE2" alt="App Router"/>
  <img src="https://img.shields.io/badge/License-Custom-FF00CC" alt="License"/>
  <img src="https://img.shields.io/badge/Status-Template%20Ready-22c55e" alt="Status"/>
</p>

<!-- Section divider (fluid, no overflow) -->
<p align="center">
  <svg viewBox="0 0 100 2" width="100%" height="2" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="divider">
    <defs><linearGradient id="d0" x1="0" x2="1"><stop offset="0%" stop-color="#00E5FF"/><stop offset="50%" stop-color="#8A2BE2"/><stop offset="100%" stop-color="#FF00CC"/></linearGradient></defs>
    <rect x="0" y="0" width="100" height="2" fill="url(#d0)" opacity="0.9"/>
  </svg>
</p>

> Build a small **“microsite” inside your main Next.js app** (e.g. `/brand`, `/press`, `/docs`) with clean, URL-mirroring folders and a local layout.  
> This guide provides a TypeScript blank template showing the structure, page files, and practical benefits.

<p align="center">
  <a href="#quick-start"><img src="https://img.shields.io/badge/QUICK_START-%E2%9A%A1-6b21e6?style=for-the-badge" alt="Quick Start"></a>
  <a href="#folder-structure"><img src="https://img.shields.io/badge/STRUCTURE-%F0%9F%93%81-ca27b9?style=for-the-badge" alt="Structure"></a>
  <a href="#page-templates-typescript"><img src="https://img.shields.io/badge/TEMPLATES-%F0%9F%96%A5-0ea5e9?style=for-the-badge" alt="Templates"></a>
  <a href="#why-microsites-benefits--use-cases"><img src="https://img.shields.io/badge/BENEFITS-%F0%9F%8C%9F-bf26ff?style=for-the-badge" alt="Benefits"></a>
</p>

## Table of Contents
- [Overview](#overview)
- [Why Microsites? (Benefits & Use Cases)](#why-microsites-benefits--use-cases)
- [Language & Compatibility](#language--compatibility)
- [Folder Structure](#folder-structure)
- [Quick Start](#quick-start)
- [Page Templates (TypeScript)](#page-templates-typescript)
- [Microsite Layout (`layout.tsx`)](#microsite-layout-layouttsx)
- [Common Gotchas](#common-gotchas)
- [FAQ](#faq)
- [Custom Open License — Microsite System Template](#custom-open-license--microsite-system-template)

<p align="center">
  <svg viewBox="0 0 100 2" width="100%" height="2" xmlns="http://www.w3.org/2000/svg"><defs><linearGradient id="d1" x1="0" x2="1"><stop offset="0%" stop-color="#00E5FF"/><stop offset="50%" stop-color="#8A2BE2"/><stop offset="100%" stop-color="#FF00CC"/></linearGradient></defs><rect x="0" y="0" width="100" height="2" fill="url(#d1)" opacity="0.9"/></svg>
</p>

## Overview
A **microsite** is a self-contained set of pages under a single path like `/<siteName>`. It shares your app’s stack and build but can have its **own navigation, styling, and layout** — ideal for affiliates, sub-brands, or campaigns.

> [!TIP]
> Assumes **Next.js 15 (App Router)** + **TypeScript**. Prefer JS? Keep the folders and drop the types.

<p align="center">
  <svg viewBox="0 0 100 2" width="100%" height="2" xmlns="http://www.w3.org/2000/svg"><defs><linearGradient id="d2" x1="0" x2="1"><stop offset="0%" stop-color="#00E5FF"/><stop offset="50%" stop-color="#8A2BE2"/><stop offset="100%" stop-color="#FF00CC"/></linearGradient></defs><rect x="0" y="0" width="100" height="2" fill="url(#d2)" opacity="0.9"/></svg>
</p>

## Why Microsites? (Benefits & Use Cases)

**Quick matrix (pros/cons)**

| Capability / Outcome            | Microsite Approach | Alternative |
|---------------------------------|:------------------:|:-----------:|
| Cost-efficient hosting          | ✔️                 | ❌          |
| Shared auth/analytics           | ✔️                 | ❌          |
| Centralized maintenance         | ✔️                 | ~           |
| Brand cohesion (sub-brands)     | ✔️                 | ~           |
| SEO synergy (subpaths)          | ✔️                 | ❌          |
| Single-repo content ops         | ✔️                 | ❌          |
| Easy cross-promotion            | ✔️                 | ❌          |
| Fast seasonal launches          | ✔️                 | ~           |
| Per-site layout/theming         | ✔️                 | ~           |
| Multi-tenant friendly           | ✔️                 | ❌          |

**Details**
1) **Cost-Efficient** — Reuse hosting & CI/CD; no extra domain/SSL.  
2) **Shared Infra** — Auth, analytics, and libs are centralized.  
3) **Centralized Maintenance** — Dependency & token updates fan-out.  
4) **Brand Cohesion** — Unique sections, consistent parent look.  
5) **SEO Synergy** — Subpaths inherit parent authority.  
6) **Simplified Content Ops** — One repo simplifies reviews & releases.  
7) **Cross-Promotion** — Internal linking boosts retention.  
8) **Fast Launch** — New microsite = a folder + `page.tsx`.  
9) **Scoped Customization** — Per-site `layout.tsx` keeps changes local.  
10) **Scalable** — Clean path to multi-tenant later.

<p align="center">
  <svg viewBox="0 0 100 2" width="100%" height="2" xmlns="http://www.w3.org/2000/svg"><defs><linearGradient id="d3" x1="0" x2="1"><stop offset="0%" stop-color="#00E5FF"/><stop offset="50%" stop-color="#8A2BE2"/><stop offset="100%" stop-color="#FF00CC"/></linearGradient></defs><rect x="0" y="0" width="100" height="2" fill="url(#d3)" opacity="0.9"/></svg>
</p>

## Language & Compatibility
- **Built for:** Next.js 15 (App Router) + **TypeScript**  
- **JavaScript usage:** rename `.tsx` → `.jsx`, remove types (e.g., `: { params: { index: string } }`)  
- **Other frameworks:** Nuxt/Remix use different routing; adapt folder names.

<p align="center">
  <img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=600&size=14&duration=2600&pause=900&center=true&vCenter=true&width=520&color=00E5FF&lines=Works+great+with+TS...;...and+easy+to+convert+to+JS" alt="typing-note" />
</p>

<p align="center">
  <svg viewBox="0 0 100 2" width="100%" height="2" xmlns="http://www.w3.org/2000/svg"><defs><linearGradient id="d4" x1="0" x2="1"><stop offset="0%" stop-color="#00E5FF"/><stop offset="50%" stop-color="#8A2BE2"/><stop offset="100%" stop-color="#FF00CC"/></linearGradient></defs><rect x="0" y="0" width="100" height="2" fill="url(#d4)" opacity="0.9"/></svg>
</p>

## Folder Structure
```txt
src/
└─ app/
   └─ (microsites)/              ← route group (not in URL)
      └─ <siteName>/             ← microsite slug (lowercase; e.g., "acme")
         ├─ layout.tsx           ← optional local layout
         ├─ page.tsx             ← /<siteName> (landing)
         ├─ about/
         │  └─ page.tsx          ← /<siteName>/about
         ├─ services/
         │  └─ page.tsx          ← /<siteName>/services
         ├─ contact/
         │  └─ page.tsx          ← /<siteName>/contact
         └─ page/
            └─ 1/
               └─ page.tsx       ← /<siteName>/page/1 (example fixed route)

> 💡 Tip: keep directories lowercase for predictable URLs.



<p align="center">
  <svg viewBox="0 0 100 2" width="100%" height="2" xmlns="http://www.w3.org/2000/svg"><defs><linearGradient id="d5" x1="0" x2="1"><stop offset="0%" stop-color="#00E5FF"/><stop offset="50%" stop-color="#8A2BE2"/><stop offset="100%" stop-color="#FF00CC"/></linearGradient></defs><rect x="0" y="0" width="100" height="2" fill="url(#d5)" opacity="0.9"/></svg>
</p>Quick Start

# 1) Create folders
mkdir -p src/app/(microsites)/<siteName>/about
mkdir -p src/app/(microsites)/<siteName>/services
mkdir -p src/app/(microsites)/<siteName>/contact
mkdir -p src/app/(microsites)/<siteName>/page/1

# 2) Add page files
#   src/app/(microsites)/<siteName>/page.tsx
#   src/app/(microsites)/<siteName>/about/page.tsx
#   src/app/(microsites)/<siteName>/services/page.tsx
#   src/app/(microsites)/<siteName>/contact/page.tsx
#   src/app/(microsites)/<siteName>/page/1/page.tsx

# 3) Optional dynamic pagination
#   src/app/(microsites)/<siteName>/page/[index]/page.tsx

# 4) Optional microsite-only layout
#   src/app/(microsites)/<siteName>/layout.tsx

# 5) Deploy normally (e.g., Vercel)
#   Routes are served under /<siteName>/

<p align="center">
  <img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=600&size=14&duration=2600&pause=900&center=true&vCenter=true&width=520&color=FF00CC&lines=Copy+the+stubs+%E2%86%92+paste+%E2%86%92+ship" alt="typing-quickstart" />
</p><p align="center">
  <svg viewBox="0 0 100 2" width="100%" height="2" xmlns="http://www.w3.org/2000/svg"><defs><linearGradient id="d6" x1="0" x2="1"><stop offset="0%" stop-color="#00E5FF"/><stop offset="50%" stop-color="#8A2BE2"/><stop offset="100%" stop-color="#FF00CC"/></linearGradient></defs><rect x="0" y="0" width="100" height="2" fill="url(#d6)" opacity="0.9"/></svg>
</p>Page Templates (TypeScript)

Home — page.tsx

export default function Home() {
  return (
    <main className="mx-auto max-w-5xl px-4 py-12">
      <h1 className="text-3xl font-bold">{'<siteName> Microsite'}</h1>
      <p className="mt-2 text-neutral-600">Welcome to your embedded microsite. Replace this with your hero content.</p>
    </main>
  );
}

<p align="center">
  <svg viewBox="0 0 100 2" width="72%" height="2" xmlns="http://www.w3.org/2000/svg"><defs><linearGradient id="d7" x1="0" x2="1"><stop offset="0%" stop-color="#00E5FF"/><stop offset="50%" stop-color="#8A2BE2"/><stop offset="100%" stop-color="#FF00CC"/></linearGradient></defs><rect x="0" y="0" width="100" height="2" fill="url(#d7)" opacity="0.9"/></svg>
</p>About — about/page.tsx

export default function About() {
  return (
    <main className="mx-auto max-w-5xl px-4 py-12">
      <h1 className="text-2xl font-bold">About</h1>
      <p className="mt-2 text-neutral-600">Brief overview of your microsite’s purpose, team, or background.</p>
    </main>
  );
}

<p align="center">
  <svg viewBox="0 0 100 2" width="72%" height="2" xmlns="http://www.w3.org/2000/svg"><defs><linearGradient id="d8" x1="0" x2="1"><stop offset="0%" stop-color="#00E5FF"/><stop offset="50%" stop-color="#8A2BE2"/><stop offset="100%" stop-color="#FF00CC"/></linearGradient></defs><rect x="0" y="0" width="100" height="2" fill="url(#d8)" opacity="0.9"/></svg>
</p>Services — services/page.tsx

export default function Services() {
  return (
    <main className="mx-auto max-w-5xl px-4 py-12">
      <h1 className="text-2xl font-bold">Services</h1>
      <p className="mt-2 text-neutral-600">Describe your offerings, tiers, or features here.</p>
    </main>
  );
}

<p align="center">
  <svg viewBox="0 0 100 2" width="72%" height="2" xmlns="http://www.w3.org/2000/svg"><defs><linearGradient id="d9" x1="0" x2="1"><stop offset="0%" stop-color="#00E5FF"/><stop offset="50%" stop-color="#8A2BE2"/><stop offset="100%" stop-color="#FF00CC"/></linearGradient></defs><rect x="0" y="0" width="100" height="2" fill="url(#d9)" opacity="0.9"/></svg>
</p>Contact — contact/page.tsx

export default function Contact() {
  return (
    <main className="mx-auto max-w-5xl px-4 py-12">
      <h1 className="text-2xl font-bold">Contact</h1>
      <p className="mt-2 text-neutral-600">Provide an email, form, or other contact method.</p>
    </main>
  );
}

<p align="center">
  <svg viewBox="0 0 100 2" width="72%" height="2" xmlns="http://www.w3.org/2000/svg"><defs><linearGradient id="d10" x1="0" x2="1"><stop offset="0%" stop-color="#00E5FF"/><stop offset="50%" stop-color="#8A2BE2"/><stop offset="100%" stop-color="#FF00CC"/></linearGradient></defs><rect x="0" y="0" width="100" height="2" fill="url(#d10)" opacity="0.9"/></svg>
</p>Fixed Pagination — page/1/page.tsx

export default function FixedPageOne() {
  return (
    <main className="mx-auto max-w-5xl px-4 py-12">
      <h1 className="text-2xl font-bold">Page 1</h1>
      <p className="mt-2 text-neutral-600">This is a fixed route at /&lt;siteName&gt;/page/1.</p>
    </main>
  );
}

<p align="center">
  <svg viewBox="0 0 100 2" width="72%" height="2" xmlns="http://www.w3.org/2000/svg"><defs><linearGradient id="d11" x1="0" x2="1"><stop offset="0%" stop-color="#00E5FF"/><stop offset="50%" stop-color="#8A2BE2"/><stop offset="100%" stop-color="#FF00CC"/></linearGradient></defs><rect x="0" y="0" width="100" height="2" fill="url(#d11)" opacity="0.9"/></svg>
</p>Dynamic Pagination — page/[index]/page.tsx

export default function Paged({ params }: { params: { index: string } }) {
  return (
    <main className="mx-auto max-w-5xl px-4 py-12">
      <h1 className="text-2xl font-bold">Page {params.index}</h1>
      <p className="mt-2 text-neutral-600">Render paginated content based on the index.</p>
    </main>
  );
}

<p align="center">
  <svg viewBox="0 0 100 2" width="100%" height="2" xmlns="http://www.w3.org/2000/svg"><defs><linearGradient id="d12" x1="0" x2="1"><stop offset="0%" stop-color="#00E5FF"/><stop offset="50%" stop-color="#8A2BE2"/><stop offset="100%" stop-color="#FF00CC"/></linearGradient></defs><rect x="0" y="0" width="100" height="2" fill="url(#d12)" opacity="0.9"/></svg>
</p>Microsite Layout (layout.tsx)

import Link from "next/link";

export default function MicrositeLayout({ children }: { children: React.ReactNode }) {
  return (
    <div className="min-h-dvh bg-white text-neutral-900">
      <nav className="sticky top-0 z-20 border-b bg-white/80 backdrop-blur">
        <div className="mx-auto flex max-w-5xl items-center gap-6 px-4 py-3">
          <Link className="hover:underline" href="/<siteName>">home</Link>
          <Link className="hover:underline" href="/<siteName>/about">about</Link>
          <Link className="hover:underline" href="/<siteName>/services">services</Link>
          <Link className="hover:underline" href="/<siteName>/contact">contact</Link>
          <Link className="hover:underline" href="/<siteName>/page/1">page 1</Link>
        </div>
      </nav>
      {children}
    </div>
  );
}

<p align="center">
  <svg viewBox="0 0 100 2" width="100%" height="2" xmlns="http://www.w3.org/2000/svg"><defs><linearGradient id="d13" x1="0" x2="1"><stop offset="0%" stop-color="#00E5FF"/><stop offset="50%" stop-color="#8A2BE2"/><stop offset="100%" stop-color="#FF00CC"/></linearGradient></defs><rect x="0" y="0" width="100" height="2" fill="url(#d13)" opacity="0.9"/></svg>
</p>Common Gotchas

404 on click? Folder names and link paths must match exactly.

Lowercase everything for predictable URLs.

Route groups like (microsites) are not in the URL.

If you add page/[index], remove the fixed /page/1.

Consistent content width: mx-auto max-w-5xl px-4.


<p align="center">
  <img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=600&size=14&duration=2600&pause=1200&center=true&vCenter=true&width=520&color=8A2BE2&lines=Tip%3A+Keep+routes+predictable.;Use+lowercase+folders+everywhere." alt="typing-tips" />
</p><p align="center">
  <svg viewBox="0 0 100 2" width="100%" height="2" xmlns="http://www.w3.org/2000/svg"><defs><linearGradient id="d14" x1="0" x2="1"><stop offset="0%" stop-color="#00E5FF"/><stop offset="50%" stop-color="#8A2BE2"/><stop offset="100%" stop-color="#FF00CC"/></linearGradient></defs><rect x="0" y="0" width="100" height="2" fill="url(#d14)" opacity="0.9"/></svg>
</p>FAQ

Can I use JavaScript instead of TypeScript? Yes — use .jsx and remove types.
Can each microsite have different styling/animations? Yes — use per-site CSS modules or Tailwind theme tokens.
Can I use subdomains? Yes — add rewrites (e.g., sub.domain.com → /sub) in your deployment.

<p align="center">
  <a href="#quick-start"><img src="https://img.shields.io/badge/Return_to-Quick_Start-0ea5e9?style=for-the-badge" alt="Back to Quick Start"></a>
  <a href="#page-templates-typescript"><img src="https://img.shields.io/badge/View-Code_Stubs-bf26ff?style=for-the-badge" alt="View Code Stubs"></a>
</p><p align="center">
  <svg viewBox="0 0 100 2" width="100%" height="2" xmlns="http://www.w3.org/2000/svg"><defs><linearGradient id="d15" x1="0" x2="1"><stop offset="0%" stop-color="#00E5FF"/><stop offset="50%" stop-color="#8A2BE2"/><stop offset="100%" stop-color="#FF00CC"/></linearGradient></defs><rect x="0" y="0" width="100" height="2" fill="url(#d15)" opacity="0.9"/></svg>
</p>Custom Open License — Microsite System Template

This repository and template represent an original system design for creating embedded microsites within a parent Next.js application.

You are free to:

Use, copy, modify, and adapt this structure for personal or commercial projects on your own repo.

Distribute educational or tutorial materials based on this guide.

Attribute the original author in any public or published derivative.


You may NOT:

Sell, resell, or commercially redistribute this exact system or guide
(in part or whole) without explicit written permission from the original author.

Submit pull requests, forks, or collaborations / modifications intended for upstream integration.


Attribution Requirement
When reusing this template or substantial parts of its structure or documentation, include a credit line such as:
“Based on the Microsite System Template (© 2025 Original Author)”


---

Tech Stack (icons)

<p><img src="https://skillicons.dev/icons?i=next,react,ts,tailwind" height="36"/></p>Feature Matrix

Feature	✔ / ❌

Clean folder routing	✔️
Documented page stubs	✔️
Per-site layout	✔️
SEO-friendly subpaths	✔️
Cross-promotion ready	✔️


Data Snapshot (example)

Metric	Value

Default pages	4
Example pagination	1
Routing depth	3
Build script	yarn build
Deploy target	Vercel
