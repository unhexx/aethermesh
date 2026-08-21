# AetherMesh Vision / Product Requirements Document (PRD)

**Version**: 0.1  
**Status**: Bootstrap / Agentic-ready  
**Last updated**: 2026-08-21

## 1. Problem Statement

Traditional VPNs and even modern mesh solutions suffer from:
- Complex, error-prone configuration of peers, keys, routes and firewalls.
- Lack of true centralized, real-time management of agent settings (policies, DNS, routes, ACLs, labels, updates) for self-hosted deployments.
- High operational burden for multi-device, multi-OS, mobile + remote endpoint networks.
- Closed control planes (Tailscale) or incomplete self-host experiences.
- Steep learning curve or fragmented tools for homelabs, small teams, MSPs and DevOps.

Users want a **private WireGuard mesh** that “just works” with one action, while retaining full sovereignty and the ability to push configuration centrally from a beautiful dashboard.

## 2. Solution

**AetherMesh** is a modern self-hosted / SaaS WireGuard-based mesh networking platform with effortless centralized agent management.

- One virtual private network per user or team.
- Agents (Linux, Windows, macOS first; mobile later) connect outbound-only.
- All settings (ACL policies, routes, DNS, labels, updates) are managed centrally and pushed to agents.
- Preferred P2P WireGuard tunnels + encrypted relay fallback.
- Microservices architecture + Docker Compose for one-action deployment.
- Fully prepared for autonomous agentic development loops until v1.0 and beyond.

**Tagline**: *Your private mesh network with effortless centralized agent control.*

## 3. Target Users & Personas

1. **Homelab & Power Users** — want simple private networking across servers, VMs, laptops, phones without cloud dependency.
2. **Small / Medium Teams & Startups** — need secure zero-trust access to internal resources, remote developers, CI runners.
3. **MSPs & DevOps** — manage many client networks or infrastructure fleets with consistent policies.
4. **Privacy / Sovereignty-focused organizations** — require full self-hosting and data ownership (EU-friendly, no US CLOUD Act dependency on control plane).

## 4. Key Differentiators (vs Tailscale / NetBird / Headscale / ZeroTier)

- **One-action install** as non-negotiable first-class goal (`curl | bash` or `docker compose up`).
- **Strong centralized agent configuration push** (not just network map — full settings lifecycle).
- **Original independent implementation** (learn from best practices, write our own code).
- **Agentic-first repository design** — Orchestrator + specialized agents can drive the project to release autonomously.
- **Native multi-tenancy readiness** and domains under `*.exception.expert`.
- Clean, modern design system focused on operator experience.

## 5. MVP Success Criteria (v1.0)

Aligned with `agentic/ORCHESTRATOR.md`:

- `docker compose up -d` brings up full control plane (auth, management, signal, relay, dashboard + deps).
- User can register/login, create a virtual network, generate enrollment / setup key.
- Linux agent can enroll, join the network, form WireGuard mesh connectivity (P2P preferred).
- Basic centralized config push works (DNS servers, simple routes, labels).
- Dashboard shows peers/agents status and allows basic management.
- `./install.sh` (or equivalent) succeeds on clean Linux VM using a domain under `.exception.expert`.

## 6. Non-Goals (for v1.0)

- Full multi-tenant SaaS billing & advanced enterprise features.
- Mobile clients (iOS/Android) — post-MVP.
- Post-quantum crypto (research later).
- Full Layer-2 bridging (ZeroTier style).

## 7. Success Metrics

- Time-to-first-mesh < 5 minutes for a technical user.
- Agent enrollment success rate > 95% on supported platforms.
- P2P connection rate > 80% in typical NAT scenarios.
- Documentation and agentic workflow allow a new agent wave to ship features without human code writing for core paths.

## 8. Brand & Domains

- Brand: **AetherMesh**
- Primary domain pattern: `aethermesh.exception.expert`, `mesh.exception.expert`, any `*.exception.expert`
- Visual identity: ethereal, modern, professional infrastructure tool (see `docs/DESIGN.md`).

---

*This document is the north star for all architecture, roadmap and agentic decisions.*
