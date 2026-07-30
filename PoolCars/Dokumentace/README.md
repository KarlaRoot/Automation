# Dokumentace

Tato složka je určena pro technickou a uživatelskou dokumentaci aplikace PoolCars.
# PoolCar

*rezervace aut na SharePointu*

# Seznamy

| Seznam | Popis |
|--------|-------|
| PoolCar Requests | Evidence veškerých žádostí o rezervace aut. Hlavní formulář. |
| PoolCar Log Book | Kniha jízd. |
| PoolCar Drives | Seznam všech jednotlivých jízd. |
| PoolCar Reservation Calendar | Kalendář, ve kterém jsou zobrazeny všechny rezervace. |
| PoolCar Cars | Seznam aut určených k rezervaci. |
| PoolCar Approvers | Seznam oprávněných schvalovatelů. |

# Workflow a seznamy nad kterými běží

| Workflow |
|----------|
| PoolCar Request: PoolCar Car Request ID |
| PoolCar Request Edit Item |
| PoolCar Log Book: PoolCar Log Book WF |
| PoolCar Cars: PoolCar CARID |
| PoolCar Drives: PoolCar Drive ID |

# PoolCar Request list

| Název sloupce | Typ pole sloupce | Typ pole ve formuláři | Popis |
|---------------|------------------|-----------------------|-------|
| ApproverPosition | Single line of text | calculated lookup do UPS | Pozice schvalovatele |
| ApproverString | Single line of text | calculated převod jména na string | Jméno schvalovatele |
| Car history | Single line of text | není ve formu | Uložení původního auta kvůli porovnání změn-WF |
| Car Request ID | Single line of text | Identifikátor v rámci listu Car Request | Počítá se pomocí WF |
| Car Request ID menu | Single line of text | Identifikátor v rámci listu Car Request | Počítá se pomocí WF |
| Cíl cesty Město | Single line of text | Single line text-edit | Město, kam je směřována cesta |
| Cíl cesty Stát | Single line of text | Single line text-edit | Stát, kam je směřována cesta |
| Created | Date and Time | defaultní pole SHP | Datum kdy byla událost vytvořena |
| Dálniční známka | Choice | Check boxes | Dálniční známky, které budou potřeba k jízdě |
| Department | Single line of text | calculated lookup do UPS | Oddělení žadatele |
| EndTime | Date and Time | Date and Time | Konec pracovní cesty |
| Jiný kontakt | Single line of text | Single line text-edit | Možnost vepsání jiného kontaktu |
| Komentáře k zamítnutí | Multiple lines of text | není ve formu | Evidence komentářů ze schvalovacího formuláře |
| Konečný stav nádrže (l) | Number | Number-edit | |
| Konečný stav tachometru | Number | Number-edit | |
| KontrolaStavu | Single line of text | není ve formu | Uložení původního stavu kvůli porovnání změn-WF |
| Modified | Date and Time | defaultní pole SHP | Datum změny |
| PhoneLine | Single line of text | calculated lookup do UPS | Interní linka na žadatele |
| Pneumatiky | Single line of text | calculated lookup do listu Cars | Typy pneumatik, které auto má evidované |
| Počet přepravovaných osob | Choice | Dropdown | Výběr počtu osob (1–12) |
| PoolCarAdmin comment | Single line of text | Multiple lines of text-edit | Komentář PoolCar administrátora |
| PoolCarCCSKarta | Lookup | calculated lookup do listu Cars | Jaká CCS karta je přiřazena k autu |
| PoolCarDZ | Single line of text | calculated lookup do listu Cars | Jaké dálniční známky má auto |
| PoolCarIDCAR | Single line of text | calculated lookup do listu Cars | Specifické ID vozidla |
| PoolCarPoskozeniVozu | Single line of text | calculated lookup do listu Cars | Poškození vozu po poslední cestě |
| PoolCarSPZ | Single line of text | calculated lookup do listu Cars | SPZ |
| PoolCarStavNadrze | Single line of text | calculated lookup do listu Cars | Stav nádrže |
| PoolCarStringCar | Single line of text | calculated lookup do listu Cars | ModelTypZnámka |
| PoolCarTachometr | Single line of text | calculated lookup do listu Cars | Tachometr |
| PoolCarVIN | Single line of text | calculated lookup do listu Cars | VIN |
| PoolCarZnackaModelTypKaroserie | Lookup | lookup do listu Cars | ModelTypZnámka |
| PositionName | Single line of text | calculated lookup do UPS | Název pozice žadatele |
| Poškození vozu po cestě | Single line of text | Single line text-edit | Poškození vozidla po cestě. Workflow propisuje hodnotu do seznamu Cars. |
| Předpokládaný nájezd km | Number | Single line text-edit | Odhad počtu kilometrů během služební cesty |
| RequestorContactEmail | Single line of text | calculated lookup do UPS | Email žadatele |
| RequestorPerson | Person or Group | calculated lookup do UPS | Jméno žadatele |
| RequestorString | Single line of text | calculated lookup do UPS | Jméno žadatele jako text |
| RequestStatus | Choice | Needitovatelné pole | Aktuální stav žádosti |
| Schvalovatel | Lookup | Lookup do listu Approvers | Jméno schvalovatele |
| Školení řidičů | Choice | Check boxes | Bez zaškrtnutí není možné pokračovat |
| Skutečný nájezd | Number | Number-edit | |
| StartTime | Date and Time | Date and Time | Datum odjezdu |
| Účel cesty | Single line of text | Single line text-edit | Účel pracovní cesty |
| Začátek cesty | Single line of text | calculated lookup do listu Cars | Lokace vozidla |
| Zahraniční cesta | Choice | Check boxes | Tuzemská nebo zahraniční cesta |
| Autor | Person or Group | defaultní pole SHP | Osoba, která podala žádost |
| Modified By | Person or Group | defaultní pole SHP | Poslední editor |
| StavVozu | Choice | Dropdown | Rezervované / Volné |


