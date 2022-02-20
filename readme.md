Praxisbericht
============

Einleitung
----------
In meiner Praxisphase bei der getpacked GmbH habe ich in den letzten 3 Monaten viel Erfahrung im Bereich der Softwareentwicklung sammeln. Ich habe die getpacked GmbH für mein Praktikum gewählt, da ich vorher hauptsächlich mit Systemprogrammiersprachen gearbeitet habe und nun auch einmal Erfahrung mit den Technologien moderner Webentwicklung sammeln wollte. Meine Aufgabe während der Praxisphase waren unter anderem die Einführung einer Continuous Integration/ Continuous Delivery Infrastruktur und das Erarbeiten und Umsetzen von Maßnahmen zur Verbesserung der Qualität des Quellcodes. Ausserdem konnte ich während meines Praktikums viel über das Arbeiten in einem agilen Team lernen.

Die Suche nach einem Praktikumsplatz habe ich lange herausgezögert, dann aber als ich mal angefangen hatte zu suchen über LinkedIn schnell einen Praktikumsplatz gefunden. Als hilfreiche Strategie hat sich herausgestellt, an Firmen mit interessanten offenen Stellen Bewerbungen zu schicken und die Firmen dann davon zu überzeugen, dass sie eigentlih keinen Angestellten, sondern nur einen Praktikanten suchen. Ausserdem ermöglicht LinkedIn das Bewerben nur mit Lebenslauf, was sehr angenehm ist, da für mich das Verfassen eines guten Anschreibens der unangenehmste Teil des Bewerbungsprozesses war.

Ich habe mir von dem Praktikum hauptsächlich erhofft, Einblick darüber, wie Webentwicklung mit einem modernen Technologiestack abläuft. Vorher habe ich hauptsächlich in modernem C++ und Rust Anwendungen entwickelt, bei beiden hatte ich aber relativ häufig das Gefühl das manche Dinge deutlich aufwendiger waren, als sie sein müssten. Mein Ziel war es ein Umfeld kennenzulernen, in dem die langfristig am wenigsten Komplexität schaffende Lösung, die ein Problem angemessen löst, als die Beste wahrgenommen wird. Da Webentwicklung den Ruf hat einsteigerfreundlich zu sein, und für viele Probleme schon eine vorgefertigte Lösung zu haben, schien es mir logisch in diesem Bereich nach eine Unternehmen zu suchen, dass mir so ein Umfeld bieten kann.

Ich habe mich am Ende für getpacked entschieden, weil ich bei ihnen den Eindruck hatte, da das reduzieren von Komplexität einen hohen Stellenwert hatten. Überzeugt haben mich vor allem drei Grundsatzentscheidungen die das gut bezeugen. Zum einen, dass das Unternehmen keine eigenen Server anmieten oder betreiben wird, sondern komplett auf serverless SaaS Technologien setzt. Zum anderen, dass keine Smartphone App, sondern nur eine mobiloptimierte Webanwendung entwickelt wird. Ausserdem wird das Projekt Server- und Clientseitig in JavaScript im selben Stil geschrieben. 

Meine Projekte während der Praxisphase waren hauptächlich im Softwarengineering Bereich angesiedelt. blablabla extend

Faktenreiche Kurzcharakteristik des Praktikums und der Institution
------------------------------------------------------------------
### Über getpacked
getpacked ist ein Startup das eine Software as a service Lösung für online Bestellungen anbietet. Der Fokus liegt dabei mehr auf Vorbestellungen zur Abholung, Bestellungen mit Lieferung sind allerdings auch möglich. Die Zielgruppe sind hauptsächlich Hofläden, aber auch Gastronomie, Bäckereien und Metzgereien. Vor allem in den Hofläden, Bäckereien und Metzgereien ist es bisher unüblich gewesen, online Vorbestellungen anzubieten. Gerade bei diesen Läden ist es aber ein klarer Vorteil Vorbestellungen anzubieten, da es hier Stoßzeiten gibt, zu denen deutlich mehr Kunden kommen, als am Rest des Tages. Wenn ein Teil der Kunden allerdings Vorbestellungen aufgibt, können diese im Vorraus gepackt und bezahlt werden und die Kunden müssen ihre Bestellung nur noch abholen.

Im Frühjahr 2021 wurde die getpacked GmbH offiziell gegründet, vorher war getpacked ein Teil der 360VIER GmbH. Aktuell hat das Unternehmen 8 Mitarbeiter, von denen 3 in der Entwicklung arbeiten. Die Firma hat rund 100 Kunden die mit getpacked erfolgreich ihre Produkte anbieten. 

