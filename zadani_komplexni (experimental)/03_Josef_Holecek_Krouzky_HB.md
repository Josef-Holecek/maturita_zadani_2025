# ZADÁNÍ MATURITNÍ PRÁCE

## Formální údaje

**Název projektu:** Kroužky a trenéři v Havlíčkově Brodě - Komunitní webová platforma  
**Student:** Josef Holeček  
**Školní rok:** 2024/2025  
**Obor:** Informační technologie  
**Vedoucí práce:** [Jméno vedoucího]  

---

## 1. ZADÁNÍ A KONTEXT PROJEKTU

### 1.1 Úvod a motivace

V Havlíčkově Brodě, jako v mnoha menších městech, existuje široká nabídka volnočasových aktivit, kroužků a služeb trenérů. Informace o těchto aktivitách jsou však často roztříštěné - na webech jednotlivých organizací, facebookových stránkách, plakátech nebo pouze formou ústního podání. Pro rodiče hledající kroužek pro své dítě nebo pro dospělé hledající trenéra je velmi obtížné získat komplexní přehled o nabídce ve městě.

Projekt řeší tento problém vytvořením centralizované webové platformy, která sjednotí informace o všech volnočasových aktivitách na jednom místě. Platforma usnadní lidem najít vhodnou aktivitu a poskytne organizátorům kroužků efektivní způsob propagace jejich služeb.

### 1.2 Cíle projektu

**Hlavní cíl:**  
Vytvořit funkční webovou aplikaci, která slouží jako centrální databáze kroužků, sportovních aktivit a trenérů v Havlíčkově Brodě, s intuitivním rozhraním pro vyhledávání a správu obsahu.

**Dílčí cíle:**

1. **Analýza a návrh**
   - Analýza potřeb uživatelů (rodiče, organizátoři, správci)
   - Návrh databázové struktury
   - Wireframe a mockup uživatelského rozhraní
   - Mapa stránek (sitemap)

2. **Implementace frontend**
   - Moderní responzivní design (desktop + mobile)
   - Implementace v Next.js (React framework)
   - Pokročilé filtrování a vyhledávání
   - Uživatelsky přívětivé formuláře

3. **Implementace backend**
   - Integrace s Firebase (Firestore database, Authentication)
   - CRUD operace pro správu kroužků
   - Systém uživatelských rolí (návštěvník, organizátor, admin)
   - Upload a správa obrázků

4. **Klíčové funkcionality**
   - Registrace a správa kroužků organizátory
   - Schvalovací systém pro admina
   - Filtrování podle kategorií, věku, lokace, ceny
   - Detail kroužku s kontaktními informacemi
   - Mapa s lokacemi kroužků

5. **Testování a deployment**
   - Testování na reálných uživatelích
   - Optimalizace výkonu
   - Nasazení na produkční prostředí (Vercel)
   - SEO optimalizace

### 1.3 Rozsah projektu

**V rozsahu projektu je:**

- Webová aplikace pro desktop a mobilní zařízení
- Databáze kroužků a trenérů
- Registrace a přihlašování uživatelů (Firebase Auth)
- Systém rolí (návštěvník, organizátor, admin)
- Správa kroužků (CRUD operace)
- Schvalovací workflow pro nové kroužky
- Pokročilé filtrování a vyhledávání
- Upload obrázků
- Responzivní design

**Mimo rozsah projektu:**

- Online platby / rezervační systém
- Mobilní aplikace (iOS/Android)
- Chat / messaging mezi uživateli
- Systém hodnocení a recenzí (možné budoucí rozšíření)
- Integrace s Google Calendar

---

## 2. SPECIFIKACE ŘEŠENÍ

### 2.1 Technický popis

**Frontend:**

- **Framework:** Next.js 14+ (React framework s SSR)
- **Styling:** Tailwind CSS nebo CSS Modules
- **UI knihovna:** shadcn/ui nebo Material-UI
- **Maps:** Google Maps API nebo Mapy.cz API
- **Formuláře:** React Hook Form + Zod validace

**Backend / Database:**

- **BaaS:** Firebase (Backend as a Service)
  - **Firestore:** NoSQL databáze pro data
  - **Firebase Auth:** Autentizace uživatelů (email/password, Google)
  - **Firebase Storage:** Ukládání obrázků
- **API:** Next.js API routes

**Deployment:**

- **Hosting:** Vercel (optimalizováno pro Next.js)
- **Domain:** Vlastní doména (volitelné)

