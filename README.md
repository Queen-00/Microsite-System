<!--
  Cyber README — Next.js Microsite Template
  Aesthetic: violet/magenta/cyan, mobile-friendly, GitHub-safe.
  Replace GIF placeholders with direct .gif/.apng URLs when you have them.
-->

<!-- Title -->
<h1 align="center" style="font-weight:800;">
  <span style="background: linear-gradient(90deg,#8A2BE2,#FF00CC,#00E5FF); -webkit-background-clip: text; background-clip: text; color: transparent;">
    Next.js Microsite Setup (TypeScript Template)
  </span>
</h1>

<!-- Animated typing subtitle (small) -->
<p align="center">
  <img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=700&size=16&duration=2600&pause=800&center=true&vCenter=true&width=520&lines=%F0%9F%92%A1+Next.js+15+App+Router;%F0%9F%93%9A+Copy%2FPaste+page.tsx+stubs;%F0%9F%9A%80+Ship+internal+sub-sites+fast" alt="Typing subtitle" />
</p>

<!-- Badges -->
<p align="center">
  <img src="https://img.shields.io/badge/Next.js-15-000000?logo=nextdotjs" />
  <img src="https://img.shields.io/badge/React-19-20232a?logo=react" />
  <img src="https://img.shields.io/badge/TypeScript-5.x-3178c6?logo=typescript&logoColor=white" />
  <img src="https://img.shields.io/badge/App_Router-Enabled-8A2BE2" />
  <img src="https://img.shields.io/badge/License-Custom-FF00CC" />
  <img src="https://img.shields.io/badge/Status-Template%20Ready-22c55e" />
</p>

<!-- Optional animated sticker row (swap in direct GIF/APNG URLs later) -->
<p align="center">
  <!-- <img src="YOUR_GIF_OR_APNG_1" height="54" /> -->
  <!-- <img src="YOUR_GIF_OR_APNG_2" height="54" /> -->
</p>

<!-- Gradient divider -->
<p align="center"><img src="assets/divider.svg" width="85%" alt="divider" /></p>

<!-- Two-column layout: main left, info rail right. Stacks on mobile. -->
<table>
  <tr>
    <td valign="top" width="68%">

> Build a small **“microsite” inside your main Next.js app** (e.g. `/brand`, `/press`, `/docs`) with clean, URL-mirroring folders and a local layout.  
> This guide provides a TypeScript-based blank template showing the structure, page files, and benefits of integrating microsites into larger applications.

<!-- Divider -->
<p align="center"><img src="assets/divider.svg" width="70%" alt="divider" /></p>

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

<!-- Divider -->
<p align="center"><img src="assets/divider.svg" width="70%" alt="divider" /></p>

## Overview

A **microsite** is a self-contained group of pages living under a single path like `/<siteName>` inside your primary Next.js app.  
It uses the same stack, styles, and build process but can have its **own navigation, design, and layout** — perfect for affiliate brands, sub-projects, or special campaigns.

> [!TIP]
> This document targets **Next.js 15 (App Router)** with **TypeScript**.  
> If you prefer JS, keep the folder structure and drop the types.

<!-- Divider -->
<p align="center"><img src="assets/divider.svg" width="70%" alt="divider" /></p>

## Why Microsites? (Benefits & Use Cases)

Microsites aren’t just smaller websites — they’re a smart, modular extension of your main platform.  
Here are ten clear benefits and technical reasons to use them:

1. **Cost-Efficient Deployment** — Reuse your existing hosting and CI/CD. No separate domain, SSL, or server needed.  
2. **Shared Infrastructure** — Auth, analytics, and runtime dependencies are centralized, lowering maintenance overhead.  
3. **Centralized Maintenance** — Updates to UI packages, design tokens, or tooling propagate to every microsite automatically.  
4. **Stronger Brand Cohesion** — Subsidiaries/affiliates keep unique sections while staying visually consistent with the parent.  
5. **SEO Synergy** — Subpaths inherit domain authority. Internal links amplify cross-discoverability.  
6. **Simplified Content Ops** — One repo means easier review, docs, and change management.  
7. **Easier Cross-Promotion** — Inter-microsite linking boosts session length and reduces bounce.  
8. **Fast Launch for New Projects** — Create folders + `page.tsx` files; ship seasonal or experimental campaigns fast.  
9. **Scoped Customization** — Per-site `layout.tsx` enables local theming without touching the parent layout.  
10. **Scalable Multi-Tenant Pattern** — The structure expands cleanly if you formalize tenants later.

