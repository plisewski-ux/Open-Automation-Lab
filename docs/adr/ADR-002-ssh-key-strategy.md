# ADR-002 - SSH Key Strategy

## Status

Accepted

## Date

2026-07-02

## Context

Open Automation Lab będzie rozwijany przez dłuższy czas i będzie obejmował
wiele niezależnych środowisk oraz usług wymagających dostępu SSH.

Należy przyjąć jednolitą strategię zarządzania kluczami SSH.

## Decision

Przyjęto następujące zasady:

- wykorzystywany będzie algorytm ED25519,
- każde środowisko otrzymuje własną parę kluczy,
- klucze posiadają jednoznaczne nazwy,
- prywatne klucze nigdy nie są kopiowane pomiędzy urządzeniami,
- administratorzy posiadają własne konta systemowe,
- logowanie użytkownika root zostanie wyłączone po zakończeniu migracji na logowanie kluczem SSH.

### Nazewnictwo

Przykładowe nazwy kluczy:

- id_ed25519_openautomationlab
- id_ed25519_github
- id_ed25519_homelab
- id_ed25519_router

## Consequences

### Advantages

- możliwość niezależnego unieważniania kluczy,
- prostsze zarządzanie dostępem,
- większe bezpieczeństwo,
- łatwiejszy audyt.

### Disadvantages

- większa liczba kluczy do zarządzania,
- konieczność prowadzenia dokumentacji.

## Alternatives Considered

### Jeden wspólny klucz SSH

Odrzucono.

Powód:

Utrata jednego klucza wymuszałaby wymianę dostępu do wszystkich środowisk.

## Review

Strategia będzie weryfikowana przy dodawaniu kolejnych środowisk wymagających dostępu SSH.