# ZADÁNÍ MATURITNÍ PRÁCE

## Formální údaje

**Název projektu:** VCR VTOL UAV - Komunikační relay systém  
**Student:** Adam Mikulič  
**Školní rok:** 2024/2025  
**Obor:** Elektrotechnika / Informační technologie  
**Vedoucí práce:** [Jméno vedoucího]  
**Spolupracující student:** Mark Joly (mechanická konstrukce letounu)

---

## 1. ZADÁNÍ A KONTEXT PROJEKTU

### 1.1 Úvod a motivace

V situacích, kdy je potřeba rozšířit dosah rádiové komunikace v obtížně dostupném terénu (hory, les, města), představují autonomní komunikační relay nody efektivní řešení. Projekt se zaměřuje na vývoj systému komunikačních modulů, které mohou být vypouštěny z bezpilotního letounu a slouží jako mezičlánky pro rozšíření dosahu mezi řídicí stanicí a dronem.

Klasický problém "ztráty signálu" při letu dronu za horizont nebo za překážky lze řešit vypuštěním komunikačního nodu na strategické místo, který pak přeposílá data mezi dronem a řídicí stanicí. Projekt řeší reálnou výzvu v oblasti dálkově řízených systémů.

### 1.2 Cíle projektu

**Hlavní cíl:**  
Navrhnout a realizovat systém autonomních komunikačních relay nodů, které lze vypustit z VTOL letounu a které rozšíří dosah rádiové komunikace o nejméně jeden skok (relay hop).

**Dílčí cíle:**

1. **Analýza a návrh systému**
   - Analýza komunikačních protokolů (MAVLink, RC protokoly)
   - Návrh architektury relay systému
   - Výběr vhodné rádiové technologie (2.4 GHz, 433 MHz, LoRa)

2. **Návrh hardware**
   - Návrh vlastního PCB pro komunikační node
   - Výběr mikrokontroléru a rádiových modulů
   - Návrh napájecího systému (baterie, řízení spotřeby)
   - Návrh ochranného pouzdra (3D tisk)

3. **Firmware a software**
   - Implementace relay logiky
   - Správa spojení (handshake, reconnect)
   - Implementace low-power režimů
   - Telemetrie (stav baterie, síla signálu)

4. **Integrace s dronem**
   - Mechanismus vypouštění z letounu (spolupráce s Markem)
   - Komunikace s flight controllerem
   - Testování dosahu a spolehlivosti

5. **Testování a optimalizace**
   - Měření dosahu komunikace
   - Testování latence relay spojení
   - Optimalizace spotřeby energie
   - Field test v reálném terénu

### 1.3 Rozsah projektu

**V rozsahu projektu je:**

- Návrh a výroba PCB pro komunikační node
- Vývoj firmware pro relay funkci
- Návrh a výroba ochranného pouzdra (node cover)
- Implementace low-power režimů
- Systém pro vypouštění nodu z dronu
- Základní telemetrie (stav baterie, RSSI)
- Dokumentace návrhu a testování

**Mimo rozsah projektu:**

- Mechanická konstrukce letounu (řeší Mark Joly)
- Vývoj autopilota (použit ArduPilot)
- Mesh networking (více nodů)
- Video přenos přes relay
- GPS tracking vypuštěných nodů (možné rozšíření)

---

## 2. SPECIFIKACE ŘEŠENÍ

### 2.1 Technický popis

**Architektura systému:**

```
[Řídicí stanice] <--RF--> [Relay Node] <--RF--> [Dron]
                            ↓
                    [Vypuštěn z dronu]
```

**Hardware komponenty:**

- **Mikrokontrolér:** ESP32 / STM32 (podle výkonu a spotřeby)
- **Rádiové moduly:**
  - 2.4 GHz transceiver (např. NRF24L01+ nebo ESP32 WiFi)
  - Alternativa: 433 MHz LoRa pro větší dosah
- **Napájení:** LiPo baterie (1S nebo 2S), řízení nabíjení
- **Senzory:** Tlačítko reset, LED indikace stavu
- **Pouzdro:** 3D tisk, odolné proti pádu z výšky

**Software stack:**

- **Jazyk:** C/C++ (Arduino nebo ESP-IDF / STM32CubeIDE)
- **Protokol:** MAVLink pro komunikaci s ArduPilot
- **RTOS:** FreeRTOS (pokud potřeba paralelních tasků)

