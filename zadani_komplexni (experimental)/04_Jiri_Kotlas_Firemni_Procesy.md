# ZADÁNÍ MATURITNÍ PRÁCE

## Formální údaje

**Název projektu:** Systém řízení firemních procesů - Project Management a správa souborů  
**Student:** Jiří Kotlas  
**Školní rok:** 2024/2025  
**Obor:** Informační technologie  
**Vedoucí práce:** [Jméno vedoucího]  
**Externí konzultant:** Martin (zástupce firmy)

---

## 1. ZADÁNÍ A KONTEXT PROJEKTU

### 1.1 Úvod a motivace

Malé a střední firmy často používají roztříštěné nástroje pro správu projektů - emaily pro komunikaci, Excel pro sledování úkolů, sdílené disky pro dokumenty. Tato roztříštěnost vede k neefektivitě, ztrátě informací a komplikované spolupráci mezi týmem.

Projekt vzniká na základě reálné potřeby externí firmy, která požaduje centralizovaný systém pro řízení projektů, zadávání úkolů, správu dokumentů a sledování pokroku. Systém musí být intuitivní, aby jej mohli používat i uživatelé bez technického vzdělání.

### 1.2 Cíle projektu

**Hlavní cíl:**  
Vytvořit webovou aplikaci pro komplexní řízení firemních projektů, která zahrnuje správu úkolů, dokumentů, formulářů a poskytuje přehledný dashboard s metrikami.

**Dílčí cíle:**

1. **Analýza a návrh**
   - Analýza požadavků externí firmy (konzultace s Martinem)
   - Návrh databázového schématu (entity a jejich vztahy)
   - Wireframe a mockup v Figma
   - Rozdělení na MVP a rozšířené funkce

2. **Databázový design**
   - Návrh entit: projekty, úkoly, uživatelé, dokumenty, komentáře
   - Definice vztahů mezi entitami
   - Optimalizace pro výkon
   - Implementace v PostgreSQL nebo MySQL

3. **Backend implementace**
   - RESTful API (Node.js + Express nebo Django/Flask)
   - CRUD operace pro všechny entity
   - Autentizace a autorizace (JWT)
   - Upload a správa souborů
   - Validace dat

4. **Frontend implementace**
   - Moderní responzivní rozhraní (React nebo Vue.js)
   - Dashboard s přehledem projektů a úkolů
   - Formuláře pro zadávání dat
   - Drag & drop pro soubory
   - Real-time notifikace (volitelné)

5. **DevOps a deployment**
   - Kontejnerizace pomocí Docker
   - Setup Git repozitáře
   - CI/CD pipeline (volitelné)
   - Deployment na server nebo cloud

### 1.3 Rozsah projektu

**V rozsahu projektu (MVP - Minimum Viable Product):**

- Správa projektů (vytvoření, úprava, mazání)
- Správa úkolů v rámci projektů
- Uživatelské role (admin, manager, člen týmu)
- Upload a správa dokumentů
- Základní dashboard s metrikami
- Formuláře pro zadávání dat
- Autentizace a autorizace

**Rozšířené funkce (pokud stihne):**

- Komentáře u úkolů
- Sledování času (time tracking)
- Notifikace (email nebo in-app)
- Export reportů (PDF, Excel)
- Kanban board pro úkoly
- Pokročilé vyhledávání

**Mimo rozsah projektu:**

- Mobilní aplikace (iOS/Android)
- Video konference / chat
- Integrace s externími nástroji (Slack, Jira)
- AI asistent

---

## 2. SPECIFIKACE ŘEŠENÍ

### 2.1 Technický popis

**Backend:**

- **Framework:** Node.js + Express (nebo alternativně Python + Django/Flask)
- **Databáze:** PostgreSQL (preferováno) nebo MySQL
- **ORM:** Sequelize (Node.js) nebo Prisma
- **Autentizace:** JWT (JSON Web Tokens)
- **File storage:** Lokální souborový systém nebo S3-kompatibilní úložiště
- **Validace:** Joi nebo Zod

**Frontend:**

