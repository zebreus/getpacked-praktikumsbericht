Praxisbericht
============

Einleitung
----------
In meiner Praxisphase bei der getpacked GmbH habe ich in den letzten 3 Monaten viel Erfahrung im Bereich der Softwareentwicklung sammeln. Ich habe die getpacked GmbH für mein Praktikum gewählt, da ich vorher hauptsächlich mit Systemprogrammiersprachen gearbeitet habe und nun auch einmal Erfahrung mit den Technologien moderner Webentwicklung sammeln wollte. Meine Aufgabe während der Praxisphase waren unter anderem die Einführung einer Continuous Integration/ Continuous Delivery Infrastruktur und das Erarbeiten und Umsetzen von Maßnahmen zur Verbesserung der Qualität des Quellcodes. Ausserdem konnte ich während meines Praktikums viel über das Arbeiten in einem agilen Team lernen.

Die Suche nach einem Praktikumsplatz habe ich lange herausgezögert, dann aber als ich mal angefangen hatte zu suchen über LinkedIn schnell einen Praktikumsplatz gefunden. Als hilfreiche Strategie hat sich herausgestellt, an Firmen mit interessanten offenen Stellen Bewerbungen zu schicken und die Firmen dann davon zu überzeugen, dass sie eigentlih keinen Angestellten, sondern nur einen Praktikanten suchen. Ausserdem ermöglicht LinkedIn das Bewerben nur mit Lebenslauf, was sehr angenehm ist, da für mich das Verfassen eines guten Anschreibens der unangenehmste Teil des Bewerbungsprozesses war.

Ich habe mir von dem Praktikum hauptsächlich erhofft, Einblick darüber, wie Webentwicklung mit einem modernen Technologiestack abläuft. Vorher habe ich hauptsächlich in modernem C++ und Rust Anwendungen entwickelt, bei beiden hatte ich aber relativ häufig das Gefühl das manche Dinge deutlich aufwendiger waren, als sie sein müssten. Mein Ziel war es ein Umfeld kennenzulernen, in dem die langfristig am wenigsten Komplexität schaffende Lösung, die ein Problem angemessen löst, als die Beste wahrgenommen wird. Da Webentwicklung den Ruf hat einsteigerfreundlich zu sein, und für viele Probleme schon eine vorgefertigte Lösung zu haben, schien es mir logisch in diesem Bereich nach eine Unternehmen zu suchen, dass mir so ein Umfeld bieten kann.

Ich habe mich am Ende für getpacked entschieden, weil ich bei ihnen den Eindruck hatte, da das reduzieren von Komplexität einen hohen Stellenwert hatten. Überzeugt haben mich vor allem drei Grundsatzentscheidungen die das gut bezeugen. Zum einen, dass das Unternehmen keine eigenen Server anmieten oder betreiben wird, sondern komplett auf serverless SaaS Technologien setzt. Zum anderen, dass keine Smartphone App, sondern nur eine mobiloptimierte Webanwendung entwickelt wird. Ausserdem wird das Projekt Server- und Clientseitig in JavaScript im selben Stil geschrieben. 

Meine Projekte während der Praxisphase waren hauptsächlich im Softwarengineering Bereich angesiedelt.

Faktenreiche Kurzcharakteristik des Praktikums und der Institution
------------------------------------------------------------------
### Über getpacked
getpacked ist ein Startup das eine Software as a service Lösung für online Bestellungen anbietet. Der Fokus liegt dabei mehr auf Vorbestellungen zur Abholung, Bestellungen mit Lieferung sind allerdings auch möglich. Die Zielgruppe sind hauptsächlich Hofläden, aber auch Gastronomie, Bäckereien und Metzgereien. Vor allem in den Hofläden, Bäckereien und Metzgereien ist es bisher unüblich gewesen, online Vorbestellungen anzubieten. Gerade bei diesen Läden ist es aber ein klarer Vorteil Vorbestellungen anzubieten, da es hier Stoßzeiten gibt, zu denen deutlich mehr Kunden kommen, als am Rest des Tages. Wenn ein Teil der Kunden allerdings Vorbestellungen aufgibt, können diese im Vorraus gepackt und bezahlt werden und die Kunden müssen ihre Bestellung nur noch abholen.