<!-- Divider -->
<p align="center"><img src="assets/divider.svg" width="70%" alt="divider" /></p>

## Language & Compatibility

- **Built for:** Next.js 15 (App Router) + **TypeScript**.  
- Works with **JavaScript**: rename `.tsx` → `.jsx` and remove type annotations (e.g., `: { params: { index: string } }`).  
- Other frameworks (Nuxt, Remix, etc.) use different routing conventions — adapt folder names accordingly.

<!-- Divider -->
<p align="center"><img src="assets/divider.svg" width="70%" alt="divider" /></p>

## Folder Structure

src/ └─ app/ └─ (microsites)/              ← route group (does not appear in the URL) └─ <siteName>/             ← microsite slug (lowercase; e.g., "acme") ├─ layout.tsx           ← optional: local layout (nav/footer for this microsite) ├─ page.tsx             ← /<siteName>  (home / landing) ├─ about/ │  └─ page.tsx          ← /<siteName>/about ├─ services/ │  └─ page.tsx          ← /<siteName>/services ├─ contact/ │  └─ page.tsx          ← /<siteName>/contact └─ page/ └─ 1/ └─ page.tsx       ← /<siteName>/page/1  (example fixed pagination route)

> 💡 **Tip:** Keep folder names **lowercase** for clean, predictable URLs.

<!-- Divider -->
<p align="center"><img src="assets/divider.svg" width="70%" alt="divider" /></p>

## Quick Start

