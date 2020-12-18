## Постраничный вывод массива в PHP
Подробное описание на [Snipp.ru](https://snipp.ru/php/paginator-array).

#### Использование класса
```php
$prods = array(
	array(
		'name'  => 'Товар №1',
		'price' => '5100',
		'img'   => '1.jpg',
	),
	array(
		'name'  => 'Товар №2',
		'price' => '5100',
		'img'   => '2.jpg',
	),
	...
	array(
		'name'  => 'Товар №100',
		'price' => '5100',
		'img'   => '100.jpg',
	)
);

require_once('ArrayPaginator.php');

$peger = new ArrayPaginator('https://example.com/', 10); 
$items = $peger->getItems($prods);
 
/* Заголовок или title страницы */
echo '<h1>Зонты' . $peger->getTitle() . '</h1>';
 
/* Инфо о текущей странице */
echo '<p>Страница ' . $peger->page . ' из ' . $peger->amt . '</p>';	
 
/* Вывод текста только на первой странице */
if ($peger->page == 1) {
	echo '<p>Описание на первой странице</p>';
}
?>
 
<div class="prod-list">
	<?php foreach ($items as $row): ?>
	<div class="prod-item">
		<div class="prod-item-img">
			<a href="#"><img src="/img/<?php echo $row['img']; ?>" alt=""></a>			
		</div>
		<div class="prod-item-name">
			<a href="#"><?php echo $row['name']; ?></a>			
		</div>
		<div class="prod-item-price">
			<?php echo $row['price']; ?> р.
		</div>	
		<div class="prod-item-btn">
			<a href="#">Купить</a>
		</div>
	</div>
	<?php endforeach; ?>
</div>
 
<?php echo $peger->display; ?>

```
