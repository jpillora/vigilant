run:
```
vigilant 'date -j' 'date -r 0'
```

produces:
```
  $ vigilant 'date -j' 'date -r 0'
  vigilant: 'date' running...
  vigilant: 'date' running...
      date: Fri  8 Nov 2013 22:12:55 EST
      date: Thu  1 Jan 1970 10:00:00 EST
  vigilant: 'date' exited with 0
  vigilant: 'date' exited with 0
```