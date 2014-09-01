#Glossar

---

###Boxen
Unter *Box* versteht man eines der Elemente, mit denen die *Containerslots* belegt werden können. Eine Box kann statischen Inhalt in Form eines einfachen Texts, eines Videos, eines Soundcloud Links oder einer Mediabox (kann mit Bildern gefüllt werden) enthalten, oder eine nicht-statische Liste von Inhalten, die eine festgelegte Anzahl von Posts anzeigt.

<br />

###Die Build-Funktion
Die *Build*-Funktion rendert eine Box im Frontend. Hier wird beschrieben, was die Box tut. Sie ist immer in eine *if* und *else* Abfrage aufgeteilt, die feststellt, ob der Nutzer sich gerade im Editor Modus oder im Frontend befindet. In ersterem Fall liefert die Box ihren Namen an das Menü, in letzterem Fall wird die Box gerendert.

<br />

###Die Content-Structure-Funktion
Die *Content Structure*-Funktion liefert ein Array, dass die *Editor Widgets* bestimmt, die eine Box im Edit Modus besitzt. Ihre Startwerte werden vom Konstruktor befüllt, daher ist es wichtig, jedem Eintrag des Arrays einen *Key* zu geben, der denselben Namen besitzt wie der zugehörige Aufruf des Konstruktors. <br />
Neben den eigenen Attributen besitzt eine Box die von der *Grid-Box* geerbten Standardattribute, die sie im Normalfall nicht überschreiben sollte.

<br />

###Editor Widgets
Eine Box kann mit verschiedenen Formen von Inhalten gefüllt werden. In der *Content Structure*-Funktion (siehe "Content Structure & Konstruktor") wird festgelegt, welche Typen von Inhalt im Editmodus zur Verfügung stehen. Die einzelnen Input Typen nennen sich "Editor Widgets". <br />
Die Editor Widgets sind zu finden unter `wp-content/plugins/grid-wordpress/lib/js/app/views/EditorWidgets`. Für eine vollständige Liste vorgefertigter Widgets siehe *Editor Widgets*.

###Meta-Typen
Die im Grid verfügbaren Boxen sind unterteilt in Kategorien, die Meta Typen genannt werden. Standardmäßig existieren die Meta Typen *Static Content*, *Lists*, *Reusable Boxes* und *Contents*. Für jeden von ihnen existiert eine Klasse, die die Kategorie im Grid Menü erstellt und eine weitere, von der die ihm zugehörigen Boxen erben, ohne dabei eine eigene Kategorie zu erzeugen. <br />
Die Meta Typen sind zu finden unter `wp-content/plugins/grid-wordpress/lib/classes`. Sie zeichnen sich dadurch aus, `isMetaType = TRUE`, einen `metaTitle` und eine `metaSearch` zu besitzen.

<br />

###Templates
Boxen bedienen sich Templates, die vom Theme oder dem Plugin gestellt werden (Hierarchie Theme > Plugin). Sie bestimmen Form und Aussehen der Boxen im Grid und im Frontend. So nutzen beispielsweise Listen-Boxen die sogenannte *post_content.tpl.php*, um die Form ihrer aufgelisteten Posts zu bestimmen. Es wird zwischen CMS- und Grid-spezifischen Templates unterschieden. Template-Dateien müssen mit der Endung `.tpl.php` benannt werden.


