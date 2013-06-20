# Omeka REST API Client

```php
// Set the autoloader.
require_once '/path/to/Zend/Loader/StandardAutoloader.php';
$loader = new Zend\Loader\StandardAutoloader(array('autoregister_zf' => true));
$loader->registerNamespace('ZendService\Omeka', '/path/to/ZendService/Omeka');
$loader->register();

// Instantiate the client and set the authentication key.
$omeka = new ZendService\Omeka\Omeka('http://yourdomain.com/api');
$omeka->setKey('fd11f6fdcdcd2f524555b089790824ede6d27cff');

// GET /items/:id
$response = $omeka->items->get(1);
echo $response->getBody();

// GET /items
$response = $omeka->items->get();
echo $response->getBody();

// POST /items
$response = $omeka->items->post('{}');
echo $response->getBody();

// POST /files
// Note the different signature. You can set callbacks to the client that handle 
// custom request behavior. This callback is set in the constructor, but others 
// can be set suing ZendService\Omeka\Omeka::setCallback().
$response = $omeka->files->post('/path/to/file', '{"item":{"id":1}}');
echo $response->getBody();

// PUT /items/:id
$response = $omeka->items->put(1, '{}');
echo $response->getBody();

// DELETE /items/:id
$response = $omeka->items->delete(1);
echo $response->getBody();
```
