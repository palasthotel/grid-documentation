//version 1.0

#Grid Styles
---

Um eine Seite weitestgehend individualisieren zu können, ist es manchmal nötig, das Aussehen einzelner Elemente anzupassen. Grid bietet mithilfe der *Grid Styles* die Möglichkeit, verschiedene Stile festzulegen, die anschließend jedem Container verliehen werden können. <br />
Das Menü zum Erstellen eigener Stile findet sich im Administratorbereich unter `Tools>Grid Styles`. Zum Stylen eines solchen Stils sind grundlegende CSS-Kenntnisse nötig.

##Erstellen und Löschen eines Stils
Um die Liste vorhandener Stile einzusehen oder eigene anzulegen, navigiere man in das *Grid Styles* Menü. Um einen neuen Stil zu erstellen, trägt man unter *Style* eine Bezeichnung oder Kurzbeschreibung ein, die später der Identifizierung des Stils in den Containereigenschaften dient. Unter *Slug* gibt man anschließend einen Namen für den Stil an (**Achtung**: Keine Leerzeichen, *Slug* wird später zu der CSS-Klasse des Stils). Die Eingabe wird anschließend mit einem Klick auf `Senden` bestätigt. <br />
Gelöscht wird ein Stil mit einem einfach Klick auf *Delete* neben dem entsprechenden Stil.

##Stylen
Das Editieren eines Styles ist entweder mit einem beliebigen Texteditor oder dem Wordpress eigenen Editor  im Administratorbereich unter `Appearance>Editor`. In beiden Fällen wird die `style.css` im Theme-Verzeichnis (`../wordpress/wp-content/themes/deinTheme/style.css`) bearbeitet. <br />
Dort kann nun an einer beliebigen Stelle ein Eintrag der Form `.deinSlug { }` eingetragen werden. Zwischen den {`  `} kann nun gestyled werden. <br />
Nach dem Abspeichern der Datei ist das Stylen abgeschlossen. Nun kann im Grid unter `Options>Edit` einem Container oder einer Box im *Containerstyle*-Dropdownmenü der gewünschte Stil zugewiesen werden. Mit dem nächsten Klick auf *Publish* ist das Styling des Containers abgeschlossen.
