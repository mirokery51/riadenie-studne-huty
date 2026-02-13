# Riadenie studne Huty

Monorepo pre riadenie a monitorovanie studne. Projekt je rozdeleny na 4 casti:
- PLC (autonomna logika v budke)
- ESP monitor (UI, diagnostika, lokalne ovladanie)
- Supervisor (remote + internet integracia)
- Simulacia (testy a scenare)

## Struktura
- `plc/` - ESP-IDF PLC
- `monitor/` - ESP monitor
- `supervisor/` - remote a internet integracia
- `sim/` - simulacie a testovacie scenare
- `shared/` - spolocne protokoly, schemy, konfiguracie
- `docs/` - architektura, poziadavky, test plan, ADR

## Start
Pozri `docs/requirements.md` a `docs/architecture.md`.
