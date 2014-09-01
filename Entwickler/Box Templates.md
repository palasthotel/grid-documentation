#Box Templates

---

Boxen bedienen sich Templates, die vom Theme oder dem Plugin gestellt werden (Hierarchie Theme > Plugin). Sie bestimmen Form und Aussehen der Boxen im Grid und im Frontend. Es wird zwischen CMS- und Grid-spezifischen Templates unterschieden. Template-Dateien müssen mit der Endung `.tpl.php` benannt werden.

**Beispiel 1 (WordPress spezifisch)**: Die Content-List-Box bedient sich der *post_content.tpl.php*, die ihr die Formatierung der einzelnen Posts liefert. Beim Rendern prüft die Box, ob das aktivierte Theme des Blogs eine *post_content.tpl.php* liefert, die das Aussehen der Posts definiert. Ist keine solche Datei vorhanden, greift die Box auf die Grid eigene Datei zu.

**post_content.tpl**:
<pre>
< h3>< ?php echo the_title(); ?>< /h3>
< ?php
if ( $this->content->viewmode == 'full' ) {
	echo the_content();
} elseif ( $this->content->viewmode == 'excerpt' ) {
	echo the_excerpt();
}
? >
</pre>
<br />

Die Grid eigenen Templates sind zu finden unter `plugins/grid-wordpress/core/classes/wordpress` (Wordpress spezifisch) und unter `plugins/grid-wordpress/lib/classes` (Allgemein).

<br />

**Beispiel 2 (Allgemein)**: Um den im Backend definierten Inhalt einer Box im Frontend auszugeben, nutzt Grid die *grid-box-box.tpl.php*. Sie schreibt dem Grid vor, in welcher Reihenfolge die einzelnen Inhalte der Box dargestellt werden und gibt ihnen html-Klassen, die es zum stylen oder gezielten Aufrufen nutzt.

**grid-box-box.tpl.php**:
<pre>
<div class="box<?php echo ($this->style)? " ".$this->style." ": " "; echo implode($this->classes," ")?>">
 <?php
 if ($this->title!="") { **// Wenn Titel nicht leer ist ...**
	  if ($this->titleurl !=""){ **// ... und die Titel URL nicht leer ist ...**
	  ?>
	 **// ... verwende den Titel und Titel-URL der Box als Überschrift mit Link**
		   < h3 class="b-title"><a href="<?php echo $this->titleurl?>"><? php echo $this->title?></a>< /h3>
	  < ?php }else{?> // **Andernfalls ...**
	  **// ... verwende den Titel der Box ohne Link als Überschrift**
	   < h3 class="b-title">< ?php echo $this->title?>< /h3>
	  < ?php }?>
 <  ?php }?>
 < div class="b-prolog"> // **Erstelle einen div mit Klasse "b-prolog" ...**
	  <  ?php echo $this->prolog ?> // **... und fülle ihn mit dem Prolog der Box**
 < /div> 
< ?php echo $content?> // **Gib anschließend den Content der Box wieder**
 < div class="b-epilog"> // **Erstelle einen div mit der Klasse "b-epilog" ...**
  < ?php echo $this->epilog?> // **... und fülle ihn mit dem Epilog der Box**
 < /div>
   < ?php
 if ($this->readmore!=""){?> // **Wenn Read more nicht leer ist ...**
 // **...gib einen Read more Link mit Klasse "b-readmore-link" an**
 < a href="<?php echo $this->readmoreurl?>" class="b-readmore-link"><?php echo $this->readmore?></a>
 < ?php }?>
 < /div>
</pre>
