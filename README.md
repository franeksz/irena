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

## Podłączenie domeny z nazwa.pl (irena.org.pl)

Źródło: [GitHub Docs – Configuring a custom domain](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site).

**Ważne:** Najpierw dodaj domenę w GitHubie (Settings → Pages → Custom domain), dopiero potem ustaw rekordy DNS u rejestratora. W przeciwnym razie ryzykujesz przejęcie domeny.

---

### Dlaczego „@” i „irena.org.pl” nie działają w nazwa.pl

- **„@”** – W panelu nazwa.pl pole „nazwa hosta” często **nie akceptuje** symbolu `@`. Dla domeny głównej (apex) trzeba użyć **pustego pola** lub opcji „domena główna”, jeśli jest w menu.
- **„irena.org.pl”** – W polu nazwy/hosta **nie wpisuj pełnej domeny**. W strefie DNS domeny `irena.org.pl` pole „nazwa” oznacza tylko **subdomenę** (np. `www` = www.irena.org.pl). Dla samej `irena.org.pl` w tym panelu to albo **puste**, albo specjalna opcja.

---

### NAJPROSTSZE: tylko www (bez rekordów A)

Jeśli wystarczy Ci adres **www.irena.org.pl** (bez „gołej” domeny):

1. **W nazwa.pl** – dodaj **jeden** rekord:
   - **Typ:** CNAME  
   - **Nazwa / Host:** `www` (tylko literki www, bez kropki i bez domeny)  
   - **Wartość / Docelowy adres:** `TWOJA-NAZWA.github.io` (Twoja nazwa użytkownika GitHub)  
   - TTL: 3600 (lub domyślne)

2. **Na GitHubie:** Settings → Pages → **Custom domain** wpisz: `www.irena.org.pl` → Save. Później włącz **Enforce HTTPS**.

Nie musisz wtedy dodawać żadnych rekordów A ani używać pola z „@”. Strona będzie pod **https://www.irena.org.pl**.

---

### Domena główna irena.org.pl (rekordy A)

Jeśli chcesz, żeby działała **irena.org.pl** (bez www), potrzebne są 4 rekordy **A** wskazujące na GitHub Pages.

W nazwa.pl przy dodawaniu rekordu A dla **domeny głównej**:

- W polu **„Nazwa hosta” / „Host” / „Subdomena”**:
  - **Zostaw pole puste** (0 znaków) – w wielu panelach to właśnie oznacza domenę główną, **albo**
  - Użyj opcji z listy rozwijanej typu **„Domena główna”**, **„Apex”**, **„(pusta)”**, jeśli taką masz.

**Nie wpisuj:** `@` ani `irena.org.pl`.

Wartości dla **4 rekordów A** (każdy z pustą nazwą / domeną główną):

| Typ | Nazwa (Host)      | Wartość (adres IP) |
|-----|-------------------|---------------------|
| A   | *(puste)*         | 185.199.108.153     |
| A   | *(puste)*         | 185.199.109.153     |
| A   | *(puste)*         | 185.199.110.153     |
| A   | *(puste)*         | 185.199.111.153     |

Na GitHubie w **Custom domain** wpisz wtedy: `irena.org.pl` (bez www).

---

### Gdy chcesz i apex, i www

- 4 rekordy **A** z pustą nazwą (jak wyżej) → `irena.org.pl`
- 1 rekord **CNAME**: nazwa `www`, wartość `TWOJA-NAZWA.github.io` → `www.irena.org.pl`

Na GitHubie ustaw **Custom domain** na `irena.org.pl`. GitHub Pages sam zrobi przekierowanie między apex a www.

---

### Na GitHubie (kolejność)

1. Repozytorium → **Settings** → **Pages** (w lewym menu).
2. W **Custom domain** wpisz `irena.org.pl` lub `www.irena.org.pl` → **Save**.
3. Po propagacji DNS (kilka minut do 24–48 h) zaznacz **Enforce HTTPS**.

---

### Gdzie to w nazwa.pl

- Zaloguj się: https://www.nazwa.pl  
- **Moje usługi** → **Domeny** → kliknij domenę **irena.org.pl**  
- **Konfiguracja** / **Zarządzaj** → **Ręczna konfiguracja DNS** (jeśli jest „Zmień” – włącz ręczną konfigurację).  
- Dodaj/edytuj rekordy w sekcji rekordów DNS (A, CNAME).

Propagacja DNS: zwykle od kilkunastu minut do ok. 24–48 godzin.