### Aufgaben im Praktikum
Meine Aufgaben in der Praxisphase waren hauptsächlich die Aufbereitung des Programmcodes und der Entwicklungsinfrastruktur.
#### Einführung einer Continuous Integration/ Continuous Delivery Infrastruktur
Mein erstes Projekt bei getpacked war es eine CI/CD pipeline aufzusetzen und einzuführen. Wir haben uns dabei für GitLab CI entschieden, da wir GitLab sowieso schon als Softwareentwicklungsplattform eingesetzt haben und wir unseren Technologiestack nicht komplizierter machen wollten, als nötig. Da ich vorher schon relativ viel Erfahrung mit verschiedenen CI Programmen gesammelt hatte, ging das aufsetzen von GitLab CI relativ schnell. Was länger gedauert hatte war, die Geschwindigkeit der Builds zu erhöhen. Da unser Projekt circa 500MB an Abhänigkeiten hat, war es keine angebrachte Lösung diese bei jedem Build erneut herunterzuladen. Die in GitLab CI integrierten Funktionen zum speichern von Artefakten waren bei der Menge auch zu langsam um sinnvoll eingesetzt werden zu können. Die Lösung für das Probblem war es dann bei jeder Änderung der Dependencies einen neuen Container mit allen Dependencies zu erstellen und den für diesen und alle zunkünftigen builds zu benutzen.
Vorher sind alle Deployments per Hand ausgelöst worden, was einige probleme zur Folge hatte, zum Bei
- Deployments passierten manuell => unklar was gerade deployed ist. 
#### Umstellen der Codebase auf striktes TypeScript
Eine meiner ersten Aufgaben war es die Codebase der Webanwendung für eine Umstellung von JavaScript auf TypeScript vorzubereiten. Das Team hatte vorher schon angefangen TypeScript im Serverseitigem Code zu verwenden. Dort wurden aber die meisten Funktionen zur starken Überprüfung der Typen abgestellt, um die Entwicklungsgeschwindigkeit zu erhöhen, wodurch allerdings die
#### Refactoring des Codes
- Code aus Anfangszeiten von getpacked 
#### Logik für datenkonsitenz auf Serverseite migrieren
Da
#### Einarbeiten und verwenden verschiedener mir neuer Technologien
#### Performance optimierung eine Webanwendung
#### Umstellen auf css auf Komponentenebene
Bei normalen css Stylesheets erstellt man global gültige Klassennamen, die auf alle HTML Elemente einer bestimmten Klasse angewandt werden. In Komponentenbasieren Webanwendungen führt das oft zu Problemen, da wenn mehrere Komponenten den selben Klassennamen verwenden, sie sich dadurch auch oft unbemerkt gegenseitig beinflussen. In getpacked hatten wir zum Beispiel die Klasse `cartButton` die zum einen einen Knopf mit dem Preis des aktuellen Warenkorbs, der diesen auch öffnet gestaltet, zum anderen aber auch den Knopf um ein Produkt in den Warenkorb hinzuzufügen. Da beide Knöpfe relativ ähnlich aussahen, ist nicht aufgefallen, dass beide den die selbe CSS Klasse benutzen, bis wir die Farbe von einem anpassen wollten, was dann aber auch den anderen betroffen hat. Die Lösung war das Problem war es auf css mdoule umzustellen, dabei sind Klassennamen immer an eine Komponente gebunden. Erreicht wird das dadurch, dass die Namen der CSS Klassen im Buildprozess so modifiziert werden, dass sie einzigartig sind. So wird aus dem `cartButton` in der Basket Komponent zum Beispiel `Basket_cartButton_be8j3`.
#### Wechsel des JavaScript Frameworks
Wenn eine Sache stereotypisch für die Entwicklung von Webanwendungen ist, so ist das die große Zahl verschiedener JavaScript Frameworks und das stetige Verlangen auf ein hipperes umzusteigen [citation]. Zu Beginn meiner Praxisphase wurde die Anwendung mit React[citation] entwickelt. Mit React wird komplett auf clientseitiges rendering gesetzt, der Webserver gibt also jedem Besucher der Webseite die komplette javascript Anwendung, die dann im Webbrowser die Seite aufbaut. Da das aber in unserem Fall zu teilweise sehr langen Ladezeiten geführt hat, da die Bestellseite für Kunden und die Adminseite für Ladenbesitzer immer zusammen geladen werden mussten. Ausserdem wirkt sich clientseitiges rendering in der Regel auch negativ auf die Platzierung in den Ergebnissen von Suchmaschinen aus. Einen meiner Aufgaben war es nun eine Lösung für dieses Problem zu finden und umzusetzen. Ein weiteres Kriterium war es, das die  die Umstellung mit möglichst wenig Aufwand verbunden sein sollte. Die Entscheidung fiel auf Next, da es sich dabei im Grunde nur um eine Erweiterung von React mit auftrennung in verschiedene Seiten und serverseitigem rendering handelt. Es gibt bei Next für jede Unterseite der Webanwendung eine eigene React Anwendung, allerdings optimiert Next die Übergänge zwischen verschiedenen Unterseiten, sodass diese ohne eine neuladen der Seite clientseitig passieren können. Außerdem wird bei Next jede Unterseite serverseitig einmal vorgerendert und das hierbei erzeugt HTML wird mit der Seite an den Webbrowser geschickt und dient als eine Art Platzhalter, bis das clientseitige rendering abgeschlossen ist.
Die Umstellung der Anwendung auf Next hat etwa einen Monat gedauert, da mit ihr auch eine Umstellung von JavaScript auf TypeScript verbunden war. Da viele Teile das Codes angepasst werden mussten, haben wir beschlossen,dass es einfacher ist alles dabei auf Typescript umzustellen, da dadurch klar wird wie die Schnittstellen von Komponenten genau aussehen. Da
- schien erst einfach
- kein typescript viele Probleme
- Aufteilen der Seite in untersieten relativ unkompliziert
- Erster durchlauf muss auch serverseitig funktionieren
#### Erarbeiten von Guidelines zur Verbesserung der Wartbarkeit
- Kein globales Styling
- Nur striktes typescript ohne any
- Einheitliche code formatierung
- Naming conventions

Anderes:
- gitlab runner local
- vercel deploys
- firestore emulator (+ hostname)
- testcafe
- keine unittests
