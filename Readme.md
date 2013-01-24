
# delay

  Delay effect module for the Web Audio API. Includes normal, inverted, and ping-pong implementations.

## Installation

    $ component install nick-thompson/delay

## API

Delay exports a constructor which takes four arguments: an AudioContext, delay type, `delayTime`, and `feedback`. The returned object supports connections from AudioNodes to its input property, and supports AudioNode prototype methods connect and disconnect.

The delay type parameter can be one of three values,

  * *0:* Normal (Default)
  * *1:* Inverted
  * *2:* Ping pong
   
```javascript
var context = new webkitAudioContext()
  , request = new XMLHttpRequest()
  , Delay = require("delay")
  , delay = new Delay(context, 2, 1.0, 0.8);

request.open("get", "/test/human-voice.wav", true);
request.responseType = "arraybuffer";
request.onload = function () {
  context.decodeAudioData(request.response, function (buffer) {

    var node = context.createBufferSource();
    node.buffer = buffer;

    node.connect(delay.input);
    delay.connect(context.destination);

    node.start(0);

  });
};
request.send();
```

## License

  Copyright (c) 2012 Nick Thompson

  Permission is hereby granted, free of charge, to any person
  obtaining a copy of this software and associated documentation
  files (the "Software"), to deal in the Software without
  restriction, including without limitation the rights to use,
  copy, modify, merge, publish, distribute, sublicense, and/or sell
  copies of the Software, and to permit persons to whom the
  Software is furnished to do so, subject to the following
  conditions:

  The above copyright notice and this permission notice shall be
  included in all copies or substantial portions of the Software.

  THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
  EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES
  OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
  NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT
  HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
  WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
  FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR
  OTHER DEALINGS IN THE SOFTWARE.
