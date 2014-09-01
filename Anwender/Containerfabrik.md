//version 1.0

#Containerfabrik
---

>Sollte die Standardauswahl von Containern zum Bau des eigenen Rasters im Grid nicht ausreichen, ist es möglich, in der Containerfabrik individuelle Container zu erstellen.

Die *Containerfabrik* ist im Admin Bereich des eigenen Wordpress-Blogs zu finden unter `Tools>Grid Container`. Standardmäßig sind bereits folgende Container installiert:

<br />

| Identifier | Sidebar-Support | Denominator | Slots (Relative Sizes) |
| --- | --- | --- | --- |
| i-0 | none | 0 | N/A (internal use) |
| c-1d1 | none | 1 | 1 (1) |
| c-1d3-1d3-1d3 | none | 3 | 3 (1,1,1) |
| c-2d3-1d3 | none | 3 |2 (2,1) |
| c-1d3-2d3	| none |	3 | 2 (1,2) |
| c-1d6-1d6-1d6-1d6-1d6-1d6 | none | 6 (1,1,1,1,1,1) |
| c-1d4-1d4-1d4-1d4 | none | 4 (1,1,1,1) |
| c-1d2-1d2 | none | 2 | 2 (1,1) |
| s-1d3-0 | places sidebar | 3 1 (1,Content) |
| s-0-1d3 | places sidebar | 3 1 (Content,1) |
| sc-1d3 | none | 3 | N/A | (internal use) |
| c-0-1d3-1d3 | left | 3 | 2 (Sidebar,1,1) |
| c-1d3-1d3-0 | right | 3 | 2 (1,1,Sidebar) |
| c-0-2d3 | left | 3 | 1 (Sidebar,2) |
| c-2d3-0 | right | 3 | 1 (2,Sidebar) |
| c-0-1d3-0 | both | 3 | 1 (Sidebar,1,Sidebar) |

<br />

* **Identifier**: Der Identifier ist die Beschreibung eines Containers. Sie setzt sich zusammen aus einem Buchstaben, der den Typ des Containers kennzeichnet (`c` steht für Container,  `s`steht für Sidebars) , gefolgt von einer Reihe von Brüchen, die die Containerslots darstellen. `0`lässt freien Platz im Container für Sidebars, welche standardmäßig eine Breite von 1/3 besitzen.
* **Sidebar-Support**: Der Sidebar-Support legt fest, ob der Container Sidebars unterstützt und wenn ja, wo diese angebracht werden sollen. Zur Auswahl stehen `none`, `left`und `right`. Sidebars besitzen hier das Attribut `places sidebar`.
* **Denominator**: Die Brüche, welche die Slots darstellen, die einen Container unterteilen, müssen alle denselben Nenner besitzen. Der Denominator legt diesen gemeinsamen Nenner fest.
* **Slots**: Setzt sich zusammen aus der Anzahl von Brüchen mit dem im Denominator festgelegten, gemeinsamen Nenner und einer Beschreibung des Aufbaus des Containers. So wird `c-2d3-0`beschrieben durch den Denominator `3` und die Slots-Beschreibung `1(2,Sidebar)`.

<br />

##Erstellen eines neuen Containers

Für das Erstellen eines Grid Containers wird zuerst festgelegt, ob und auf welcher Seite neben diesem später eine Sidebar platziert werden soll. Ist der *Sidebar-Support* nicht gewünscht, lasse man einfach den Standard `none`stehen.
Anschließend ist der *Denominator* zu wählen. Es ist dringend empfohlen, sich bereits von vorneherein über die Aufteilung der *Slots* des Containers im Klaren zu sein. Eben diese wird im nächsten Schritt festgelegt. Die Größen der *Slots* werden dabei als ganze Zahlen, getrennt durch ein Komma angegeben - diese Zahlen stellen später die Zähler der Brüche dar. An der Stelle, an der der *Sidebar-Support* gewünscht wurde, sollte eine `0`eingetragen werden.
Mit einem Klick auf `Create Container` wird der neue Container schließlich der Liste hinzugefügt und ist im Grid verfügbar.

**Wichtig**: Sidebars besitzen die festgelegte Größe von 1/3. Ist der *Sidebar-Support* eingeschaltet, ist es also nötig, für jede Sidebar 1/3 von der Gesamtgröße abzuziehen.