- **Framework:** React.js (s TypeScript - doporučeno)
- **Routing:** React Router
- **State management:** Context API nebo Redux Toolkit
- **UI knihovna:** Material-UI nebo Ant Design
- **Formuláře:** React Hook Form + validace
- **HTTP klient:** Axios

**DevOps:**

- **Kontejnerizace:** Docker + Docker Compose
- **Version control:** Git + GitHub/GitLab
- **Database management:** DBeaver (pro development)
- **API testing:** Postman nebo Insomnia

**Deployment (produkce):**

- Backend: VPS (např. DigitalOcean, Hetzner) nebo Railway/Render
- Frontend: Vercel nebo Netlify
- Databáze: Managed PostgreSQL (např. Supabase, Neon)

### 2.2 Funkční požadavky

**Správa projektů:**

1. Vytvoření nového projektu (název, popis, deadline, přiřazení týmu)
2. Zobrazení seznamu všech projektů
3. Detail projektu s úkoly a dokumenty
4. Úprava a mazání projektu
5. Filtrování projektů (aktivní, dokončené, podle deadline)

**Správa úkolů:**

1. Vytvoření úkolu v rámci projektu
2. Přiřazení úkolu členovi týmu
3. Nastavení priority (low, medium, high)
4. Nastavení statusu (todo, in progress, done)
5. Deadline pro úkol
6. Komentáře u úkolu (rozšířená funkce)

**Správa dokumentů:**

1. Upload souborů k projektu nebo úkolu
2. Stažení souboru
3. Zobrazení náhledu (pro obrázky, PDF)
4. Smazání souboru (pouze autor nebo admin)
5. Verze dokumentů (rozšířená funkce)

**Uživatelé a role:**

1. Registrace nového uživatele (pouze admin)
2. Přihlášení (email + heslo)
3. Role:
   - **Admin:** Plná práva, správa uživatelů
   - **Manager:** Může vytvářet projekty, přiřazovat úkoly
   - **Člen týmu:** Vidí jen své projekty a úkoly
4. Profil uživatele (změna hesla, avatar)

**Dashboard:**

1. Přehled aktivních projektů
2. Moje úkoly (deadline blízko, priority)
3. Statistiky (dokončené úkoly tento týden, přehledy)
4. Graf průběhu projektu (progress bar)

**Formuláře:**

1. Formulář pro vytvoření projektu
2. Formulář pro vytvoření úkolu
3. Formulář pro upload souborů
4. Validace všech vstupů (frontend i backend)

### 2.3 Nefunkční požadavky

- **Výkon:** API odpověď do 500 ms (pro běžné dotazy)
- **Bezpečnost:**
  - HTTPS v produkci
  - Hash hesel (bcrypt)
  - SQL injection ochrana (ORM)
  - XSS ochrana (sanitizace vstupů)
  - CORS správně nakonfigurováno
- **Použitelnost:** Intuitivní UI, max. 3 kliky k akci
- **Spolehlivost:** Ošetření chyb, error logging
- **Škálovatelnost:** Databáze zvládne 1000+ úkolů, 100+ projektů
- **Responzivita:** Funguje na tabletech (mobilní telefony volitelné)

---

## 3. HARMONOGRAM A MILNÍKY

### ✅ Září - Říjen 2024 (Hotovo)

- Schválení tématu
- Úvodní analýza požadavků firmy

### ✅ Listopad 2024 (R1 - hotovo)

**R1 hodnocení:** 1 (super práce)

- Analýza požadavků
- Wireframe v Figma
- Základní databázové schéma

**Poznámka:** Bylo potřeba domluvit meet s Martinem (externím konzultantem)

### ✅ Prosinec 2024 (R2 - hotovo)

**R2 hodnocení:** 1 (good job)

**Splněné cíle:**

- Popis formulářů na zadávání souborů
- Zkušební projekt (todo list) - procvičení základů
- Rozdělení na MVP a rozšířené funkce
- Založení projektu, základní entity v databázi

### Leden 2025 (R3 - deadline 8.1.)

