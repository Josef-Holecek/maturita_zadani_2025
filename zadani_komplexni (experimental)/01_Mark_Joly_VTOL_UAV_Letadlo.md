# ZADÁNÍ MATURITNÍ PRÁCE

## Formální údaje

**Název projektu:** VCR VTOL UAV - Konstrukce letadla s vertikálním vzletem  
**Student:** Mark Joly  
**Školní rok:** 2024/2025  
**Obor:** Elektrotechnika / Mechatronika  
**Vedoucí práce:** [Jméno vedoucího]  
**Spolupracující student:** Adam Mikulič (komunikační systém)

---

## 1. ZADÁNÍ A KONTEXT PROJEKTU

### 1.1 Úvod a motivace

Bezpilotní letouny (UAV) s možností vertikálního vzletu a přistání (VTOL) představují univerzální platformu pro různé aplikace včetně rozšíření dosahu komunikačních systémů. Projekt se zaměřuje na konstrukci mechanické části letounu, který bude sloužit jako nosič komunikačních modulů pro rozšíření dosahu rádiové komunikace.

Klasické UAV vyžadují vzletovou a přistávací dráhu, což omezuje jejich nasazení v terénu. VTOL letouny kombinují výhody multikoptér (vertikální vzlet) s výhodami křídla (efektivní let vpřed, delší dolet). Projekt řeší reálnou potřebu v situacích, kdy je nutné rychle rozšířit komunikační dosah v nedostupném terénu.

### 1.2 Cíle projektu

**Hlavní cíl:**  
Navrhnout a zkonstruovat mechanickou část bezpilotního VTOL letounu schopného nést komunikační modul o hmotnosti min. 250g, s dobrými letovými vlastnostmi a možností snadného ovládání.

**Dílčí cíle:**

1. **Analýza a návrh**
   - Analýza existujících VTOL konfigurací
   - Výběr optimální konfigurace pro daný účel
   - Návrh geometrie křídla a ocasních ploch

2. **Konstrukce kostry**
   - Návrh uhlíkové trubkové kostry v CAD software (Fusion 360)
   - Výpočet pevnosti a hmotnosti konstrukce
   - Výroba uhlíkových komponent

3. **Aerodynamické povrchy**
   - Návrh šablon pro řezání EPP pěny
   - Výroba křídel a ocasních ploch z EPP
   - Optimalizace pro minimální hmotnost při zachování pevnosti

4. **Integrace a testování**
   - Montáž všech mechanických komponent
   - Vyvážení těžiště letounu
   - Testování stability a letových vlastností
   - Integrace se systémem Adama Mikuliče

5. **Dokumentace**
   - Výrobní výkresy a postupy
   - Návod na údržbu a opravy
   - Analýza letových vlastností

### 1.3 Rozsah projektu

**V rozsahu projektu je:**

- Návrh mechanické konstrukce letounu
- Výroba uhlíkové trubkové kostry
- Výroba křídel a ocasních ploch z EPP pěny
- Integrace motorů, regulátorů a serv
- Testování letových vlastností
- Možnost vypuštění komunikačního modulu
- Dokumentace konstrukce a výrobních postupů

**Mimo rozsah projektu:**

- Vývoj elektroniky (řeší Adam Mikulič)
- Programování autopilota (použit hotový ArduPilot)
- Vývoj komunikačního protokolu
- Testování na velké vzdálenosti (mimo praktické možnosti)

---

## 2. SPECIFIKACE ŘEŠENÍ

### 2.1 Technický popis

**Konfigurace letounu:**

- Typ: VTOL (Vertical Take-Off and Landing)
- Uspořádání: Tailsitter nebo tilt-rotor (podle výběru v analýze)
- Rozpětí křídel: cca 1,2 - 1,5 m
- Vzletová hmotnost: max. 2,5 kg (včetně komunikačního modulu)

**Materiály:**

