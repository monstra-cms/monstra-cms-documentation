<p>The Options API is a simple and standardized way of storing data in the database. The Options API makes it easy to create, access, update, and delete those options. All the data is being stored in the options.table.xml under a given custom name.</p>

<br>

<h3>Add new option</h3>

<pre class="prettyprint">
Option::add('pages_limit', 10);
Option::add(array('pages_count' => 10, 'pages_default' => 'home'));
</pre>

<br>

<h3>Update option value</h3>

<pre class="prettyprint">
Option::update('pages_limit', 12);
Option::update(array('pages_count' => 10, 'pages_default' => 'home'));
</pre>

<br>

<h3>Get option value</h3>

<pre class="prettyprint">
$pages_limit = Option::get('pages_limit');
if ($pages_limit == '10') {
    // do something...
}
</pre>

<br>

<h3>Check if option exist</h3>

<pre class="prettyprint">
if (Option::exists('pages_limit')) {
    // do something...        
}
</pre>

<br>

<h3>Delete option</h3>

<pre class="prettyprint">
Option::delete('pages_limit');
</pre>
