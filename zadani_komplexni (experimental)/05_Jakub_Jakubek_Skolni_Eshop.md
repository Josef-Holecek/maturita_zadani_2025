# ZADÁNÍ MATURITNÍ PRÁCE

## Formální údaje

**Název projektu:** Školní e-shop - Systém pro prodej a správu školního merche  
**Student:** Jakub Jakůbek  
**Školní rok:** 2024/2025  
**Obor:** Informační technologie  
**Vedoucí práce:** [Jméno vedoucího]  

---

## 1. ZADÁNÍ A KONTEXT PROJEKTU

### 1.1 Úvod a motivace

Školy běžně prodávají propagační předměty (trička, mikiny, tašky) s logem školy, ale jejich prodej je často komplikovaný - papírové objednávky, Excel tabulky, ruční vyřizování. To vede k chybám, ztrátě přehledu a neefektivní správě skladu a objednávek.

Projekt řeší tento problém vytvořením moderního e-shopu specificky navrženého pro školní potřeby, včetně podpory předobjednávek (pre-orders), správy minimálních objednávkových množství a praktického systému vyzvednutí pomocí QR kódů.

### 1.2 Cíle projektu

**Hlavní cíl:**  
Vytvořit funkční webovou e-commerce aplikaci pro prodej školního merche s kompletní správou produktů, objednávek, skladu a efektivním systémem vyzvednutí zboží.

**Dílčí cíle:**

1. **E-shop frontend**
   - Katalog produktů s filtrováním
   - Nákupní košík
   - Proces objednávky (checkout)
   - Responzivní design (desktop + mobile)

2. **Administrační rozhraní**
   - Správa produktů (CRUD operace)
   - Správa objednávek
   - Přehled skladu
   - Dashboard se statistikami

3. **Specifické funkce pro školu**
   - Systém předobjednávek (pre-orders)
   - Minimální požadované množství pro objednání
   - QR kódy pro vyzvednutí objednávky
   - Schvalovací workflow (učiteli)

4. **Autentizace a autorizace**
   - Login přes Microsoft (Azure AD / Entra ID)
   - Role: student, učitel, admin
   - Propojení s školním Active Directory

5. **Deployment a testování**
   - Nasazení na veřejný server
   - Testování s reálnými uživateli (studenti, učitelé)
   - Optimalizace výkonu

### 1.3 Rozsah projektu

**V rozsahu projektu (podle současného stavu):**

- ✅ Kompletní e-shop frontend (katalog, košík, checkout)
- ✅ Správa produktů (CRUD) v admin panelu
- ✅ Správa objednávek
- ✅ QR kódy pro vyzvednutí (generování a skenování)
- ✅ Systém požadavků na změnu produktu
- ✅ Stav skladu s automatickou aktualizací
- ✅ PostgreSQL databáze
- ✅ Docker setup
- ✅ Nodemailer (email notifikace)
- ✅ Responzivní design

**Zbývá dodělat do obhajoby:**

- 🔄 Login přes Microsoft (Azure AD integrace)
- 🔄 Systém načítání minimálního požadavku na objednání
- 🔄 Finální konzultace stavu skladu s učiteli
- 🔄 Nasazení aplikace na produkční server
- 🔄 Testování s reálnými uživateli

**Mimo rozsah projektu:**

- Online platby (platba pouze při vyzvednutí)
- Integrace s bankovním účtem
- Mobilní aplikace (iOS/Android)
- Hodnocení produktů / recenze
- Wishlist / oblíbené produkty

---

## 2. SPECIFIKACE ŘEŠENÍ

### 2.1 Technický popis

**Backend:**

- **Framework:** Node.js + Express.js
- **Databáze:** PostgreSQL
- **ORM / Query builder:** (specifikovat - Sequelize, Prisma, nebo raw SQL)
- **Autentizace:** Azure AD / Microsoft Entra ID (OAuth 2.0)
- **Email:** Nodemailer
- **QR kódy:** qrcode library (Node.js)

**Frontend:**

