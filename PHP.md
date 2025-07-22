### Redirect to WordPress index.

```
<?php
// Lista de slugs e URLs de redirecionamento
$redirects = array(
    'slug1' => 'https://example.com/destino1',
    'slug2' => 'https://example.com/destino2',
    'slug3' => 'https://example.com/destino3',
);

// Obtém o caminho da URL atual
$request_uri = trim($_SERVER['REQUEST_URI'], '/');

// Verifica se o slug está na lista de redirecionamentos
if (array_key_exists($request_uri, $redirects)) {
    header("Location: " . $redirects[$request_uri], true, 301);
    exit;
}

// Continua o carregamento normal do WordPress
define('WP_USE_THEMES', true);
require __DIR__ . '/wp-blog-header.php';
```
