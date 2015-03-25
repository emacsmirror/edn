# Edn.el

Edn.el is an emacs lisp library for reading and writing the data
format [edn](https://github.com/edn-format/edn).

## Installation

I highly recommend installing edn.el through elpa.

It's available on [melpa](http://melpa.milkbox.net/):

    M-x package-install edn

## Usage

`edn-parse` will read a string of edn into emacs lisp structures.

`edn-print-string` will write emacs lisp data structures into edn.

`edn-set-to-list` will turn our internal representation of a set into a list.

`edn-list-to-set` will create a list from our internal representation of a set.

## Known limitations

### Set representation
Emacs lisp doesn't have have a data structure dedicated to sets.  In emacs lisp, and in other lisps like common lisp, sets are just lists without duplicate elements.  This means that when outputting edn and we encounter a list without duplicates we can't know if we should write a set or not.  There are three solutions to this problem:

1. Let the user tag the lists that should be turned into sets prior to serialization.
2. Always create lists, unless the user passes an option to eagerly create sets.
3. Use our own datastructure to represent sets.

I've chosen to take the third approach.

### Bignums

Elisp doesn't have support for bignums without pulling in `calc` or an external lib.  For now I've opted to just throw an error when edn containing bignums is put on the input stream.

## Is it any good?

Yes!

## Contribute

Please do!  There is a suite of tests that I'd like you to add to whenever a bug is fixed or a new feature is added.  If you don't do this I'm likely to break your code when I stumble around the codebase.

To fetch the test dependencies, install [cask](https://github.com/rejeep/cask.el) if you haven't already, then:

    $ cd /path/to/edn.el
    $ cask

Run the tests with:

    $ make test

## License

Copyright (c)  2015, Lars Andersen

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
