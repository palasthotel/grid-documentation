#Editor Widgets

---

Eine Box kann mit verschiedenen Formen von Inhalten gefüllt werden. In der *Content Structure*-Funktion (siehe "Content Structure & Konstruktor") wird festgelegt, welche Typen von Inhalt im Editmodus zur Verfügung stehen. Die einzelnen Input Typen nennen sich "Editor Widgets". <br />
Die Editor Widgets sind zu finden unter `wp-content/plugins/grid-wordpress/lib/js/app/views/EditorWidgets`.

<br />
###Liste möglicher Editor Widgets
+ `autocomplete`: Textfeld mit Autocomplete. Autocomplete benötigt eine eigens geschriebene Funktion "performElementSearch", die ihm Inhalte liefert.
+ `autocomplete_with_links`:  Textfeld mit Autocomplete. Liefert Autocompletes  als Links. Autocomplete benötigt eine eigens geschriebene Funktion "performElementSearch", die ihm Inhalte liefert.
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

##In detail

---

###Autocomplete
Das Autocomplete-Widget führt für jede neue Eingabe *performElementSearch* aus, das ihm ein Array aus Keys mit zugehörigen Values an das Javascript liefert. performElementSearch muss selbst programmiert werden, damit Autocomplete weiß, wo es wonach suchen soll. Desweiteren benötigt das Widget die *getElementValue*-Funktion, die später mithilfe des durch getElementSearch gespeicherten Keys (=id) diesem wieder seinen Titel zuweisen kann.

**Beispiel-Syntax**
<pre>
public function performElementSearch( $key, $querystr ) {
  if($key!='postid') {
   return array( array( 'key' => -1, 'value' => 'invalid key' ) );
  }
  $results = array();
  $sidebar_type = get_option( 'grid_sidebar_post_type', 'sidebar' );
  $count = wp_count_posts( $sidebar_type );
  // START of WordPress Loop
  $query = new WP_Query( array( 'post_type' => $sidebar_type, 'posts_per_page' => $count->publish ) );
  $i = 0;
  while ( $query->have_posts() && $i < 15 ) {
   $i++;
   $query->the_post();
   $post = get_post();
   if ( is_numeric ( strpos ( mb_strtolower( $post->post_title, 'UTF-8' ), mb_strtolower( $querystr, 'UTF-8' ) ) ) ) {
    $results[] = array( 'key' => $post->ID, 'value' => $post->post_title);
   }
  }
  wp_reset_postdata();
  return $results;
  // END of WordPress Loop
 }
</pre>


<br />
###Autocomplete with links
Das Autocomplete-With-Links-Widget verhält sich wie ein Autocomplete mit zwei zusätzlichen URLs, die im Edit Mode unter dem Autocomplete-Textfeld erscheinen. Dabei handelt es sich um eine vom Key des ausgewählten Elements abhängige URL und eine statische URL. Wenn nur einer oder keiner der beiden Links gewünscht ist, kann der Wert dieses Links leer gelassen werden.

**Beispiel-Syntax:**
<pre>
url="/node/%/grid"		// %=key, ermöglicht vom key abhängige Verlinkung
linktext="Hier steht ein Text"		//Text des Links
emptyurl:"http://test.sample"		//Statischer Link, beispielsweise zum erstellen einer 
								neuen Sidebar,	wenn der in der Suche eingegebene 
								Name noch nicht existiert 
emptylinktext:"Hier steht ein Text"		//Text des statischen Links
</pre>

<br />
###Select
Select benötigt den Zusatz *Selections* vom Typ Array, der ihm seine Auswahlmöglichkeiten liefert. Das Array muss mehrere Einträge enthalten, die jeweils einen `key`und einen `text`zuweisen.

**Beispiel Syntax:**
<pre>
array(
    'key' => 'viewmode',
    'type' => 'select',
    'label' => t( 'Viewmode' ),
    'selections' => array( array( 'key' => 'excerpt', 'text' => 'Anriss' ), array( 'key' => 'full', 'text' => 'Voll' ) ),
   ),		//bietet die Auswahlmöglichkeiten "Anriss" und "Voll"
</pre>

<br />
###List
List enthält eine eigene contentStructure in die andere Widgets gesetzt werden können. List selbst speichert keine Werte seiner Kinder. Bei der Verwendung einer List muss ein leeres Array im Konstruktor der Box angelegt werden.

**Beispiel-Syntax:**
<pre>
public function contentStructure() {
	return array(
		array('key' => 'list',
			'label' => 'Name',
			'contentstructure'=>array(
								array('key'=>'test','type'=>'text','label'=>'listentext'),
			),
			'type'=>'list',
		));
}
</pre>

<br />
###File-upload
File-Upload benötigt den Zusatz `upload path`, mit dem ein Endpoint definiert wird. In Drupal liegt dieser Endpoint standardmäßig bei `/grid_file_endpoint`
Das Widget funktioniert vorerst nur für Drupal, WordPress würde das manuelle Anlegen eines Endpoints vorraussetzen. Des weiteren benötigt File-Upload die *performFileUpload*-Funktion, die die Datei nach Erreichen des Endpoints abspeichert.

**Beispiel-Syntax:**
<pre>
public function performFileUpload($key,$path,$original_file)
{
	if($key != 'fileid')
		return FALSE
		$content=file_get_contents($path);		//bildinformationen werden in $content gespeichert
		$path="public://grid/".date("Y/m/d")."/";		//speicherpfad, optimiert für kleine ordner
		file_prepare_directory($path,FILE_CREATE_DIRECTORY);	//wenn es pfad noch nicht gibt: erstellen
		$file=file_save_data($content,$path,$original_file); //speichert datei in dem festgelegten pfad
		return $file->fid; 	//liefert die datei-id
}
</pre>

Die Box kann die Datei anschließend rendern, indem es die von performFileUpload gelieferte ID verwendet.



<br />
###Mediaselect
Das Mediaselect-Widget ist ein WordPress eigenes Widget, dass Dateien aus der WordPress Mediabibliothek zu verwenden. Dazu wird zunächst eine File-ID-Standardklasse benötigt, die im Konstruktor initialisiert werden muss, um die Daten der geladenen Datei zu speichern.
**Syntax:**
<pre>
public function __construct() {
	$this->content = new StdClass();
	$this->content->fileid = new StdClass();
	$this->content->fileid->id = ' ';
	$this->content->fileid->size = ' ';
}
</pre>

Die Daten der Datei werden in der build-Funktion der Box mithilfe von WordPress-eigenen Funktionen eingeholt, um das Medium zu rendern.
So ist es möglich, mithilfe von
<pre>
$metadata = wp_get_attachment_metadata($this->content->fileid->id);
</pre>
die ID zuzuweisen, wie auch mit
<pre>
$img_tag = wp_get_attachment_image($this->content->fileid->id, $this->content->fileid->size);
</pre>
ein Thumbnail. <br />
Momentan ist die Anwendung von Mediaselect nur für Bilder möglich. Bildgrößen bekommt das Widget ebenfalls von WordPress geliefert.
