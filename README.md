
# Typescript #3: Generics, Utility Types, Validering med Zod

👋 Se föreläsningen i tisdags och onsdags ✅ 

**Syftet med denna workshop:** Vi går vidare från grunderna i Typescript och utforskar:

* Generics
* Utility Types 
* Index signatures
* Utility Types
* Narrowing och typeguards
* Validering med Zod


### Setup med vanilla TS-projekt

Vi fortsätter jobba i vanilla TS med Node. Förutom övning 2 där vi kör vår tsc-kompilearade js i browsern.

```
npm init
npm install typescript ts-node --save-dev
npx tsc --init
npx tsc // bygg om .ts => .js
ts-node index.ts // kör ts-filen i node
```


### Bra att veta

Alla uppgifter + extrauppgifter är framåtsyftande mot provet i Typescript i v 44.

Förutom övningen finns även extrauppgifter på externa sidor. Gör dessa för att repetera, få djupare förståelse. För att relatera tll kommande prov anger jag G-nivå eller VG-nivå.

På provet kommer man få använda sig av Typescriptdokumentationen, så börja bli vän med den redan nu :-)

[https://www.typescriptlang.org/docs/](https://www.typescriptlang.org/docs/)

# 👩🏽‍💻 Övning 1: Generiska typer

(Om du inte gjorde Generics från förra workshopen)

**Din uppgift:** 

Börja med att svara på frågan: 

**Vad är generics? Vad är fördelen med att använda en generiska typer i en funktion/interface/type/class?**

Läs i Typescriptdokumentation och leta även i andra källor.
[https://www.typescriptlang.org/docs/handbook/2/generics.html#handbook-content
](https://www.typescriptlang.org/docs/handbook/2/generics.html#handbook-content)

**Uppgifter:**

1. Skapa en funktion som använder generiska typer. Funktionen ska ta in en array av vilken typ som helst och returna arrayen i omvänd ordning.
2. Skapa en funktion som tar in två parametrar "key" och "value" som vardera är en generisk typ (inte samma!) och returnera objektet av properties "key" och "value"

 ```
 makePair("name", "sandra")
 makePair("age", 28)
 
 //Returns
 {
  "key": "name",
  "value": "sandra"
} 
{
  "key": "age",
  "value": 28
} 
```
3. Skapa ett interface "Box" med en generisk typ T. Interfaces ska ha ett property "item" av typen T. Skapa en funktion "unbox" som tar in interfacet Box och returnerar "item".

	```
	const stringBox: Box<string> = { item: "Hello, TypeScript!" };
	console.log(unbox(stringBox)); // "Hello, TypeScript!"
	
	```
4. Hur kan man begränsa så att exempelvis en funktion med generiska typer inte tillåter alla typer utan endast exempelvis string eller number? 

# 👩🏽‍💻 Övning 2: Index signatures

Index signtures är typescript:s sätt att skapa dynamiska nycklar. Se [https://www.typescriptlang.org/docs/handbook/2/objects.html#index-signatures](https://www.typescriptlang.org/docs/handbook/2/objects.html#index-signatures)

**Din uppgift:** Skapa ett interface med index signatures där värdet på en key är av generisk typ.

```
// Här skapar du interfacet


function createDataStore<T>() {
    const store: any = {}; // Byt ut any till ovan definerade interface

    function addItem(key: string, item: T): void {
        store[key] = item;
    }

    function getItem(key: string): T | undefined {
        return store[key]; 
    }

    return { addItem, getItem}; // Return the functions
}

const stringStore = createDataStore<string>();
stringStore.addItem('greeting', 'Hello, world!');
console.log(stringStore.getItem('greeting')); 

const numberStore = createDataStore<number>();
numberStore.addItem('age', 30);
console.log(numberStore.getItem('age'));

```


# 👩🏽‍💻 Övning 3: Utility Types


G-nivå 

**Din uppgift:** Skapa en ny typ av en redan befintlig typ m.h.a Utility types. Se
[https://www.typescriptlang.org/docs/handbook/utility-types.html
](https://www.typescriptlang.org/docs/handbook/utility-types.html)

Låt grundtypen bestå av några valfria properties och applicera en utilty type för att göra en ny typ där:

* Alla properties optional
* Alla properties required 
* Innehåller en utvald property
* Innehåller alla properties förutom en bortvald property

# 👩🏽‍💻 Övning 4: Narrowing och Typequards

G-nivå

**Din uppgift:** Svara på frågorma:

1. Vad innebär narrowing inom typescript? 
1. Ange olika tekniker för att åstadkomma narrowing i typescript, d.v.s olika sätt att använda typeguards.

[https://www.typescriptlang.org/docs/handbook/2/narrowing.html](https://www.typescriptlang.org/docs/handbook/2/narrowing.html)


# 👩🏽‍💻 Övning 5: Validering med Zod

G till VG-nivå (hur pass noga man validerar)

Zod är ett bibliotek för validering som är anpassat till Typescript. Du ska validera inkommande data från API:et [https://swapi.dev/](https://swapi.dev/) för karaktären Luke Skywalker. Om du hellre vill validera för annan karaktär går det också bra  🌌!

Innan du börjar, besvara frågan: **Vad är vikten av att validera?**

**Obs!** Du väljer själv på vilken nivå du validerar, men minst "typen" för datat. Tänk också på att date:s kan vara lite krångliga. Här väljer du själv om de validerar som sträng eller exakt datum format (som kan behövas extra bibliotek för)



# 🏃🏽‍♂️ Extrauppgifter

Välj och vraka efter eget tycke, träna inför provet :-)


1. [https://www.totaltypescript.com/tutorials/beginners-typescript
  ](https://www.totaltypescript.com/tutorials/beginners-typescript) Uppgift 11,12,13, 15, 16 G-nivå
2. [https://typescript-exercises.github.io/](https://typescript-exercises.github.io/) 
3. [https://github.com/LearningTypeScript/projects](https://github.com/LearningTypeScript/projects) - Följer [denna O'really bok](https://www.oreilly.com/library/view/learning-typescript/9781098110321/?_gl=1*pv2bzi*_ga*MTgzNjg0Njk0Ny4xNjk1MDMwMDU5*_ga_092EL089CH*MTY5NTIxMjAxOS4yLjEuMTY5NTIxMjIzNS40MS4wLjA.), men du måste inte ha boken. Utgå från mapparna "Generics". De delar in övningarna Appertizer (= G-nivå), Entrees (VG-nivå), Desserts (VG-nivå)
4. [Matt Pocock Generics Workshop ](https://github.com/total-typescript/typescript-generics-workshop)
5. [Matt Pocock Zod Tutorial] (https://www.totaltypescript.com/tutorials/zod)




# ✅ Redovisning:
* Du redovisar minst uppgiften för övningen. 
* ***Om du inte kan delta på workshopen, redovisar du ovanstående nästkommande workshop***