- **Dodělání vstupních formulářů** (frontend)
- **Revize vztahů entit** - finální databázové schéma
- **Založení projektu a entit do databáze** - migrace
- **Setup Dockeru** - docker-compose.yml
- **Setup repozitáře** - Git, README
- **Přidání formulářů** - integrace s backend API
- **Úprava UX a design** - vizuální vylepšení
- **Instalace DBeaver** - pro práci s databází

### Únor 2025

- **CRUD API endpoints** - dokončení všech operací
- **Autentizace a autorizace** - JWT implementace
- **Upload souborů** - file upload endpoint
- **Dashboard** - implementace základních metrik
- **Testování API** - Postman testy

### Březen 2025

- **Integrace frontend s backend** - propojení všech formulářů
- **Správa uživatelských rolí** - permissions
- **Testování na uživatelích** (zaměstnanci firmy Martina)
- **Opravy bugů** podle feedbacku
- **Docker optimization**

### Duben 2025

- **Dokončení rozšířených funkcí** (pokud zbyde čas)
- **Deployment na produkční server**
- **Performance optimalizace**
- **Security audit** - kontrola bezpečnosti
- **Dokumentace API** (Swagger/OpenAPI - volitelné)

### Květen 2025

- **Finální testování**
- **Dokončení dokumentace**
- **Příprava prezentace a obhajoby**
- **Předání firmě** - školení uživatelů

---

## 4. POŽADOVANÉ VÝSTUPY

### 4.1 Funkční projekt

**Webová aplikace:**

- Dostupná na produkční URL
- Plně funkční MVP
- Otestovaná v reálném provozu (firma Martina)
- Obsahuje testovací i produkční data

**Demonstrace:**

- Live demo během obhajoby
- Video walkthrough (5 minut) - všechny klíčové funkce
- Ukázka Docker setupu

### 4.2 Vědecký/odborný článek (paper)

**Rozsah:** 10-15 stran

**Obsah:**

1. **Úvod** - problematika řízení projektů v malých firmách
2. **Analýza požadavků** - výsledky konzultací s firmou
3. **Existující řešení** - porovnání (Asana, Trello, Monday.com)
4. **Návrh systému** - architektura, databázové schéma
5. **Výběr technologií** - zdůvodnění použitých nástrojů
6. **Implementace backend** - struktura API, bezpečnost
7. **Implementace frontend** - komponenty, UX design
8. **Databázový design** - ER diagram, optimalizace
9. **Testování** - unit testy, user testing ve firmě
10. **Deployment** - Docker, CI/CD
11. **Výsledky** - metriky výkonu, feedback od uživatelů
12. **Diskuse** - problémy a jejich řešení
13. **Závěr** - přínos pro firmu, možná rozšíření

### 4.3 Poster (A3)

**Obsah:**

- Název projektu a logo (pokud je)
- Blokové schéma architektury (Frontend - API - Database)
- Screenshot dashboardu
- Screenshot formuláře pro vytvoření úkolu
- Použité technologie (ikony React, Node.js, PostgreSQL, Docker)
- Klíčové metriky (počet projektů, úkolů)
- QR kód na živou aplikaci nebo demo video

### 4.4 Technická dokumentace

**Rozsah:** 25-35 stran

**Obsah:**

1. **Přehled systému**
   - Architektura (diagram: Frontend - Backend - Database)
   - Technologický stack
   - Struktura repozitáře

2. **Setup a instalace**
   - Požadavky (Node.js, Docker, PostgreSQL)
   - Klonování repozitáře
   - Instalace dependencies
   - Konfigurace environment variables (.env soubor)
   - Spuštění s Dockerem (`docker-compose up`)
   - Spuštění bez Dockeru (lokální development)

3. **Databázové schéma**
   - ER diagram
   - Popis všech tabulek a sloupců
   - Vztahy mezi entitami (1:N, M:N)
   - Indexy pro optimalizaci
   - Migrace (jak vytvořit/změnit schéma)

