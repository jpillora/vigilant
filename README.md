# vigilant

  Simple command-line tool to contain and run multiple processes. Each process's stdio and stderr will be combined in beautiful technicolor. Vigilant will exit after the last process has exited.

## Installation

    $ npm install -g vigilant

## Usage

```
  Usage: vigilant [options] [commands]

  Options:

    -h, --help           output usage information
    -V, --version        output the version number
    -c, --config <file>  vigilant.json config pathname (default ./vigilant.json)
```

Note: Vigilant will run all commands if none are specified.

## Silly Example

Run:
``` sh
vigilant 'date +"%y-%m-%d"' 'ls -a' 'du -d 1'
```

Produces:
```
  vigilant: 'date' running...
  vigilant: 'ls' running...
  vigilant: 'du' running...
      date: 13-11-08
        ls: .
        ls: ..
        ls: README.md
        ls: print-args.js
  vigilant: 'date' exited with 0
        du: 16  .
  vigilant: 'ls' exited with 0
  vigilant: 'du' exited with 0
```

Equivalently, create the `vigilant.json` file:

``` json
{
  "date": "date +\"%y-%m-%d\"",
  "ls": "ls -a",
  "du": "du -d 1"
}
```

And just run `vigilant` where the `vigilant.json` resides.

## Useful Example

See the [example](./example) directory

Install some useful CLIs

`npm install -g coffee-script jade stylus serve`

Make a `vigilant.json`

``` json
{
  "coffee": "coffee -w -l -j build/app.js -c src/scripts",
  "jade": "jade -w -P src/views/ -O build/",
  "stylus": "stylus -w src/styles/ -o build/",
  "serve": "serve -p 8888 build/"
}
```

Run `vigilant`

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

Vigilant is now watching and compiling all your HTML, CSS, JS and serving the result on port 8888

## Todo

* Execution sequences
* Custom working directories

## MIT License

Copyright © 2013 Jaime Pillora &lt;dev@jpillora.com&gt;

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
