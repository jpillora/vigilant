
# vigilant

  Simple command-line tool to contain and run multiple processes. Each process's stdio and stderr will be combined in beautiful technicolor. Vigilant will exit after the last process has exited.

## Installation

    $ npm install -g vigilant

## Usage

```
Usage: vigilant [options] [dir]

```

## Silly Example

vigilant.json

``` json
{
  "date": "date +\"%y-%m-%d\"",
  "ls"  : "ls -a"
}
```

`vigilant`

```
  vigilant: 'date' running...
  vigilant: 'ls' running...
      date: "13-03-24"
  vigilant: 'date' exited with 0
        ls: .
        ls: ..
        ls: .git
        ls: .gitignore
        ls: .npmignore
        ls: README.md
        ls: bin
        ls: example
        ls: node_modules
        ls: package.json
        ls: vigilant.json
  vigilant: 'ls' exited with 0
```


## Useful Example

See [example](./example)

vigilant.json

``` json
{
  "coffee": "coffee -w -l -j build/app.js -c src/scripts",
  "jade": "jade -w -P src/views/ -O build/",
  "stylus": "stylus -w src/styles/ -o build/",
  "serve": "serve -p 8888 build/"
}
```

`npm install -g coffee-script jade stylus serve`
`vigilant`

```
  vigilant: 'coffee' running...
  vigilant: 'jade' running...
  vigilant: 'stylus' running...
  vigilant: 'serve' running...
      jade: 
      jade:   rendered build/index.html
    coffee: path.exists is now called `fs.exists`.
    coffee: 
    coffee: 16:37:12 - compiled build/app.js
    stylus:   watching /usr/local/share/npm/lib/node_modules/stylus/lib/functions/index.styl
    stylus:   compiled build/app.css
    stylus:   watching src/styles/app.styl
     serve: serving /***/vigilant/example/build on port 8888
```

## MIT License

Copyright (c) 2013 Jaime Pillora &lt;dev@jpillora.com&gt;

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.