# node-m3u

A node.js module for creating m3u / m3u8 files. Supported dialects are [m3u][],
[extended m3u][] and [http live streaming m3u][].

[m3u]: http://en.wikipedia.org/wiki/M3U
[extended m3u]: http://en.wikipedia.org/wiki/M3U#Extended_M3U_directives
[http live streaming m3u]:http://tools.ietf.org/html/draft-pantos-http-live-streaming

## Installation

    npm install m3u

## Usage

    // Basic M3U
    var writer = require('m3u').writer();
    writer.comment('I am a comment');
    writer.write(); // blank line
    writer.uri('foo.mp3');

    console.log(writer.toString());

    // Extended M3U
    var writer = require('m3u').extendedWriter();
    writer.comment('I am a comment');
    writer.info('10', 'Artist - Title');
    writer.info('42'); // duration only, no title
    writer.uri('foo.mp3');
    writer.uri('bar.mp3', 23); // include a duration

    console.log(writer.toString());

    // Http Live Streaming M3U
    var writer = require('m3u').httpLiveStreamingWriter();
    writer.comment('I am a comment');
    writer.info('10', 'Artist - Title');
    writer.info('42'); // duration only, no title
    writer.uri('foo.mp3');
    writer.uri('bar.mp3', 23); // include a duration

    console.log(writer.toString());


## Todo

* npm package
* Implement http live streaming writer
* Use writeable stream interface for writers (I don't need this, but I will accept patches)
* Implement a reader (I don't need this, but I will accept patches)

## License

node-m3u is licensed under the MIT license.
