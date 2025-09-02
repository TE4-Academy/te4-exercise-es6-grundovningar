# 🎯 Personregister - Progressiv vägledning

Detta dokument guidar dig steg för steg genom alla uppgifter i index3.html. Läs tips för din aktuella uppgift och använd länkar för djupare förståelse.

---

## 🚀 SNABBSTART

**Första intryck är viktigt!** Börja med att avkommentera koden i `visaAllaPersoner()`:

```javascript
function visaAllaPersoner() {
    // visaPersoner(personer, "Alla personer");  // Ta bort // framför denna rad
}
```

Nu kan du klicka på "Visa alla personer" och se att allt fungerar! 🎉

---

## 📚 GRUNDLÄGGANDE KONCEPT

Innan du börjar koda, förstå dessa grundstenar:

### Arrays och objekt
Vår `personer`-array innehåller objekt som ser ut så här:
```javascript
{ fornamn: "Anna", efternamn: "Andersson", stad: "Stockholm", vip: true }
```

### ES6 Array-metoder
Du kommer använda dessa kraftfulla verktyg:
- `map()` - transformera varje element
- `filter()` - välja ut element som uppfyller villkor  
- `find()` - hitta första elementet som matchar
- `reduce()` - bygga upp ett nytt värde från arrayen

📖 **Läs mer:** [Array methods på MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)

---

## 🎯 STEG 1: HJÄLPFUNKTIONER (DATA-PROCESSING)

### 1.1 skapaFullaNamn() ⭐
**Vad ska funktionen göra?**  
Ta en lista med personer och returnera en ny lista med fullständiga namn.

**Tankesätt:**
- Från: `[{fornamn: "Anna", efternamn: "Andersson"}, ...]`
- Till: `["Anna Andersson", ...]`
- Detta är en **transformation** - perfekt för `map()`!

**Progressiva tips:**
1. **Börja enkelt:** Skriv först en funktion som bara returnerar ett hårdkodat namn
2. **Lägg till map():** Använd `personLista.map()` för att gå igenom alla
3. **Bygg strängar:** Inne i map() behöver du `person.fornamn + " " + person.efternamn`
4. **Template literals:** Ännu snyggare med backticks: `` `${person.fornamn} ${person.efternamn}` ``

**Exempel-struktur:**
```javascript
function skapaFullaNamn(personLista) {
    return personLista.map(person => {
        // Bygg ihop förnamn och efternamn här
    });
}
```

📖 **Läs mer:** [Array.map() på MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)

**Vanligt fel:** Glöm inte `return`-satsen!

---

### 1.2 hittaSvensson() ⭐
**Vad ska funktionen göra?**  
Hitta den första personen med efternamnet "Svensson".

**Tankesätt:**
- Du letar efter **en specifik** person - perfekt för `find()`!
- `find()` returnerar första objektet som matchar villkoret
- Om ingen hittas, returneras `undefined`

**Progressiva tips:**
1. **Förstå find():** Den tar en funktion som testar varje element
2. **Skriv villkoret:** Du vill att `person.efternamn === "Svensson"`
3. **Arrow function:** `personer.find(person => person.efternamn === "Svensson")`
4. **Testa:** Använd `console.log()` för att se vad funktionen returnerar

**Exempel-struktur:**
```javascript
function hittaSvensson() {
    return personer.find(person => {
        // Skriv ditt villkor här
    });
}
```

📖 **Läs mer:** [Array.find() på MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/find)

**Vanligt fel:** Använd `===` för jämförelse, inte `=`!

---

### 1.3 filtreraEfterStad() ⭐⭐
**Vad ska funktionen göra?**  
Returnera alla personer från en specifik stad (eller alla om "alla" väljs).

**Tankesätt:**
- Du filtrerar baserat på ett villkor - perfekt för `filter()`!
- Specialfall: "alla" betyder ingen filtrering
- `filter()` returnerar en ny array med matchande element

**Progressiva tips:**
1. **Hantera specialfallet:** Om `stad === "alla"`, returnera hela `personer`-arrayen
2. **Använd filter():** `personer.filter(person => person.stad === stad)`
3. **Testa med olika städer:** Stockholm, Göteborg, Malmö
4. **Debug:** Använd `console.log(stad)` för att se vad som skickas in

