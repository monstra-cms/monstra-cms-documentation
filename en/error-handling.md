The Monstra error handler converts all errors to ErrorExceptions.  
This allows Monstra to display a error page that contains a lot more information than the standard PHP error pages when something bad happens.  
The error handler will also try to log the error.

Note that error page with error information will be displayed if the `Monstra::$environment` is `Monstra::DEVELOPMENT`

### Examples

Here's an example of what an error can look like in Monstra CMS:
![Error handling](http://monstra.org/public/uploads/images/general/docs/error-handling.png)