# PoolCar Request Form

V úvodu je třeba zaškrtnout, že žadatel absolvoval školení řidičů. Bez zaškrtnutí není formulář vůbec viditelný.

Ostatní úvodní pole jsou needitovatelná a vytváří se automaticky.

Po zaškrtnutí výše zmíněného pole se objeví většina formuláře až na část **Shrnutí cesty**, která bude vidět až když je auto ve stavu **Vráceno**.

## Formulář má 4 části

### 1. Informace o žadateli

**Vyplňuje Autor nebo Žadatel**

Pole **Žadatel** je typu **Person**. Po vepsání počátečních písmen nabízí jména uživatelů ve firmě.

Pole je povinné.

Do pole **Jiný kontakt** je možné vyplnit jiný kontakt, než máme registrovaný v systému.

V tomto oddílu se zároveň vyplňuje **Schvalovatel** (Lookup do listu Approvers). Toto pole je povinné.

Ostatní pole jsou needitovatelná a informace k osobám se pouze zobrazují z dat v SharePointu.

---

### 2. Informace o služební cestě

**Vyplňuje Autor nebo Žadatel**

Pole **Začátek cesty** je lokace auta, která se propisuje z listu **PoolCar Cars**.

Jinak jsou všechna pole editovatelná.

---

### 3. PoolCar - výběr auta

**Vyplňuje Autor nebo Žadatel**

V tomto oddílu se vybírá příslušné auto.

Pole **Značka, model, typ karoserie a dálniční známka** je povinné.

Ostatní pole nejsou editovatelná a pouze se zobrazují z jiných seznamů:

- PoolCar Cars
- PoolCar Reservation Calendar

---

### 4. Shrnutí služební cesty

**Vyplňuje PoolCar administrátor**

Oddíl se zobrazí ve chvíli, kdy je auto ve stavu **Vráceno**.

Poté je možné všechna pole vyplnit.

---

## Povinná pole

- Žadatel
- Schvalovatel
- Značka, model, typ karoserie a dálniční známka

