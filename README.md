Api Video HTML5 Player JavaScript Client
======================================

### Installation and use

The script `avp_client.min.js` must be included either inside the `<head>` document part, 
or at the end of the HTML page, just before the closing `</body>` tag.

Then you must instanciate one `ApiVideoPlayer` object per embed:
```javascript
var player = new ApiVideoPlayer('player_id');
```

See `demo/index.html` for a complete example of how to use this client.

After client instantiation, api.video embeds should behave like the standard 
HTML5 MediaElement API (see https://developer.mozilla.org/en/docs/Web/API/HTMLMediaElement).


### Available player methods

The following list of methods is available from embed `<iframe>` elements 
once the api.video client has been instantiated.

- `play()`
- `pause()`
- `toggle()` [*]
- `seek(seconds)` [*] where `seconds` must be an integer or a float
- `mute()` [*]
- `setVolume(level)` [**] where `level` must be a float between 0 and 1 (percentage)

(* non HTML5 MediaElement API standard)

(** a bit different from the HTML5 MediaElement API standard because of JavaScript limitations)

### Available player attributes

The following list of attributes is available from embed `<iframe>` elements 
once the api.video client has been instantiated.

- `volume`
- `duration`
- `currentTime`


### Available player events

The following list of events is emitted by embed `<iframe>` elements once the 
api.video client has been instantiated.

- `loadedmetadata`
- `loadeddata`
- `canplay`
- `play`
- `playing`
- `pause`
- `timeupdate`
- `volumechange`
- `ended`