- **Framework:** (specifikovat - React, Vue.js, nebo template engine EJS/Pug)
- **Styling:** CSS / Tailwind CSS / Bootstrap
- **HTTP klient:** Fetch API nebo Axios

**DevOps:**

- **Kontejnerizace:** Docker + Docker Compose
- **Version control:** Git + GitHub/GitLab
- **Deployment:** VPS, Railway, nebo Render

**Specifické funkce:**

- QR kód obsahuje: order_id, timestamp, hash (pro zabezpečení)
- Skenování QR: Mobilní kamera nebo dedikovaná stránka

### 2.2 Funkční požadavky

**Pro studenty (zákazníci):**

1. Prohlížení katalog produktů (trička, mikiny, tašky, atd.)
2. Filtrování podle kategorie, velikosti, ceny
3. Přidání produktu do košíku
4. Zobrazení košíku a upravení množství
5. Objednání (checkout) - vyplnění kontaktu
6. Potvrzení objednávky emailem s QR kódem
7. Sledování stavu objednávky (čeká, připravena, vyzvednuta)

**Pro učitele / správce skladu:**

1. Přihlášení přes Microsoft účet
2. Přehled všech objednávek
3. Změna stavu objednávky (připravena k vyzvednutí)
4. Skenování QR kódu pro potvrzení vyzvednutí
5. Přehled stavu skladu (kolik kusů zbývá)

**Pro admina (správce e-shopu):**

1. Přihlášení přes Microsoft účet (admin role)
2. Správa produktů:
   - Přidání nového produktu (název, popis, cena, foto, velikosti, skladem)
   - Úprava produktu
   - Smazání produktu
   - Nastavení minimálního objednávkového množství
3. Správa objednávek:
   - Přehled všech objednávek
   - Detail objednávky
   - Zrušení objednávky
4. Dashboard:
   - Statistiky (tržby, počet objednávek)
   - Graf nejprodávanějších produktů
5. Systém požadavků na změnu (studenti mohou navrhnout nové produkty)

**Systém minimálního množství:**

- Admin nastaví minimální počet objednávek pro výrobu produktu
- Pokud produkt nedosáhne minimálního množství, objednávky se zruší a vrátí platba
- Studenti vidí "progress bar" - kolik objednávek ještě zbývá

### 2.3 Nefunkční požadavky

- **Výkon:** Načtení stránky do 2 sekund
- **Bezpečnost:**
  - HTTPS v produkci
  - SQL injection ochrana (prepared statements)
  - XSS ochrana (sanitizace vstupů)
  - QR kódy zabezpečené hashem (HMAC-SHA256)
  - Microsoft OAuth 2.0 pro autentizaci
- **Použitelnost:** Intuitivní rozhraní i pro technicky méně zdatné učitele
- **Responzivita:** Funguje na mobilech (košík, objednávka, skenování QR)
- **Spolehlivost:** Email notifikace musí být doručeny (retry mechanismus)
- **Škálovatelnost:** Zvládne 500+ objednávek, 50+ produktů

---

## 3. HARMONOGRAM A MILNÍKY

### ✅ Září - Říjen 2024 (Hotovo)

- Schválení tématu
- Analýza požadavků školy

### Listopad 2024 (R1)

**R1 hodnocení:** 2.5 (analýza ~50%, report málo čitelný)

**Poznámka vedoucího:** Report nebyl čitelný, nedával dobrou představu o stavu projektu. Očekává se v lepší kvalitě příště.

**Stav:** Základní analýza hotova, projekt rozjetý

### Prosinec 2024 (R2)

**R2 hodnocení:** 1 (hodně práce hotovo)

**Splněné cíle:**

- ✅ Aplikace připravená na odprezentování na localhostu
- ✅ Správa produktů (CRUD)
- ✅ Správa objednávek
- ✅ Praktická správa pomocí načítání QR kódů
- ✅ Systém požadavků na změnu

**Poznámka:** Hodně práce hotovo, prezentace reportu horší (mělo by být lepší)

### Leden 2025 (R3 - deadline 8.1.)

- **Login přes Microsoft** - integrace Azure AD
  - Registrace aplikace v Azure Portal
  - OAuth 2.0 flow implementace
  - Získání informací o uživateli (jméno, email, role)
