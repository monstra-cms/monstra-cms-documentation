<h3>Plugin</h3><br>

<h4>Register new plugin in system.</h4><br>

<pre class="prettyprint">
Plugin::register( __FILE__,                    
                 __('Blog'),
                 __('Blog plugin'),  
                 '1.0.0',
                 'Awilum',               
                 'http://example.org/',
                 'blog');
</pre>

<br />

<h4>Get plugin admin.</h4><br>

<pre class="prettyprint">Plugin::admin('blog');</pre>

<br />

<h3>View</h3><br>

<h4>Create a new view object.</h4><br>

<pre class="prettyprint">
// Create new view object
$view = new View('blog/views/backend/index');

// Assign some new variables
$view->assign('msg', 'Some message...');

// Get view
$output = $view->render();

// Display view
echo $output;
</pre>

<br />

<h4>View factory.</h4><br>

<pre class="prettyprint">
// Create new view object, assign some variables
// and displays the rendered view in the browser.
View::factory('blog/views/backend/index')
   ->assign('msg', 'Some message...')
   ->display();
</pre>

<br />

<h4>Assign a view variable.</h4><br>

<pre class="prettyprint">
$view->assign('msg', 'Some message...');
</pre>

<br />

<h4>Include the view file and extracts the view variables before returning the generated output.</h4><br>

<pre class="prettyprint">
// Get view
$output = $view->render();

// Display output
echo $output;
</pre>

<br />

<h4>Displays the rendered view in the browser.</h4><br>

<pre class="prettyprint">
$view->display();
</pre>

<br />

<h3>I18n</h3><br>

<h4>Returns translation of a string. If no translation exists, the original will be returned. No are replaced.</h4><br>

<pre class="prettyprint">
$hello = I18n::find('Hello friends, my name is :name', 'namespace');
</pre>

<h4>Global Translation/internationalization function.</h4> Accepts an English string and returns its translation to the active system language. If the given string is not available in the current dictionary the original English string will be returned.<br><br>

<pre class="prettyprint">
// Display a translated message
echo __('Hello, world', 'namespace');

// With parameter replacement
echo __('Hello, :user', 'namespace', array(':user' => $username));
</pre>

<br />

<h3>Action</h3><br>



<h4>Hooks a function on to a specific action.</h4><br>

<pre class="prettyprint">
// Hooks a function "newLink" on to a "footer" action.
Action::add('footer', 'newLink', 10);

function newLink() {
   echo '<a href="#">My link</a>';
}     
</pre>

<br />

<h4>Run functions hooked on a specific action hook.</h4><br>

<pre class="prettyprint">
// Run functions hooked on a "footer" action hook.
Action::run('footer');
</pre>

<br />

<h3>Filter</h3><br>

<h4>Apply filters.</h4><br>

<pre class="prettyprint">
Filter::apply('content', $content);
</pre>

<br />

<h4>Add filter.</h4><br>

<pre class="prettyprint">
Filter::add('content', 'replacer');

function replacer($content) {
   return preg_replace(array('/\[b\](.*?)\[\/b\]/ms'), array('<strong>\1</strong>'), $content);
}
</pre>

<br />

<h3>Stylesheet</h3><br>

<h4>Add stylesheet</h4><br>

<pre class="prettyprint">
Stylesheet::add('path/to/my/stylesheet1.css');
Stylesheet::add('path/to/my/stylesheet2.css', 'frontend', 11);
Stylesheet::add('path/to/my/stylesheet3.css', 'backend',12);
</pre>

<br />

<h4>Minify, combine and load site stylesheet.</h4><br>

<pre class="prettyprint">
Stylesheet::load();
</pre>

<br />

<h3>Javascript</h3><br>

<h4>Add javascript</h4><br>

<pre class="prettyprint">
Javascript::add('path/to/my/script1.js');
Javascript::add('path/to/my/script2.js', 'frontend', 11);
Javascript::add('path/to/my/script3.js', 'backend', 12);
</pre>

<br />

<h4>Combine and load site javascript.</h4><br>

<pre class="prettyprint">
Javascript::load();
</pre>

<br />

<h3>Navigation</h3><br>

<h4>Add new item</h4><br>

<pre class="prettyprint">
// Add link for left navigation
Navigation::add(__('Blog'), 'content', 'blog', 11);

// Add link for top navigation
Navigation::add(__('View site'), 'top', 'http://site.com/', 11, Navigation::TOP, true);
</pre>

<br />

<h4>Draw items</h4><br>

<pre class="prettyprint">
Navigation::draw('content');
Navigation::draw('top', Navigation::TOP);
</pre>
