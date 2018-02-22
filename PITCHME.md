



















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

+++?image=https://raw.githubusercontent.com/ahojsenn/assets/master/img/FirmaReorga01.jpg
Note:
Wir schneiden vertikal. Das ist das Hauptprinzip der Vertikalisierung

---
# Vertikalisierung, what?

+++?image=images/schneiden.jpg
Note:
Wie schneiden wir die Teams?









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
# Oles Content

+++
# DEVS VS. OPS - KLASSISCHES SETUP
- Devs und Ops in zwei Org-Einheiten.
- 2 Projekte/Planungsstände, dadurch Wartezeit bei Abhängigkeiten Kostenstellen, Budgetstreits
- Kommunikationskette Linie (hoch-quer-runter) mit entsprechenden Kommunikationsstörungen

+++
# KLASSISCHE STEREOTYPEN

+++
# DER DEV HASST DIE OPSLER
- Jede Änderung dauert (gefühlt) ewig (Kommunikation, Erstellung der Anforderungsdokumente, Prozesse, getrennte Priorisierung der Backlogs, fehlende Transparenz über Workloads/Workitems)
- Opsler bauen an meinen -Anforderungen vorbei und bauen eigene Anforderungen ein (Beispiel Kubernetes-Cluster)
- Ich bekomme den Jahresbonus nur, wenn wir bis Weihnachten noch 4 live-deployments schaffen.

+++
# DER OPSLER HASST DIE DEVS
- Die kommen immer mit Spezialanforderungen, sehen nicht das große Ganze. Die Anforderungen der Dev-Teams widersprechen sich teilweise. Wenn ich dann eine generische Lösung baue, die allen weiterhelfen sollte, sind sie unglücklich. Bitte, Danke.
- Wieso bauen die eigentlich immer so komplizierte Sachen? Wenn die mal verstehen würden, was ZFS für tolle Deduplikation und Snapshotting hat, dann könnte man so viele Ressourcen sparen. Ich muss die Kontrolle über die Storage holen, und das als Service anbieten, sonst haben wir echte Probleme.
- die machen 15.000 LOC Java code, wo es 50 Zeilen bash auch tun
- Entwickler machen immer alles kaputt und wollen dann mehr Server
- root Rechte auf der shell anfordern und nicht wissen, was ein crontab ist...
- mir wächst immer ein Pelz auf dem Rücken, wenn wieder einer kommt und mir stolz erzählt, dass er nun keine Firewall-Freischaltung mehr braucht, weil er ssh-port- forwarding irgendwo eingebaut hat.
- neulich habe ich erst wieder zwei Passworte in einer Property-Datei gefunden...
- ich bekomme meinen Jahresbonus nur, wenn wir 99,995% Verfügbarkeit erreichen.

+++
# ZUSAMMEN ARBEITEN
- Nach der Klassik die Moderne, z.B. nach Scrum: Opsler und Devs bilden interdisziplinäre Teams, planen und arbeiten gemeinsam. Ein Backlog. Probleme:
- Bus Factor (1 Opsler ist nicht genug)
- Aufgrund alter Strukturen unterschiedliche Chefs, Kostenstellen, - Ziele.
- Dem Spezialisten (Opsler) fehlt Austausch zu seinen Aufgaben

+++
# hier weiter machen...



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
