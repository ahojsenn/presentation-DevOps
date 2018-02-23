---?image=https://raw.githubusercontent.com/ahojsenn/assets/master/img/_mandelbrot01.png
# Vertikale Organisation
<!-- .element: style="font-size: 3em; color: orange"-->
da muss sich was um 90° drehen im Kopf!
<!-- .element: style="font-size: 2em; color: orange"-->

+++?image=images/profilbild.jpg&size=auto 90%
+++?image=images/johannes-mainusch.jpg&size=auto 90%

---?image=images/zebra.png&size=auto 90%
Note:
Querstreifen machen dick. Und wenn man viel zu dick ist, wird man langsam und träge.

+++?image=images/FirmaReorga01.jpg
Note:
Übertrag auf Dev-Teams: Spezialisten-Teams (Frontend, Backend, Operations, Data Science, ...) sind schlecht.
Eigentlich mehrere Teams in einem (Scrum Smell: PO muss alle Spezialisten auslasten)
Gegenbewegungen: DevOps, Full Stack Developer

+++?image=images/entwicklerwolke_.jpg
Note:
Selbst wenn man z.B. ein Team aus Full Stack Devs hat, skaliert das bei großen Aufgaben nicht gut.
Kommunikation, Anzahl theoretische Beziehungen, nicht schlagkräftig.
Was macht man dann? Mehrere Teams. Und welchen Schnitt wählt man dann?
+++?image=images/FirmaReorga01.jpg
Note:
Wenn man Teams horizontal nach Aufgabe schneidet (Frontend-Backend-Split), berührt fast jede Anforderung alle Schichten.

+++?image=https://raw.githubusercontent.com/ahojsenn/assets/master/img/FirmaReorga02.jpg
Note:
Wir schneiden vertikal. Das ist das Hauptprinzip der Vertikalisierung

---
# Vertikalisierung, what?

+++?image=images/schneiden.jpg
Note:
Wie schneiden wir die Teams? Schnitte rückgängig machen ist schwer.
Es gibt keine Standard-Antwort.
Reaktiv ist eine gute Antwort: Der Schnitt ergibt sich in einer konkreten Situation teils von selbst.
Aber aufpassen: Vertikal bleiben, keine horizontalen Schnitte.
Einfache Regel für E-Commerce: jedes Team sollte direkten Kontakt zum Kunden/Benutzer haben.

+++?image=images/customerjourney_.jpg&size=auto 90%
Note:
Gelöst: Die meisten Use-Cases/Feature Requests berühren nur ein Team. Abteilungen haben ein Dev-Team als Ansprechpartner.

+++?image=https://raw.githubusercontent.com/ahojsenn/assets/master/img/vertikaleKomponenten.png
Note:
Andere Kultur: Jedes Team managt Produkt, Technik, Organisation selbst.
Konzept Triade bei Otto.
Entwickler bauen in solch fachlich fokussierten Teams Domänenwissen auf. Teams sprechen Stakeholder-Sprache.

+++?image=https://github.com/ahojsenn/assets/blob/master/img/vertikaleTeams.png
Note:
Im Team besteht auch wieder die Möglichkeit, z.B. über Microservices vertikale Strukturen aufzubauen.
Teams können viel leichter verteilt arbeiten.

+++?image=https://github.com/ahojsenn/assets/blob/master/img/TeamSplitVertikal.png

+++?image=images/speedboats_.jpg&size=auto 90%
Note:
Geschwindigkeit durch Parallelisierung, trotzdem kleine, flexible Teams.


---
# Vertikalisierung, how?

+++?image=images/sharednothing_.jpg&size=auto 90%
Note:
Jedes Team hat eigene Infrastruktur, trifft eigene Technologieentscheidungen (Sprache, Datenbank). Analog zum DDD hat jedes Team seine Domain mit seinen Fachobjekten (Bei Kaufen hat ein Kunde Adressen, bei Entdecken stattdessen einen Clickstream)
Es gibt dennoch übergreifende Aspekte, die zu sharing führen. (Die Wolke im Background ist shared, fällt gar nicht auf, oder?)
+++?image=https://raw.githubusercontent.com/ahojsenn/assets/master/img/DJ-MikroMakroArch.jpg
Note:
Es folgen ein paar Makroarchitektur-Klassiker

+++?image=images/integration_.jpg&size=auto 90%
Note:
Frontend-Integration, Backend-Integration (Datenaustausch)

+++
# Frontend-Integration
Vortrag von Oliver Zeigermann

https://djcordhose.github.io/architecture/2018_oop.html

Note:
Möglichkeiten: Links, SSIs, Microcomponents (SPAs)