4. **Backend API**
   - Seznam všech endpoints
   - Request/Response formáty (příklady JSON)
   - Autentizace (jak používat JWT tokeny)
   - Error handling (standardní chybové kódy)
   - Příklady volání API (curl nebo Postman)

5. **Frontend**
   - Struktura komponent
   - Routing (seznam všech routes)
   - State management
   - Formuláře a validace
   - Komunikace s API (Axios interceptors)

6. **Autentizace a autorizace**
   - Jak funguje JWT
   - Login flow (diagram)
   - Refresh tokeny (pokud implementováno)
   - Permissions podle rolí

7. **File upload**
   - Jak funguje upload souborů
   - Limity velikosti
   - Podporované formáty
   - Kde jsou soubory uloženy

8. **Docker**
   - Struktura docker-compose.yml
   - Dockerfile pro backend a frontend
   - Volumes pro persistenci dat
   - Networking mezi containery

9. **Deployment**
   - Production build (`npm run build`)
   - Environment variables v produkci
   - Database migrace v produkci
   - Monitoring a logging (pokud implementováno)

10. **Testování**
    - Unit testy (pokud jsou)
    - API testování (Postman kolekce)
    - User acceptance testing - výsledky

11. **Troubleshooting**
    - Časté problémy a řešení
    - Debugging backend (logy)
    - Debugging frontend (DevTools)

### 4.5 Prezentace pro obhajobu

**Rozsah:** 18-22 slidů

**Struktura:**

1. Úvod - problém řízení projektů v malých firmách
2. Zadání od externí firmy
3. Cíle projektu
4. Analýza existujících řešení
5. Návrh architektury
6. Databázové schéma (ER diagram)
7. Technologie - zdůvodnění výběru
8. Backend - API design
9. Frontend - UX/UI design
10. **Live demo** - vytvoření projektu a úkolu
11. **Live demo** - upload souboru
12. **Live demo** - dashboard
13. Docker setup - ukázka `docker-compose up`
14. User testing - feedback od firmy
15. Výsledky - metriky, výkon
16. Problémy a jejich řešení
17. Budoucí rozšíření
18. Závěr

**Vizuální materiál:**

- Wireframes z Figma
- ER diagram databáze
- Screenshots aplikace
- Screen recording klíčových funkcí
- Graf výsledků testování

---

## 5. HODNOTICÍ KRITÉRIA

### 5.1 Funkčnost projektu (40%)

- ✅ MVP plně implementováno
- ✅ Aplikace je stabilní, testována ve firmě
- ✅ API je dobře navržené (RESTful)
- ✅ Databáze správně normalizovaná
- ⭐ Kvalita kódu (čistý, komentovaný, TypeScript)
- ⭐ Docker setup funguje bez problémů

### 5.2 Dokumentace (25%)

- Úplnost technické dokumentace
- Kvalita API dokumentace
- Jasnost ER diagramu
- Kvalita instalačního návodu
- Kvalita vědeckého článku

### 5.3 Prezentace a obhajoba (20%)

- Kvalita prezentace
- Live demo (vytvoření projektu, úkolu)
- Schopnost vysvětlit architekturu
- Znalost použitých technologií
- Diskuse o alternativách (proč Node.js a ne Python, atd.)

### 5.4 Proces a samostatnost (15%)

- Pravidelná práce na projektu
- Kvalita průběžných reportů (R1, R2, R3)
- Komunikace s externím konzultantem (Martin)
- Reakce na feedback
- Git commits (pravidelné, s popisnými messages)

---

## 6. TECHNICKÉ POŽADAVKY NA OBHAJOBU

### Co student musí umět vysvětlit

**Backend:**

- Co je RESTful API, jaké jsou jeho principy
- Jak funguje JWT autentizace
- Co je middleware v Express.js
- Jak funguje ORM (Sequelize/Prisma)
- SQL injection - co to je a jak se bránit
- Validace dat na backendu

**Frontend:**

- React komponenty - props, state, lifecycle
- React Hooks (useState, useEffect, useContext)
- Jak funguje routing (React Router)
- State management (Context API vs Redux)
- Async operace (promises, async/await)

