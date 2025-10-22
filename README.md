# Next.js Microsite Setup Guide (TypeScript Template)








> Build a small “microsite” inside your main Next.js app (e.g. /brand, /press, /docs) with clean, URL-mirroring folders and a local layout.
This guide provides a TypeScript-based blank template showing the structure, page files, and benefits of integrating microsites into larger applications.




---

Table of Contents

Overview

Why Microsites? (Benefits & Use Cases)

Language & Compatibility

Folder Structure

Quick Start

Page Templates (TypeScript)

Microsite Layout (layout.tsx)

Common Gotchas

FAQ

Custom Open License — Microsite System Template



---

Overview

A microsite is a self-contained group of pages living under a single path like /<siteName> inside your primary Next.js app.
It uses the same stack, styles, and build process but can have its own navigation, design, and layout — perfect for affiliate brands, sub-projects, or special campaigns.


---

Why Microsites? (Benefits & Use Cases)

Microsites aren’t just smaller websites — they’re a smart, modular extension of your main platform.
Here are ten clear benefits and technical reasons to use them:

1. Cost-Efficient Deployment

A microsite reuses your existing hosting and CI/CD pipeline. No separate domain, SSL, or server needed.



2. Shared Infrastructure

All microsites run under the same app instance, so performance, authentication, and analytics systems are shared automatically.



3. Centralized Maintenance

Updates to dependencies, UI components, or design tokens apply across all microsites simultaneously, keeping everything in sync.



4. Stronger Brand Cohesion

Sub-brands, affiliates, and subsidiaries maintain unique sections while staying visually and technically consistent with the parent brand.



5. SEO Synergy

Search engines recognize each microsite as part of the main domain, improving domain authority and discoverability for all related pages.



6. Simplified Content Management

Content editors and developers work inside one unified repository, streamlining approval, review, and deployment workflows.



7. Easier Cross-Promotion

Internal linking between microsites increases engagement and retention while reducing bounce rates.



8. Fast Launch for New Projects

Spinning up a new microsite requires only a folder and a few pages—ideal for seasonal campaigns or temporary brand collaborations.



9. Scoped Customization

Each microsite can have its own layout, theme, or navigation while safely isolating those customizations from the parent app.



10. Scalable Multi-Tenant Architecture

This pattern supports future expansion into a true multi-tenant ecosystem with minimal structural change.





---

Language & Compatibility

Built for Next.js 15 (App Router) using TypeScript.

Folder structure also works for JavaScript projects, but you’ll need to:

Rename files from .tsx → .jsx,

Remove TypeScript annotations (e.g., : { params: { index: string } }).


Other frameworks (e.g., Nuxt, Remix) have different routing conventions and will need adjustments.



---

Folder Structure

src/
└─ app/
   └─ (microsites)/              ← route group (does not appear in the URL)
      └─ <siteName>/             ← microsite slug (lowercase; e.g., "acme")
         ├─ layout.tsx           ← optional: local layout (nav/footer for this microsite)
         ├─ page.tsx             ← /<siteName>  (home / landing)
         ├─ about/
         │  └─ page.tsx          ← /<siteName>/about
         ├─ services/
         │  └─ page.tsx          ← /<siteName>/services
         ├─ contact/
         │  └─ page.tsx          ← /<siteName>/contact
         └─ page/
            └─ 1/
               └─ page.tsx       ← /<siteName>/page/1  (example fixed pagination route)

> 💡 Always use lowercase folder names for consistent, clean URLs.




---

Quick Start

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

# 5) Deploy normally (e.g. Vercel)
#   Routes automatically served under /<siteName>/


---

Page Templates (TypeScript)

Home (page.tsx)

export default function Home() {
  return (
    <main className="mx-auto max-w-5xl px-4 py-12">
      <h1 className="text-3xl font-bold">{"<siteName> Microsite"}</h1>
      <p className="mt-2 text-neutral-600">
        Welcome to your embedded microsite. Replace this with your hero content.
      </p>
    </main>
  );
}

About (about/page.tsx)

export default function About() {
  return (
    <main className="mx-auto max-w-5xl px-4 py-12">
      <h1 className="text-2xl font-bold">About</h1>
      <p className="mt-2 text-neutral-600">
        Brief overview of your microsite’s purpose, team, or background.
      </p>
    </main>
  );
}

Services (services/page.tsx)

export default function Services() {
  return (
    <main className="mx-auto max-w-5xl px-4 py-12">
      <h1 className="text-2xl font-bold">Services</h1>
      <p className="mt-2 text-neutral-600">
        Describe your offerings, tiers, or features here.
      </p>
    </main>
  );
}

Contact (contact/page.tsx)

export default function Contact() {
  return (
    <main className="mx-auto max-w-5xl px-4 py-12">
      <h1 className="text-2xl font-bold">Contact</h1>
      <p className="mt-2 text-neutral-600">
        Provide an email, form, or other contact method.
      </p>
    </main>
  );
}

Fixed Pagination (page/1/page.tsx)

export default function FixedPageOne() {
  return (
    <main className="mx-auto max-w-5xl px-4 py-12">
      <h1 className="text-2xl font-bold">Page 1</h1>
      <p className="mt-2 text-neutral-600">
        This is a fixed route at /&lt;siteName&gt;/page/1.
      </p>
    </main>
  );
}

Dynamic Pagination (page/[index]/page.tsx)

export default function Paged({ params }: { params: { index: string } }) {
  return (
    <main className="mx-auto max-w-5xl px-4 py-12">
      <h1 className="text-2xl font-bold">Page {params.index}</h1>
      <p className="mt-2 text-neutral-600">
        Render paginated content based on the index.
      </p>
    </main>
  );
}


---

Microsite Layout (layout.tsx)

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


---

Common Gotchas

404 on click? Folder names and link paths must match exactly.

Lowercase everything. Keeps URLs predictable.

Don’t include route group names in URLs (the (microsites) folder is invisible in routing).

Avoid conflicts: If you add [index] pagination, remove the fixed /page/1 folder.

Consistent layout: Use mx-auto max-w-5xl px-4 for centered responsive design.



---

FAQ

Q: Can I build this in JavaScript instead of TypeScript?
A: Yes — remove types and use .jsx files.

Q: Can each microsite have different styling or animations?
A: Yes — add custom CSS modules or Tailwind configs at the microsite level.

Q: Can I convert this to subdomains?
A: Yes — configure rewrites (e.g., sub.domain.com → /sub) in your deployment platform.


---

Custom Open License — Microsite System Template

This repository and template represent an original system design for creating embedded
microsites within a parent Next.js application.

You are free to:
 • Use, copy, modify, and adapt this structure for personal or commercial projects on your own repo.
 • Distribute educational or tutorial materials based on this guide.
 • Attribute the original author in any public or published derivative.

You may NOT:
 • Sell, resell, or commercially redistribute this exact system or guide
   (in part or whole) without explicit written permission from the original author.
 • Submit pull requests, forks, or collaborations / modifications.

Attribution Requirement:
When reusing this template or substantial parts of its structure or documentation,
please include a clear credit line such as:
  “Based on the Microsite System Template (© 2025 Original Author:Queen_00)”

This license is custom and non-standard. It grants open use and replication rights
while reserving commercial distribution rights to the original creator.
