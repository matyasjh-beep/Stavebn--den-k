# Stavební deník — Demo

Digitální stavební deník pro stavební firmy. Čistá statická aplikace (HTML + CSS + JS), žádný backend ani instalace.

## Stránky

| Soubor | Popis |
|--------|-------|
| `index.html` | Přihlášení — dvě role (Stavbyvedoucí / Nadřízený) |
| `dashboard.html` | Přehled staveb stavbyvedoucího |
| `denik.html` | Zápis do deníku (počasí, pracovníci, mechanizace, práce) |
| `kalendar.html` | Kalendář s poznámkami |
| `prehled.html` | Přehled a statistiky stavby |
| `pracovnici.html` | Správa pracovníků na stavbě |
| `nastaveni.html` | Nastavení aplikace |
| `profil.html` | Profil uživatele |
| `dashboard-nadrizeny.html` | Přehled všech staveb pro nadřízeného |
| `denik-nadrizeny.html` | Read-only náhled deníku + export do PDF |

## Demo přihlášení

- **Stavbyvedoucí** — klikni „Demo – Stavbyvedoucí" na přihlašovací stránce
- **Nadřízený / Ředitel** — klikni „Demo – Nadřízený / Ředitel"

## Datový model (localStorage)

Aplikace ukládá vše do `localStorage` v prohlížeči. Klíče:

| Klíč | Obsah |
|------|-------|
| `stavby` | Pole objektů staveb `{id, nazev, adresa, stav, ...}` |
| `zaznamy` | Pole zápisů deníku `{id, stavbaId, datum, pocasi, popis, pracovnici[], mechanizace[], foto[]}` |
| `pracovnici` | Pole pracovníků `{id, jmeno, pozice, telefon}` |
| `kalendarNotes` | Objekt `{datum: poznamka}` |
| `user` | Přihlášený uživatel `{role: "stavbyvedouci"|"nadrizeny", jmeno}` |

## Role uživatelů

- **Stavbyvedoucí** — plný přístup k zápisům, pracovníkům, kalendáři
- **Nadřízený / Ředitel** — read-only náhled všech staveb, export PDF

## Technologie

- Čisté HTML5 + CSS3 + Vanilla JavaScript
- Žádný backend, žádná instalace
- Data v `localStorage` (pro mobilní app nahradit SQLite / REST API)
- Export záznamu do PDF přes `window.print()`
- Styl: vlastní CSS (`style.css`), bez frameworků

## Doporučení pro mobilní aplikaci

Tato webová verze slouží jako **design a UX prototyp**. Pro mobilní aplikaci:

1. **Data** — nahradit `localStorage` za SQLite (React Native) nebo Room DB (Android) nebo CoreData (iOS)
2. **Synchronizace** — přidat REST API / Firebase pro sdílení mezi uživateli
3. **Fotodokumentace** — přidat přístup ke kameře a galerii
4. **Offline režim** — aplikace by měla fungovat bez internetu, sync při připojení
5. **Push notifikace** — upozornění na nové záznamy od stavbyvedoucích
6. **Export** — PDF nebo CSV export záznamů

## Struktura navigace

```
index.html (přihlášení)
├── dashboard.html (stavbyvedoucí)
│   ├── denik.html
│   ├── kalendar.html
│   ├── prehled.html
│   ├── pracovnici.html
│   ├── profil.html
│   └── nastaveni.html
└── dashboard-nadrizeny.html (nadřízený)
    └── denik-nadrizeny.html
```
