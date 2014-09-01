#Content Structure

---

Die *Content Structure*-Funktion liefert ein Array, dass die *Editor Widgets* bestimmt, die eine Box im Edit Modus besitzt. Ihre Startwerte werden vom Konstruktor befüllt, daher ist es wichtig, jedem Eintrag des Arrays einen *Key* zu geben, der denselben Namen besitzt wie der zugehörige Aufruf des Konstruktors. <br />
Neben den eigenen Attributen besitzt eine Box die von der *Grid-Box* geerbten Standardattribute, die sie im Normalfall nicht überschreiben sollte.

###Liste der Grid-Box Standardattribute
Name | Interne Bezeichnung | Zweck
--- | --- | --- 
Title | `$title` | Titel der Box
Title-URL | `$titleurl` | Optionaler Titel-Link
Prolog | `$prolog` | Prolog Textareal
Content | `$content` | Primärer Inhalt
Epilog | `$epilog` | Epilog Textareal
Style | `$style` | Von der Box verwendeter Style
Readmore | `$readmore` | *Read more* Text
Readmore-URL | `$readmoreurl` |  Optionaler Link für den *read more* Text

<br />
Neben dem *Key* benötigt jeder Eintrag noch ein *Label*, einen *Typ* und unter Umständen einen *Typ Zusatz*. Das Label ist dabei lediglich die Überschrift des entsprechenden Feldes im Edit Modus. Der Typ bestimmt, welche Form von Input das Feld besitzt, wobei manche Typen, wie zB. *select* einen Zusatz benötigen. Für eine vollständige Liste von *Editor Widgets* siehe "Editor Widgets".
<br />
<br />
##Syntax des Box-Konstruktors#
<pre>

public function __construct() {
	$this->content = new Stdclass;					//Pflichtfeld
	$this->content->internName = Startwert;			//Setzt Startwert für EditorWidget
	$this->content->internName2 = Startwert2;
	.
	.
	.
}

</pre>

<br />
##Syntax der Content Structure
<pre>

public function contentStructure() {
	return array(
		array('key' => 'internName',		// Bezeichnung wie im Konstruktor
			'label' => 'shownName',		//Beliebiger Name, sollte beschreibend sein
			'select' => 'editorWidget',		//Siehe "Editor Widgets" für eine 
												komplette Liste der verfügbaren Typen
		),
		array('key' => 'internName',
			'label' => 'shownName',
			'select' => 'editorWidget',
		),
		.
		.
		.
	);
}

</pre>