**Mechanismus vypouštění:**

- Elektromagnetický nebo servo-driven zámek
- Integrace s PWM výstupem flight controlleru
- Bezpečné oddělení během letu

### 2.2 Funkční požadavky

1. **Relay funkce:** Node musí přeposílat data mezi dvěma RF zařízeními
2. **Dosah:** Rozšíření komunikačního dosahu minimálně o 500 m (1 hop)
3. **Latence:** Latence relay max. 50 ms (pro RC control)
4. **Výdrž baterie:** Min. 30 minut aktivního relay režimu
5. **Autonomní start:** Node se aktivuje po vypuštění (detekce volného pádu)
6. **Indikace stavu:** LED indikace (power on, relay active, low battery)
7. **Odolnost:** Musí vydržet pád z výšky 50 m na trávu/půdu
8. **Hmotnost:** Max. 250 g včetně baterie a pouzdra

### 2.3 Nefunkční požadavky

- **Spotřeba energie:** Optimalizováno na co nejnižší spotřebu
- **Spolehlivost:** 95%+ úspěšnost relay komunikace
- **Teplotní rozsah:** Provoz 0-40°C
- **Rozměry:** Max. 10 × 10 × 5 cm (aby se vešel do dronu)
- **Náklady:** Do 1500 Kč na jeden node (včetně PCB výroby)
- **Opravitelnost:** Modulární design, snadno vyměnitelné komponenty

---

## 3. HARMONOGRAM A MILNÍKY

### ✅ Září - Říjen 2024 (Hotovo)

- Schválení tématu
- Analýza komunikačních protokolů
- Výběr hardware komponent

### ✅ Listopad 2024 (R1 - hotovo)

- Základní koncept zapojení
- Objednávka součástek
- První experimenty s rádiovou komunikací

### 🔄 Prosinec 2024 (R2 - probíhá)

- **Node cover** - návrh a 3D tisk ochranného pouzdra
- **Nákup materiálů** - PCB materiál, konektory, baterie
- **Prototyp na breadboardu** - ověření funkčnosti zapojení
- Testování základní relay komunikace

### Leden 2025 (R3 - deadline 8.1.)

- **Návrh PCB v KiCAD** - kompletní schéma a layout
- **Objednání PCB** výroby (např. JLCPCB)
- **Firmware v0.1** - základní relay funkce
- První testování dosahu

### Únor 2025

- Osazení PCB, testování
- Implementace MAVLink protokolu
- Integrace s ArduPilot flight controllerem
- Návrh mechanismu vypouštění (spolupráce s Markem)

### Březen 2025

- Optimalizace spotřeby (low-power režimy)
- Implementace telemetrie
- Testování v reálných podmínkách
- Finalizace node cover designu

### Duben 2025

- Kompletní integrace s dronem
- Testování vypouštění a relay funkce během letu
- Měření dosahu a latence
- Dokumentace výsledků

### Květen 2025

- Finální testování
- Dokončení dokumentace
- Příprava prezentace a obhajoby

---

## 4. POŽADOVANÉ VÝSTUPY

### 4.1 Funkční projekt

**Fyzické prototypy:**

- Minimálně 2 funkční relay nody (PCB + pouzdro)
- Jeden node integrovaný do dronu s vypouštěcím mechanismem
- Demonstrace relay komunikace v reálném prostředí

**Demonstrace:**

- Video: Vypuštění nodu z dronu
- Video: Testování relay komunikace přes node
- Live demo: Řízení dronu přes relay node

### 4.2 Vědecký/odborný článek (paper)

**Rozsah:** 8-12 stran

**Obsah:**

1. **Úvod** - problematika dosahu RF komunikace u dronů
2. **Analýza řešení** - přehled existujících relay systémů
3. **Návrh architektury** - blokové schéma systému
4. **Hardware design** - popis PCB návrhu, výběr komponent
5. **Software implementace** - relay logika, protokoly, optimalizace
6. **Integrace s dronem** - mechanismus vypouštění
7. **Testování** - metodika, měření dosahu, latence, výdrže
8. **Výsledky** - dosažené parametry, grafy
9. **Diskuse** - problémy, řešení, možná vylepšení
10. **Závěr** - shrnutí přínosu projektu

