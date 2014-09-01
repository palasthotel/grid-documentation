#Meta Typen & Standardattribute

---

##Meta Typen
Die im Grid verfügbaren Boxen sind unterteilt in Kategorien, die Meta Typen genannt werden. Standardmäßig existieren die Meta Typen *Static Content*, *Lists*, *Reusable Boxes* und *Contents*. Für jeden von ihnen existiert eine Klasse, die die Kategorie im Grid Menü erstellt und eine weitere, von der die ihm zugehörigen Boxen erben, ohne dabei eine eigene Kategorie zu erzeugen. <br />
Die Meta Typen sind zu finden unter `wp-content/plugins/grid-wordpress/lib/classes`. Sie zeichnen sich dadurch aus, `isMetaType = TRUE`, einen `metaTitle` und eine `metaSearch` zu besitzen.

###Die Grid-Box
Die Mutter aller Meta Typen ist die *Grid-Box*. Sie enthält alle Standardattribute und-Funktionen, die für  das Grid benötigt werden. Alle Meta Typen erben von ihr und überschreiben Funktionen mit eigenem Inhalt.

<br />
##Boxen
Eine Box erbt von einem Metatypen, der die ihr zugehörige Kategorie darstellt. Sie überschreibt wenn nötig die geerbten Funktionen und Attribute mit eigenen Werten.

<br />
##Liste standardmäßiger Meta Types und ihren Boxen

###Static Content

* Html-Box

* Video-Box

* Soundcloud-Box

* Media-Box


<br />

###Lists
* List-Box

<br />

###Reusable Boxes
Liste aller als *reusable* markierten Boxen.

<br />

###Contents
Bietet Suche nach vorhandenen statischen Seiten, um diese als Box zu verwenden.
