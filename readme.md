Praxisbericht
============

Einleitung
----------
In meiner Praxisphase bei der getpacked GmbH habe ich in den letzten 3 Monaten viel Erfahrung im Bereich der Softwareentwicklung sammeln. Ich habe die getpacked GmbH für mein Praktikum gewählt, da ich vorher hauptsächlich mit Systemprogrammiersprachen gearbeitet habe und nun auch einmal Erfahrung mit den Technologien moderner Webentwicklung sammeln wollte. Meine Aufgabe während der Praxisphase waren unter anderem die Einführung einer Continuous Integration/ Continuous Delivery Infrastruktur und das Erarbeiten und Umsetzen von Maßnahmen zur Verbesserung der Qualität des Quellcodes. Ausserdem konnte ich während meines Praktikums viel über das Arbeiten in einem agilen Team lernen.

Die Suche nach einem Praktikumsplatz habe ich lange herausgezögert, dann aber als ich mal angefangen hatte zu suchen über LinkedIn schnell einen Praktikumsplatz gefunden. Als hilfreiche Strategie hat sich herausgestellt, an Firmen mit interessanten offenen Stellen Bewerbungen zu schicken und die Firmen dann davon zu überzeugen, dass sie eigentlih keinen Angestellten, sondern nur einen Praktikanten suchen. Ausserdem ermöglicht LinkedIn das Bewerben nur mit Lebenslauf, was sehr angenehm ist, da für mich das Verfassen eines guten Anschreibens der unangenehmste Teil des Bewerbungsprozesses war.

Ich habe mir von dem Praktikum hauptsächlich erhofft, Einblick darüber, wie Webentwicklung mit einem modernen Technologiestack abläuft. Vorher habe ich hauptsächlich in modernem C++ und Rust Anwendungen entwickelt, bei beiden hatte ich aber relativ häufig das Gefühl das manche Dinge deutlich aufwendiger waren, als sie sein müssten. Mein Ziel war es ein Umfeld kennenzulernen, in dem die langfristig am wenigsten Komplexität schaffende Lösung, die ein Problem angemessen löst, als die Beste wahrgenommen wird. Da Webentwicklung den Ruf hat einsteigerfreundlich zu sein, und für viele Probleme schon eine vorgefertigte Lösung zu haben, schien es mir logisch in diesem Bereich nach eine Unternehmen zu suchen, dass mir so ein Umfeld bieten kann.

Ich habe mich am Ende für getpacked entschieden, weil ich bei ihnen den Eindruck hatte, da das reduzieren von Komplexität einen hohen Stellenwert hatten. Überzeugt haben mich vor allem drei Grundsatzentscheidungen die das gut bezeugen. Zum einen, dass das Unternehmen keine eigenen Server anmieten oder betreiben wird, sondern komplett auf serverless SaaS Technologien setzt. Zum anderen, dass keine Smartphone App, sondern nur eine mobiloptimierte Webanwendung entwickelt wird. Ausserdem wird das Projekt Server- und Clientseitig in JavaScript im selben Stil geschrieben. 

Meine Projekte während der Praxisphase waren hauptächlich im Softwarengineering Bereich angesiedelt.

Faktenreiche Kurzcharakteristik des Praktikums und der Institution
------------------------------------------------------------------
### Über getpacked
getpacked ist ein Startup das eine Software as a service Lösung für online Bestellungen anbietet. Der Fokus liegt dabei mehr auf Vorbestellungen zur Abholung, Bestellungen mit Lieferung sind allerdings auch möglich. Die Zielgruppe sind hauptsächlich Hofläden, aber auch Gastronomie, Bäckereien und Metzgereien. Vor allem in den Hofläden, Bäckereien und Metzgereien ist es bisher unüblich gewesen, online Vorbestellungen anzubieten. Gerade bei diesen Läden ist es aber ein klarer Vorteil Vorbestellungen anzubieten, da es hier Stoßzeiten gibt, zu denen deutlich mehr Kunden kommen, als am Rest des Tages. Wenn ein Teil der Kunden allerdings Vorbestellungen aufgibt, können diese im Vorraus gepackt und bezahlt werden und die Kunden müssen ihre Bestellung nur noch abholen.