Im Frühjahr 2021 wurde die getpacked GmbH offiziell gegründet, vorher war getpacked ein Teil der 360VIER GmbH. Aktuell hat das Unternehmen 8 Mitarbeiter, von denen 3 in der Entwicklung arbeiten. Die Firma hat rund 100 Kunden die mit getpacked erfolgreich ihre Produkte anbieten. 

### Aufgaben im Praktikum
Meine Aufgaben in der Praxisphase waren hauptsächlich die Aufbereitung des Programmcodes und der Entwicklungsinfrastruktur, aber auch viele andere Dinge.

#### Einführung einer Continuous Integration/ Continuous Delivery Infrastruktur
Mein erstes Projekt bei getpacked war es eine CI/CD pipeline aufzusetzen und einzuführen. Wir haben uns dabei für GitLab CI entschieden, da wir GitLab sowieso schon als Softwareentwicklungsplattform eingesetzt haben und wir unseren Technologiestack nicht komplizierter machen wollten, als nötig. Da ich vorher schon relativ viel Erfahrung mit verschiedenen CI Programmen gesammelt hatte, ging das aufsetzen von GitLab CI relativ schnell. Was länger gedauert hatte war, die Geschwindigkeit der Builds zu erhöhen. Da unser Projekt circa 500MB an Abhänigkeiten hat, war es keine angebrachte Lösung diese bei jedem Build erneut herunterzuladen. Die in GitLab CI integrierten Funktionen zum speichern von Artefakten waren bei der Menge auch zu langsam um sinnvoll eingesetzt werden zu können. Die Lösung für das Probblem war es dann bei jeder Änderung der Dependencies einen neuen Container mit allen Dependencies zu erstellen und den für diesen und alle zunkünftigen Builds zu benutzen.
Dadurch konnten wir die Deploymentfrequenz von ~3mal pro Woche auf ~4mal pro Tag erhöhen.

#### Sicherstellung einer hohen Codequalitaet
Eine Aufgabe die durchgehend an der ich durchgehend beschaeftigt war, war die Verbesserung der Codequalitaet. Die Entwicklung bei getpacked wurde oft durch Bugs ausgebremst, die durch klareren Code vermeidbar gewesen waeren. Oft war es allein durch die Betrachtung ihrer Schnittstelle unklar, wie Komponenten verwendet werden, damit sie das tun was man erwartet. Der Code in den Komponenten war allerdings auch oft zu komplex, um schnell zu verstehen, wie sie verwendet werden. Ausserdem war die Formatierung des Quelltexts inkonsistent, und der Zustand der Anwendung war nicht immer klar. Einige Massnahmen zur Sicherstellung einer der Codequalitaet wurden mir anfangs aufgetragen, andere habe ich selbst erarbeitet.

#### Erarbeiten von Guidelines zur Verbesserung der Wartbarkeit
Um die Codequalität auch langfristig hoch zu halten habe ich Guidelines zur Verbesserung der Wartbarkeit erarbeitet.

Die Guidelines sind zum einen Regeln für linter, formatter oder ähnlichen Programmen die diese automatisiert durchsetzen können. In diese Kategorie fallen vor allem
- Statische analyse mit TypeScript
- Statische analyse mit eslint
- Automatische Codeformatierung
- Automatisches verwalten von imports
- Globales CSS verbieten
- Naming conventions für Interfaces und Funktionen
Diese Regeln werden direkt in vscode, beim Speichern, in Precommit-Hooks, oder in CI jobs durchgesetzt, um die Codequalität sicherzustellen