- **Kostra:** Uhlíkové trubky (průměr 6-10 mm, různé tloušťky stěny)
- **Křídla a ocas:** EPP pěna (Expanded Polypropylene) - odolný, lehký materiál
- **Spojovací části:** 3D tisk (PLA/PETG), případně uhlíkové desky
- **Potah:** Samolepicí fólie nebo lak

**Nástroje a technologie:**

- CAD modelování: Autodesk Fusion 360
- Řezání EPP: Odporová řezačka (hot wire cutter) - vlastní výroba
- Práce s uhlíkem: Lepení epoxidem, řezání, broušení

**Flight controller:**

- Pixhawk nebo ArduPilot kompatibilní deska
- Integrace se systémem Adama Mikuliče

### 2.2 Funkční požadavky

1. **Nosnost:** Letoun musí unést min. 250g užitečného nákladu (komunikační box)
2. **VTOL schopnost:** Musí být schopen vzlétnout a přistát vertikálně
3. **Stabilita:** Stabilní let ve všech režimech (hover, přechod, let vpřed)
4. **Odolnost:** Konstrukce musí vydržet běžné nárazy při přistání
5. **Opravitelnost:** Poškozené části musí být snadno vyměnitelné
6. **Vyvážení:** Těžiště musí být v požadované poloze (cca 25-30% délky tětivy křídla)
7. **Modulárnost:** Možnost vypuštění/upuštění komunikačního boxu během letu
8. **Ovladatelnost:** Responzivní ovládání manuálním režimu

### 2.3 Nefunkční požadavky

- **Hmotnost:** Celková hmotnost max. 2,5 kg (optimálně pod 2 kg)
- **Dolet:** Min. 15 minut letu (závislé na baterii a konfiguraci)
- **Aerodynamika:** Minimální odpor, efektivní tvar křídla
- **Estetika:** Čistý, profesionální vzhled
- **Bezpečnost:** Fail-safe mechanismy (ochrana vrtulí, nouzové přistání)
- **Výrobní náklady:** Do 8 000 Kč (bez elektroniky)

---

## 3. HARMONOGRAM A MILNÍKY

### ✅ Září - Říjen 2024 (Hotovo)

- Schválení tématu
- Úvodní analýza VTOL konfigurací
- Výběr optimální konfigurace

### ✅ Listopad 2024 (R1 - hotovo)

- Základní návrh v CAD
- Objednávka materiálů
- Plán výroby

### 🔄 Prosinec 2024 (R2 - probíhá)

- **Uhlíková kostra** - kompletní CAD model
- **Fusion model** - finalizace designu
- **Šablony na EPP** - návrh a výroba odporové řezačky
- **Křídla + ocas** - výroba prototypových částí
- **Výzkum broušení EPP** - techniky pro kvalitní povrch

### Leden 2025 (R3 - deadline 8.1.)

- Dokončení všech mechanických komponent
- První kompletní sestavení letounu
- Vyvážení těžiště
- Integrace s elektronikou (spolupráce s Adamem)

### Únor 2025

- První testovací lety (hover test)
- Ladění PID regulátorů
- Úpravy podle výsledků testů

### Březen 2025

- Testování přechodového režimu (VTOL → let vpřed)
- Testování s komunikačním modulem
- Optimalizace hmotnosti

### Duben 2025

- Finální testování všech režimů
- Testování vypuštění komunikačního boxu
- Dokumentace výsledků

### Květen 2025

- Dokončení dokumentace
- Příprava prezentace a obhajoby
- Finální úpravy

---

## 4. POŽADOVANÉ VÝSTUPY

### 4.1 Funkční projekt

**Fyzický prototyp:**

- Kompletně funkční VTOL letoun
- Ověřeno testovacími lety
- Schopný nést komunikační modul
- Stabilní ve všech letových režimech

**Demonstrace:**

