### XML

#### Create safe xml data. Removes dangerous characters for string.

```php
$xml_safe = XML::safe($xml_unsafe);
```

#### Get XML file

```php
$xml_file = XML::loadFile('path/to/file.xml');
```


### DB

#### Create new database

```php
DB::create('db_name');
```

#### Drop database

```php
DB::drop('db_name');
```


### Table

#### Table construct

```php
$users = new Table('table_name');
```

#### Create new table

```php
Table::create('table_name', array('field1', 'field2'));
```

#### Delete table

```php
Table::drop('table_name');
```

#### Get table

```php
$table = Table::get('table_name');
```

#### Get information about table

```php
var_dump($users->info());
```

#### Get table fields

```php
var_dump($users->fields());
```

#### Add new field

```php
$users->addField('test');
```

#### Delete field

```php
$users->deleteField('test');
```

#### Add new record

```php
$users->insert(array('login'=>'admin', 'password'=>'pass'));
```

#### Select record(s) in table

```php
$records = $users->select('[id=2]');
$records = $users->select(null, 'all');
$records = $users->select(null, 'all', null, array('login'));
$records = $users->select(null, 2, 1);
```

#### Delete current record in table

```php
$users->delete(2);
```

#### Delete with xPath query record in xml file

```php
$users->deleteWhere('[id=2]');
```

#### Update record with xPath query in XML file

```php
$users->updateWhere('[id=2]', array('login'=>'Admin', 'password'=>'new pass'));
```

#### Update current record in table

```php
$users->update(1, array('login'=>'Admin','password'=>'new pass'));
```

#### Get last record id

```php
echo $users->lastId();
```

#### Get count of records

```php
echo $users->count();
```
