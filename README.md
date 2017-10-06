Given
```
$ cat input/resource.properties 
baz=${foo}
alice=${env.BOB}
$ cat filters.properties 
foo=bar
```

I want the first line of `input/resource.properties` filtered and the second not.

Obviously it works if the env is not set:
```
jbochenski@Latitude-E5470:~/maven-filtering-explicit$ unset BOB; mvn -q && cat target/* 
baz=bar
alice=${env.BOB}
```

But I'd like a way to disable interpolating enviorment variables altogether:
```
jbochenski@Latitude-E5470:~/maven-filtering-explicit$ export BOB=CECIL; mvn -q && cat target/* 
baz=bar
alice=CECIL
```
