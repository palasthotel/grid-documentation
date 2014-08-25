//version 1.0

#Glossar
---

###Container
Grid unterteilt in Elemente, die frei platziert und konfiguriert werden können. Diese Elemente nennen sich *Container*. Sie setzen sich zusammen aus einer vorher festgelegten Anzahl von Slots, die mit Content gefüllt werden können. <br />
Container können *Sidebars* unterstützen.

<br />

### Slots
Die Plätze eines *Containers*, in die *Content-Boxen* gesetzt werden können, nennen sich *Slots*.

<br />

###Boxen
Unter *Box* versteht man eines der Elemente, mit denen die *Containerslots* belegt werden können. Eine Box kann statischen Inhalt in Form eines einfachen Texts, eines Videos, eines Soundcloud Links oder einer Mediabox (kann mit Bildern gefüllt werden) enthalten, oder eine nicht-statische Liste von Inhalten, die eine festgelegte Anzahl von Posts anzeigt.

<br />

### Sidebar
Eine *Sidebar* ist ein statischer *Container*, der am Rand einer Seite entlangläuft. Sie kann allen üblichen *Boxen* gefüllt werden. In der *Containerfabrik* besitzen Sidebars die festgelegte Breite von 1/3.

<br />

###Containerfabrik
Sollte die Standardauswahl von *Containern* zum Bau des eigenen Rasters im Grid nicht ausreichen, ist es möglich, in der Containerfabrik individuelle Container zu erstellen. Die Containerfabrik ist im Admin Bereich des eigenen Wordpress-Blogs zu finden unter `Tools>Grid Container`.

<br />

###Identifier
Der *Identifier* ist die Beschreibung eines *Containers* in der *Containerfabrik*. Sie setzt sich zusammen aus einem Buchstaben, der den Typ des Containers kennzeichnet (`c` steht für Container,  `s`steht für *Sidebars*) , gefolgt von einer Reihe von Brüchen, die die Containerslots darstellen. `0`lässt freien Platz im Container für Sidebars, welche standardmäßig eine Breite von 1/3 besitzen.

<br />

###Denominator
Die Brüche, welche die Slots darstellen, die einen Container unterteilen, müssen alle denselben Nenner besitzen. Der *Denominator* legt diesen gemeinsamen Nenner fest.

<br />

###Stages
Die Veränderungen einer Seite durch das Grid werden es gültig und gespeichert, sobald der Nutzer auf `Publish` klickt. Frühere Versionen der Seite, genannt *Stages*, können im Grid unter "Revisions" gefunden werden.

<br />

###Grid Privileges
Da viele Seiten von mehreren Mitarbeitern gleichzeitig bearbeitet werden, die nicht nur unterschiedliche Aufgaben wahrnehmen sondern auch verschiedene Rechte zur Bearbeitung besitzen, ermöglicht Grid das Vergeben von *Privilegien*.
Die Einstellungen dazu sind im Administratorbereich unter `Tools>Grid Privileges` zu finden. 

<br />

###Grid Styles
Um eine Seite weitestgehend individualisieren zu können, ist es manchmal nötig, das Aussehen einzelner Elemente anzupassen. Grid bietet mithilfe der *Grid Styles* die Möglichkeit, verschiedene Stile festzulegen, die anschließend jedem Container verliehen werden können. <br />
Das Menü zum Erstellen eigener Stile findet sich im Administratorbereich unter `Tools>Grid Styles`. 
<br />
Zum Stylen eines solchen Stils sind grundlegende CSS-Kenntnisse nötig.