Im Frühjahr 2021 wurde die getpacked GmbH offiziell gegründet, vorher war getpacked ein Teil der 360VIER GmbH. Aktuell hat das Unternehmen 8 Mitarbeiter, von denen 3 in der Entwicklung arbeiten. Die Firma hat rund 100 Kunden die mit getpacked erfolgreich ihre Produkte anbieten. 

### Aufgaben im Praktikum
Meine Aufgaben in der Praxisphase waren hauptsächlich die Aufbereitung des Programmcodes und der Entwicklungsinfrastruktur.
#### Einführung einer Continuous Integration/ Continuous Delivery Infrastruktur
Mein erstes Projekt bei getpacked war es eine CI/CD pipeline aufzusetzen und einzuführen. Wir haben uns dabei für GitLab CI entschieden, da wir GitLab sowieso schon als Softwareentwicklungsplattform eingesetzt haben und wir unseren Technologiestack nicht komplizierter machen wollten, als nötig. Da ich vorher schon relativ viel Erfahrung mit verschiedenen CI Programmen gesammelt hatte, ging das aufsetzen von GitLab CI relativ schnell. Was länger gedauert hatte war, die Geschwindigkeit der Builds zu erhöhen. Da unser Projekt circa 500MB an Abhänigkeiten hat, war es keine angebrachte Lösung diese bei jedem Build erneut herunterzuladen. Die in GitLab CI integrierten Funktionen zum speichern von Artefakten waren bei der Menge auch zu langsam um sinnvoll eingesetzt werden zu können. Die Lösung für das Probblem war es dann bei jeder Änderung der Dependencies einen neuen Container mit allen Dependencies zu erstellen und den für diesen und alle zunkünftigen Builds zu benutzen.
Dadurch konnten wir die Deploymentfrequenz von ~3mal pro Woche auf ~4mal pro Tag erhöhen.
#### Sicherstellung einer hohen Codequalitaet
Eine Aufgabe die durchgehend an der ich durchgehend beschaeftigt war, war die Verbesserung der Codequalitaet. Die Entwicklung bei getpacked wurde oft durch Bugs ausgebremst, die durch klareren Code vermeidbar gewesen waeren. Oft war es allein durch die Betrachtung ihrer Schnittstelle unklar, wie Komponenten verwendet werden, damit sie das tun was man erwartet. Der Code in den Komponenten war allerdings auch oft zu komplex, um schnell zu verstehen, wie sie verwendet werden. Ausserdem war die Formatierung des Quelltexts inkonsistent, und der Zustand der Anwendung war nicht immer klar. Einige Massnahmen zur Sicherstellung einer der Codequalitaet wurden mir anfangs aufgetragen, andere habe ich selbst erarbeitet.
##### Erarbeiten von Massnahmen zur Sicherstellung der Codequalitaet
Hier eine ungeordnete Liste an allen sachen, die ich gemacht habe
Die die eigentliche Logik nicht beeinflussen
- Typen & Typescript
- linter regeln definieren, als fehler
- formatierung automatisieren
- imports vereinheitlichen
- Kein globales css
- Naming conventions fuer dinge
- precommit hooks & checks in ci
- Updates von Komponenten vermeiden
- branchless programming for readability
- Zum nachdenken ueber code anregen
- weniger code ist besser
Die die Logik beinflussen
- Zustand vereinheitlichen. focus on pure components
- 

- Code aus Anfangszeiten von getpacked
Da der Code aus den ersten Monaten von getpacked 
#### Erarbeiten von Schritten zur Verbesserung 
- Kein globales Styling
- Nur striktes typescript ohne any
- Einheitliche code formatierung
- Naming conventions
#### Erarbeiten von Guidelines zur Verbesserung der Wartbarkeit
-
##### Warum brauchen wir sowas und was muss da rein.
Guide