### 4.3 Poster (A3)

**Obsah:**

- Blokové schéma relay systému
- Fotografie PCB (osazeného a neosazeného)
- Fotografie node coveru (3D tisk)
- Schéma komunikace (řídicí stanice → node → dron)
- Graf: Dosah vs. latence
- Fotografie dronu s integrovaným nodem
- QR kód na demo video

### 4.4 Technická dokumentace

**Rozsah:** 20-30 stran

**Obsah:**

1. **Systémová architektura**
   - Blokové schéma celého systému
   - Popis komunikačních toků
   - Stavový diagram firmware

2. **Hardware dokumentace**
   - Kompletní schéma zapojení (KiCAD schematic PDF)
   - PCB layout (PDF)
   - Bill of Materials (BOM) - seznam součástek s objednacími kódy
   - Pinout mikrokontroléru
   - Zapojení rádiových modulů

3. **Firmware dokumentace**
   - Struktura kódu (moduly, funkce)
   - Flow chart hlavních procesů
   - Popis použitých knihoven
   - API dokumentace (pokud relevantní)
   - Konfigurace (nastavitelné parametry)

4. **Výrobní a montážní návod**
   - Postup objednání PCB
   - Seznam potřebných nástrojů (páječka, multimetr, etc.)
   - Krok za krokem osazení PCB
   - Programování firmware (jak nahrát kód)
   - Testování funkčnosti po montáži

5. **Uživatelská příručka**
   - Nabíjení baterie
   - Indikace stavů (LED kódy)
   - Postup aktivace nodu
   - Párování s řídicí stanicí a dronem

6. **Integrace s dronem**
   - Instalace nodu do dronu
   - Nastavení flight controlleru
   - Postup pro vypuštění během letu
   - Bezpečnostní opatření

7. **Testování a výsledky**
   - Metodika testování dosahu
   - Naměřené hodnoty (dosah, latence, spotřeba)
   - Grafy a tabulky
   - Vyhodnocení úspěšnosti

8. **Troubleshooting**
   - Časté problémy a jejich řešení
   - Debugování komunikace
   - Výměna poškozených komponent

### 4.5 Prezentace pro obhajobu

**Rozsah:** 15-20 slidů

**Struktura:**

1. Úvod - problém dosahu RF komunikace
2. Cíle projektu
3. Analýza existujících řešení
4. Návrh architektury systému
5. Hardware design - PCB návrh
6. Výběr komponent - zdůvodnění
7. Software - relay logika
8. 3D model node cover
9. Výrobní proces - fotodokumentace
10. Integrace s dronem
11. Testování - metodika
12. Výsledky - grafy dosahu a latence
13. Demo video - vypuštění a relay
14. Problémy a jejich řešení
15. Závěr a možná vylepšení

**Vizuální materiál:**

- Schémata zapojení (zjednodušené pro prezentaci)
- 3D render PCB
- Fotografie z výroby
- Grafy výsledků testování
- Video ukázka funkčnosti

---

## 5. HODNOTICÍ KRITÉRIA

### 5.1 Funkčnost projektu (40%)

- ✅ Node funguje jako relay pro RF komunikaci
- ✅ Rozšíření dosahu minimálně o 500 m
- ✅ Stabilní komunikace, nízká latence
- ✅ Bezproblémové vypouštění z dronu
- ⭐ Kvalita hardware designu (PCB)

### 5.2 Dokumentace (25%)

- Úplnost technické dokumentace (schéma, BOM, firmware)
- Kvalita PCB návrhu (správné routing, termální management)
- Dokumentace testování
- Kvalita vědeckého článku
- Vizuální zpracování posteru

### 5.3 Prezentace a obhajoba (20%)

- Kvalita prezentace
- Schopnost vysvětlit hardware design
- Znalost RF komunikačních protokolů
- Schopnost obhájit volbu komponent
- Demonstrace funkčnosti

### 5.4 Proces a samostatnost (15%)

- Pravidelná práce na projektu
- Kvalita průběžných reportů (R1, R2, R3)
- Schopnost řešit technické problémy
- Spolupráce s Markem Jolym
- Dodržování harmonogramu

---

## 6. TECHNICKÉ POŽADAVKY NA OBHAJOBU

### Co student musí umět vysvětlit

**Hardware:**

