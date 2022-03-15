## Operasi Data String

### Set the string value of a key
command : set key "value"
example : > set test0 "test redis 0"
result : OK

### Get the value of a key
command : get key
example : > get test0
result : OK

### Determine id a key exists
command: exists key
example : > exists test0
result (integer) 0 >> if key not exists
result (integer) 1 >> if key exists

### Delete a key
command : del key
example : > del test0
example : > del test0 test1
result (integer) number of delete key

### Append a value a key or insert value with key
command : set test0 "test"
command : append test0 "again"
result (integer) total string "(integer) 9"

command : > get test0
result : "testagain"
===============================
command : append test1 "ini test"
result : (integer) 8

comamnd : > get test1
result : "ini test"

### Find all key matching the given pattern (key pattern) using regex
command : > keys test\*
result :

1. "test0"
2. "test1"

command : > keys \*1
reesult : 1) "test1"

## Operasi Range Data String

setrange key offset value - Overwrite part of a string at key starting at the specified offset or raplace data in value
command : > setrange test0 0 halah
result : (integer) total string in key - (integer) 9"

command : > get test0
result : "halahgain"

getrange key start end - Get a substring of the string stored at a key
command : > getrange test0 0 3
result : "test"

command : > getrange test0 2 4
result : "sta"


## Operasi Multiple Data String

### Get the values of all the given keys

command : mget key [key ...]
example command : mget test0 test1 test2
result : 
1) "halahgain"
2) "ini test"
3) (nil)

### Set multiple keys to multiple values

command : mset key value [key value ...]
example command : mset test3 "im test" test4 "im testing again"
result : OK

command : > keys test*
result : 
1) "test0"
2) "test4"
3) "test1"
4) "test3"

command : mget test0 test1 test2 test3 test4
result : 
1) "halahgain"
2) "ini test"
3) "ini test lagi"
4) "im test"
5) "im testing again"

## Operasi Expiration Data String

### Set a key time to live in seconds

command : expire key seconds
example command : > expire test0 60
result : (integer) 1

### Set the value and expiration of a key

command : > setex key seconds value
example command : > setex test10 60 "example"
result : OK

### Get the time to live for a key

command : > ttl key
example command : > ttl test0
result : 
(integer) -1 = never expire
(integer) -2 = expire
(integer) ttl number = expire

check key test0
command : > get test0
result : (nil)

## Increment & Decrement

### 