#### Umstellen der Codebase auf striktes TypeScript
Eine meiner ersten Aufgaben war es die Codebase der Webanwendung für eine Umstellung von JavaScript auf TypeScript vorzubereiten. Das Team hatte vorher schon angefangen TypeScript im Serverseitigem Code zu verwenden. Dort wurden aber die meisten Funktionen zur starken Überprüfung der Typen abgestellt, um die Entwicklungsgeschwindigkeit zu erhöhen, wodurch allerdings auch keine der Vorteile von Typescript genutzt wurden.
##### Was ist TypeScript und wie wollen wir es nutzen
Die Grundidee hinter TypeScript ist, das es normales Javascript mit zusaetzlichen Typinformationen ist, die beim kompiliern erst zur Ueberpruefung der Korrektheit benutzt und dann komplett entfernt werden. Uebrig bleibt normales JavaScript. Als Folge dessen hat TypeScript die Eigenschaft, dass es beim kompilieren komplett statisch getyped ist, bei der Ausfuehrung aber dynamisch. Man kann deshalb in Typescript den Typ einer Variable auch als `any` angeben und damit komplett auf Ueberpruefung der Korrektheit in der Verwendung dieser Variable verzichten. Das fuehrt allerdings zu weniger Klarheit darueber, welche Werte Variablen annehmen koennen. Damit gibt TypeScript die Entscheidung, wie stark Typen ueberprueft werden sollen an die Entwickler.

Die erste Teilaufgabe der Umstellen der Codebase auf TypeScript war es also das zu entscheiden. Dazu habe ich mit allen Teammitgliedern gesprochen um zu verstehen, wie sie dazu stehen. Die Grundhaltung war etwas Angst, dass durch TypeScript die allgemeine Produktivitaet sinkt, da man sich mehr Gedanken darueber machen muss, wie die Schnittstellen von Komponenten aussehen und wie man diese in TypeScript definiert. Allerdings sind genau das auch die Gruende, weshalb wir zu TypeScript wechseln wollten. Klar definierte und gut durchdachte Komponenten sind wesentlich einfacher zu verwenden und wartbarer. Deshalb haben wir uns dazu entschieden TypeScript so strikt wie moeglich einzustellen.
##### Und was hab ich dafuer gemacht
Die zwei groessten Herausforderungen bei der Umstellung auf Typescript waren zum einen herauszufinden was die Typen in existierendem Code sind und sicherzustellen das auch aller zukuenftige Quelltext mit sinnvollen und korrekten Typen versehen ist. 

Beim Herausfinden und Definieren von Typen in existierendem Code habe ich hauptsaechlich darauf gesetzt Annahmen ueber die Typen von Dingen aufzustellen und diese bei Unklarheit dann im Debugger zu verifizieren. Die Annahmen habe ich entweder durch Gespraeche mit den anderen Teammitgliedern oder durch den Kontext des Codes versucht aufzustellen. Meistens war es nicht noetig die Annahmen durch Tests zu ueberpruefen, da wenn alle Orte an denen ein Komponent verwendet wird mit Typen versehen sind, sich der Compiler beschwert, wenn etwas nicht passt.

Nachdem die Kernkomponenten der Codebase mit Typen versehen waren, habe ich sichergestellt, dass auch aller neuer Code in striktem TypeScript geschrieben wird und  das der Rest der Codebase im Laufe der Zeit zu TypeScript wird. Dazu habe ich unter anderem Linterregeln eingefuehrt, die weder die explizite, noch die implizite Verwendung von `any` zu erlauben. Ich mit dem Team einen kurzen Crashkurs gemacht, damit alle ein Verstaendnis dafuer haben, wie und warum wir TypeScript einsetzen. Ausserdem habe ich dafuer gesorgt das Team stetig mit Informationen zum Anteil von TypeScript und JavaScript an der Codebase zu versorgen und es zu feiern, wenn der JavaScript Anteil sinkt.


- Insert stats
- Insert reflection
  - Gluck, dass sie dazu bereit waren
  - Productivity stats waeren cooL
#### Logik für datenkonsitenz auf Serverseite migrieren
Da
#### Einarbeiten und verwenden verschiedener mir neuer Technologien