**Exempel-struktur:**
```javascript
function filtreraEfterStad(stad) {
    if (stad === "alla") {
        return personer;
    }
    
    return personer.filter(person => {
        // Skriv ditt villkor här
    });
}
```

📖 **Läs mer:** [Array.filter() på MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)

---

### 1.4 filtreraVipStatus() ⭐⭐
**Vad ska funktionen göra?**  
Filtrera personer baserat på VIP-status: "alla", "vip", eller "icke-vip".

**Tankesätt:**
- Tre olika fall att hantera
- VIP-status är en boolean: `true` eller `false`
- Använd `filter()` med olika villkor

**Progressiva tips:**
1. **Tre if-satser:** Hantera varje fall separat
2. **Boolean-jämförelse:** `person.vip === true` för VIP
3. **Motsatsen:** `person.vip === false` för icke-VIP
4. **Förenkling:** `person.vip` är samma som `person.vip === true`

**Exempel-struktur:**
```javascript
function filtreraVipStatus(vipStatus) {
    if (vipStatus === "alla") {
        return personer;
    } else if (vipStatus === "vip") {
        return personer.filter(person => person.vip === true);
    } else if (vipStatus === "icke-vip") {
        return personer.filter(person => person.vip === false);
    }
}
```

**Vanligt fel:** Glöm inte `return` i alla fall!

---

### 1.5 räknaPersonerPerStad() ⭐⭐⭐
**Vad ska funktionen göra?**  
Räkna hur många personer som bor i varje stad och returnera ett objekt.

**Tankesätt:**
- Från: `[{stad: "Stockholm"}, {stad: "Stockholm"}, {stad: "Göteborg"}]`
- Till: `{Stockholm: 2, Göteborg: 1}`
- Detta är **aggregering** - perfekt för `reduce()`!

**Progressiva tips:**
1. **Förstå reduce():** Bygger upp ett resultat genom att gå igenom alla element
2. **Startvärde:** Börja med ett tomt objekt `{}`
3. **För varje person:** Öka räknaren för personens stad
4. **Skapa nyckel:** Om staden inte finns, sätt den till 0 först

**Exempel med for...of (enklare att förstå):**
```javascript
function räknaPersonerPerStad() {
    const stadRäknare = {};
    
    for (const person of personer) {
        const stad = person.stad;
        if (stadRäknare[stad]) {
            stadRäknare[stad]++;
        } else {
            stadRäknare[stad] = 1;
        }
    }
    
    return stadRäknare;
}
```

**Exempel med reduce() (mer avancerat):**
```javascript
function räknaPersonerPerStad() {
    return personer.reduce((stadRäknare, person) => {
        const stad = person.stad;
        stadRäknare[stad] = (stadRäknare[stad] || 0) + 1;
        return stadRäknare;
    }, {});
}
```

📖 **Läs mer:** [Array.reduce() på MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce)

---

## 🎯 STEG 2: UI-FUNKTIONER (ENKLA KNAPP-FUNKTIONER)

### 2.1 visaAllaPersoner() ⭐
**Vad ska funktionen göra?**  
Visa alla personer i listan på webbsidan.

**Tankesätt:**
- Du har redan en färdig funktion `visaPersoner()` som gör det tunga jobbet
- Du behöver bara anropa den med rätt parametrar
- Första parametern: vilken lista? (hela `personer`-arrayen)
- Andra parametern: vilken rubrik? (en beskrivande text)

**Progressiva tips:**
1. **Enklast:** Avkommentera koden - den är klar att använda!
2. **Förstå:** Vad gör `visaPersoner()`? Titta på dess kod för att förstå
3. **Experimentera:** Prova olika rubriker och se vad som händer

**Vanligt fel:** Glöm inte kommatecknet mellan parametrarna!

---

### 2.2 visaFullaNamn() ⭐
**Vad ska funktionen göra?**  
Anropa `skapaFullaNamn()` och visa resultatet på webbsidan som en lista.

**Tankesätt:**
- Kombinera två steg: 1) Hämta namn, 2) Visa dem
- Namnen kommer som en array av strängar
- Du behöver visa dem som HTML-lista