- **Aplikace nasazená na server** - dostupná veřejně pro testování
- **Systém načítání minimálního požadavku** - progress bar, zrušení objednávek
- **Stav skladu - finální konzultace** s učiteli

### Únor 2025

- **Testování s reálnými uživateli** (studenti, učitelé)
- **Opravy bugů** podle feedbacku
- **Optimalizace výkonu** (lazy loading obrázků, caching)
- **Email notifikace** - testování doručitelnosti

### Březen 2025

- **Security audit** - kontrola bezpečnosti QR kódů, autentizace
- **User experience vylepšení** podle feedbacku
- **Dokumentace API** (pokud bude potřeba)
- **Příprava na produkční nasazení**

### Duben 2025

- **Finální testování** - kompletní průchod všemi funkcemi
- **Dokumentace** - technická dokumentace, uživatelský manuál
- **Video tutoriál** pro učitele (jak spravovat e-shop)
- **Předání škole** - školení učitelů

### Květen 2025

- **Příprava prezentace a obhajoby**
- **Vědecký článek** - finalizace
- **Poster** - grafické zpracování
- **Drobné úpravy** podle poslední zpětné vazby

---

## 4. POŽADOVANÉ VÝSTUPY

### 4.1 Funkční projekt

**Webová aplikace:**

- Dostupná na produkční URL (např. merch.skola.cz)
- Plně funkční včetně Microsoft loginu
- Otestovaná na reálných uživatelích (studenti, učitelé)
- Obsahuje reálné produkty (školní merch)

**Demonstrace:**

- Live demo během obhajoby (objednání produktu, skenování QR)
- Video walkthrough (5 minut) - celý proces od objednávky po vyzvednutí
- Ukázka admin panelu

### 4.2 Vědecký/odborný článek (paper)

**Rozsah:** 10-12 stran

**Obsah:**

1. **Úvod** - problematika prodeje školního merche
2. **Analýza požadavků** - specifické potřeby školy
3. **Existující řešení** - porovnání s klasickými e-shopy (Shopify, WooCommerce)
4. **Návrh systému** - architektura, databázové schéma
5. **Implementace QR systému** - jak funguje generování a ověřování
6. **Microsoft autentizace** - integrace Azure AD
7. **Systém minimálního množství** - algoritmus, business logika
8. **Frontend** - UX/UI design, responzivita
9. **Backend** - API, databázové operace
10. **Testování** - metodika, výsledky user testingu
11. **Výsledky** - statistiky použití, feedback
12. **Diskuse** - problémy při vývoji, bezpečnostní aspekty
13. **Závěr** - přínos pro školu

### 4.3 Poster (A3)

**Obsah:**

- Logo e-shopu / školy
- Screenshot homepage e-shopu
- Screenshot admin panelu
- Ilustrace: Jak funguje QR vyzvednutí (3 kroky)
- Příklad QR kódu
- Použité technologie (ikony Node.js, PostgreSQL, Docker)
- Statistiky (počet produktů, objednávek)
- QR kód na živou aplikaci

### 4.4 Technická dokumentace

**Rozsah:** 25-30 stran

**Obsah:**

1. **Přehled systému**
   - Architektura aplikace (diagram)
   - Technologický stack
   - Struktura projektu (složky)

2. **Instalace a setup**
   - Požadavky (Node.js, PostgreSQL, Docker)
   - Klonování repozitáře
   - Instalace dependencies
   - Konfigurace `.env` (database, Azure AD credentials, email)
   - Spuštění s Dockerem
   - Spuštění bez Dockeru

3. **Databázové schéma**
   - ER diagram
   - Tabulky: `products`, `orders`, `order_items`, `users`, `qr_codes`
   - Vztahy mezi tabulkami
   - Migrace

4. **Backend API**
   - Seznam endpoints
   - Request/Response formáty
   - Autentizace (JWT po Microsoft loginu)
   - Error handling