Neben den Dingen die man überprüfen kann gibt es noch einige Faktoren in den Codingstandarts die nicht automatisch überprüft werden können, da sie mehr die Art betreffen wie man Code schreibt und darüber nachdenkt. Wir fanden es sinnvoll auch dafür Richtlinien festzulegen, damit sich die Codebase auch im Stil einheitlicher anfühlt. In diese Kategorie fallen:
- Erst denken, dann programmieren
- Weniger Code meist besser als viel Code ist
- Dinge richtig zu bennenen ist die halbe Miete
- Guard clauses sind die bevorzugte Art von Verzweigungen

#### Umstellen der Codebase auf striktes TypeScript
Eine meiner ersten Aufgaben war es die Codebase der Webanwendung für eine Umstellung von JavaScript auf TypeScript vorzubereiten. Das Team hatte vorher schon angefangen TypeScript im Serverseitigem Code zu verwenden. Dort wurden aber die meisten Funktionen zur starken Überprüfung der Typen abgestellt, um die Entwicklungsgeschwindigkeit zu erhöhen, wodurch allerdings auch keine der Vorteile von Typescript genutzt wurden.

##### Was ist TypeScript und wie wollen wir es nutzen
Die Grundidee hinter TypeScript ist, das es normales Javascript mit zusaetzlichen Typinformationen ist, die beim kompiliern erst zur Ueberpruefung der Korrektheit benutzt und dann komplett entfernt werden. Uebrig bleibt normales JavaScript. Als Folge dessen hat TypeScript die Eigenschaft, dass es beim kompilieren komplett statisch getyped ist, bei der Ausfuehrung aber dynamisch. Man kann deshalb in Typescript den Typ einer Variable auch als `any` angeben und damit komplett auf Ueberpruefung der Korrektheit in der Verwendung dieser Variable verzichten. Das fuehrt allerdings zu weniger Klarheit darueber, welche Werte Variablen annehmen koennen. Damit gibt TypeScript die Entscheidung, wie stark Typen ueberprueft werden sollen an die Entwickler.

Die erste Teilaufgabe der Umstellen der Codebase auf TypeScript war es also das zu entscheiden. Dazu habe ich mit allen Teammitgliedern gesprochen um zu verstehen, wie sie dazu stehen. Die Grundhaltung war etwas Angst, dass durch TypeScript die allgemeine Produktivitaet sinkt, da man sich mehr Gedanken darueber machen muss, wie die Schnittstellen von Komponenten aussehen und wie man diese in TypeScript definiert. Allerdings sind genau das auch die Gruende, weshalb wir zu TypeScript wechseln wollten. Klar definierte und gut durchdachte Komponenten sind wesentlich einfacher zu verwenden und wartbarer. Deshalb haben wir uns dazu entschieden TypeScript so strikt wie moeglich einzustellen.

##### Und was habe ich dafuer gemacht
Die zwei groessten Herausforderungen bei der Umstellung auf Typescript waren zum einen herauszufinden was die Typen in existierendem Code sind und sicherzustellen das auch aller zukuenftige Quelltext mit sinnvollen und korrekten Typen versehen ist. 

Beim Herausfinden und Definieren von Typen in existierendem Code habe ich hauptsaechlich darauf gesetzt Annahmen ueber die Typen von Dingen aufzustellen und diese bei Unklarheit dann im Debugger zu verifizieren. Die Annahmen habe ich entweder durch Gespraeche mit den anderen Teammitgliedern oder durch den Kontext des Codes versucht aufzustellen. Meistens war es nicht noetig die Annahmen durch Tests zu ueberpruefen, da wenn alle Orte an denen ein Komponent verwendet wird mit Typen versehen sind, sich der Compiler beschwert, wenn etwas nicht passt.

Nachdem die Kernkomponenten der Codebase mit Typen versehen waren, habe ich sichergestellt, dass auch aller neuer Code in striktem TypeScript geschrieben wird und  das der Rest der Codebase im Laufe der Zeit zu TypeScript wird. Dazu habe ich unter anderem Linterregeln eingefuehrt, die weder die explizite, noch die implizite Verwendung von `any` zu erlauben. Ich mit dem Team einen kurzen Crashkurs gemacht, damit alle ein Verstaendnis dafuer haben, wie und warum wir TypeScript einsetzen. Ausserdem habe ich dafuer gesorgt das Team stetig mit Informationen zum Anteil von TypeScript und JavaScript an der Codebase zu versorgen und es zu feiern, wenn der JavaScript Anteil sinkt.