**Progressiva tips:**
1. **Första steget:** Anropa `skapaFullaNamn(personer)` och spara i en variabel
2. **Skapa HTML:** Bygg upp en `<ul>` med `<li>` för varje namn
3. **Sätt innehåll:** Använd `document.getElementById('resultat').innerHTML = html`
4. **Snyggare:** Använd CSS-klassen `name-list` för bättre utseende

**Exempel-struktur:**
```javascript
function visaFullaNamn() {
    const fullaNamn = skapaFullaNamn(personer);
    let html = '<h3>Fullständiga namn</h3><ul class="name-list">';
    
    fullaNamn.forEach(namn => {
        html += `<li>${namn}</li>`;
    });
    
    html += '</ul>';
    document.getElementById('resultat').innerHTML = html;
}
```

**Vanligt fel:** Glöm inte att stänga `</ul>`-taggen!

---

### 2.3 sökEfternamn() ⭐
**Vad ska funktionen göra?**  
Anropa `hittaSvensson()` och visa den hittade personen.

**Tankesätt:**
- Du får tillbaka EN person (eller `undefined`)
- Använd `visaPersoner()` men med en array som bara innehåller denna person
- Hantera fallet när ingen hittas

**Progressiva tips:**
1. **Anropa funktionen:** `const svensson = hittaSvensson()`
2. **Kontrollera resultat:** Använd `if (svensson)` för att se om någon hittades
3. **Skapa array:** `visaPersoner([svensson], "Sökresultat: Svensson")`
4. **Hantera "ingen träff":** Visa meddelande om `svensson` är `undefined`

**Exempel-struktur:**
```javascript
function sökEfternamn() {
    const svensson = hittaSvensson();
    
    if (svensson) {
        visaPersoner([svensson], "Sökresultat: Svensson");
    } else {
        // Visa meddelande att ingen hittades
    }
}
```