5. **Microsoft autentizace**
   - Registrace aplikace v Azure Portal (návod)
   - OAuth 2.0 flow (diagram)
   - Získání access tokenu
   - Propojení s databází uživatelů

6. **QR kód systém**
   - Generování QR kódu (format, hash)
   - Ověřování QR kódu (security check)
   - Skenování QR (webová kamera nebo upload)
   - Zabezpečení proti podvržení

7. **Email notifikace**
   - Nodemailer konfigurace
   - Šablony emailů
   - Retry mechanismus (pokud implementováno)

8. **Frontend**
   - Struktura stránek
   - Košík (session / local storage)
   - Checkout proces
   - Admin panel

9. **Deployment**
   - Production build
   - Environment variables v produkci
   - Database migrations
   - HTTPS setup (Let's Encrypt)

10. **Uživatelská příručka**
    - Pro studenty: Jak objednat
    - Pro učitele: Jak spravovat objednávky, skenovat QR
    - Pro admina: Jak přidat produkt, nastavit minimum

11. **Troubleshooting**
    - Časté problémy
    - Debugging
    - Logy

### 4.5 Prezentace pro obhajobu

**Rozsah:** 18-22 slidů

**Struktura:**

1. Úvod - problém prodeje školního merche
2. Cíle projektu
3. Analýza požadavků školy
4. Existující řešení vs. vlastní systém
5. Architektura aplikace
6. Databázové schéma
7. Technologie - zdůvodnění výběru
8. E-shop frontend - ukázka
9. Admin panel - ukázka
10. **QR systém** - jak funguje (diagram)
11. **Live demo**: Objednání produktu
12. **Live demo**: Skenování QR kódu
13. **Live demo**: Admin - správa produktů
14. Microsoft autentizace - jak jsme integrovali
15. Systém minimálního množství - business logika
16. User testing - feedback
17. Výsledky - statistiky
18. Problémy a jejich řešení
19. Budoucí rozšíření (online platby, wishlist)
20. Závěr

**Vizuální materiál:**

- Screenshots e-shopu
- Screen recording objednávky
- Ukázka QR kódu
- Graf nejprodávanějších produktů
- Diagram QR workflow

---

## 5. HODNOTICÍ KRITÉRIA

### 5.1 Funkčnost projektu (40%)

- ✅ E-shop plně funkční (katalog, košík, checkout)
- ✅ Admin panel pro správu
- ✅ QR systém funguje bezchybně
- ✅ Microsoft login implementován
- ✅ Aplikace nasazena a dostupná veřejně
- ⭐ Kvalita kódu (struktura, komentáře)

### 5.2 Dokumentace (25%)

- Úplnost technické dokumentace
- Kvalita uživatelské příručky
- Jasnost diagramů (ER, architektura, QR flow)
- Kvalita vědeckého článku
- Vizuální zpracování posteru

### 5.3 Prezentace a obhajoba (20%)

- Kvalita prezentace
- Live demo e-shopu
- Live demo QR skenování
- Schopnost vysvětlit architekturu
- Diskuse o bezpečnosti QR kódů
- Znalost OAuth 2.0 / Azure AD

### 5.4 Proces a samostatnost (15%)

- Pravidelná práce na projektu
- **Zlepšení kvality reportů** (R1 a R2 měly rezervy)
- Reakce na feedback vedoucího
- Git commits (pravidelné)
- Dodržování harmonogramu

**Poznámka:** Student má již většinu práce hotovou (R2 hodnocení 1), očekává se kvalitní finalizace a zejména **zlepšení dokumentace a reportingu**.

---

## 6. TECHNICKÉ POŽADAVKY NA OBHAJOBU

### Co student musí umět vysvětlit

**E-commerce:**

- Jak funguje košík (session vs local storage)
- Jak se zpracovává objednávka (flow diagram)
- Jak se aktualizuje stav skladu

**Autentizace:**

- Co je OAuth 2.0
- Jak funguje Microsoft login (Azure AD / Entra ID)
- Co je access token a refresh token
- Jak se propojuje s databází uživatelů

**QR kódy:**

- Jak se generuje QR kód (knihovna, format)
- Co obsahuje QR kód (order_id, hash)
- Jak se ověřuje pravost QR kódu (HMAC-SHA256)
- Bezpečnostní aspekty (prevence podvržení)

**Databáze:**

- Struktura tabulek (products, orders, order_items)
- Vztahy mezi entitami
- Transakce (atomic operations při objednávce)

**Backend:**

- RESTful API principy
- Error handling
- Validace vstupů
- Email notifikace (Nodemailer)

**Frontend:**

- Responzivní design
- Formuláře a validace
- Asynchronní volání API

**Security:**

- SQL injection prevence
- XSS prevence
- HTTPS
- Bezpečnost QR kódů

---

## 7. OČEKÁVANÉ PROBLÉMY A ŘEŠENÍ

### Možné výzvy

1. **Azure AD integrace** - složité nastavení
   - Řešení: Důkladně prostudovat Microsoft docs, použít knihovnu `passport-azure-ad`

2. **QR bezpečnost** - možnost podvržení
   - Řešení: HMAC hash s tajným klíčem, časové omezení platnosti

3. **Email doručitelnost** - emaily končí ve spamu
   - Řešení: SPF/DKIM konfigurace, použít SMTP školy

4. **Stav skladu** - race conditions při souběžných objednávkách
   - Řešení: Database transactions, locking

5. **Minimální množství** - složitá business logika
   - Řešení: Scheduled job (cron), kontrola každý den

6. **Deployment** - problémy s konfigurací na produkci
   - Řešení: Docker konzistence dev/prod, environment variables

---

## 8. LITERATURA A ZDROJE

**Dokumentace:**

- Node.js Documentation - nodejs.org
- Express.js Documentation - expressjs.com
- PostgreSQL Documentation - postgresql.org
- Microsoft Identity Platform - docs.microsoft.com/azure/active-directory
- Nodemailer Documentation - nodemailer.com

**Knihy:**

- "Node.js Design Patterns" - Mario Casciaro
- "Building Microservices" - Sam Newman

**Tutoriály:**

- Microsoft Learn: Integrate Azure AD with Node.js
- YouTube: QR Code Authentication Systems
- Medium: Building E-commerce with Node.js

**Nástroje:**

- Azure Portal - registrace aplikace
- Postman - API testování
- QR code generators/scanners

---

## 9. ODEVZDÁNÍ

**Termín:** Nejpozději 5. května 2025

**Forma odevzdání:**

```
/Jakub_Jakubek_Skolni_Eshop/
  ├── README.md (kompletní návod)
  ├── paper.pdf (vědecký článek)
  ├── poster.pdf (poster A3)
  ├── dokumentace/
  │   ├── technicka_dokumentace.pdf
  │   ├── uzivatelska_prirucka.pdf
  │   ├── ER_diagram.png
  │   ├── architecture_diagram.png
  │   └── qr_workflow.png
  ├── prezentace/
  │   └── obhajoba.pptx
  ├── videa/
  │   ├── demo_eshop.mp4
  │   ├── demo_qr_sken.mp4
  │   └── admin_tutorial.mp4
  └── zdrojovy_kod/
      ├── docker-compose.yml
      ├── package.json
      ├── .env.example
      ├── src/
      │   ├── routes/
      │   ├── controllers/
      │   ├── models/
      │   ├── views/
      │   └── public/
      └── database/
          └── migrations/
```

**GitHub repozitář:**

- Kód verzovaný na GitHubu
- README s instrukcemi
- .gitignore (node_modules, .env, secrets)
- Pravidelné commity

---

## SCHVÁLENÍ ZADÁNÍ

**Datum vydání zadání:** 10. prosince 2024  
**Podpis studenta:** ___________________  
**Podpis vedoucího:** ___________________

---

**Poznámka:** Student má již většinu projektu hotového (stav "de facto finished" podle dokumentů). Důraz je kladen na **finalizaci zbývajících funkcí** (Microsoft login, nasazení), **kvalitní dokumentaci** a **zlepšení kvality reportování**.

*Toto zadání je závazné. Jakékoliv změny musí být schváleny vedoucím práce.*
