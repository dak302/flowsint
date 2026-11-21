# Flowsint: brag plan

**What it is:** an open-source OSINT graph tool. You drop in one entity, run enrichers on it, and every result becomes a new node you can pivot from.
**Who it's for:** investigators, journalists and security researchers mapping what's behind a domain, IP, email or username.
**What sets it apart:** the investigation *is* the graph. Right-click any node and run an enricher (`domain_to_subdomains`, `domain_to_ip`, `ip_to_asn`…), or chain enrichers into a reusable flow. Self-hosted with `make prod`.
**Visual hook:** one lonely node on a dotted canvas that turns into a whole map.
**Share caption:** "Start with one domain. End with the map."

## Angle
Show one domain unfold, live: one node, one right-click, and the graph grows wave by wave. The product does the talking.

## Tone
`default`: punchy, clean, soft transitions. The investigative dark UI provides the mood.

## Visual identity (from the source)
- Canvas `#161616` with a 1px dot grid every 24px (graph `BACKGROUND_DARK`, `--dot-spacing`); app chrome `#1f2123`, borders and muted `#2e2f31`.
- Accent: brand coral `#ec615e` (`--primary`), the only saturated UI accent. Highlighted edges use `rgba(255,115,0,.68)`.
- Nodes mirror `node-renderer.ts`: filled circle in the type color, subtle border `rgba(222,222,222,.13)`, white Lucide icon at 0.9 alpha, label in a rounded pill `rgba(32,32,32,.75)`. Edge labels use the real relationship names (`HAS_SUBDOMAIN`, `RESOLVES_TO`, `BELONGS_TO`, `HAS_PORT`, `HAS_WHOIS`, `REGISTERED_BY`).
- Type colors from `node-display-settings.ts`: domain `#66A892`, ip `#5AA1C8`, asn `#D97474`, port `#4CB5DA`, whois `#9B6F9B`, email `#8E7CC3`, username `#8B83C1`, socialaccount `#A76DAA`, cryptowallet `#D4B030`, organization `#BCA18A`, individual `#4C8EDA`.
- Context menu mirrors `node-context-menu.tsx`: header "label - type", Enrichers/Flows tabs, search field, rows with Zap + BadgeCheck + name + description. Descriptions are the enrichers' real docstrings.
- Flow cards mirror `enricher-node.tsx`: class name (`SubdomainEnricher`, `ResolveEnricher`, `IpToAsnEnricher`) plus docstring.
- Fonts: Inter (`--font-sans`) and JetBrains Mono (`--font-mono`). Logo: `public/logo-wordmark.svg`.

**Placeholder data:** every entity is fictional and uses reserved documentation ranges: `example.com` and its subdomains, IPs from 203.0.113.0/24 and 198.51.100.0/24, AS64500, `admin@example.com`. No real targets appear.

## Music
120 BPM in 4/4, so one beat is 0.5s and one bar is 2s, all counted from frame 0. Key: A minor, progression Am–F–C–G. Bar 1 is pad plus pluck only. Drums come in at 3.0s on the first cut. Node pops are soft plucks on A-minor-pentatonic notes, placed on 8th-note positions. Final chord at 17.0s rings out to 21s.

## Storyboard (21s, 30fps = 630 frames)
| # | Time | Beat | Scene |
|---|---|---|---|
| 1 Hook | 0.0–3.0 | 0–6 | Empty dotted canvas. `example.com` node pops in at 0.25s. Headline types: **"Start with one domain."** |
| 2 Reveal | 3.0–6.0 | 6–12 | Headline: **"Right-click. Run an enricher."** Context menu opens beside the node (3.25). Cursor glides in, hovers `domain_to_subdomains`, clicks on beat 10 (5.0s). Menu closes. |
| 3 Highlight: graph grows | 6.0–11.0 | 12–22 | Wave 1 (5.5s): 5 subdomains on HAS_SUBDOMAIN. Wave 2 (7.0): 3 IPs on RESOLVES_TO. Wave 3 (8.5): AS64500 on BELONGS_TO plus ports 443/22 on HAS_PORT. Wave 4 (9.5): whois and `admin@example.com`. Camera eases out. Headlines: **"Every result becomes a node."** (6.0) then **"Every node is a new lead."** (8.5). |
| 4 Highlight: flows | 11.0–15.0 | 22–30 | Graph dims. Flow cards slide in: Domain → SubdomainEnricher → ResolveEnricher → IpToAsnEnricher, with animated edges. The Run button is clicked on beat 27 (13.5s) and states flip to "completed" one by one. Headline: **"Chain enrichers into flows."** |
| 5 Highlight: breadth | 15.0–17.0 | 30–34 | Zoom out to a larger graph with emails, usernames, socials, wallets and orgs. Headline: **"Domains. IPs. Emails. Wallets."** |
| 6 Outro | 17.0–21.0 | 34–42 | Wordmark logo. **"Open-source OSINT graph exploration."** Mono: `git clone reconurge/flowsint && make prod`. |

Transitions: headline lines swap out then in (old fades up, new types in). No crossfades between busy layouts.