- Video z testovacích letů
- Demonstrace všech režimů (hover, přechod, let vpřed, přistání)
- Demonstrace vypuštění komunikačního boxu

### 4.2 Vědecký/odborný článek (paper)

**Rozsah:** 8-12 stran

**Obsah:**

1. **Úvod** - motivace, přehled VTOL technologií
2. **Analýza existujících řešení** - porovnání VTOL konfigurací (tailsitter, tilt-rotor, tilt-wing)
3. **Návrh konstrukce** - výběr konfigurace, návrh geometrie
4. **Výběr materiálů** - proč uhlík a EPP, vlastnosti materiálů
5. **Výrobní proces** - postup výroby, použité technologie
6. **Integrace systémů** - propojení s elektronikou, mechanika vypouštění boxu
7. **Testování** - metodika, výsledky letových testů
8. **Diskuse** - problémy při vývoji, řešení, vylepšení
9. **Závěr** - zhodnocení, dosažené parametry

### 4.3 Poster (A3)

**Obsah:**

- Vizualizace letounu (3D render z Fusion 360)
- Schéma konstrukce (rozložený pohled)
- Fotografie z výroby
- Fotografie/screenshot z testovacích letů
- Klíčové parametry (rozpětí, hmotnost, dolet)
- QR kód na video z testovacích letů

### 4.4 Technická dokumentace

**Rozsah:** 20-30 stran

**Obsah:**

1. **Technické specifikace**
   - Rozměry a hmotnostní bilance
   - Seznam všech komponent
   - Schéma zapojení mechanických částí

2. **CAD modely a výkresy**
   - Exportované výkresy z Fusion 360
   - Kótované rozměry všech dílů
   - Sestavovací výkresy

3. **Výrobní postupy**
   - Postup výroby uhlíkové kostry
   - Postup řezání EPP pěny
   - Postup lepení a montáže
   - Tipy a triky pro práci s materiály

4. **Montážní návod**
   - Krok za krokem sestavení letounu
   - Fotodokumentace montáže
   - Nastavení těžiště

5. **Provozní návod**
   - Předletová kontrola
   - Postup vzletu a přistání
   - Nastavení flight controlleru (základní parametry)

6. **Údržba a opravy**
   - Pravidelná údržba
   - Postup opravy poškozeného křídla/ocasu
   - Výměna poškozených trubek

7. **Měření a výsledky**
   - Naměřené letové vlastnosti
   - Spotřeba energie
   - Dolet a čas letu

### 4.5 Prezentace pro obhajobu

**Rozsah:** 15-20 slidů

**Struktura:**

1. Úvod - co je VTOL, proč je užitečný
2. Cíle projektu
3. Analýza konfigurací - porovnání variant
4. Návrh konstrukce - CAD modely
5. Materiály a technologie
6. Výrobní proces - fotodokumentace
7. Sestavení a integrace
8. Testování - video ukázky
9. Výsledky - dosažené parametry
10. Problémy a jejich řešení
11. Závěr a budoucí vylepšení

**Vizuální materiál:**

- 3D rendery z Fusion 360
- Fotografie z výroby
- Video z testovacích letů (embedded nebo GIF)
- Grafy (hmotnostní bilance, spotřeba energie)

---

## 5. HODNOTICÍ KRITÉRIA

### 5.1 Funkčnost projektu (40%)

- ✅ Letoun je schopen vertikálního vzletu a přistání
- ✅ Stabilní let ve všech režimech
- ✅ Unese požadovanou zátěž (250g)
- ✅ Ověřeno testovacími lety
- ⭐ Kvalita zpracování konstrukce

### 5.2 Dokumentace (25%)

- Úplnost technické dokumentace
- Kvalita CAD modelů a výkresů
- Jasnost výrobních postupů
- Kvalita vědeckého článku
- Vizuální zpracování posteru

### 5.3 Prezentace a obhajoba (20%)

