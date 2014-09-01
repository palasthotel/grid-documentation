#Build

---

Die *Build*-Funktion rendert eine Box im Frontend. Hier wird beschrieben, was die Box tut. Sie ist immer in eine *if* und *else* Abfrage aufgeteilt, die feststellt, ob der Nutzer sich gerade im Editor Modus oder im Frontend befindet. In ersterem Fall liefert die Box ihren Namen an das Menü, in letzterem Fall wird die Box gerendert.

##Syntax

<pre>

public function build($editmode) {
	if($editmode) {
		return 'officialBoxName';						//Backend
	}
	else {
		insert function syntax here;					//Frontend
	}
}

</pre>
