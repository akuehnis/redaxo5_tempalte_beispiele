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
