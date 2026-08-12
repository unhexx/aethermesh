# AetherMesh

**AetherMesh** — современный self-hosted / SaaS mesh-networking платформа с лёгким централизованным управлением агентами на remote endpoints и мобильных устройствах.

Создавайте персональную защищённую виртуальную сеть (WireGuard-based mesh) для всех ваших устройств и серверов. Один клик — агенты подключены, настройки управляются централизованно из dashboard.

**Домены**: можно использовать subdomain третьего уровня в зоне `.exception.expert` (например `aethermesh.exception.expert`, `mesh.exception.expert`).

## Ключевая ценность

- **Одна виртуальная сеть** на пользователя/команду
- **Централизованное управление настройками агентов** (политики, маршруты, DNS, ACL, labels, updates) — push из web-UI
- Remote endpoints + mobile devices в одной сети
- Микросервисная архитектура + Docker Compose (все зависимости)
- Установка в **одно действие**
- Независимая реализация на лучших мировых практиках (Tailscale / NetBird / ZeroTier inspired, собственный код и бренд)
- Полностью готово к **автономной agentic-loop разработке** до первого релиза

## Быстрый старт (концепт)

```bash
# One-action (будет реализован)
curl -fsSL https://get.aethermesh.exception.expert | bash

# Или
git clone https://github.com/unhexx/aethermesh.git
cd aethermesh
cp .env.example .env
# DOMAIN=aethermesh.exception.expert
docker compose up -d
```

## Архитектура (high-level)

См. [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md)

- **Data plane**: WireGuard (P2P preferred + encrypted relay fallback)
- **Control plane microservices**: auth, management-api, signal, relay, dashboard, dns, policy
- **Agents**: Go binary (Linux/Win/macOS first), outbound-only, central config push

## Agentic Development Loop

Репозиторий **специально спроектирован** для полностью автономной разработки агентами до v1.0.

См. папку [agentic/](agentic/):

- **ORCHESTRATOR.md** — оркестратор перед каждой волной анализирует состояние и ставит конкретные задачи с acceptance criteria
- **AGENTS.md** — роли агентов (Backend, Frontend, Agent-Client, DevOps, Tester, Debugger, Reviewer)
- **WORKFLOW.md** — полный цикл: Orchestrator → Tasks → Agents execute → PR/Test/Review → Fix → Next wave
- BACKLOG.md + SPRINT templates

**Все задачи разработки, отладки и исправления ошибок выполняются агентами самостоятельно.** Оркестратор только ставит задачи перед началом следующей волны.

## Структура репозитория

```
.
├── README.md
├── docker-compose.yml
├── .env.example
├── install.sh
├── docs/
│   ├── VISION.md          # PRD / Vision
│   ├── ARCHITECTURE.md
│   ├── ROADMAP.md
│   ├── DEPLOYMENT.md
│   ├── SECURITY.md
│   └── API.md
├── agentic/
│   ├── ORCHESTRATOR.md
│   ├── AGENTS.md
│   ├── WORKFLOW.md
│   ├── BACKLOG.md
│   ├── SPRINT_0.md
│   └── prompts/
└── services/              # (будет реализовано агентами)
    ├── auth/
    ├── management/
    ├── signal/
    ├── relay/
    ├── dashboard/
    └── agent/
```

## Brand & Domains

**AetherMesh** — Your private mesh network with effortless centralized agent control.

Доступные subdomain: `*.exception.expert` (например aethermesh.exception.expert).

Repo: https://github.com/unhexx/aethermesh

**Оркестратор**: начинайте с Sprint 0 после наполнения docs.