**Vanligt fel:** Glöm inte att wrappa personen i `[` ]` för att göra det till en array!

---

## 🎯 STEG 3: MEDEL-FUNKTIONER (KOMBINERA HJÄLPFUNKTIONER)

### 3.1 visaStockholmare() ⭐⭐
**Vad ska funktionen göra?**  
Visa alla personer från Stockholm.

**Tankesätt:**
- Kombinera filtrering och visning
- Använd din redan färdiga `filtreraEfterStad()` funktion
- Hårdkoda staden till "Stockholm"

**Progressiva tips:**
1. **Återanvänd kod:** `const stockholmare = filtreraEfterStad("Stockholm")`
2. **Visa resultatet:** `visaPersoner(stockholmare, "Personer från Stockholm")`
3. **En rad:** Kan göras på en rad om du vill!

**Exempel-struktur:**
```javascript
function visaStockholmare() {
    const stockholmare = filtreraEfterStad("Stockholm");
    visaPersoner(stockholmare, "Personer från Stockholm");
}
```

---

### 3.2 visaVipPersoner() ⭐⭐
**Vad ska funktionen göra?**  
Visa alla VIP-personer.

**Tankesätt:**
- Samma mönster som `visaStockholmare()`
- Använd `filtreraVipStatus("vip")`

**Tips:**
```javascript
function visaVipPersoner() {
    const vipPersoner = filtreraVipStatus("vip");
    visaPersoner(vipPersoner, "VIP-personer");
}
```

---

### 3.3 visaStatistik() ⭐⭐⭐
**Vad ska funktionen göra?**  
Visa statistik om städer och VIP-medlemmar i snygga kort.

**Tankesätt:**
- Kombinera flera beräkningar
- Bygg HTML med statistik-kort
- Räkna både städer och VIP-status

**Progressiva tips:**
1. **Hämta statistik:** `const stadStats = räknaPersonerPerStad()`
2. **Räkna VIP:** `const antalVip = personer.filter(p => p.vip).length`
3. **Bygg HTML:** Skapa `stat-card` divs för varje statistik
4. **Loopa genom städer:** `Object.entries(stadStats)` för att få nyckel-värde par

**Exempel-struktur:**
```javascript
function visaStatistik() {
    const stadStats = räknaPersonerPerStad();
    const antalVip = personer.filter(p => p.vip).length;
    const totaltAntal = personer.length;
    
    let html = '<h3>Statistik</h3><div class="stats">';
    
    // Lägg till totalt antal
    html += `
        <div class="stat-card">
            <div class="stat-number">${totaltAntal}</div>
            <div>Totalt antal personer</div>
        </div>
    `;
    
    // Lägg till VIP-statistik
    html += `
        <div class="stat-card">
            <div class="stat-number">${antalVip}</div>
            <div>VIP-medlemmar</div>
        </div>
    `;
    
    // Loopa genom städer
    Object.entries(stadStats).forEach(([stad, antal]) => {
        html += `
            <div class="stat-card">
                <div class="stat-number">${antal}</div>
                <div>Från ${stad}</div>
            </div>
        `;
    });
    
    html += '</div>';
    document.getElementById('resultat').innerHTML = html;
}
```

📖 **Läs mer:** [Object.entries() på MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/entries)

---

## 🎯 STEG 4: AVANCERAD FILTRERING (SVÅR - DOM + LOGIK)

### 4.1 filtreraEfterValdStad() ⭐⭐⭐
**Vad ska funktionen göra?**  
Läsa värdet från dropdown-menyn och filtrera personer efter den valda staden.

**Tankesätt:**
- Nu börjar vi interagera med DOM-element
- Läsa användarens val från `<select>`-element
- Kombinera DOM-läsning med din befintliga filtreringslogik

**Progressiva tips:**
1. **Hitta elementet:** `document.getElementById('stadFilter')`
2. **Läs värdet:** `.value` på select-elementet
3. **Använd befintlig funktion:** Skicka värdet till `filtreraEfterStad()`
4. **Visa resultatet:** Använd `visaPersoner()` med en beskrivande titel

**Exempel-struktur:**
```javascript
function filtreraEfterValdStad() {
    const stadFilter = document.getElementById('stadFilter');
    const valdStad = stadFilter.value;
    
    const filtrerade = filtreraEfterStad(valdStad);
    
    const titel = valdStad === "alla" ? "Alla personer" : `Personer från ${valdStad}`;
    visaPersoner(filtrerade, titel);
}
```

📖 **Läs mer:** [getElementById på MDN](https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementById)

**Vanligt fel:** Glöm inte `.value` för att få det valda värdet!

---

### 4.2 filtreraEfterValdVip() ⭐⭐⭐
**Vad ska funktionen göra?**  
Läsa VIP-filtret från dropdown och filtrera personer.

**Tankesätt:**
- Samma mönster som `filtreraEfterValdStad()`
- Läs från `vipFilter` istället
- Använd `filtreraVipStatus()`

**Tips:**
```javascript
function filtreraEfterValdVip() {
    const vipFilter = document.getElementById('vipFilter');
    const valdVipStatus = vipFilter.value;
    
    const filtrerade = filtreraVipStatus(valdVipStatus);
    
    let titel;
    if (valdVipStatus === "alla") {
        titel = "Alla personer";
    } else if (valdVipStatus === "vip") {
        titel = "VIP-personer";
    } else {
        titel = "Icke-VIP personer";
    }
    
    visaPersoner(filtrerade, titel);
}
```

---

### 4.3 kombineraFilter() ⭐⭐⭐⭐
**Vad ska funktionen göra?**  
Kombinera både stads- och VIP-filter för att visa personer som matchar båda kriterierna.

**Tankesätt:**
- Läs båda dropdown-värden
- Applicera båda filtren efter varandra
- Detta är **komposition** - använd resultatet från ett filter som input till nästa

**Progressiva tips:**
1. **Läs båda värdena:** Från både `stadFilter` och `vipFilter`
2. **Första filtreringen:** Filtrera efter stad först
3. **Andra filtreringen:** Använd resultatet och filtrera efter VIP-status
4. **Smart titel:** Bygg upp en beskrivande titel baserat på båda filtren

**Exempel-struktur:**
```javascript
function kombineraFilter() {
    // Läs båda filter-värden
    const valdStad = document.getElementById('stadFilter').value;
    const valdVipStatus = document.getElementById('vipFilter').value;
    
    // Börja med alla personer
    let filtrerade = personer;
    
    // Applicera stadsfilter om det inte är "alla"
    if (valdStad !== "alla") {
        filtrerade = filtrerade.filter(person => person.stad === valdStad);
    }
    
    // Applicera VIP-filter om det inte är "alla"
    if (valdVipStatus === "vip") {
        filtrerade = filtrerade.filter(person => person.vip === true);
    } else if (valdVipStatus === "icke-vip") {
        filtrerade = filtrerade.filter(person => person.vip === false);
    }
    
    // Bygg beskrivande titel
    let titel = "Filtrerade personer";
    if (valdStad !== "alla" && valdVipStatus !== "alla") {
        titel = `${valdVipStatus === "vip" ? "VIP" : "Icke-VIP"}-personer från ${valdStad}`;
    } else if (valdStad !== "alla") {
        titel = `Personer från ${valdStad}`;
    } else if (valdVipStatus !== "alla") {
        titel = `${valdVipStatus === "vip" ? "VIP" : "Icke-VIP"}-personer`;
    }
    
    visaPersoner(filtrerade, titel);
}
```

**Alternativ metod (mer elegant):**
```javascript
function kombineraFilter() {
    const valdStad = document.getElementById('stadFilter').value;
    const valdVipStatus = document.getElementById('vipFilter').value;
    
    // Använd befintliga funktioner
    let stadFiltrerade = filtreraEfterStad(valdStad);
    let slutresultat = filtreraVipStatus(valdVipStatus);
    
    // Hitta intersection (gemensamma element)
    if (valdStad !== "alla") {
        slutresultat = slutresultat.filter(person => 
            stadFiltrerade.includes(person)
        );
    }
    
    visaPersoner(slutresultat, "Kombinerat filter");
}
```

---

## 🎨 BONUS: CSS-UPPGRADERING

När alla funktioner fungerar, gör denna magiska förändring:

**I `<head>`-sektionen, ändra:**
```html
<link rel="stylesheet" href="styles-basic.css">
```

**Till:**
```html
<link rel="stylesheet" href="styles-advanced.css">
```

Klicka F5 och se den spektakulära transformationen! 🚀✨

---

## 🐛 FELSÖKNING

### Vanliga fel och lösningar:

**"Funktionen är inte definierad"**
- Kontrollera stavning av funktionsnamnet
- Se till att funktionen är definierad innan den anropas

**"Cannot read property of undefined"**
- Kontrollera att du använder rätt objektegenskap (fornamn, efternamn, stad, vip)
- Använd `console.log()` för att inspektera objekt

**"Filter/map/find is not a function"**
- Kontrollera att du anropar metoden på en array
- Använd `console.log(typeof variabel)` för att kontrollera typ

**Inget händer när du klickar**
- Kontrollera stavning av funktionsnamn i onclick
- Öppna Developer Tools (F12) och kolla Console för fel

### Debug-tips:
1. **Använd console.log()** överallt för att se vad som händer
2. **Öppna Developer Tools** (F12) och kolla Console-fliken
3. **Testa bit för bit** - kommentera ut kod och testa mindre delar
4. **Läs felmeddelanden** noggrant - de berättar ofta exakt vad som är fel

---

## 📚 EXTRA RESURSER

### MDN Documentation (Din bästa vän!)
- [JavaScript Arrays](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)
- [DOM Manipulation](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model)
- [Template Literals](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals)
- [Arrow Functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)

### Progressiv fördjupning:
1. **Börja med** grundläggande array-metoder
2. **Förstå** DOM-manipulation
3. **Experimentera** med kombinationer
4. **Optimera** din kod när allt fungerar

---

## 🎯 SLUTMÅL

När du är klar ska du ha:
- ✅ Förstått ES6 array-metoder (map, filter, find, reduce)
- ✅ Lärt dig DOM-manipulation med JavaScript
- ✅ Byggt interaktiva UI funktioner

**Lycka till! Du klarar det här! 🚀**

---

*Kom ihåg: Programmering handlar om att lösa problem steg för steg. Ta det lugnt, läs felmeddelanden noggrant, och använd console.log() som din bästa vän!*
