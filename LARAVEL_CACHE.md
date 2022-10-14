## LARAVEL_CACHE

Generate dummy data to full up redis:

```

$bigArray = ['randomData' => str_random(1024 * 1024 * 50)];

Cache::set('test_key', $bigArray)

```

Can just repeat for different keys till redis memory is at max:

```

>>> $biggerArray = ['randomData' => str_random(1024 * 1024 * 50)];

>>> Cache::set('test_key12', $biggerArray)
=> true
>>> Cache::set('test_key', $biggerArray)
=> true
>>> Cache::set('test_key1', $biggerArray)
=> true
>>> Cache::set('test_key2', $biggerArray)
=> true
>>> Cache::set('test_key3', $biggerArray)
=> true
>>> Cache::set('test_key4', $biggerArray)
=> true
>>> Cache::set('test_key5', $biggerArray)
=> true
>>> Cache::set('test_key6', $biggerArray)
=> true
>>> Cache::set('test_keys', $bigArray)
RedisException with message 'OOM command not allowed when used memory > 'maxmemory'.'

```