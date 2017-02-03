### XML данные и файлы

#### Создание безопасных xml данных. Удаление опастных символов из строки.

```php
$xml_safe = XML::safe($xml_unsafe);
```

#### Получение xml файла

```php
$xml_file = XML::loadFile('path/to/file.xml');
```


### DB База данных

#### Создание новой базы данных

```php
DB::create('db_name');
```

#### Удаление базы данных

```php
DB::drop('db_name');
```


### Таблицы

#### Новый объект таблицы

```php
$users = new Table('table_name');
```

#### Создание новой таблицы

```php
Table::create('table_name', array('field1', 'field2'));
```

#### Удаление таблицы

```php
Table::drop('table_name');
```

#### Получение таблицы

```php
$table = Table::get('table_name');
```

#### Получение информации о таблицы

```php
var_dump($users->info());
```

#### Получение полей таблицы

```php
var_dump($users->fields());
```

#### Добавление нового поля

```php
$users->addField('test');
```

#### Удаление поля

```php
$users->deleteField('test');
```

#### Добавление новой записи

```php
$users->insert(array('login'=>'admin', 'password'=>'pass'));
```

#### Выбрать запись(и) из таблицы

```php
$records = $users->select('[id=2]');
$records = $users->select(null, 'all');
$records = $users->select(null, 'all', null, array('login'));
$records = $users->select(null, 2, 1);
```

#### Удалить запись из таблицы по его id

```php
$users->delete(2);
```

#### Удаление записи используя запрос xPath

```php
$users->deleteWhere('[id=2]');
```

#### Обновление записи с применением запроса xPath

```php
$users->updateWhere('[id=2]', array('login'=>'Admin', 'password'=>'new pass'));
```

#### Обновление записи по его id

```php
$users->update(1, array('login'=>'Admin','password'=>'new pass'));
```

#### Получение id последней записи

```php
echo $users->lastId();
```

#### Получить количество записей в таблице

```php
echo $users->count();
```