- Kvalita prezentace
- Schopnost vysvětlit konstrukční řešení
- Znalost materiálů a technologií
- Schopnost obhájit konstrukční rozhodnutí
- Demonstrace funkčnosti

### 5.4 Proces a samostatnost (15%)

- Pravidelná práce na projektu
- Kvalita průběžných reportů (R1, R2, R3)
- Iniciativa při řešení problémů
- Spolupráce s Adamem Mikuličem
- Dodržování harmonogramu

---

## 6. TECHNICKÉ POŽADAVKY NA OBHAJOBU

### Co student musí umět vysvětlit

**Konstrukce:**

- Proč byla zvolena daná VTOL konfigurace
- Jak byly dimenzovány nosné plochy (křídlo, ocas)
- Výpočet těžiště a vyvážení
- Pevnostní výpočty uhlíkové konstrukce

**Materiály:**

- Vlastnosti uhlíkových kompozitů
- Proč EPP pěna pro křídla
- Techniky spojování různých materiálů
- Povrchová úprava

**Aerodynamika:**

- Základní aerodynamické principy VTOL
- Jak funguje přechod z hoveru do letu vpřed
- Stabilita a řiditelnost
- Vlivy těžiště na letové vlastnosti

**Výroba:**

- Postup výroby uhlíkové konstrukce
- Práce s odporovou řezačkou
- Techniky broušení a finální úpravy EPP
- Lepení a spojování komponent

---

## 7. OČEKÁVANÉ PROBLÉMY A ŘEŠENÍ

### Možné výzvy

1. **Vyvážení těžiště** - bude pravděpodobně potřeba několik iterací
2. **Přechodový režim** - nejtěžší fáze, vyžaduje správné PID nastavení
3. **Vibrace** - eliminace vibrací motů, vyvážení vrtulí
4. **Pevnost konstrukce** - najít optimum mezi hmotností a pevností
5. **Broušení EPP** - získání kvalitního povrchu

### Strategie řešení

- Modulární konstrukce pro snadné úpravy
- Postupné testování (nejdřív hover, pak přechod)
- Konzultace s vedoucím práce
- Využití simulací v Fusion 360
- Dokumentace všech změn a iterací

---

## 8. LITERATURA A ZDROJE

**Doporučená literatura:**

- ArduPilot VTOL Documentation
- RC Groups - VTOL section (forum)
- "Design and Control of Hybrid VTOL UAVs" (články a whitepapers)
- Model Airplane News - konstrukce RC letadel

**Online nástroje:**

- eCalc - kalkulačka pro návrh RC letadel
- Airfoil Tools - databáze profilů křídel
- RC Calculator - hmotnostní kalkulačky

---

## 9. ODEVZDÁNÍ

**Termín:** Nejpozději 5. května 2025

**Forma odevzdání:**

```
/Mark_Joly_VTOL_UAV/
  ├── README.md
  ├── paper.pdf (vědecký článek)
  ├── poster.pdf (poster A3)
  ├── dokumentace/
  │   ├── technicka_dokumentace.pdf
  │   ├── CAD_modely/
  │   │   ├── fusion360_projekt.f3d
  │   │   ├── exporty_PDF/
  │   │   └── exporty_STL/
  │   └── fotodokumentace/
  ├── prezentace/
  │   └── obhajoba.pptx
  └── videa/
      ├── testovaci_lety.mp4
      └── montaz_timelapse.mp4
```

---

## SCHVÁLENÍ ZADÁNÍ

**Datum vydání zadání:** 10. prosince 2024  
**Podpis studenta:** ___________________  
**Podpis vedoucího:** ___________________

---

**Poznámka:** Tento projekt je realizován ve spolupráci s Adamem Mikuličem, který se věnuje elektronické části (komunikační nody). Je nutná koordinace obou částí projektu.

*Toto zadání je závazné. Jakékoliv změny musí být schváleny vedoucím práce.*