#### Umstellen auf css auf Komponentenebene
Bei normalen css Stylesheets erstellt man global gültige Klassennamen, die auf alle HTML Elemente einer bestimmten Klasse angewandt werden. In Komponentenbasieren Webanwendungen führt das oft zu Problemen, da wenn mehrere Komponenten den selben Klassennamen verwenden, sie sich dadurch auch oft unbemerkt gegenseitig beinflussen. In getpacked hatten wir zum Beispiel die Klasse `cartButton` die zum einen einen Knopf mit dem Preis des aktuellen Warenkorbs, der diesen auch öffnet gestaltet, zum anderen aber auch den Knopf um ein Produkt in den Warenkorb hinzuzufügen. Da beide Knöpfe relativ ähnlich aussahen, ist nicht aufgefallen, dass beide den die selbe CSS Klasse benutzen, bis wir die Farbe von einem anpassen wollten, was dann aber auch den anderen betroffen hat. Die Lösung war das Problem war es auf css mdoule umzustellen, dabei sind Klassennamen immer an eine Komponente gebunden. Erreicht wird das dadurch, dass die Namen der CSS Klassen im Buildprozess so modifiziert werden, dass sie einzigartig sind. So wird aus dem `cartButton` in der Basket Komponent zum Beispiel `Basket_cartButton_be8j3`.
#### Performance optimierung eine Webanwendung
Eines meiner Projekte war die Optimierung der Ladezeit der Webseite.
Da getpacked mit React gebaut ist, wurde komplett auf clientseitiges rendering gesetzt. Da die Unterscheidug zwischen verschiedenen Unterseiten (z.B. der Shop für Kunden oder das Admininterface zur verwaltung der Shops) dabei nur Clientseitig erfolgt wurden auf jedet Seite alle Skripte geladen. Ausserdem wird bei clientseitigem rendering erstmal eine leere Webseite qusfeliefert, die dann noch mit Inhalt gefüllt werden muss, was auch etwas Zeit braucht.
Wir haben verschiedene Lösungen für diese Probleme geprüft und haben uns dann für nextjs entschieden, da es diese beiden Problem relativ automatisch löst. 
Ein weiteres Performanceproblem war, dass auf der Seite oft Dinge in mehreren Stufen geladen aus der Datenbank geladen werden mussten. Zum Beispiel mussten im Frontend erst alle Produktgruppen geladen werden, und danach konnten erst die einzelnen Artikel geladen werden, da ihre IDs in den Produktgruppen gespeichert sind.

Wir konnten diese Probleme auf nicht durch vorgenerierte nextjs Seiten lösen, da alle angezeigten Daten in echtzeit mit der Datenbank synchronisiert werden, wozu aber eine Verbindung mit der Datenbank bestehen muss, die beim Übergang zwischen server und cliebt logischerweise verloren geht. Meine Lòsung für dieses Problem war es einen Cache in die Webseite einzubauen, damit, bis einen Verbindung zu Firestore aufgebaut ist und dir aktuellen Dokumente erhalten werden, schon möglicherweise veraltete gecachted Daten angezeigt werden. Bei vorgenerierten Seiten, wird der cache schon serverseitig mit den für die jeweilige Seite relevanten Daten gefüllt und dann in die vorgenerierte Seite mit eingebaut.
Dadurch sind die vorgenerierten Seiten in allen Fällen in den sich die Daten in der zwischenzeit nicht verändert haben identisch zu den clienseitig gerenderten Seiten. Damit kann die Webseite schon benutzt werden, sobald sie geladen hat.
Die Ladezeit für eine durchschnittliche Shopseite ist von ~6 Sekunden auf ~0.7 Sekunden gesunken.

