# ES6 Grundövningar

## Översikt
Sex grundläggande övningar för att träna ES6-syntax och JavaScript-koncept. Varje övning bygger på den föregående och har tydliga in- och utvärden.

## Hur du arbetar med övningarna

1. **Skapa JavaScript-filer:** Skapa en ny `.js`-fil för varje övning (t.ex. `exercise1.js`, `exercise2.js`).

2. **Skriv din kod:** Implementera lösningen i JavaScript-filen.

3. **Koppla till HTML:** Lägg till `<script src="exercise1.js"></script>` längst ner i `index.html`.

4. **Testa:** Öppna `index.html` i webbläsaren och använd F12 > Console för att se resultatet.

5. **Använd console.log():** Logga värden och resultat för att se att din kod fungerar.

## Öppna i webbläsaren från VS Code

1. Installera tillägget "Live Server" av Ritwick Dey i VS Code (Extensions → sök "Live Server")
2. Öppna `index.html` i editorn
3. Högerklicka i editorn → "Open with Live Server"
4. Webbläsaren öppnas automatiskt med lokal server (t.ex. http://127.0.0.1:5500)
5. Sidan uppdateras automatiskt när du sparar ändringar i dina `.js`-filer

## Exempel på arbetssätt

**För övning 1:**
```javascript
// exercise1.js
function addNumbers(a, b) {
    return a + b;
}

const result = addNumbers(3, 7);
console.log("Summan är:", result);
```

**I index.html:**
```html
<script src="exercise1.js"></script>
```

**I Console (F12):**
```
Summan är: 10
```

## Övningarna

Se `index.html` för alla sex övningar med instruktioner, in-värden, ut-värden och tips.

## Tips
- Testa och experimentera!
- Ändra värden och se vad som händer
- Varje övning bygger på den föregående
- Använd console.log() för att debugga och se resultat
