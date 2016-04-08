The Monstra error handler converts all errors to ErrorExceptions.<br>

This allows Monstra to display a error page that contains a lot more information than the standard PHP error pages when something bad happens.<br>

The error handler will also try to log the error.<br>

<br>

Note that error page with error information will be displayed if the <code>Monstra::$environment</code> is <code>Monstra::DEVELOPMENT</code>

<h3>Examples</h3>

Here's an example of what an error can look like in Monstra CMS:<br>

<img src="http://monstra.org/public/uploads/docs/error-handling.png" alt="error-handling" align="left" width="600" />
