# planeamientos.md

## Punto de partida

Parto de una experiencia real:
- El DNS forwarder base funciona.
- Al introducir DNSSEC, el sistema se volvió frágil.
- El SERVFAIL apareció sin control claro.

Conclusión: **DNSSEC no puede meterse "de golpe"**.

---

## Decisión clave

Separar el proyecto en capas:

1. **Core DNS estable**
2. **DNSSEC como librería independiente**
3. **Control y bloqueo como capa superior**
4. **UI como último paso**

Esto evita:
- deuda técnica temprana
- forks difíciles
- acoplamiento innecesario

---

## Visión del proyecto

No existe en el mercado un DNS:
- minimalista
- rápido
- observable
- con control explícito
- diseñado desde el dataplane hacia arriba

Este proyecto apunta a llenar ese espacio.

---

## Filosofía técnica

- DNS primero, UI después
- Performance > features
- Política explícita > magia implícita
- Crates pequeñas, testeables, aisladas

---

## DNSSEC: enfoque conceptual

### Problema observado
DNSSEC mezcla:
- criptografía
- red
- cache
- política

Eso vuelve el sistema opaco.

### Solución propuesta
- DNSSEC offline primero (sin red)
- Validación de RRsets aislada
- Chain-of-trust después
- Política configurable

---

## Estados claros de validación

- Secure
- Insecure
- Indeterminate
- Bogus

Cada estado tiene impacto explícito en la respuesta.

---

## Referencias conceptuales

- RFC 1034 / 1035 — DNS base
- RFC 4033 / 4034 / 4035 — DNSSEC
- RFC 6840 — DNSSEC operational practices
- Unbound resolver architecture
- Knot Resolver design notes
- PowerDNS Recursor documentation

---

## Dónde estoy

- Core forwarder funcional
- DNSSEC identificado como riesgo técnico
- Arquitectura redefinida

## Hacia dónde voy

- Core robusto
- DNSSEC controlable
- Bloqueo y panel como consecuencia natural
- Escalabilidad real