**Vývojové nástroje:**

- Git + GitHub pro version control
- VS Code jako IDE
- Figma pro design (wireframes, mockupy)

### 2.2 Funkční požadavky

**Pro návštěvníky (veřejnost):**

1. Prohlížení všech schválených kroužků bez přihlášení
2. Filtrování podle:
   - Kategorie (sport, umění, jazyky, technologie, atd.)
   - Věková skupina (děti, dospělí, senioři)
   - Lokace (část města)
   - Cena (zdarma, do 500 Kč, 500-1000 Kč, atd.)
   - Den v týdnu / čas konání
3. Vyhledávání podle klíčových slov
4. Zobrazení detailu kroužku (popis, kontakt, cena, čas, fotky)
5. Zobrazení lokace na mapě

**Pro organizátory (po registraci):**

1. Registrace / přihlášení (email + heslo, Google login)
2. Vytvoření profilu organizace
3. Přidání nového kroužku (formulář)
4. Úprava vlastních kroužků
5. Smazání vlastního kroužku
6. Upload obrázků (logo organizace, fotky z kroužku)
7. Přehled stavu kroužků (čeká na schválení, schváleno, zamítnuto)

**Pro administrátora:**

1. Přihlášení s admin právy
2. Přehled všech kroužků (i neschválených)
3. Schvalování / zamítání nových kroužků
4. Editace / smazání jakéhokoli kroužku
5. Správa uživatelů (ban, změna rolí)
6. Dashboard se statistikami (počet kroužků, organizátorů, návštěvníků)

### 2.3 Nefunkční požadavky

- **Výkon:** Načtení stránky do 2 sekund (na průměrném připojení)
- **Responzivita:** Plně funkční na mobilních zařízeních (min. šířka 320px)
- **Dostupnost:** 99% uptime (díky Vercel a Firebase)
- **Bezpečnost:**
  - HTTPS
  - Validace vstupů na frontend i backend
  - Firebase Security Rules
  - Ochrana proti XSS, SQL injection
- **SEO:** Optimalizace pro vyhledávače (meta tagy, SSR v Next.js)
- **Použitelnost:** Intuitivní UI, jasná navigace, minimálně 3 kliky k cíli
- **Škálovatelnost:** Databáze zvládne min. 500 kroužků, 200 organizátorů

---

## 3. HARMONOGRAM A MILNÍKY

### ✅ Září - Říjen 2024 (Hotovo)

- Schválení tématu
- Úvodní analýza (průzkum uživatelských potřeb)
- Seznámení s AI nástroji pro vývoj

### 🔄 Listopad - Prosinec 2024 (R1-R2)

**R1 hodnocení:** 1.5 (očekává se více vlastní iniciativy, zkoušení AI nástrojů)

**Cíle do R2:**

- ✅ **Dokončit wireframe** všech stránek v Figma
- ✅ **Popsat mapu stránek** (sitemap) - navigační struktura
- ✅ **Připravit Next.js projekt** - iniciální setup
- ✅ **Připravit všechny potřebné programy** na domácím PC
- 🔄 **Napojit projekt na Firebase** (Firestore + Auth)
- 🔄 **Mít něco funkčního** - alespoň homepage a seznam kroužků

### Leden 2025 (R3 - deadline 8.1.)

- **Kompletní frontend struktura** - všechny stránky (i prázdné)
- **Firebase integrace** - databáze, autentizace funguje
- **CRUD operace** - přidání, úprava, mazání kroužků
- **Základní filtrování** - alespoň podle kategorie
- **Responzivní design** - funguje na mobilu

### Únor 2025

- **Schvalovací systém** - admin může schvalovat kroužky
- **Pokročilé filtrování** - všechny filtry funkční
- **Upload obrázků** - integrace Firebase Storage
- **Uživatelské role** - rozlišení návštěvník/organizátor/admin

### Březen 2025

- **Mapa s lokacemi** - integrace Google Maps
- **SEO optimalizace** - meta tagy, Open Graph
- **Testování na uživatelích** - získat feedback
- **Opravy bugů** - podle feedbacku

### Duben 2025

- **Finální design** - vizuální vylepšení
- **Optimalizace výkonu** - lazy loading, caching
- **Testování na různých zařízeních**
- **Deployment na Vercel** - produkční prostředí

### Květen 2025

- **Finální testování**
- **Dokumentace**
- **Příprava prezentace a obhajoby**
- **Drobné úpravy podle poslední zpětné vazby**

