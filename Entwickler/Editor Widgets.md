#Editor Widgets

---

Eine Box kann mit verschiedenen Formen von Inhalten gefüllt werden. In der *Content Structure*-Funktion (siehe "Content Structure & Konstruktor") wird festgelegt, welche Typen von Inhalt im Editmodus zur Verfügung stehen. Die einzelnen Input Typen nennen sich "Editor Widgets". <br />
Die Editor Widgets sind zu finden unter `wp-content/plugins/grid-wordpress/lib/js/app/views/EditorWidgets`.

<br />
###Liste möglicher Editor Widgets
+ `autocomplete`: Textfeld mit Autocomplete. Autocomplete benötigt eine eigens geschriebene Funktion, die ihm Inhalte liefert.
+ `autocomplete_with_links`:  Textfeld mit Autocomplete. Liefert Autocompletes  als Links. Autocomplete benötigt eine eigens geschriebene Funktion, die ihm Inhalte liefert.
+ `checkbox`: Checkbox mit Beschriftung.
+ `file`: Ermöglicht Datei-Upload.
+ `hidden`: Textfeld, das weder im Back- noch im Frontend gerendert wird. Dient lediglich zur Übermittlung interner Daten.
+ `html`: Textareal, das html interpretiert und ausgibt.
+ `info`: Textfeld zur Dokumentation anderer Felder. Benötigt `value`.
+ `list`: Erzeugt Liste, benötigt als Zusatz eine eigene contentStructure.
+ `number`: Textfeld, dass nur Zahlen (int & float) akzeptiert. Kann per Klick um 1 erhöht/erniedrigt werden.
+ `select`: Dropdown Menü, benötigt den Zusatz `selections`, der mit einem Array gefüllt wird. *Select* bietet den Inhalt dieses Arrays zur Auswahl an.
+ `text`: Einfaches Textfeld, gibt Text 1:1 aus.
+ `textarea`: Skalierbares Textareal, gibt Text 1:1 aus.
+ `wp_mediaselect`: Ermöglicht die Auswahl von Dateien aus der Wordpress Mediathek. Nur in Wordpress enthalten.
