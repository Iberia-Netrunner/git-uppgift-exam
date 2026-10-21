## Fråga 1: Versionshanterin vs vanliga filer

**G:** 
Versionshantering innebär att du sparar olika delar av din kod längs en tidlinje, detta så att du kan gå tillbaka, se och jämföra ändringar och använda som ett fail-safe system ifall något i din nuvarande kod gått sönder. Det är ett system som gör att du kan hålla koll på alla ändringar i filerna som görs under projektets gång/cykel.

Spara lokalt: i editorn så skriver du endast över filen när du sparar den på din hårddisk, den gamla versionen försvinner. Detta gör att du inte har historiken, I vissa fall kan du gå tillbaka med ctrl + z, men när man väl stänger filen och öppnar igen kan man inte längre gå tillbaka då korttidsminnet har rensats.

**VG:**
En commit innebär att git skapar en ögonblicksbild av koden/projektet i exakt det tillstånd och den tidpunkt som är, tillsammans med ett meddelande beroende på vad man har gjort för förändringar och vad man väljer att skriva som sitt commit-meddelande. Git spårar exakt vilka rader som man har ändrat, lagt till eller tagit bort. Detta gör att man alltid kan jämföra sina förändringar med git diff, gå tillbaka och återskapa sina tidigare versioner utav koden.

Man kan bevisa commits genom att använda sig av kommandon git log –oneline och git show …
Med git log –oneline får du fram en överblick på alla commits som gjorts med sin unika hashkod. 
Hashkoden kan du sedan använda med git show för att kunna jämföra och se förändringar mellan två olika commits eller se vad som har förändrats vid en viss commit.

Att man kan klicka på sina första commit på Github och fortfarande se alla tre todo kvar visar att Git lagrar frysta ögonblicksbilder över tid än att bara skriva över den senaste versionen vilket sker lokalt på datorn när man sparar. Filen på datorn visar projektets nuvarandra tillstånd alltså det senaste versionen medan den första commiten på Github visar hur det såg ut exakt vid den tidpunkten i historiken.
Det innebär att git behåller hela projektets tidslinje och att tidigare commits aldrig förändras.

Man kan se det som en checkpoint eller när man sparar sin framgång i ett spel för att senare kunna gå tillbaka.

## Fråga 2: beskriv kommandon

**G**
git status använder man för att kolla läget på projektet. Det visar om det har skett någon förändring, vilka filer som är ändrade, samt om de ligger i staging area (är tillagda) eller inte. Jag brukar köra det ofta för att ha koll på vilka filer jag har ändrat och vad som är redo att committas.

git add väljer ut och plockar fram ändringarna du har gjort till staging area, det är här du bestämmer exakt vad som ska med i nästa sparning. Du kan lägga till allt i projektet med git add . men det rekommenderas inte alltid då man lätt får med filer man inte tänkt sig. Det är bättre att ha som vana att välja exakt vilken fil som ska stageas, som till exempel git add index.html.

git commit tar sedan allt som man har lagt i staging area och sparar det som en permanent ögonblicksbild i historiken, exakt i det tillstånd som filerna befinner sig i just då.

**VG** 
Arbetsyta (Working Tree): Är de förändringar som finns sparade på hårddisken, detta är lokalt på din dator.
Det är här man arbetar och gör ändringar i filerna. 

Staging area (git add):
Det är med git add som man lägger fram förändringen/filen som ska med i staging area och förbereds, man lägger fram sina förändringar i “kuvertet” och förbereder inför nästa ögonblicksbild. 

Commit (git commit -m):
Här sker försegligen utav kuvertet med en beskrivning/meddelande och sparas sedan som en ögonblicksbild/snapshot. Ögonblicksbilden ligger sedan I gits historiken.

Om man försöker att göra git commit på en fil som man enbart har sparat lokalt så kommer det inte gå, och man kommer att få ett felmeddelande “no changes added to commit”. Detta innebär att git inte kan commita för att förändringen inte har lagts fram i staging area, utan den står tom. Det är precis som att man skulle försegla och beskriva en kuver som är tom.

## Fråga 3: Lådan hemma vs Montern på Github 

**G**
Mappen på din dator (det lokala git repot) är din egen arbetsmiljö/arbetsyta där man skapar och sparar filerna och historik lokalt på datorn (lådan). Repot på Github är en kopia av den lokala repot i molnet, det gör att andra också kan ta del av projeket samt skapa branches, ute på arbetsmarknaden pushar man aldrig mot main utan man skapar branches som sedan blir merged med main branchen.
Git push gör att du skickar förändringarna du har gjort på git lokalt till Github Cloud.

**VG**
Konceptet handlar om relationen mellan din lokala “låda” vilket är historiken du bygger lokalt med förseglade kuver. Glassmontern I trapphuset är din Github repo, en kopia i molnet.

Lådan och glasmonterna är separata och uppdatera inte varandra automatiskt. Montern fylls först efter att man har skickat dit kopian.
Git svarar med Everything-up-to-date för att den vet inte om att man har gjort några förädringar då man inte har lagt fram det för staging och inte har skapat en ögonblicksbild. 

Kommandot git push utgår från färdiga commits (förseglade kuvert) I din lokala låda. 
Så finns det inte nya commits skapade i lådan så ser Git endast den senaste commit i din låda och ser att den är densamma som den som redan finns I glasmonterna, eftersom det inte finns några nya kuvert att jämföra med så skriver den ut “Everything up-to-date”.