## Tlačítka formuláře

Formulář obsahuje 9 tlačítek.

| Tlačítko | Funkce |
|----------|--------|
| Zrušeno | Nastaví Request Status na **Zrušeno** a uloží záznam. |
| Vráceno | Nastaví Request Status na **Vráceno** a uloží záznam. |
| Předáno | Nastaví Request Status na **Předáno** a uloží záznam. |
| Uzavřeno | Nastaví Request Status na **Uzavřeno** a uloží záznam. |
| Potvrdit | Nastaví Request Status na **Potvrzeno** a uloží záznam. |
| Odeslat ke schválení | Nastaví Request Status na **Ke schválení** a uloží záznam. |
| Uložit | Uloží záznam. |
| Storno | Zruší editaci formuláře. |
| Kniha jízd | Uloží záznam a otevře nový formulář nad listem **PoolCar Log Book**. |

Tlačítka jsou viditelná pouze pro příslušné stavy žádosti a skrývají se podle aktuálního stavu žádosti.

Viz stavový diagram.

---

# Workflow

## 1. PoolCar Car Request ID

Workflow se spouští při založení položky.

Provádí následující operace:

- vytvoření specifického ID záznamu (CarReqID),
- změna stavu na **Ke schválení**,
- odeslání notifikace o založení žádosti,
- vytvoření úkolu pro schvalovatele.

Schvalovatel může:

- žádost schválit,
- žádost zamítnout.

Po schválení:

- stav se změní na **Schváleno**,
- identifikátor schváleného auta (**CarID**) se uloží do pole **Car History**.

Po zamítnutí:

- stav se změní na **Zamítnuto**.

V obou případech workflow odešle notifikace zúčastněným osobám.

---

## 2. PoolCar Request Edit Item

Workflow se spouští při editaci položky.

Jednotlivé akce provádí podle aktuálního stavu žádosti.

### Stav Potvrzeno

Workflow využívá pole **Car History** pro porovnání, zda bylo změněno rezervované vozidlo.

Pokud bylo vozidlo změněno, nastaví stav:

**Potvrzeno se změnou**

Ve stavech:

- Potvrzeno
- Potvrzeno se změnou

je vozidlo rezervováno v listu **PoolCar Reservation Calendar** jako rezervace.

### Stav Uzavřeno

Workflow aktualizuje údaje v seznamu **PoolCar Cars**:

- stav tachometru,
- stav nádrže,
- poškození vozidla.

### Stav Vráceno

Workflow změní v **PoolCar Reservation Calendar** hodnotu **CalendarStatus**

z:

- Rezervované

na:

- Volné.

### Stav Zrušeno

Pokud PoolCar administrátor záznam zruší, workflow:

- nastaví stav **Zrušeno**,
- změní CalendarStatus na zrušenou rezervaci,
- rezervace se přesune do pohledu **Smazané rezervace**.

# PoolCar Cars list

Spravuje **PoolCar administrátor**.

> **Poznámka k typům polí:**  
> U některých polí je typ sloupce (**Number**) odlišný od typu pole ve formuláři (**Single line of text**). Formuláře jsou vytvořené v SharePointu 2016 a hodnoty se do těchto polí propisují z formuláře jako text, přestože datový typ sloupce je číselný.

Evidence veškerého vozového parku určeného ke krátkodobým služebním cestám.

