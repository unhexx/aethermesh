# AetherMesh Design System & Dashboard UX

**Version**: 0.1  
**Updated after deep research** of Tailscale Admin Console, NetBird Dashboard, Linear, Vercel, and modern infrastructure UI best practices (2026).

## 1. Design Goals

- **Operator-first**: Dark mode primary, high information density without clutter, clear status at a glance.
- **Ethical & professional**: Trustworthy, calm, modern “aether” aesthetic — not gaming neon, not enterprise grey.
- **Accessible**: WCAG 2.1 AA, keyboard navigation, screen-reader friendly.
- **Responsive**: Desktop primary, usable on tablet/mobile for status checks.
- **Fast to implement**: Built on shadcn/ui + Tailwind so agents can ship UI quickly.

## 2. Brand Identity

- **Name**: AetherMesh
- **Essence**: The invisible fabric that connects your devices securely and effortlessly.
- **Voice**: Clear, confident, technical but approachable. No hype.

### Color Palette (Tailwind tokens)

```css
/* Primary accent — ethereal cyan */
--aether-cyan: 187 95% 53%;          /* #22d3ee */
--aether-cyan-foreground: 222 47% 11%;

/* Secondary — deep indigo */
--aether-indigo: 239 84% 67%;        /* #6366f1 */

/* Neutrals — slate */
--background: 222 47% 6%;            /* near #0f172a */
--foreground: 210 40% 98%;
--card: 222 47% 8%;
--muted: 217 33% 17%;
--border: 217 33% 17%;

/* Status */
--success: 142 71% 45%;              /* green */
--warning: 38 92% 50%;               /* amber */
--destructive: 0 84% 60%;            /* red */
```

- Light mode supported but secondary.
- Accent used sparingly for CTAs, status indicators, active states.

### Typography

- **UI**: Inter or Geist Sans (system fallback stack).
- **Mono**: JetBrains Mono / Geist Mono for keys, IPs, logs.
- Scale: 14px base, clear hierarchy (text-sm / text-base / text-lg / text-xl).

### Iconography

- Lucide React icons exclusively.
- Consistent stroke width, size tokens (16 / 20 / 24).

## 3. Component Library

Base: **shadcn/ui** (Radix primitives + Tailwind).

Key custom components:
- `PeerCard` / `PeerTable` — status badge (online / offline / relayed), latency, OS icon, connection type.
- `NetworkTopology` — React Flow based interactive graph (nodes = peers, edges = direct / relayed).
- `PolicyEditor` — visual group + rule builder (source → destination → action).
- `EnrollmentKeyCard` — with QR, copy, expiry, usage counter.
- `StatusBadge`, `ConnectionTypePill`, `MetricSparkline`.

## 4. Information Architecture & Key Screens

**Sidebar Navigation** (collapsible):
- Overview
- Peers / Agents
- Networks
- Access Control (ACLs / Policies)
- DNS
- Enrollment Keys
- Settings (account, domains, integrations)
- (later) Audit Log, Users, Billing

**Overview Dashboard**:
- High-level KPIs: Online peers, P2P %, average latency, last config push.
- Recent activity feed.
- Quick actions: Create enrollment key, Invite user.

**Peers View**:
- Table + card toggle.
- Filters: status, OS, tags, connection type.
- Detail drawer: full metadata, applied routes/ACLs, live metrics, “Force reconnect”.

**Topology View**:
- Interactive graph showing current mesh state.
- Color-coded edges (green = direct, amber = relayed).

**Policy Editor**:
- Group-based ACLs (inspired by best of Tailscale + NetBird).
- Visual + JSON/YAML toggle for power users.

## 5. UX Principles Specific to Mesh Networking

1. Always show connection quality (direct vs relayed) — users care about latency.
2. One-click “Copy install command” per OS with pre-filled setup key.
3. Clear empty states with progressive disclosure (“Add your first agent”).
4. Real-time updates via WebSocket / SSE — no manual refresh for peer status.
5. Destructive actions (delete peer, revoke key) require confirmation + reason.
6. Dark mode default; respect system preference + manual toggle.

## 6. Implementation Notes for Agents

- Use shadcn/ui CLI to scaffold components.
- Prefer server components + React Query / SWR for data.
- Real-time: WebSocket connection to Management service.
- Topology: `@xyflow/react` (React Flow).
- Charts: Recharts or Tremor for metrics.
- Forms: React Hook Form + Zod.

## 7. Future Design Extensions

- Mobile-responsive agent status PWA.
- Command palette (⌘K) for power users.
- Theme customization (accent color) for white-label / multi-tenant.

---

*This design system is mandatory for all Dashboard work. Deviations require Orchestrator approval.*