```bash
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

<!-- Divider --><p align="center"><img src="assets/divider.svg" width="70%" alt="divider" /></p>Page Templates (TypeScript)

// src/app/(microsites)/<siteName>/page.tsx
export default function Home() {
  return (
    <main className="mx-auto max-w-5xl px-4 py-12">
      <h1 className="text-3xl font-bold">{'<siteName> Microsite'}</h1>
      <p className="mt-2 text-neutral-600">Welcome to your embedded microsite. Replace this with your hero content.</p>
    </main>
  );
}

// src/app/(microsites)/<siteName>/about/page.tsx
export default function About() {
  return (
    <main className="mx-auto max-w-5xl px-4 py-12">
      <h1 className="text-2xl font-bold">About</h1>
      <p className="mt-2 text-neutral-600">Brief overview of your microsite’s purpose, team, or background.</p>
    </main>
  );
}

// src/app/(microsites)/<siteName>/services/page.tsx
export default function Services() {
  return (
    <main className="mx-auto max-w-5xl px-4 py-12">
      <h1 className="text-2xl font-bold">Services</h1>
      <p className="mt-2 text-neutral-600">Describe your offerings, tiers, or features here.</p>
    </main>
  );
}

// src/app/(microsites)/<siteName>/contact/page.tsx
export default function Contact() {
  return (
    <main className="mx-auto max-w-5xl px-4 py-12">
      <h1 className="text-2xl font-bold">Contact</h1>
      <p className="mt-2 text-neutral-600">Provide an email, form, or other contact method.</p>
    </main>
  );
}

// src/app/(microsites)/<siteName>/page/1/page.tsx
export default function FixedPageOne() {
  return (
    <main className="mx-auto max-w-5xl px-4 py-12">
      <h1 className="text-2xl font-bold">Page 1</h1>
      <p className="mt-2 text-neutral-600">This is a fixed route at /&lt;siteName&gt;/page/1.</p>
    </main>
  );
}

// src/app/(microsites)/<siteName>/page/[index]/page.tsx
export default function Paged({ params }: { params: { index: string } }) {
  return (
    <main className="mx-auto max-w-5xl px-4 py-12">
      <h1 className="text-2xl font-bold">Page {params.index}</h1>
      <p className="mt-2 text-neutral-600">Render paginated content based on the index.</p>
    </main>
  );
}

<!-- Divider --><p align="center"><img src="assets/divider.svg" width="70%" alt="divider" /></p>Microsite Layout (layout.tsx)

import Link from "next/link";

export default function MicrositeLayout({
  children,
}: {
  children: React.ReactNode;
}) {
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

<!-- Divider --><p align="center"><img src="assets/divider.svg" width="70%" alt="divider" /></p>Common Gotchas

404 on click? Folder names and link paths must match exactly.

Lowercase everything. Keeps URLs predictable.

Don’t include route group names in URLs — (microsites) is invisible in routing.

Avoid conflicts: If you add page/[index], remove the fixed /page/1 folder.

Consistent layout: Use mx-auto max-w-5xl px-4 for centered responsive design.


> [!IMPORTANT] This README uses dynamic SVG images (typing banner + gradient dividers). They render on GitHub without scripts.



> [!NOTE] The right-side rail collapses under the main content on mobile automatically.



<!-- Divider --><p align="center"><img src="assets/divider.svg" width="70%" alt="divider" /></p>FAQ

Q: Can I build this in JavaScript instead of TypeScript?
A: Yes — remove types and use .jsx files.

Q: Can each microsite have different styling or animations?
A: Yes — add custom CSS modules or Tailwind configs at the microsite level.

Q: Can I convert this to subdomains?
A: Yes — configure rewrites (e.g., sub.domain.com → /sub) in your deployment platform.

<!-- Divider --><p align="center"><img src="assets/divider.svg" width="70%" alt="divider" /></p>Custom Open License — Microsite System Template

This repository and template represent an original system design for creating embedded
microsites within a parent Next.js application.

You are free to:
 • Use, copy, modify, and adapt this structure for personal or commercial projects on your own repo.
 • Distribute educational or tutorial materials based on this guide.
 • Attribute the original author in any public or published derivative.

You may NOT:
 • Sell, resell, or commercially redistribute this exact system or guide
   (in part or whole) without explicit written permission from the original author.
 • Submit pull requests, forks, or collaborations / modifications intended for upstream integration.

Attribution Requirement:
When reusing this template or substantial parts of its structure or documentation,
please include a clear credit line such as:
  “Based on the Microsite System Template (© 2025 Original Author)”

This license is custom and non-standard. It grants open use and replication rights
while reserving commercial distribution rights to the original creator.

<!-- Divider --><p align="center"><img src="assets/divider.svg" width="60%" alt="divider" /></p><!-- end main column --></td>
<td valign="top" width="32%">

<!-- =========================
     RIGHT INFO RAIL (no personal info)
     ========================= --><h3>Tech Stack</h3>
<p>
  <img src="https://skillicons.dev/icons?i=next,react,ts,tailwind" height="36" />
</p><h3>Feature Matrix</h3>Feature	Microsite Template	Other Setup

Clean folder routing	✔️	~
Documented page stubs	✔️	❌
Per-site layout	✔️	❌
SEO-friendly subpaths	✔️	~
Cross-promotion ready	✔️	❌


<h3>Data Snapshot (Example)</h3>Metric	Value

Default pages	4
Example pagination	1
Routing depth	3
Build script	yarn build
Deploy target	Vercel


<!-- Placeholder for small looping stickers --><p align="center">
  <!-- <img src="YOUR_SMALL_CYBER_GIF" height="54" /> -->
</p><!-- end rail --></td>

  </tr>
</table>
```
---

Add this file: assets/divider.svg

Put this file in an assets/ folder at the repo root. It animates a cyan→violet→magenta gradient bar and works on GitHub.

<svg viewBox="0 0 1200 12" xmlns="http://www.w3.org/2000/svg" width="1200" height="12" role="img" aria-label="divider">
  <defs>
    <linearGradient id="g" x1="0" x2="1">
      <stop offset="0%" stop-color="#00E5FF"/>
      <stop offset="50%" stop-color="#8A2BE2"/>
      <stop offset="100%" stop-color="#FF00CC"/>
    </linearGradient>
  </defs>
  <rect x="0" y="5" width="1200" height="2" fill="url(#g)" opacity="0.65"/>
  <rect x="-1200" y="5" width="1200" height="2" fill="url(#g)">
    <animate attributeName="x" from="-1200" to="1200" dur="6s" repeatCount="indefinite" />
  </rect>
</svg>