- Proč byla zvolena konkrétní rádiová technologie
- Jak funguje RF komunikace (základy)
- Návrh PCB - routing, impedance matching (pokud relevantní)
- Výběr mikrokontroléru - parametry, zdůvodnění
- Napájecí systém - LiPo charging, voltage regulation

**Software:**

- Struktura firmware (main loop, interrupt handling)
- Implementace relay logiky
- MAVLink protokol - struktura, použité zprávy
- Low-power režimy - jak fungují, kdy se aktivují
- Debugging - jak testovat a ladit RF komunikaci

**RF komunikace:**

- Rozdíl mezi 2.4 GHz a 433 MHz (výhody/nevýhody)
- Co ovlivňuje dosah (výkon, anténa, prostředí)
- Latence - co ji způsobuje, jak minimalizovat
- RSSI - co znamená, jak se používá

**Integrace:**

- Jak node komunikuje s flight controllerem
- Jak funguje vypouštěcí mechanismus
- Bezpečnostní opatření (fail-safe)

---

## 7. OČEKÁVANÉ PROBLÉMY A ŘEŠENÍ

### Možné výzvy

1. **Dosah rádiové komunikace** - může být nižší než očekáváno
   - Řešení: Lepší anténa, zvýšení výkonu, optimalizace umístění

2. **Latence relay** - může být příliš vysoká pro RC control
   - Řešení: Optimalizace kódu, použití rychlejšího MCU

3. **Spotřeba energie** - baterie vydrží krátce
   - Řešení: Implementace deep sleep, optimalizace TX power

4. **Interference** - rušení od motorů dronu
   - Řešení: Stínění, EMI filtering, vzdálenost od zdrojů rušení

5. **Mechanické poškození při pádu** - node se rozbije
   - Řešení: Silnější pouzdro, tlumící materiál (pěna)

6. **PCB chyby v návrhu** - nefunkční první revize
   - Řešení: Pečlivé review schématu, testování na breadboardu předem

---

## 8. LITERATURA A ZDROJE

**Doporučená literatura:**

- MAVLink Protocol Documentation
- ESP32 / STM32 Datasheet a Reference Manual
- "Wireless Communication Principles" - základy RF
- ArduPilot Documentation - integrace s flight controllerem
- KiCAD Documentation - návrh PCB

**Online zdroje:**

- RCGroups.com - fórum pro RC projekty
- DroneCode.org - open source drone software
- Hackaday.io - projekty podobného typu
- GitHub - open source relay projekty

**Nástroje:**

- KiCAD - návrh PCB (open source)
- Fusion 360 - návrh 3D pouzdra
- Arduino IDE / PlatformIO - vývoj firmware
- QGroundControl - testování MAVLink komunikace

---

## 9. ODEVZDÁNÍ

**Termín:** Nejpozději 5. května 2025

**Forma odevzdání:**

```
/Adam_Mikulic_VTOL_UAV_Node/
  ├── README.md
  ├── paper.pdf (vědecký článek)
  ├── poster.pdf (poster A3)
  ├── dokumentace/
  │   ├── technicka_dokumentace.pdf
  │   ├── hardware/
  │   │   ├── schematic.pdf (schéma zapojení)
  │   │   ├── pcb_layout.pdf
  │   │   ├── BOM.xlsx (seznam součástek)
  │   │   └── kicad_projekt/ (zdrojové soubory)
  │   ├── firmware/
  │   │   └── src/ (zdrojové kódy)
  │   ├── 3d_models/
  │   │   └── node_cover.stl
  │   └── fotodokumentace/
  ├── prezentace/
  │   └── obhajoba.pptx
  └── videa/
      ├── vypousteni_nodu.mp4
      ├── relay_test.mp4
      └── range_test.mp4
```

---

## SCHVÁLENÍ ZADÁNÍ

**Datum vydání zadání:** 10. prosince 2024  
**Podpis studenta:** ___________________  
**Podpis vedoucího:** ___________________

---

**Poznámka:** Tento projekt je realizován ve spolupráci s Markem Jolym, který se věnuje mechanické konstrukci VTOL letounu. Je nutná úzká koordinace obou částí projektu, zejména při integraci vypouštěcího mechanismu.

*Toto zadání je závazné. Jakékoliv změny musí být schváleny vedoucím práce.*
