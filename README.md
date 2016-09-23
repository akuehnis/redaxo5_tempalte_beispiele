# redaxo5_template_beispiele

## Artikel aufrufen und ausgeben
```php
<?php
$article_id = 3;
$clang_id   = 2;
$art = new rex_article_content($article_id, $clang_id);
if (null !== $art) {
    echo $art->getArticle();
}
?>
```
## Kategorie aufrufen
```php
<?php
$category_id = 3;
$clang_id    = 2;
$cat = rex_category::get($category_id, $clang_id);
?>
```

## Unterkatgorien der Kategorie
```php
<?php
$ignore_offlines = false;
$children = $cat->getChildren($ignore_offlines);
?>
```

## Artikel der Kategorie
```php
<?php
$ignore_offlines = false;
$children = $cat->getArticles($ignore_offlines);
?>
```

## Unternavigation ausgeben

Ausgabe einer Unternavigation ausgehend von der obersten Ebene des aktuellen Standorts
```php
<?php 
//Subnavigation
$cat = rex_category::get($this->getValue("category_id"));
$subnav_content = '';
$subnav_title = '';
if (null !== $cat) {
    $path = $cat->getPath();
    if ('|' != $path) {
        $a = explode('|', $path);
        if (!empty($a[1])) {
            $subnav_start_id = $a[1];
        } else {
            $subnav_start_id = 0;
        }
        $subnav = rex_navigation::factory(); 
        $subnav->setClasses(array('sub1', 'sub2'));
        $subnav_content = $subnav->get($subnav_start_id, 4 , true ,true);
        $root_cat = rex_category::get($subnav_start_id); 
        if (null !== $root_cat) {
            $subnav_title = $root_cat->getName();
       }
    }
}
if ('' != $subnav_content) {
    echo '<h6>'. $subnav_title.'</h6>';
    echo $subnav_content;
}
?>
```

