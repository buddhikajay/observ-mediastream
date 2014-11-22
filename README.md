# observ-mediastream

An attempt at making a [MediaStream](http://www.w3.org/TR/mediacapture-streams/#mediastream)
represented simply using [observables](https://github.com/Raynos/observ)


[![NPM](https://nodei.co/npm/observ-mediastream.png)](https://nodei.co/npm/observ-mediastream/)



## Example Usage

```js
var ObservStream = require('observ-mediastream');
var getUserMedia = require('getusermedia');
var stream = ObservStream();

getUserMedia({ audio: true, video: true }, function(err, s) {
  if (err) {
    return console.error('could not capture media stream: ', err);
  }

  setTimeout(function() {
    stream.muted.set(true);
  }, 1000);

  stream(function(value) {
    console.log('captured changes: ', value);
  });

  stream.update(s);
});

```

## License(s)

### ISC

Copyright (c) 2014, Damon Oehlman <damon.oehlman@gmail.com>

Permission to use, copy, modify, and/or distribute this software for any
purpose with or without fee is hereby granted, provided that the above
copyright notice and this permission notice appear in all copies.

THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES WITH
REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF MERCHANTABILITY
AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR ANY SPECIAL, DIRECT,
INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES WHATSOEVER RESULTING FROM
LOSS OF USE, DATA OR PROFITS, WHETHER IN AN ACTION OF CONTRACT, NEGLIGENCE OR
OTHER TORTIOUS ACTION, ARISING OUT OF OR IN CONNECTION WITH THE USE OR
PERFORMANCE OF THIS SOFTWARE.