---

## 4. POŽADOVANÉ VÝSTUPY

### 4.1 Funkční projekt

**Webová aplikace:**

- Dostupná na veřejné URL (např. krouzky-hb.vercel.app)
- Plně funkční všechny požadované features
- Otestovaná na reálných uživatelích
- Obsahuje testovací data (min. 20 různých kroužků)

**Demonstrace:**

- Live demo během obhajoby
- Video walkthrough (3-5 minut) ukazující všechny funkce
- Mobilní i desktop verze

### 4.2 Vědecký/odborný článek (paper)

**Rozsah:** 10-12 stran

**Obsah:**

1. **Úvod** - problematika roztříštěných informací o volnočasových aktivitách
2. **Analýza problému** - průzkum mezi rodiči a organizátory
3. **Existující řešení** - analýza podobných platforem (např. Kroužky.cz)
4. **Návrh řešení** - architektura aplikace, wireframes
5. **Technologie** - zdůvodnění výběru Next.js a Firebase
6. **Implementace** - popis klíčových funkcionalit
7. **Databázové schéma** - struktura dat v Firestore
8. **Testování** - metodika, výsledky user testingu
9. **Výsledky** - dosažené parametry (výkon, použitelnost)
10. **Diskuse** - problémy při vývoji, možná vylepšení
11. **Závěr** - přínos projektu pro komunitu

### 4.3 Poster (A3)

**Obsah:**

- Logo/název aplikace
- Screenshot homepage
- Screenshot mobilní verze
- Infografika: Jak to funguje (3-4 kroky)
- Použité technologie (ikony Next.js, Firebase, Vercel)
- Klíčové statistiky (např. počet kroužků v databázi)
- QR kód na živou aplikaci

### 4.4 Technická dokumentace

**Rozsah:** 20-25 stran

**Obsah:**

1. **Přehled systému**
   - Architektura aplikace (diagram)
   - Technologický stack
   - Struktura projektu (složky a soubory)

2. **Instalace a setup**
   - Požadavky (Node.js, Git)
   - Klonování repozitáře
   - Instalace dependencies (`npm install`)
   - Nastavení Firebase (konfigurace, API klíče)
   - Spuštění vývojového serveru

3. **Databázové schéma**
   - Struktura Firestore kolekcí
   - Příklad dokumentu `krouzek`
   - Firestore Security Rules
   - Indexy

4. **Autentizace a autorizace**
   - Firebase Authentication setup
   - Implementace uživatelských rolí
   - Ochrana routes (middleware)

5. **Klíčové komponenty**
   - Popis hlavních React komponent
   - Props a jejich význam
   - State management

6. **API routes**
   - Seznam všech API endpointů
   - Request/Response formáty
   - Error handling

7. **Deployment**
   - Build process (`npm run build`)
   - Deployment na Vercel
   - Environment variables
   - Custom domain setup (pokud použito)

8. **Testování**
   - Metodika uživatelského testování
   - Výsledky a zpětná vazba
   - Performance metriky

9. **Troubleshooting**
   - Časté problémy a jejich řešení
   - Debugging Firebase
   - Logování chyb

### 4.5 Prezentace pro obhajobu

**Rozsah:** 15-20 slidů

**Struktura:**

1. Úvod - problém roztříštěných informací
2. Cíle projektu
3. Analýza - průzkum mezi uživateli
4. Existující řešení - co už existuje
5. Návrh - wireframes, sitemap
6. Technologie - proč Next.js a Firebase
7. Databázové schéma - struktura dat
8. Implementace - klíčové funkce
9. **Live demo** - ukázka aplikace
10. User testing - metodika a výsledky
11. Výsledky - metriky, feedback
12. Problémy a jejich řešení
13. Budoucí rozšíření
14. Závěr

**Vizuální materiál:**

- Wireframes z Figma
- Screenshots aplikace
- Screen recording hlavních funkcí
- Grafy z user testingu

---

## 5. HODNOTICÍ KRITÉRIA

### 5.1 Funkčnost projektu (40%)

- ✅ Všechny požadované funkce implementovány
- ✅ Aplikace je stabilní, bez kritických bugů
- ✅ Responzivní design funguje na mobilech
- ✅ Testováno na reálných uživatelích
- ⭐ Kvalita kódu (čistý, komentovaný)

### 5.2 Dokumentace (25%)

