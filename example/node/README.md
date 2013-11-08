run:
```
vigilant 'print-args 1 2 3' 'print-args x y z'
```

produces:
```
  $ vigilant 'print-args 1 2 3' 'print-args x y z'
  vigilant: 'print-args' running...
  vigilant: 'print-args' running...
print-args: [ 'node',
print-args:   '/Users/jpillora/Code/Node/vigilant/example/node/print-args',
print-args:   '1',
print-args:   '2',
print-args:   '3' ]
  vigilant: 'print-args' exited with 0
print-args: [ 'node',
print-args:   '/Users/jpillora/Code/Node/vigilant/example/node/print-args',
print-args:   'x',
print-args:   'y',
print-args:   'z' ]
  vigilant: 'print-args' exited with 0
```