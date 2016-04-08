<p>The Shortcode API s a simple regex based parser that allows you to replace simple bbcode-like tags within a HTMLText or HTMLVarchar field when rendered into a content.</p><br>

<p>Examples of shortcode tags:</p>

<pre class="prettyprint">
{{shortcode}}
{{shortcode parameter="value"}}
</pre>

<p>Example of escaping shortcodes:</p>

<pre class="prettyprint">
{{{shortcode}}}
</pre>

<br>

<h3>Add new shortcode</h3>

<p>Your shorcode function:</p>

<pre class="prettyprint">
function returnSiteUrl() {
   return Option::get('siteurl');
}
</pre>

<p>Add shortcode {siteurl}</p>

<pre class="prettyprint">
Shortcode::add('siteurl', 'returnSiteUrl');
</pre>

<br>

<h3>Add new shortcode with Variables</h3>

<p>Your shorcode function:</p>

<pre class="prettyprint">
function foo($attributes) {
    // Extract
    extract($attributes);

    // text
    if (isset($text)) $text = $text; else $text = '';

    // return
    return $text;
}
</pre>



<p>Add shortcode {foo text="Hello World"}</p>

<pre class="prettyprint">
Shortcode::add('foo', 'foo');
</pre>

<p>Usage:</p>

<pre class="prettyprint">
{foo text="Hello World"}
</pre>

<p>Result:</p>

<pre>
Hello World
</pre>


<br>

<h3>Add new shortcode with Variables and Content</h3>

<p>Your shorcode function:</p>

<pre class="prettyprint">
function foo($attributes, $content) {
    // Extract
    extract($attributes);

    // text
    if (isset($color)) $color = $color; else $color = 'black';

    // return
    return '&lt;span style="color:'.$color.'"&gt;'.Filter::apply('content', $content).'&lt;/span&gt;';
}

</pre>

<p>Add shortcode {foo color="red"}</p>

<pre class="prettyprint">
Shortcode::add('foo', 'foo');
</pre>

<p>Usage:</p>

<pre class="prettyprint">
{foo color="red"}Hello World{/foo}
</pre>


<p>Result:</p>

<pre>
<span style="color:red">Hello World</span>
</pre>

<br>

<h3>Check if a shortcode has been registered.</h3>

<pre class="prettyprint">
if (Shortcode::exists('foo')) {
    // do something...
}
</pre>

<br>

<h3>Remove a specific registered shortcode.</h3>

<pre class="prettyprint">
Shortcode::delete('foo');
</pre>

<br>

<h3>Remove all registered shortcodes.</h3>

<pre class="prettyprint">
Shortcode::clear();
</pre>

<br>

<h3>Braces</h3>

<p>The shortcode parser does not accept braces within attributes. Thus the following will fail:</p>

<pre class="prettyprint">
{foo attribute="{Some value}"}Hello World{/foo}
</pre>
