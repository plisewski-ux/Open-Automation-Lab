# ADR-001 - Wybór platformy VPS

## Status

Accepted

## Data

2026-07-02

## Kontekst

Potrzebujemy środowiska R&D do budowy platformy automatyzacji.

Wymagania:

- niski koszt utrzymania,
- pełny dostęp root,
- możliwość uruchamiania Dockera,
- środowisko działające 24/7,
- możliwość późniejszej rozbudowy.

## Rozważane opcje

- Mikrus
- Hetzner Cloud
- OVH
- Oracle Cloud Free

## Decyzja

Wybrano Mikrus VPS 2.1.

## Uzasadnienie

- bardzo niski koszt,
- wystarczające parametry do rozpoczęcia projektu,
- możliwość upgrade'u,
- dobre opinie społeczności,
- idealny do projektów R&D.

## Konsekwencje

### Zalety

- niski koszt
- prostota
- Docker

### Wady

- ograniczona ilość RAM
- ograniczony dysk

## Przegląd decyzji

Po wdrożeniu n8n oraz pozostałych usług należy ocenić wykorzystanie zasobów i zdecydować, czy konieczny jest upgrade do wyższego planu.