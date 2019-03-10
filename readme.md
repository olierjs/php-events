# EventEmitter

[![Build Status](https://travis-ci.com/TbhT-lib/php-events.svg?branch=master)](https://travis-ci.com/TbhT-lib/php-events)


Install
-------

> loading


Usage
-----

## `add_listener`

```php

use Press\Utils\Events;

$ee = new Events();

$ee->add_listener('foo', function () {
    echo "this is a listener for php \n";
});

// the same as $ee->on()
$ee->on('foo', function () {
    echo "this is a listener for php \n";
})

$ee->emit('foo');

// the same as 
$ee->emit_event('foo');

```

## `remove_listener`


### `string` 

```php

use Press\Utils\Events;

$ee = new Events();

$bar_listener = function ($arg) {
    var_dump($arg);
};

$ee->add_listener('bar', $bar_listener);

$ee->remove_listener('bar', $bar_listener);

```

### `regular expression`

```php
use Press\Utils\Events;

$ee = new Events();
$fn1 = function () {};
$fn2 = function () {};
$fn3 = function () {};
$fn4 = function () {};
$fn5 = function () {};

$ee->add_listeners([
    'foo' => [$fn1, $fn2, $fn3, $fn4, $fn5],
    'bar' => [$fn1, $fn2, $fn3, $fn4, $fn5],
    'baz' => [$fn1, $fn2, $fn3, $fn4, $fn5]
]);

$ee->remove_listener('/ba[rz]/', $fn3);

assert([$fn5, $fn4, $fn2, $fn1] === $ee->flatten_listeners($ee->get_listeners('bar')));

```


## `add_once_listener`

```php

use Press\Utils\Events;

$ee = new Events();
$counter = 0;

$bar_listener_once = function ($counter) use (&$counter) {
    $counter++;
};

$ee->add_once_listener('foo', $bar_listener_once);

$ee->emit('foo');
$ee->emit_event('foo');

assert($counter === 1, 'the counter should be 1');

```

## `get_`