+++
# Frontend-Integration
Pattern Library
Note:
Übergreifendes, konsistentes Design auf der Webseite, Sicherstellen von Reaktivität, Konformität über Viewports hinweg.
Die einzelnen Frontends können auf High-Level-Komponenten zurückgreifen, die in der Darstellung korrekt sind. Entwicklung zentral, Verteilung über versionierte Library.

Bei Breuninger technische Bindung (handlebars templating), was besseres ist uns nicht eingefallen.

+++?image=images/integration_.jpg&size=auto 90%
Note:
Datenaustausch:
Service Discovery z.B. über JSON Home (Endpunkte können zur Laufzeit geändert werden)
Datenaustausch bei Breuninger asynchron über REST, Multipart.
Was wären Alternativen?
Bei Realtime-Anforderung: Kein Messagebus, sondern WebSockets.

+++?image=images/rfc.png
Note:
Generell: RFCs/Standards statt Technologien. Beispiel GKH media types
Beispiel: Cassandra als zentrale DB.

+++?image=images/resilienz.jpg
Note:
Wichtig: Resilienz, Stabilität. Schon unterstützt durch asynchrone Kommunikation. Bei Implementierung von Schnittstellen immer auch an den Schlechtfall denken. Alte Daten sind besser als keine Daten. Entschuldigungen sind besser als Exceptions.
Datendesign: Beispiel Preise: mehrere mit Startdatum.
Rückwärtskompatibilität.
Schemata: Muss nicht, kann aber helfen.
CDC-Tests als Alternative.

+++?image=images/seismograph.jpg
Note:
Anforderung von außen könnte sein: Zentrales System für Einsicht von Monitoring & Logging.
Pitfall Beispiel Logging: Wenn ein Team ein zentrales System für alle betreibt, dann sind alle anderen sorgenfrei: Datenvolumen, Logging Spikes etc.
Empfehlung: Den zentralen Loggingserver restriktiv auf den Use Case Support auslegen.

+++?image=images/tracking.png&size=auto 90%
Note:
Tracking-Integration ist in einem Webshop Makroarchitektur. Anforderungen müssen teamübergreifend erarbeitet werden, dann in jedes Team gereicht und umgesetzt werden.

+++?image=images/infrastructure.jpg
Note:
Wer baut und betreibt solche Infrastruktur?
Git-Repository, Kubernetes-Cluster, ...
Beispiel git-Repo: Wenn der von einem Team betrieben wird, ist das nicht deren Fokus, es leiden Upgrades/Security-Patches/Innovation.
Empfehlung: Infrastructure as Code-Rezepte erstellen und teilen, die leicht angepasst werden können. Open Source Community Lifestyle: Merge Request, Fork
separate Teams haben keinen direkten Kontakt zum Kunden, da müsste man Kunde anders definieren.

+++?image=images/gilden_.jpg&size=auto 90%
Note:
Wie schafft man Synergien über Teams hinweg?
Organisations-Maßnahme: Gilden bilden, ähnlich zu Matrix-Organisation, nur ohne Lead ausserhalb der Teams. Betriebsverantwortung!

---?image=images/fazit_.jpg
# Fazit
* Pattern für skalierbare, schnelle Softwareentwicklung
  * Wartbarkeit und Ersetzbarkeit wird erhöht
  * Verteilung wird möglich
* Hat sich in mehreren Projekten bewährt
  * Lernen aus den Erfahrungen, die es schon gibt!

Note:
Organisationsstruktur ist nur eine Hilfe, genau wie Agilität, Passt nicht in Struktur / ist nicht in meiner Verantwortung ist keine gute Antwort (Denken hilft)

+++?image=images/wer.jpg




+++
<!-- .slide: data-background="#9B3036" style="text-align: left; font-size: 0.6em;"-->
# Related stuff

- [Ralf Wirdemann, Johannes Mainusch, Scrum mit User Stories, Kapitel 12 "SCRUM@OTTO"](http://www.hanser-fachbuch.de/buch/Scrum+mit+User+Stories/9783446450523)
<!-- .element: style="color: white;" -->
- [Dr. John Kotter, Accelerate! The Evolution of the 21st Century Organization](https://www.youtube.com/watch?v=Pc7EVXnF2aI)
<!-- .element: style="color: white;" -->
- [Johannes Mainusch, "otto.de – wie die Titanic den Eisberg verfehlte"](https://www.heise.de/developer/artikel/Johannes-Mainusch-otto-de-wie-die-Titanic-den-Eisberg-verfehlte-3491223.html)
<!-- .element: style="color: white;" -->
- [Johannes Mainusch, Manage Chaos](https://gitpitch.com/kommitment/verticals/master?grs=bitbucket&p=p-intro)
<!-- .element: style="color: white;" -->
- [2018-02-05 Workshop Doku](https://drive.google.com/drive/folders/0Bzr9vgG2NdI0U0tjWkszd1dUNWc?usp=sharing)
<!-- .element: style="color: white;" -->