#### Wechsel des JavaScript Frameworks
Wenn eine Sache stereotypisch für die Entwicklung von Webanwendungen ist, so ist das die große Zahl verschiedener JavaScript Frameworks und das stetige Verlangen auf ein modischeres umzusteigen [citation]. Zu Beginn meiner Praxisphase wurde die Anwendung mit React[citation] entwickelt. Mit React wird komplett auf clientseitiges rendering gesetzt, der Webserver gibt also jedem Besucher der Webseite die komplette javascript Anwendung, die dann im Webbrowser die Seite aufbaut. Da das aber in unserem Fall zu teilweise sehr langen Ladezeiten geführt hat, da die Bestellseite für Kunden und die Adminseite für Ladenbesitzer immer zusammen geladen werden mussten. Ausserdem wirkt sich clientseitiges rendering in der Regel auch negativ auf die Platzierung in den Ergebnissen von Suchmaschinen aus. Einen meiner Aufgaben war es nun eine Lösung für dieses Problem zu finden und umzusetzen. Ein weiteres Kriterium war es, das die  die Umstellung mit möglichst wenig Aufwand verbunden sein sollte. Die Entscheidung fiel auf Next, da es sich dabei im Grunde nur um eine Erweiterung von React mit auftrennung in verschiedene Seiten und serverseitigem rendering handelt. Es gibt bei Next für jede Unterseite der Webanwendung eine eigene React Anwendung, allerdings optimiert Next die Übergänge zwischen verschiedenen Unterseiten, sodass diese ohne eine neuladen der Seite clientseitig passieren können. Außerdem wird bei Next jede Unterseite serverseitig einmal vorgerendert und das hierbei erzeugt HTML wird mit der Seite an den Webbrowser geschickt und dient als eine Art Platzhalter, bis das clientseitige rendering abgeschlossen ist.
Die Umstellung der Anwendung auf Next hat etwa einen Monat gedauert, da mit ihr auch eine Umstellung von JavaScript auf TypeScript verbunden war. Da viele Teile das Codes angepasst werden mussten, haben wir beschlossen, dass es einfacher ist alles dabei auf Typescript umzustellen, da dadurch klar wird wie die Schnittstellen von Komponenten genau aussehen.
- schien erst einfach
- kein typescript viele Probleme
- Aufteilen der Seite in untersieten relativ unkompliziert
- Erster durchlauf muss auch serverseitig funktionieren


Anderes:
- gitlab runner local
- vercel deploys
- firestore emulator (+ hostname)
- testcafe
- keine unittests
- sentry

Reflexion
---------

### Welche Ziele habe ich mir im praktium gesetzt
Im Praktikum hatte ich mehrere Ziele und Aufgaben, vor allem wollte ich die Codebase und alles drumherum aufräumen und strukturieren, und dafür sorgen dass sie auch sauber bleibt. Ein weiteres Aufgabe war es eine Such und Übersichtsseite für alle Betriebe in getpacked zu erstellen. Ausserdem hab ich mir selbst das Ziel gesetzt, nachhaltig zu lernen, wie man möglichst effektiv moderne Webanwendungen baut und wollte dazu möglichst viele Werkzeuge ausprobieren.

### Ziele erfüllt:
#### Aufräumen und strukturieren
Ich glaube ich konnte während meiner Zeit bei getpacked die Lesbarkeit und Wartbarkeit des Programms deutlich verbessern. Was ich in der Zeit besonders geschätzt habe, war das ich relativ viel Zeit in Dinge investieren durfte, die nicht direkt Features für das Produkt bringen, sondern nur langfristig die Geschwindigkeit mit der neue Dinge entwickelt werden können erhöhen. Ausserdem fand ich es cool, dass nahezu alle meiner Bestrebungen in die Richtungen auch von meinen Kollegen angenommen wurden. (Nur das entfernen von unbenutzten imports beim speichern ist auf Wiederstand gestossen).

- Noch irgendwie erwähnen, dass das schon irgendwie eins meiner Ziele von anfang an war, ich hab afaik sogar im Vorstellungsgespräch verlangt, dass ich 1 woche im Monat komplett auf refactoring setzen darf.

#### Lernen von Webentwicklung
Webentwicklung mit React ist jetzt auch eine der Sachen die ich kann. Was mich überrascht hat, war es zu sehen, wie einfach man mit moderenen Frameworks/Tools komplexe UIs strukturien kann. Vorher hatte ich hauptsächlich mit Qt gearbeitet, dabei kam mir das erstellen von UIs immer unnötig aufwändig vor, ich hatte aber akzeptiert, dass es wahrscheinlich nicht viel einfacher geht. Ausserdem kann ich jetzt JavaScript, was auch nützlich ist.

#### Was hab ich sonst noch gelernt oder ausprobiert
- webbasierte entwicklung (gitpod)
- ai autocomplete (tabnine & copilot)
- ttd
- gitlab ci
- no code api glue tools ???  (integromat, n8n)
- überhaupt Dinge möglichst simpel modellieren

### Herausforderungen:
- anfangs Diskussionen über Geschäftsmodell, aber irgendwann ignoriert, weil nicht im Aufgabenbereich 
- Web-Entwicklung, weil noch nie vorher gemacht; aber gut geklappt, weil Programmieren an sich schon bekannt + Google -> hat gereicht; selbst aufs Projekt bezogen beigebracht -> Projekt bzw Praktikum in dem Bereich hat geholfen, dass Web-Entwicklung jetzt deutlich routinierter und kompetenter (alle Möglichkeiten bekannt) ablaufen würde; 


