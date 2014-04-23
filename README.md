It's a quick and dirty snippet in order to add a markdown() function to Twig with Slim Framework via Parsedown by @erusev :
```php
<?php
require DIR_VENDORS . 'Parsedown/Parsedown.php';
[...]
$twig = $app->view()->getEnvironment();
 
$function = new Twig_SimpleFunction('markdown', function ($text) {
    $mkparser = new Parsedown();
    return $mkparser->text($text);
});

$twig->addFunction($function);
[...]
```

Now, in your template file/Twig file :
```html
{{ markdown(string)|raw }}
```

And voila!