- Úplnost technické dokumentace
- Kvalita databázového návrhu
- Jasnost instalačního návodu
- Kvalita vědeckého článku
- Vizuální zpracování posteru

### 5.3 Prezentace a obhajoba (20%)

- Kvalita prezentace
- Live demo aplikace
- Schopnost vysvětlit architekturu
- Znalost Next.js a Firebase
- Vyhodnocení user testingu

### 5.4 Proces a samostatnost (15%)

- Pravidelná práce na projektu
- Kvalita průběžných reportů (R1, R2, R3)
- Vlastní iniciativa (experimentování s AI nástroji)
- Reakce na feedback
- Dodržování harmonogramu

---

## 6. TECHNICKÉ POŽADAVKY NA OBHAJOBU

### Co student musí umět vysvětlit

**Next.js:**

- Rozdíl mezi SSR, SSG, CSR
- Jak funguje routing v Next.js
- Co jsou API routes
- Server vs Client components (Next.js 14+)

**React:**

- Základní principy (komponenty, props, state)
- Hooks (useState, useEffect, useContext)
- Formuláře a validace

**Firebase:**

- Co je Firestore, jak funguje NoSQL
- Security Rules - jak chránit data
- Firebase Authentication - jak funguje
- Rozdíl mezi Realtime Database a Firestore

**Web development:**

- Responzivní design (media queries, flexbox, grid)
- REST API principy
- Základy HTTP (GET, POST, PUT, DELETE)
- Co je CORS a jak se řeší

**Databázový návrh:**

- Struktura kolekcí ve Firestore
- Denormalizace vs. normalizace (NoSQL specifika)
- Indexy a výkon dotazů

---

## 7. OČEKÁVANÉ PROBLÉMY A ŘEŠENÍ

### Možné výzvy

1. **Firebase Security Rules** - složité na pochopení
   - Řešení: Důkladně prostudovat dokumentaci, testovat v simulátoru

2. **Async operations** - práce s promises a async/await
   - Řešení: Použít async/await konzistentně, error handling

3. **State management** - synchronizace dat mezi komponenty
   - Řešení: Context API nebo Zustand pro globální state

4. **Výkon** - pomalé načítání velkého množství dat
   - Řešení: Pagination, lazy loading, caching

5. **Responzivní design** - náročné na mobilech
   - Řešení: Mobile-first přístup, testování na reálných zařízeních

6. **Formuláře** - validace a error handling
   - Řešení: React Hook Form + Zod schema validation

---

## 8. LITERATURA A ZDROJE

**Dokumentace:**

- Next.js Documentation - nextjs.org/docs
- Firebase Documentation - firebase.google.com/docs
- React Documentation - react.dev
- Tailwind CSS - tailwindcss.com

**Kurzy a tutoriály:**

- Next.js by Vercel (YouTube)
- Fireship.io - Firebase tutoriály
- Web Dev Simplified - React basics

**Knihy:**

- "Learning React" - O'Reilly
- "Fullstack React" - Accomazzo, Murray, Lerner

**Nástroje:**

- Figma - design a wireframes
- VS Code - editor
- Chrome DevTools - debugging
- Postman - API testování

---

## 9. ODEVZDÁNÍ

**Termín:** Nejpozději 5. května 2025

**Forma odevzdání:**

```
/Josef_Holecek_Krouzky_HB/
  ├── README.md (návod na spuštění)
  ├── paper.pdf (vědecký článek)
  ├── poster.pdf (poster A3)
  ├── dokumentace/
  │   ├── technicka_dokumentace.pdf
  │   ├── wireframes/ (Figma exporty)
  │   ├── database_schema.png
  │   └── user_testing_results.pdf
  ├── prezentace/
  │   └── obhajoba.pptx
  ├── videa/
  │   └── demo_walkthrough.mp4
  └── zdrojovy_kod/
      ├── next.config.js
      ├── package.json
      ├── src/
      │   ├── app/
      │   ├── components/
      │   └── lib/
      └── firebase.config.js
```

**GitHub repozitář:**

- Kód musí být verzovaný na GitHubu
- README s instrukcemi pro spuštění
- Pravidelné commity během vývoje

---

## SCHVÁLENÍ ZADÁNÍ

**Datum vydání zadání:** 10. prosince 2024  
**Podpis studenta:** ___________________  
**Podpis vedoucího:** ___________________

---

*Toto zadání je závazné. Jakékoliv změny musí být schváleny vedoucím práce.*