| Název sloupce | Typ pole sloupce | Typ pole ve formuláři | Popis |
|---------------|------------------|-----------------------|-------|
| VIN | Single line of text | Single line of text-edit | |
| SPZ | Single line of text | Single line of text-edit | |
| Barva | Single line of text | Single line of text-edit | |
| Rok výroby | Date and Time | Date and Time | |
| Dálniční známka | Choice | Check Boxes | CZ, PL, HU, SK |
| Typ karoserie | Choice | Dropdown | Sedan, kombi |
| Obsah motoru (cm3) | Number | Number-edit | |
| Výkon (KW) | Number | Number-edit | |
| Průměrná spotřeba dle TP | Number | Number-edit | |
| Počet míst | Number | Number-edit | |
| Doba držení (dny) | Number | Number-edit | |
| Min nájezd km | Number | Number-edit | |
| Max nájezd km | Single line of text | Single line of text-edit | |
| CARID | Single line of text | Identifikátor v rámci listu Car | Počítá se pomocí WF |
| Aktuální stav tachometru | Number | Number-edit | |
| Aktuální stav nádrže | Number | Number-edit | |
| Status vozu | Choice | Dropdown | Volné / Rezervované |
| Popis poškození vozu | Single line of text | Single line of text | Aktualizuje se na základě vstupu z Requestu |
| Číslo CCS karty | Number | Number-edit | |
| Značka a model auta | Single line of text | Single line of text-edit | |
| ZnačkaModelTypKaroserieAuta | Calculated | | Sloučení několika sloupců |
| ModelTypZnámka | Single line of text | Single line of text | Sloučení textu pomocí WF |
| LokaceAuta | Choice | Dropdown | Praha, Bratislava |
| Modified | Date and Time | defaultní pole SHP | Naposledy změněno dne |
| Created | Date and Time | defaultní pole SHP | Vytvořeno dne |
| Created By | Person or Group | defaultní pole SHP | Osoba, která podala žádost |
| Modified By | Person or Group | defaultní pole SHP | Osoba, která naposledy změnila žádost |

---

# PoolCar Log Book list

| Název sloupce | Typ pole sloupce | Typ pole ve formuláři | Popis |
|---------------|------------------|-----------------------|-------|
| Car Request ID menu | Single line of text | | Identifikátor v rámci listu Car. Počítá se pomocí WF |
| Datum | Date and Time | Date and Time | |
| Počáteční stav tachometru (km) | Single line of text | Single line of text | Propisuje se z PoolCar Request |
| Soukromě ujeté km | Number | Number | Počítá se pomocí WF |
| Služebně ujeté km | Number | Number | Počítá se pomocí WF |
| Poškození auta | Multiple lines of text | | |
| Tankování litry | Number | Number | Počítá se pomocí WF |
| Tankování cena | Number | Number | Počítá se pomocí WF |
| Konečný stav nádrže | Number | Number | |
| Konečný stav tachometru (km) | Number | Number | Propisuje se pomocí WF do PoolCar Cars |
| Měsíc | Choice | Dropdown | Měsíc uzavření záznamu |
| Cena PHM služební km | Number | Number | |
| Cena PHM soukromé km | Number | Number | |
| IDLOGBOOK | Single line of text | Single line of text | Počítá se pomocí WF |
| ID DRIVE | Single line of text | Single line of text | Propisuje se z PoolCar Drives |
| CARID | Single line of text | Single line of text | Propisuje se z PoolCar Request |
| Jméno žadatele | Single line of text | Single line of text | Propisuje se z PoolCar Request |
| UcelCesty | Single line of text | Single line of text | Propisuje se z PoolCar Request |
| PoolCarRequestID | Single line of text | Single line of text | Propisuje se z PoolCar Request |
| SPZ | Single line of text | Single line of text | Propisuje se z PoolCar Request |
| CelkovyNajezdKm | Single line of text | Single line of text | Počítá se pomocí WF |
| Modified | Date and Time | defaultní pole SHP | Naposledy změněno dne |
| Created | Date and Time | defaultní pole SHP | Vytvořeno dne |
| Created By | Person or Group | defaultní pole SHP | Osoba, která podala žádost |
| Modified By | Person or Group | defaultní pole SHP | Osoba, která naposledy změnila žádost |

---

# PoolCar Log Book form

V hlavním formuláři **PoolCar Request** ve stavu **Vráceno** je odkaz na **Knihu jízd**.

Zakládá se po vyplnění poslední části formuláře **Shrnutí služební cesty**.

Po kliknutí na tlačítko **Kniha jízd** je uživatel přesměrován na list **PoolCar LogBook**, kde se otevře nový formulář.

