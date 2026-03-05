# Irena – strona na GitHub Pages

## Wrzucenie na GitHub Pages

1. Załóż repozytorium na GitHubie (np. `irena` lub `twoja-nazwa.github.io`).
2. W folderze projektu w terminalu:
   ```bash
   git init
   git add index.html
   git commit -m "Strona Irena"
   git branch -M main
   git remote add origin https://github.com/TWOJ_LOGIN/nazwa-repo.git
   git push -u origin main
   ```
3. Na GitHubie: **Settings → Pages** → Source: **Deploy from a branch** → Branch: **main** → folder **/ (root)** → Save.
4. Strona będzie pod adresem: `https://twoja-nazwa.github.io/nazwa-repo/` (albo `https://twoja-nazwa.github.io/` jeśli repo nazywa się `twoja-nazwa.github.io`).

## Podłączenie domeny z nazwa.pl

### Co musisz mieć z nazwa.pl

- **Domena** – np. `irena.pl` lub `twojadomena.pl`
- **Panel DNS** – w nazwa.pl: **Moje usługi → Domeny → [Twoja domena] → Zarządzaj → DNS / Rekordy DNS** (lub „Strefa DNS”, „Ustawienia DNS”).

### Rekordy DNS do ustawienia w nazwa.pl

**Opcja A – domena wskazuje na GitHub Pages (bez www):**

| Typ | Nazwa (Host) | Wartość (Points to) | TTL |
|-----|--------------|---------------------|-----|
| A   | @            | 185.199.108.153     | 3600 |
| A   | @            | 185.199.109.153     | 3600 |
| A   | @            | 185.199.110.153     | 3600 |
| A   | @            | 185.199.111.153     | 3600 |

**Opcja B – subdomena www (np. www.twojadomena.pl):**

| Typ   | Nazwa (Host) | Wartość (Points to)     | TTL  |
|-------|--------------|-------------------------|------|
| CNAME | www          | twoja-nazwa.github.io  | 3600 |

*(zamień `twoja-nazwa` na swoją nazwę użytkownika GitHub)*

**Jeśli chcesz i „gołą” domenę, i www:** ustaw obie opcje (4 rekordy A dla @ + 1 CNAME dla www).

### Na GitHubie (custom domain)

1. W repozytorium: **Settings → Pages**.
2. W polu **Custom domain** wpisz swoją domenę (np. `twojadomena.pl` lub `www.twojadomena.pl`).
3. Zapisz (Save). Zaznacz **Enforce HTTPS** gdy będzie dostępne (po propagacji DNS).

### Gdzie to znaleźć w nazwa.pl

- **Logowanie:** https://www.nazwa.pl → Zaloguj się.
- **Domeny:** Moje usługi → **Domeny** → wybierz domenę.
- **DNS:** Przy domenie: **Zarządzaj** / **Panel** → **DNS**, **Rekordy DNS** lub **Strefa DNS**.  
  Tam dodajesz/edytujesz rekordy **A** i **CNAME** jak w tabelach powyżej.

Propagacja DNS trwa zwykle od kilku minut do ok. 24–48 godzin. Po tym strona powinna otwierać się pod Twoją domeną.