#### Logik für datenkonsitenz auf Serverseite migrieren
TODO
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
Wenn eine Sache stereotypisch für die Entwicklung von Webanwendungen ist, so ist das die große Zahl verschiedener JavaScript Frameworks und das es immer ein neues cooleres Framework gibt. Zu Beginn meiner Praxisphase wurde die Anwendung mit React entwickelt. Mit React wird komplett auf clientseitiges rendering gesetzt, der Webserver gibt also jedem Besucher der Webseite die komplette javascript Anwendung, die dann im Webbrowser die Seite aufbaut. Da das aber in unserem Fall zu teilweise sehr langen Ladezeiten geführt hat, da die Bestellseite für Kunden und die Adminseite für Ladenbesitzer immer zusammen geladen werden mussten. Ausserdem wirkt sich clientseitiges rendering in der Regel auch negativ auf die Platzierung in den Ergebnissen von Suchmaschinen aus. Einen meiner Aufgaben war es nun eine Lösung für dieses Problem zu finden und umzusetzen. Ein weiteres Kriterium war es, das die  die Umstellung mit möglichst wenig Aufwand verbunden sein sollte. Die Entscheidung fiel auf Next, da es sich dabei im Grunde nur um eine Erweiterung von React mit auftrennung in verschiedene Seiten und serverseitigem rendering handelt. Es gibt bei Next für jede Unterseite der Webanwendung eine eigene React Anwendung, allerdings optimiert Next die Übergänge zwischen verschiedenen Unterseiten, sodass diese ohne eine neuladen der Seite clientseitig passieren können. Außerdem wird bei Next jede Unterseite serverseitig einmal vorgerendert und das hierbei erzeugt HTML wird mit der Seite an den Webbrowser geschickt und dient als eine Art Platzhalter, bis das clientseitige rendering abgeschlossen ist.

Die Umstellung der Anwendung auf Next hat etwa einen Monat gedauert, da mit ihr auch eine Umstellung von JavaScript auf TypeScript verbunden war. Da viele Teile das Codes angepasst werden mussten, haben wir beschlossen, dass es einfacher ist alles dabei auf Typescript umzustellen, da man dabei auch die Schnittstellen von Komponenten klar definieren muss. Vorher war es ein Problem, dass oft unklar war was es bewirkt, wenn man eine Eigenschaft auf einem Komponenten setzt und ob die überhaupt verwendet wird. Zum Beispiel gab es viele Situationen in denen Komponenten Eigenschaften mitgegeben wurden, die es inzwischen garnicht mehr gibt.

Der erste Teil der Migration zu Next war es die Anwendung von einer Seite in mehrere Teilseiten aufzutrennen. Da wir vorher ddie Entscheidung welche Seite angezeigt werden soll auch schon auf Basis der URL getroffen haben, hatten wir schon Reactkomponenten für die meisten Seiten. Dadurch war das auftrennen in Nextjs Seiten relativ einfach. Da ich allerdings dabei die Dateien auch auf TypeScript portiert haben hat das auftrennen auch ungefähr eine Woche gedauert.

Der Großteil der Arbeit der Umstellung auf nextjs war es sicherzustellen, das jede Unterseite auch erfolgreich Serverseitig rendered. Das Hauptproblem dabei ist, dass man auf die Informationen die nur im Browser des Nutzers verfügbar sind, serverseitig keinen Zugriff hat. Das umfasst unter anderem Bildschirmgröße, Cookies, Localstorage und Zugriff auf DOM Elemente. Deshalb mussten wir alle Stellen finden an denen das passierte und jeweils eine individuelle Lösung finden, wie man damit umgeht.