Do formuláře se z Requestu propisuje:

- jméno žadatele,
- číslo Requestu,
- účel cesty,
- počáteční stav tachometru.

V listu je třeba přeuložit záznam tlačítkem **Vytvoř záznam**.

Pokud se neobjeví **LBookID**, je třeba aktualizovat stránku (**F5**).

Jinak se neobjeví odkaz **Add New Item** a není možné přidávat jízdy.

---

# Workflow

## PoolCar Log Book WF

Workflow:

- přiděluje jedinečné **LBook ID**,
- sčítá celkové km,
- sčítá tankování,
- sčítá služební km,
- sčítá soukromé km,
- ukládá výsledky do **PoolCar LogBook**,
- kontroluje vyplnění konečného stavu tachometru,
- aktualizuje údaje v seznamu **PoolCar Cars**,
- používá nový stav tachometru jako počáteční hodnotu pro další rezervaci.

# PoolCar Reservation Calendar list

V tomto kalendáři workflow z **PoolCar Request** automaticky vytváří rezervaci, pokud je nastaven stav **Potvrzeno**.

Základní view je **Calendar**, kde jsou zobrazena pouze auta s hodnotou **CalendarStatus = Rezervace**.

Další dostupná zobrazení:

- **Historie rezervací** - obsahuje všechna vrácená vozidla.
- **Smazané rezervace** - obsahuje historii zrušených rezervací.

Hodnota **CalendarStatus** je řízena workflow z **PoolCar Request**.

---

# PoolCar Drives list

| Název sloupce | Typ pole sloupce | Typ pole ve formuláři | Popis |
|---------------|------------------|-----------------------|-------|
| IDDrive | Single line of text | | Identifikátor v rámci listu Drives. Počítá se pomocí WF |
| Datum | Date and Time | Date and Time | |
| Odkud-kam | Single line of text | Single line of text-edit | |
| Účel cesty | Single line of text | Single line of text-edit | |
| Stav tachometru po jízdě | Number | Single line of text-edit | |
| Ujeto služebně | Number | Single line of text-edit | |
| Ujeto soukromě | Number | Single line of text-edit | |
| Tankování litry | Number | Single line of text-edit | |
| Tankování cena | Number | Single line of text-edit | |
| Platba | Choice | Dropdown | CCS, Cash |
| IDLOGBOOK | Single line of text | Single line of text | Propsaný záznam z knihy jízd |
| CARID | Single line of text | Single line of text | Propsaný záznam z knihy jízd |
| ZadatelString | Single line of text | Single line of text | Propsaný záznam z knihy jízd |
| SkutecnyNajezdDrive | Single line of text | Calculated Value | Součet služebních a soukromých kilometrů |
| Modified | Date and Time | defaultní pole SHP | Naposledy změněno dne |
| Created | Date and Time | defaultní pole SHP | Vytvořeno dne |
| Created By | Person or Group | defaultní pole SHP | Osoba, která podala žádost |
| Modified By | Person or Group | defaultní pole SHP | Osoba, která naposledy změnila žádost |

---

# PoolCar Drives form

Po kliknutí na odkaz **Add New Item** z formuláře **PoolCar Log Book** je uživatel přesměrován do seznamu **PoolCar Drives**, kde přidává jednotlivé jízdy.

Do každé jízdy se automaticky propisují údaje:

- LBookID,
- jméno žadatele,
- CARID.

Ve spodní části formuláře jsou dvě tlačítka:

| Tlačítko | Funkce |
|----------|--------|
| Save and continue | Uložení záznamu a pokračování v zadávání dalších jízd |
| Save and Back | Uložení záznamu a návrat do knihy jízd |

Ve výsledku je jedné knize jízd přiřazeno více záznamů jízd.

---

# PoolCar Approvers list

Seznam jmen schvalovatelů oprávněných schválit služební cestu.

Slouží jako **Lookup** z formuláře **PoolCar Request**.