## Irgendwas anders machen?
Idee mit Geschwindigkeit hinschreiben und dann quasi Argumente dagegen 😊
- weniger Wert auf guten Code, mehr auf Geschwindigkeit? Weil: Firma jetzt pleite! Langfristig schneller durch guten Code jetzt irrelevant. ABER: Konnte man da nicht wissen -> nächstes Mal vielleicht anderen Fokus legen…? Entspricht aber nicht unbedingt eigenen Werten, deshalb wenn dann Fokus nur in Absprache mit Firma/Vorgesetzten verschieben (SOLL es später wiederverwendbar/anpassbar bleiben?) 
Also eigentlich nö. Weil konnte man nicht wissen. Und so mehr bei gelernt! Also gerade für als Praktikum richtig so gewesen.

### Höhepunkte
- die Leute (unternehmerische Meschen): neue Erfahrung in der Einstellung, Lebensstil, Verhalten im Team (Reflexion dazu: dass viel Kommunikation möglich, war gut (übers Projekt, aber auch persönlich); Arbeit in so einem „engen“ Team war neue Erfahrung, gerne wieder)

### Am meisten stolz/ auch Höhepunkt: 
- automatische Fehlererkennung, dass nicht nur abstürzt oder so, sondern stattdessen automatische Nachricht. Einmal die Nachricht über ne fehlgeschlagene EBstellung, bei der Paypal kaputt war -> in wenigen Minuten behoben und ohne Kundenkontakt rechtzeitig für 3. Versuch des Kunden gelöst! 
Hier kam Aufräumen -> Anpassung mit besserer Geschwindigkeit mit Fehlererkennung zusammen -> Hat alles geklappt! Hatte Sinn

### Was kann ich besonders gut im Vergleich?
selbstständig arbeiten (Aufgaben selbst suchen bei nur sehr losen Erwartungen)
Sich Sachen selbst ergooglen (eigenständig Lösungen für Probleme finden, ohne Anleitung) Problemlöse-Kompetenz
viele Möglichkeiten mit den automatischen Sachen und so waren dem Team nicht bekannt, aber Dir schon -> durchs Erklären hat sich das alles gefestigt

### Schwächen/ Grenzen?
- oft selbst überschätzt (zeitlich) realistische Zeitplanung
passiert, weil: unvorhersehbar (bei Einschätzung denkt man immer, dass alles klappen wird) -> lernen, einen realistischen Zeitpuffer einzuplanen
- Soziales schwierig: v.a. anfangs, wenn Leute noch nicht so gut einschätzbar. z.B: Chef: bei Entscheidungen (wo Login-Knopf hinmachen) erstmal lieber nicht mit ihm geredet (weil nicht gewusst, wie kommunizieren); irgendwann dann doch diskutiert, Meinungen auseinander -> keine Freunde gemacht, weil sehr vehement auf eigener Meinung beharrt -> erst irgendwann klein bei gegeben
Reflexion: schon VOR/ WÄHREND des Gesprächs eine Sekunde nehmen und nachdenken: So wichtig, jetzt zu diskutieren (Sinn hinterfragen)? Nicht doch möglich, einfach nachzugeben? Vllt auch vorher Argumente sammeln, um vorbereitet reinzugehen.
! auch schon angefangen, das so umzusetzen!

## Neu gelernt: 
- Manche Diskussionen nicht anzetteln, sondern die Aufgaben einfach erledigen, wie es einem gesagt wurde (sozialer Bereich)

### Von andern eingeschätzt: s. Brief vom Chef
Vergleich s. Stärken und Schwächen von oben im Vergleich zum Chef-Brief



### Aufgaben waren sehr eigenverantwortlich gesucht, hat Dir aber gelegen 😊 -> gute Passung: Freiheit vom Team aus, dass Eigenverantwortung möglich 
Alle Ziele erreicht, also erfolgreiches Praktikum. 
Jetzt Arbeitsstelle bei was, was damit zusammenhängt -> Coole Möglichkeit