**Databáze:**

- Normalizace databáze (1NF, 2NF, 3NF)
- Vztahy mezi entitami (1:1, 1:N, M:N)
- Co jsou indexy a proč se používají
- ACID vlastnosti transakcí
- SQL vs NoSQL - kdy co použít

**Docker:**

- Co je kontejner vs. virtuální stroj
- Jak funguje Docker Compose
- Co jsou volumes (pro persistenci dat)
- Networking v Dockeru
- Výhody kontejnerizace

**Security:**

- Jak hashovat hesla (bcrypt)
- Co je CORS a jak se konfiguruje
- XSS útok a jak se bránit
- HTTPS vs HTTP
- Environment variables (proč neukládat v kódu)

---

## 7. OČEKÁVANÉ PROBLÉMY A ŘEŠENÍ

### Možné výzvy

1. **Složitá databázová schéma** - mnoho vztahů
   - Řešení: Postupná iterace, konzultace s vedoucím

2. **File upload** - složité na backendu
   - Řešení: Použít knihovnu `multer` (Node.js)

3. **Permissions** - role-based access control
   - Řešení: Middleware pro kontrolu rolí

4. **Docker networking** - komunikace mezi containery
   - Řešení: Správně nastavit docker-compose.yml

5. **Performance** - pomalé dotazy do databáze
   - Řešení: Indexy, optimalizace N+1 queries

6. **CORS errors** - frontend nemůže volat API
   - Řešení: Správně nastavit CORS middleware

---

## 8. LITERATURA A ZDROJE

**Dokumentace:**

- Node.js Documentation - nodejs.org
- Express.js Documentation - expressjs.com
- React Documentation - react.dev
- PostgreSQL Documentation - postgresql.org
- Docker Documentation - docs.docker.com

**Knihy:**

- "Node.js Design Patterns" - Mario Casciaro
- "Learning React" - O'Reilly
- "Database Design for Mere Mortals" - Michael J. Hernandez

**Kurzy:**

- Udemy: "Node.js, Express, MongoDB & More: The Complete Bootcamp"
- Udemy: "React - The Complete Guide"
- YouTube: Traversy Media - Docker Crash Course

**Nástroje:**

- DBeaver - databázový klient
- Postman - API testing
- Figma - wireframes a mockups
- VS Code - editor

---

## 9. ODEVZDÁNÍ

**Termín:** Nejpozději 5. května 2025

**Forma odevzdání:**

```
/Jiri_Kotlas_Firemni_Procesy/
  ├── README.md (kompletní návod na spuštění)
  ├── paper.pdf (vědecký článek)
  ├── poster.pdf (poster A3)
  ├── dokumentace/
  │   ├── technicka_dokumentace.pdf
  │   ├── ER_diagram.png
  │   ├── architecture_diagram.png
  │   ├── API_documentation.pdf
  │   └── user_testing_results.pdf
  ├── prezentace/
  │   └── obhajoba.pptx
  ├── videa/
  │   └── demo_walkthrough.mp4
  └── zdrojovy_kod/
      ├── docker-compose.yml
      ├── backend/
      │   ├── Dockerfile
      │   ├── package.json
      │   ├── src/
      │   └── .env.example
      └── frontend/
          ├── Dockerfile
          ├── package.json
          ├── src/
          └── .env.example
```

**GitHub repozitář:**

- Kód verzovaný na GitHubu
- README s detailními instrukcemi
- .gitignore (node_modules, .env)
- Pravidelné commity s popisnými messages

---

## SCHVÁLENÍ ZADÁNÍ

**Datum vydání zadání:** 10. prosince 2024  
**Podpis studenta:** ___________________  
**Podpis vedoucího:** ___________________

---

**Poznámka:** Tento projekt je vyvíjen pro externí firmu (konzultant Martin). Je nutná pravidelná komunikace s klientem a zapracování jeho požadavků do finálního řešení.

*Toto zadání je závazné. Jakékoliv změny musí být schváleny vedoucím práce a konzultovány s externím konzultantem.*
