## Deploy Redis using docker

### Redis Default
```
docker-compose -f redis-default/docker-compose.yml up -d
```

### Redis with config
```
docker-compose -f redis-with-config/docker-compose.yml up -d
```

### Access Redis
```
docker exec -it redis /bin/sh
```

## Operasi Data String

### Set the string value of a key
```
set key "value"
```
example :
```
> set test0 "test redis 0"
```
result : OK

### Get the value of a key
```
get key
```
example :
```
> get test0
```
result : OK

### Determine id a key exists
```
exists key
```
example :
```
> exists test0
```
result
```
(integer) 0 >> if key not exists
```
```
(integer) 1 >> if key exists
```

### Delete a key
```
del key
```
example :
```
> del test0
```
```
> del test0 test1
```
result
```
(integer) number of delete key
```

### Append a value a key or insert value with key
```
set test0 "test"
```
```
append test0 "again"
```
result
```
(integer) total string "(integer) 9"
```

check a key test0 :
```
> get test0
```
result :
```
"testagain"
```
===============================
```
append test1 "ini test"
```
result :
```
(integer) 8
```

comamnd :
```
> get test1
```
result :
```
"ini test"
```

### Find all key matching the given pattern (key pattern) using regex
command :
```
> keys test\*
```
result :
```
1. "test0"
2. "test1"
```
command :
```
> keys \*1
```
reesult :
```
1) "test1"
```

## Operasi Range Data String

setrange key offset value - Overwrite part of a string at key starting at the specified offset or raplace data in value
command :
```
> setrange test0 0 halah
```
result :
```
(integer) total string in key - (integer) 9"
```

command :
```
> get test0
```
result :
```
"halahgain"
```

getrange key start end - Get a substring of the string stored at a key
command :
```
> getrange test0 0 3
```
result :
```
"test"
```
command :
```
> getrange test0 2 4
```
result :
```
"sta"
```


## Operasi Multiple Data String

### Get the values of all the given keys

command :
```
mget key [key ...]
```
example command :
```
mget test0 test1 test2
```
result :
```
1) "halahgain"
2) "ini test"
3) (nil)
```
### Set multiple keys to multiple values

command :
```
mset key value [key value ...]
```
example command :
```
mset test3 "im test" test4 "im testing again"
```
result :
```
OK
```
command :
```
> keys test*
```
result :
```
1) "test0"
2) "test4"
3) "test1"
4) "test3"
```
command :
```
mget test0 test1 test2 test3 test4
```
result :
```
1) "halahgain"
2) "ini test"
3) "ini test lagi"
4) "im test"
5) "im testing again"
```
## Operasi Expiration Data String

### Set a key time to live in seconds

command :
```
expire key seconds
```
example command :
```
> expire test0 60
```
result :
```
(integer) 1
```

### Set the value and expiration of a key

command :
```
> setex key seconds value
```
example command :
```
> setex test10 60 "example"
```
result :
```
OK
```
### Get the time to live for a key

command :
```
> ttl key
```
example command :
```
> ttl test0
```
result :
```
(integer) -1 = never expire
(integer) -2 = expire
(integer) ttl number = expire
```
check key test0
command :
```
> get test0
(nil)
```

## Increment  Decrement

### Increment the integer value of a key by one

```
incr key
```

example
```
incr counter
(integer) 1
```
get value of key with command
```
> get counter
"1"
```
increment value of key counter
```
> incr counter
(integer) 2
```
get value of key counter again
```
> get counter
"2"
```

### Decrement the integer value of a key by one

```
decr key
```

example
```
> decr counter
(integer) 1
```

check value of key after decrement
```
> get counter
"1"
```

### Increment the integer value of a key by one the given amount

```
incrby key increment
```

example
```
> incrby counter 100
(integer) 101
```
check value data of key
```
> get counter
"101"
```

### Decrement the integer value of a key by one the given number

```
decrby key decrement
```

example
```
decrby counter 50
(integer) 51
```

check value of key counter
```
> get counter
"51"
```

## Flush Operation

### Remove all keys from the current database

```
flushdb
```

### Remove all keys from all database

```
flushall
```


## Pipeline
Bulk insert to redis

### Operation Pipeline using Redis CLI

```
redis-cli --pipe
```

## Transaction

