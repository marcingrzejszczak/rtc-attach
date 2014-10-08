# rtc-attach

Roughly equivalent to the
[`attachMediaStream`](https://www.npmjs.org/package/attachmediastream)
package but with support for rtc.io plugins.


[![NPM](https://nodei.co/npm/rtc-attach.png)](https://nodei.co/npm/rtc-attach/)

[![Build Status](https://img.shields.io/travis/rtc-io/rtc-attach.svg?branch=master)](https://travis-ci.org/rtc-io/rtc-attach) [![unstable](https://img.shields.io/badge/stability-unstable-yellowgreen.svg)](https://github.com/dominictarr/stability#unstable) 
[![Gitter chat](https://badges.gitter.im/rtc-io.png)](https://gitter.im/rtc-io)



## Example Usage

```js
var capture = require('rtc-capture');
var attach = require('rtc-attach');

capture({ video: true, audio: true }, function(err, stream) {
  if (err) {
    return console.error('could not capture stream: ', stream);
  }

  document.body.appendChild(attach(stream));
});

```

## Example with using Plugins

```js
var capture = require('rtc-capture');
var attach = require('rtc-attach');
var opts = {
  plugins: [
    require('rtc-plugin-nicta-ios'),
    require('rtc-plugin-temasys')
  ]
};

capture({ audio: true, video: true }, opts, function(err, stream) {
  if (err) {
    return console.error('could not capture stream: ', err);
  }

  document.body.appendChild(attach(stream, opts));
});

```

## Reference

### `attach(stream, opts?)`

Attach `stream` to the specified target `el` (a new element is created if
null). The following options can be supplied to tweak behaviour:

- `autoplay` (default: `true`) - by default after the stream has been
  attached to the element it will be played.  This is done by calling
  the `play()` function on the element rather than relying on `autoplay`
  attribute functionality.

- `el` (default: `null`) - if you with to supply an element to be used
  instead of creating a new element to receive the stream specify it here.

- `plugins` (default: `[]`) - specify one or more plugins that can be used
  to render the media stream appropriate to the current platform in the
  event that WebRTC and/or media capture is supported via a browser plugin.

## License(s)

### Apache 2.0

Copyright 2014 National ICT Australia Limited (NICTA)

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

     http://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.