NextJS hat integrierte Lösungen für einige Probleme für die wir vorher andere Libraries verwendet haben. Zum Beispiel kann NextJS Bilder selbst serverseitig skalieren und dadurch Bilder nur in der benötigten Größe auslieferen. Damit das funktioniert musste ich alle Bilder auf die NextJS Image Komponente umstellen.

#### Gitlab CI pipeline optimieren
Am Anfang meines Praktikum hatte ich Gitlab CI aufgesetzt. Die CI war so konfiguriert, dass jeder Branch der auf den `main` Branch gemerged werden soll erst die CI tests erfolgreich durchlaufen muss. Mit der Zeit hat sich allerdings herausgestellt, dass das unsere Entwicklungsgeschwindigkeit ein wenig ausbremst. Wenn man erst 10 Minuten warten muss, bis die Pipeline durchgelaufen ist. Meine Aufgabe war es dann auszuwerten, warum die Pipelines so lange brauchen. Der Hauptgrund war, dass die von Gitlab gehosteten Jobrunner den Dockercontainer in dem die Tests ausgeführt wurden für jeden Schritt immer wieder neu herunterladen mussten, da für jeden Schritt ein anderer Runner verwended wird.

Die Lösung für das Problem ist es in der Regel eigene Runner zu hosten, die die Dockerimages lokal vorhalten, sobald sie einmal heruntergeladen wurden. Eigene Runner auf Servern zu hosten kam für uns allerdings nicht in Frage, da schnelle Server doch relativ teuer sind. Gitlab bietet zwar die Möglichkeit ein Kubernetes Cluster anzubinden und darauf dann bei Bedarf Runner zu erschaffen. Der administrativa Aufwand wäre allerdings ziemlich hoch gewesen und es hätte unsere Probleme auch nicht komplett gelöst, da Kubernetes auch immer mindestens einen aktiven Server braucht, der Kosten verursacht.

Als nächstes hatte ich versucht, ob es sinnvoll möglich ist, die Runner lokal auf den Computern der Entwickler laufen zu lassen. Den Runner auszuführen war überraschend unkompliziert, da er als docker container verfügbar ist. Die Kopplung mit Gitlab war auch einfach zu lösen, dabei wird beim Starten des Runners nur ein Token für das Projekt benötigt, das wir auf dem selben Kanal wie unsere restlichen secrets verteilen können. Das letzte Problem war noch das die Runner automatisch gestartet werden. Meine erste Idee war es dazu den Runner beim starten der Anwendung im Debug modus automatisch mitzustarten. Das hatte allerdings den Nachteil, dass die Runner immer gestartet wurden, auch wenn man es nicht wollte (z.B. weil man wusste, das man gleich offline geht). Ausserdem war es schwer möglich herauszufinden, wann der Runner beendet werden sollte. Nach etwas Recherche habe ich herausgefunden, dass vscode eine integrierte Funktion hat, um den Nutzer beim Öffnen eines Projekts zu fragen, ob ein bestimmter Task ausgeführt werden soll. Den Runner darüber zu starten hat den Vorteil, dass der Entwickler nichts machen muss außer das Popup zu bestätigen und der Runner auch wieder beendet wird, sobald man für den Tag fertig entwickelt hat.

Dadurch haben wir Runner auf Computern mit Desktop CPUs, die für unsere hauptsächlich nicht parallel ausgeführten Jobs ein ganzes Stück schneller sind als Server CPUs. Der einzige Nachteil ist, dass Jobs manchmal fehlschlagen können, weil ein Entwickler seinen Computer ausschaltet während der Job dort ausgeführt wird. In der Praxis ist das aber nur knapp ein mal pro Monat passiert. Mit dieser Lösung konnte ich ohne mehrkosten zu verursachen die Dauer unserer Pipelines von 7-10 auf 1-4 Minuten zu reduzieren (je nachdem ob noch Container geladen werden müssen und wie viele Runner online sind). 

