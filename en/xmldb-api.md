<h3>XML</h3><br>

<h4>Create safe xml data. Removes dangerous characters for string.</h4><br>

<pre class="prettyprint">$xml_safe = XML::safe($xml_unsafe);</pre>

<br><h4>Get XML file</h4><br>

<pre class="prettyprint">$xml_file = XML::loadFile('path/to/file.xml');</pre>



<br><h3>DB</h3><br>



<h4>Create new database</h4><br>

<pre class="prettyprint">DB::create('db_name');</pre>



<br><h4>Drop database</h4><br>

<pre class="prettyprint">DB::drop('db_name');</pre>





<br><h3>Table</h3><br>



<h4>Table construct</h4><br>

<pre class="prettyprint">$users = new Table('table_name');</pre>



<br><h4>Create new table</h4><br>

<pre class="prettyprint">Table::create('table_name', array('field1', 'field2'));</pre>



<br><h4>Delete table</h4><br>

<pre class="prettyprint">Table::drop('table_name');</pre>



<br><h4>Get table</h4><br>

<pre class="prettyprint">$table = Table::get('table_name');</pre>



<br><h4>Get information about table</h4><br>

<pre class="prettyprint">var_dump($users->info());</pre>



<br><h4>Get table fields</h4><br>

<pre class="prettyprint">var_dump($users->fields());</pre>



<br><h4>Add new field</h4><br>

<pre class="prettyprint">$users->addField('test');</pre>



<br><h4>Delete field</h4><br>

<pre class="prettyprint">$users->deleteField('test');</pre>



<br><h4>Add new record</h4><br>

<pre class="prettyprint">$users->insert(array('login'=>'admin', 'password'=>'pass'));</pre>



<br><h4>Select record(s) in table</h4><br>

<pre class="prettyprint">

$records = $users->select('[id=2]');

$records = $users->select(null, 'all');

$records = $users->select(null, 'all', null, array('login'));

$records = $users->select(null, 2, 1);

</pre>



<br><h4>Delete current record in table</h4><br>

<pre class="prettyprint">$users->delete(2);</pre>



<br><h4>Delete with xPath query record in xml file</h4><br>

<pre class="prettyprint">$users->deleteWhere('[id=2]');</pre>



<br><h4>Update record with xPath query in XML file</h4><br>

<pre class="prettyprint">$users->updateWhere('[id=2]', array('login'=>'Admin', 'password'=>'new pass'));</pre>



<br><h4>Update current record in table</h4><br>

<pre class="prettyprint">$users->update(1, array('login'=>'Admin','password'=>'new pass'));</pre>



<br><h4>Get last record id</h4><br>

<pre class="prettyprint">echo $users->lastId();</pre>



<br><h4>Get count of records</h4><br>

<pre class="prettyprint">echo $users->count();</pre>
