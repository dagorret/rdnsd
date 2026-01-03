# TODO.md

## Estado actual
- Forwarder DNS funcional (Fase 1 sin DNSSEC)
- Problemas identificados al introducir DNSSEC (SERVFAIL no controlado)

---

## Objetivo general
Construir un **DNS forwarder moderno, puro y duro**, con foco en:
- rendimiento
- control explícito
- extensibilidad
- base sólida para Home Lab → Universidad → ISP

---

## FASE 1 — CORE DNS (ACTUAL)

### Red y protocolo
- [x] UDP listener
- [x] TCP fallback
- [x] EDNS(0) básico
- [ ] Robustecer manejo de paquetes inválidos
- [ ] Tests de truncation y TCP

### Cache
- [x] Cache TTL
- [x] Negative cache
- [ ] Separar claves correctamente (flags)
- [ ] Serve-stale controlado

### Upstreams
- [x] Pool de upstreams
- [x] Timeouts y retries
- [ ] Health-check con backoff

### Seguridad básica
- [ ] Rate limit por IP
- [ ] Anti-amplificación

### Observabilidad
- [x] Métricas Prometheus
- [ ] Logs estructurados con sampling

---

## FASE 2 — DNSSEC (EN DISEÑO)

### Diseño previo
- [ ] Definir modos:
  - passthrough
  - validate-if-possible
  - strict

### Crates planificados
- [ ] dns-wire
- [ ] dnssec-types
- [ ] dnssec-validate (etapas 1, 2, 3)

### Integración futura
- [ ] Control explícito de SERVFAIL
- [ ] Cache separada validado/no validado

---

## FASE 3 — BLOQUEO Y PANEL

### Policy engine
- [ ] Block/allow lists
- [ ] Reglas por cliente/subred
- [ ] Acciones (NXDOMAIN, redirect)

### Control-plane
- [ ] API admin (Axum)
- [ ] Persistencia (SQLite)
- [ ] UI mínima

---

## BACKLOG FUTURO
- DNSSEC completo
- DoT / DoH
- HA / Anycast
- Recursor iterativo