#### Andere Aufgaben
Außerdem habe ich während meiner Zeit bei getpacked noch ein paar andere Dinge getan:
- Automatisieren von vercel deploys
- Aufsetzen von firestore emulatoren
- Versuch des etablieren von End-To-End Tests mit testcafe
- Aufsetzen von Sentry zum Fehlertracking

Reflexion
---------

### Welche Ziele habe ich mir im praktium gesetzt
Im Praktikum hatte ich mehrere Ziele und Aufgaben, vor allem wollte ich die Codebase und alles drumherum aufräumen und strukturieren, und dafür sorgen dass sie auch sauber bleibt. Ein weiteres Aufgabe war es eine Such und Übersichtsseite für alle Betriebe in getpacked zu erstellen. Ausserdem hab ich mir selbst das Ziel gesetzt, nachhaltig zu lernen, wie man möglichst effektiv moderne Webanwendungen baut. Dazu wollte ich mir anschauen, was es aktuell für Werkzeuge gibt, um effektiver programmieren zu können.

### Ziele erfüllt:
#### Aufräumen und strukturieren
Ich glaube ich konnte während meiner Zeit bei getpacked die Lesbarkeit und Wartbarkeit des Programms deutlich verbessern. Was ich in der Zeit besonders geschätzt habe, war das ich relativ viel Zeit in Dinge investieren durfte, die nicht direkt Features für das Produkt bringen, sondern nur langfristig die Geschwindigkeit mit der neue Dinge entwickelt werden können erhöhen. Ausserdem fand ich es cool, dass nahezu alle meiner Bestrebungen in die Richtungen auch von meinen Kollegen angenommen wurden. (Nur das entfernen von unbenutzten imports beim speichern ist auf Wiederstand gestossen).

TODO
- Noch irgendwie erwähnen, dass das schon irgendwie eins meiner Ziele von anfang an war, ich hab afaik sogar im Vorstellungsgespräch verlangt, dass ich 1 woche im Monat komplett auf refactoring setzen darf.

#### Lernen von Webentwicklung
Webentwicklung mit React ist jetzt auch eine der Sachen die ich kann. Was mich überrascht hat, war es zu sehen, wie einfach man mit moderenen Frameworks/Tools komplexe UIs strukturien kann. Vorher hatte ich hauptsächlich mit Qt gearbeitet, dabei kam mir das erstellen von UIs immer unnötig aufwändig vor, ich hatte aber akzeptiert, dass es wahrscheinlich nicht viel einfacher geht. Ausserdem kann ich jetzt JavaScript, was auch nützlich ist.

#### Werkzeuge ausprobieen
Während dem Praktikum konnte ich viele Werkzeuge ausprobieren. Teilweise kannte ich einige davon schon vorher und hatte nur noch keine Chance sie in der Praxis zu verwenden. Andere haben aber auch erst während der Praxisphase durch meine Kollegen meine Aufmerksamkeit gewonnen.
Von Anfang wollte ich KI basierte automatische Vervollständigung  verwenden. Anfangs habe ich dazu tabnine benutzt, dann hatte ich die Möglichkeit GitHub Copilot einzusetzen und bin dann auch dabei geblieben, weil Copilot deutlich besser Vorschläge macht.
Mit GitLab CI wollte ich auch ein weiteres CI tool kennenlernen und das hat auch funktioniert.

Ein weiteres Werkzeug das ich zu schätzen gelernt habe, war der nix package manager, mit dem es ziemlich einfach möglich ist auf allen Computern in der selben Umgebung zu entwicklen. Wir hatten anfangs ab und an Probleme damit, dass jeder andere Versionen von verschiedenen Programmen installiert hatte. Mit nix konnten wir das nachhaltig lösen.

Ausserdem habe ich während meiner Zeit in der Praxisphase angefangen viel mit gitpod zu arbeiten. Dabei handelt es sich im Grunde um vscode, aber es läuft komplett im Browser. Vorallem bei Codereviews hat das den Prozess enorm beschleunigt, da man mit einem Klick auf dem Pullrequest direkt eine IDE mit den zu reviewenden Änderungen hat.

