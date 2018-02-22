



















---?image=https://raw.githubusercontent.com/ahojsenn/assets/master/img/_mandelbrot01.png
# Vertikale Organisation
- da muss sich was um 90° drehen im Kopf!
<!-- .element: style="font-size: 3em; color: orange"-->
Wer hat hier eigentlich den Hut auf?
+++?image=https://i.ytimg.com/vi/rhU9_TbABvw/maxresdefault.jpg
Ole Langbehn
Johannes Mainusch
+++?image=images/profilbild.jpg&size=auto 90%

---?image=images/zebra.png&size=auto 90%
Note:
Querstreifen machen dick. Und wenn man viel zu dick ist, wird man langsam und träge.

+++?image=https://raw.githubusercontent.com/ahojsenn/assets/master/img/FirmaReorga01.jpg
Note:
Übertrag auf Dev-Teams: Spezialisten-Teams (Frontend, Backend, Operations, Data Science, ...) sind schlecht.
Eigentlich mehrere Teams in einem (Scrum Smell: PO muss alle Spezialisten auslasten)
Gegenbewegungen: DevOps, Cross Functional Teams

+++
# TODO: Cloud of people
Note:
Selbst wenn man z.B. ein cross functional team hat, skaliert das bei großen Aufgaben nicht gut.
Kommunikation, Anzahl theoretische Beziehungen, nicht schlagkräftig.
Was macht man dann? Mehrere Teams. Und welchen Schnitt wählt man dann?
+++?image=https://raw.githubusercontent.com/ahojsenn/assets/master/img/FirmaReorga01.jpg
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

+++
# TODO: Customer Journey
suchen oder entdecken, bewerten, kaufen, prüfen
Note:
Gelöst: Die meisten Use-Cases/Feature Requests berühren nur ein Team. Abteilungen haben ein Dev-Team als Ansprechpartner.

+++?image=https://raw.githubusercontent.com/ahojsenn/assets/master/img/vertikaleKomponenten.png
Note:
Andere Kultur: Jedes Team managt Produkt, Technik, Organisation selbst.
Konzept Triade bei Otto.
Geschwindigkeit durch Parallelisierung, trotzdem kleine, flexible Teams.

---
# Vertikalisierung, how?

+++
# TODO: Shared nothing
Note:
Jedes Team hat eigene Infrastruktur, trifft eigene Technologieentscheidungen (Sprache, Datenbank). Analog zum DDD hat jedes Team seine Domain mit seinen Fachobjekten (Bei Kaufen hat ein Kunde Adressen, bei Entdecken stattdessen einen Clickstream)
Es gibt dennoch übergreifende Aspekte, die zu sharing führen.
+++?image=https://raw.githubusercontent.com/ahojsenn/assets/master/img/DJ-MikroMakroArch.jpg
Note:
Es folgen ein paar Makroarchitektur-Klassiker

+++?image=https://raw.githubusercontent.com/ahojsenn/assets/master/img/VertikaleIntegration.png
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

+++?image=https://raw.githubusercontent.com/ahojsenn/assets/master/img/VertikaleIntegration.png
Note:
Datenaustausch:
Service Discovery z.B. über JSON Home (Endpunkte können zur Laufzeit geändert werden)
Datenaustausch bei Breuninger asynchron über REST, Multipart.
Wichtig: Resilienz, Stabilität. Schon unterstützt durch asynchrone Kommunikation. Bei Implementierung von Schnittstellen immer auch an den Schlechtfall denken. Alte Daten sind besser als keine Daten. Entschuldigungen sind besser als Exceptions.
Datendesign: Beispiel Preise: mehrere mit Startdatum.
Rückwärtskompatibilität.
Schemata: Muss nicht, kann aber helfen.
CDC-Tests als Alternative.
Was wären Alternativen?
Bei Realtime-Anforderung: Kein Messagebus, sondern WebSockets.
Generell: RFCs/Standards statt Technologien. Beispiel GKH media types
Beispiel: Cassandra als zentrale DB.

+++
# TODO: Monitoring & Logging
Note:
Anforderung von außen könnte sein: Zentrales System für Einsicht von Monitoring & Logging.
Pitfall Beispiel Logging: Wenn ein Team ein zentrales System für alle betreibt, dann sind alle anderen sorgenfrei: Datenvolumen, Logging Spikes etc.
Empfehlung: Den zentralen Loggingserver restriktiv auf den Use Case Support auslegen.

+++?image=images/tracking.png
Note:
Tracking-Integration ist in einem Webshop Makroarchitektur. Anforderungen müssen teamübergreifend erarbeitet werden, dann in jedes Team gereicht und umgesetzt werden.

+++?image=images/infrastructure.jpg
Note:
Wer baut und betreibt solche Infrastruktur?
Git-Repository, Kubernetes-Cluster, ...
Beispiel git-Repo: Wenn der von einem Team betrieben wird, ist das nicht deren Fokus, es leiden Upgrades/Security-Patches/Innovation.
Empfehlung: Infrastructure as Code-Rezepte erstellen und teilen, die leicht angepasst werden können. Open Source Community Lifestyle: Merge Request, Fork
separate Teams haben keinen direkten Kontakt zum Kunden, da müsste man Kunde anders definieren.

+++
# TODO: reinventing the wheel
Wie schafft man Synergien über Teams hinweg?
Organisations-Maßnahme: Gilden bilden, ähnlich zu Matrix-Organisation, nur ohne Lead ausserhalb der Teams. Betriebsverantwortung!

---?image=images/fazit.jpg
# Fazit
* Tool zum Managen von Größe/Komplexität
** Haste keine Komplexität, lass es! (Keep it simple)
* Nur ein Tool, wie z.B. Agile
** Wenn das Tool mal nicht passt, hilft Denken & Tweaken!
* Hat sich in mehreren Projekten bewährt
** Lernen aus den Erfahrungen, die es schon gibt!


Note:
Organisationststruktur ist nur eine Hilfe, genau wie Agilität, Passt nicht in Struktur / ist nicht in meiner Verantwortung ist keine gute Antwort
Speaker notes: s drücken (Denken hilft)


---
# Verticals
+++?include=/p-verticals/PITCHME.md


---
# Warum Vertikale
--> Time to market

+++?image=https://raw.githubusercontent.com/ahojsenn/assets/master/img/_swArchitecture.jpg
    beware of black boxes
    beware of monoliths
<!-- .element: class="fragment fade-out" style="font-size: 1em; color: #ff7700;" -->

+++?image=https://raw.githubusercontent.com/ahojsenn/assets/master/img/SW-Lebenszyklus01.png

+++
# Was passiert bei Vertikalisierung?

+++?image=https://raw.githubusercontent.com/ahojsenn/assets/master/img/FirmaReorga01.jpg

+++?image=https://raw.githubusercontent.com/ahojsenn/assets/master/img/FirmaReorga02.jpg

+++?image=https://raw.githubusercontent.com/ahojsenn/assets/master/img/TeamSplitVertical.png

+++?image=https://raw.githubusercontent.com/ahojsenn/assets/master/img/DJ-MikroMakroArch.jpg



---
# Fazit

- Vertikslisierung ist cool, wenns groß wird
- frühzeitig vertiakl denken

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


+++
<!-- .slide: data-background="#9B3036" -->

[![kommitment][1]][2]
[1]: ttps://raw.githubusercontent.com/ahojsenn/assets/master/img/kommitment.png
[2]: http://www.kommitment.biz
<!-- .element: style="border: 0px !important;" -->
