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

Api Video HTML5 Player URL Fragments
==================================

### Introduction

Some Api Video Player features may be activated with what's called `URL fragments`. 

In other words, it means that the Api Video embed (iFrame) source URL may be completed by query parameters introduced by a hash (#).

Here is the example of a Api Video embed code:
```
<iframe src="https://embed.api.video/vod/vi54sj9dAakOHJXKrUycCQZp" class="av_player" width="1280" height="720" frameborder="0" scrolling="no" allowfullscreen></iframe>
```

The source URL is `https://embed.api.video/vod/vi54sj9dAakOHJXKrUycCQZp`. 

Any fragment must be appened to the end of this URL after a hash `#`.
Example : `https://embed.api.video/vod/vi54sj9dAakOHJXKrUycCQZp#autoplay`

Multiple fragments may be concatenated with a semi-colon `;`.
Example : `https://embed.api.video/vod/vi54sj9dAakOHJXKrUycCQZp#autoplay;api`


### Autoplay

To launch video as soon as the player can, use `#autoplay`.


### Sequence

To start a video from `x`, use: `#t=x`.

To start a video from `x` and pause it at `y`, use: `#t=x,y`.

To start from the beginning and pause at `y`, use: `#t=,y`.

Time may be expressed in the following formats:
- `ss` (eg. `120` for 2 minutes)
- `mm:ss` (ex. `2:30` for two minutes and a half)
- `hh:mm:ss` (ex. `1:30:00` for one hour and a half)


### Allow API

To allow player to listen to API calls, use `#api`.


### Hide poster title

To hide the Player's title that is displayed on the bottom left corner of the poster, use `#hide-title`.


### Hide controls

To hide the Player's control bar, use `#hide-controls`.
Caution as you should integrate your own controls if you prevent users from accessing Api Video Player native ones.


### Complex example

Here is a URL fragment that automatically launches a sequence (from 10 seconds to 15 seconds) and enables API calls:
```
<iframe src="https://embed.api.video/vod/vi54sj9dAakOHJXKrUycCQZp#t=10,15;autoplay;api" class="av_player" width="1280" height="720" frameborder="0" scrolling="no" allowfullscreen></iframe>
```