Auch etwas, dass ich vor der Praxisphase überhaupt nicht auf dem Schirm hatte waren nocode workflow automation Programme, bei denen man verschiedene APIs relativ unkompliziert grafisch ansteuern kann. Die sind überraschend praktisch, wenn man einfach nur zwei Dinge schnell verbinden will, aber dafür nicht extra einen Server aufsetzen möchte. Wir konnten es damit zum Beispiel relativ unkompliziert umsetzen, dass bei jeder neuen Bestellung eine Nachricht darüber in einen Slack Channel gesendet wird.

### Herausforderungen
Die wohl grä
- anfangs Diskussionen über Geschäftsmodell, aber irgendwann ignoriert, weil nicht im Aufgabenbereich 
- Web-Entwicklung, weil noch nie vorher gemacht; aber gut geklappt, weil Programmieren an sich schon bekannt + Google -> hat gereicht; selbst aufs Projekt bezogen beigebracht -> Projekt bzw Praktikum in dem Bereich hat geholfen, dass Web-Entwicklung jetzt deutlich routinierter und kompetenter (alle Möglichkeiten bekannt) ablaufen würde; 


## Irgendwas anders machen?
Idee mit Geschwindigkeit hinschreiben und dann quasi Argumente dagegen 😊
- weniger Wert auf guten Code, mehr auf Geschwindigkeit? Weil: Firma jetzt pleite! Langfristig schneller durch guten Code jetzt irrelevant. ABER: Konnte man da nicht wissen -> nächstes Mal vielleicht anderen Fokus legen…? Entspricht aber nicht unbedingt eigenen Werten, deshalb wenn dann Fokus nur in Absprache mit Firma/Vorgesetzten verschieben (SOLL es später wiederverwendbar/anpassbar bleiben?) 
Also eigentlich nö. Weil konnte man nicht wissen. Und so mehr bei gelernt! Also gerade für als Praktikum richtig so gewesen.

### Höhepunkte
#### Arbeiten in einem coolen Team
An dem Praktikum hat mir besonders gefallen mit Leuten die aus so einer Startup Blase kommen zu arbeiten. Im Vergleich zu meiner vorherigen Arbeitserfahrung waren alle viel motivierter etwas cooles zu bauen und dabei auch noch Spaß zu haben. Außerdem wurde viel Wert auf gute Kommunikation gelegt was mir auch sehr gefallen hat. Wir hatten zum Beispiel immer eine guten Überblick darüber wer gerade was macht und wenn sich herausgestellt hat das jemand anders schon Erfahrung mit einem Thema hatte konnte man das dann einfach schnell zusammen bearbeiten. Was ich auch cool fand war das sich niemand zu fein war um Hilfe zu fragen, so hab ich wahrscheinlich ähnlich viel Hilfe gegeben wie bekommen. Arbeit in so einem offenen Team war für mich eine neue Erfahrung, gerne wieder.

#### Inhaltliche Hoehepunkte
TODO
- automatische Fehlererkennung, dass nicht nur abstürzt oder so, sondern stattdessen automatische Nachricht. Einmal die Nachricht über ne fehlgeschlagene EBstellung, bei der Paypal kaputt war -> in wenigen Minuten behoben und ohne Kundenkontakt rechtzeitig für 3. Versuch des Kunden gelöst! 
Hier kam Aufräumen -> Anpassung mit besserer Geschwindigkeit mit Fehlererkennung zusammen -> Hat alles geklappt! Hatte Sinn

### Was kann ich besonders gut im Vergleich?
TODO
selbstständig arbeiten (Aufgaben selbst suchen bei nur sehr losen Erwartungen)
Sich Sachen selbst ergooglen (eigenständig Lösungen für Probleme finden, ohne Anleitung) Problemlöse-Kompetenz
viele Möglichkeiten mit den automatischen Sachen und so waren dem Team nicht bekannt, aber Dir schon -> durchs Erklären hat sich das alles gefestigt

