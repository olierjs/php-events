# EventEmitter

[![Build Status](https://travis-ci.com/TbhT-lib/php-events.svg?branch=master)](https://travis-ci.com/TbhT-lib/php-events)


Install
-------

> loading


Usage
-----

### `add_listener`

```php

use Press\Utils\Events;

$ee = new Events();

$ee->add_listener('foo', function () {
    echo "this is a listener for php \n";
});

$ee->emit('foo');

// the same as 
$ee->emit_event('foo');

```

### `remove_listener`

```php

use Press\Utils\Events;

$ee = new Events();

$bar_listener = function ($arg) {
    var_dump($arg);
};

$ee->add_listener('bar', $bar_listener);

$ee->remove_listener('bar', $bar_listener);

```
