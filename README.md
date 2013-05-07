This [Slim Framework](http://slimframework.com/) middleware will compile
[LESS CSS](http://lesscss.org) files on-the-fly using the
[`Assetic`](https://github.com/kriswallsmith/assetic) library. It supports
minification and caching, also via `Assetic`.

It will intercept requests for CSS files and attempt to find a corresponding
LESS file. If one is found, it will compile the file to CSS and serve it,
optionally saving the CSS to a filesystem cache. Inspired by
[`less.js-middleware`](https://github.com/emberfeather/less.js-middleware).

### Usage

* `src` - Directory to look for LESS files. __REQUIRED__
  Example: if `src` is set to `/path/to/public`, and a request for
  `http://mysite.com/css/style.css` is received, then it will look for a LESS
  file in `/path/to/public/css/style.less`.
* `cache` - Cache CSS file to filesystem. Default is `true`.
* `cache.dir` - Directory for the cached CSS file. Default is `src`.
* `minify` - Minify the CSS output. Default is `true`.
* `debug` - Send debug messages to Slim Logger. Default is `false`.

Example:

```php

use \Slim\Slim;
use \Slim\Middleware\Less;

$app = new Slim();
$app->add(new Less(array(
    'src' => '/path/to/public',
    'cache' => true,
    'cache.dir' => '/path/to/cache',
    'minify' => true,
    'debug' => false
));
```