### Was halte ich für meine Schwächen und Grenzen?
#### Zeitplanung
Ich habe bei getpacked gelernt, dass ich mir relativ schwer damit tue realistisch einzuschätzen, wie lange ich für Dinge brauchen werde. Es ist mir relativ häufig passiert, dass ich Aufgaben gnadenlos unterschätzt habe, und sie in Realität deutlich länger gedauert haben. Ich fühle mich dann oft schlecht, wenn irgendwie alles hinter dem Zeitplan liegt. Ich glaube das das Hauptproblem ist, dass ich bei der Einschätzung von Zeiten meistens davon ausgehe, dass alles direkt gut funktioniert, aber dann bei der Durchführung dann oft unvorhergesehene Hindernisse auftauchen. In Zunkunft werde ich versuchen prinzipiell Aufgaben mit einem großzügigen Zeitpuffer zu planen, wenn es schneller geht ist, ist es dann eine positive Erfahrung und wenn nicht ist es auch ok.

#### Ich tendiere dazu mich in subjektiven Diskussionen festzufahren
Es ist mir besonders gegen Anfang oft passiert, dass ich mich dazu verleiten lassen übermässig viel Zeit und Energie in eigentlich relativ sinnlose Diskussionen zu stecken. Eins der extremsten Beispiel war die Diskussion darüber, wie der Knopf zum anmelden mit Email und Password im Kontrast zur den Knöpfen zur Anmeldung mit third-party Authentication Providern dargestellt werden soll, sodass möglichst wenige Nutzer eine Anmeldung mit Email und Passwort wählen. In den Gesprächen hatte niemand Daten darüber wie sich die Gestaltung des Knopfes tatsächliche auf das Anmeldeverhältnis auswirkt. Alle waren sich auch einig, dass es wahrscheinlcih keinen großen Unterschied macht, welche der beiden trivialen Lösungen wir wählen. Realistisch gesehen haben wir zwei Stunden ohne Grundlage über ein sinnloses Thema diskutiert. Inzwischen akzeptiere ich bei solchen Diskussionen einfach irgendeine Lösung, da sie zu dem Zeitpunkt gleichwertig sind. Wenn sich dann herausstellt, dass die Wahl falsch war, kann man immernoch mehr Daten darüber sammeln und dann später nochmal beide Ansätze sinnvoll vergleichen. Im Praktikum habe ich gelernt, zu erkennen, wenn ich mich in so einer Situation befinde und diese dann zu verlassen.

#### Reden mit Leuten die ich nicht gut einschätzen kann
Wenn ich mit Leuten reden muss, die ich nicht gut einschätzen kann, fühle ich mich meistens sehr unsicher. Weil ich nicht genau weiss wie ich mich verhalten soll um nicht zu seltsam zu wirken. Das scheint allerdings größtenteils ein Problem zu sein, das nur in meinem Kopf stattfindet, da ich nie das Feedback bekommen habe, dass ich da tatsächlich seltsam gewirkt habe. Nachdem ich ein paar mal mit jemandem Kontakt hatte legt sich das aber in der Regel und ich fühle mich sicherer. Auch wenn ich mir solche Situationen unangenehm sind, habe ich festgestellt, dass es mir auch irgendwie Spaß macht in solchen Situationen zu sein.

## Neu gelernt:
TODO: Maybe remove
- Manche Diskussionen nicht anzetteln, sondern die Aufgaben einfach erledigen, wie es einem gesagt wurde (sozialer Bereich)

### Von andern eingeschätzt: s. Brief vom Chef
TODO: Maybe remove
Vergleich s. Stärken und Schwächen von oben im Vergleich zum Chef-Brief


### Fazit

#### Aufgaben waren sehr eigenverantwortlich gesucht, hat Dir aber gelegen 😊 -> gute Passung: Freiheit vom Team aus, dass Eigenverantwortung möglich 
Alle Ziele erreicht, also erfolgreiches Praktikum. 
Jetzt Arbeitsstelle bei was, was damit zusammenhängt -> Coole Möglichkeit
