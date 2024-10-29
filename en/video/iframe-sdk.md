# Video player SDK for IFrame reference

You can embed a [video player](./concepts/player.md) with content from {{ video-name }} in an HTML page using the video player SDK for IFrame.

Add an [iframe](https://en.wikipedia.org/wiki/HTML_element#Frames) container to the page code:

```html
<iframe
    frameborder="0"
    scrolling="no"
    allowfullscreen
    allow="autoplay; fullscreen; encrypted-media; accelerometer; gyroscope; picture-in-picture; clipboard-write; web-share; screen-wake-lock"
    src="https://runtime.video.cloud.yandex.net/player/...?autoplay=1&mute=1"
></iframe>
```

{% include [video-content-id-desc](../_includes/video/video-content-id-desc.md) %}

The embed code contains an iframe container that shows the player with the specified video.

You can also set up [video size](#size) and the player [startup options](#parameters).

## Setting up video size {#size}

To specify video size, set the following parameters in the `iframe` tag: `height` for height and `width` for width.

Example:

```html
<iframe width="560" height="315"
  frameborder="0"
    scrolling="no"
    allowfullscreen
    allow="autoplay; fullscreen; encrypted-media; accelerometer; gyroscope; picture-in-picture; clipboard-write; web-share; screen-wake-lock"
    src="https://runtime.video.cloud.yandex.net/player/..."
></iframe>
```

To adjust the video to the container width, change the embed code as follows:

```html
<div style="min-width: 100%">
  <div style="position: relative; padding-bottom: 56.25%; height: 0;">
    <iframe style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;"
        frameborder="0"
        scrolling="no"
        allowfullscreen
        allow="autoplay; fullscreen; encrypted-media; accelerometer; gyroscope; picture-in-picture; clipboard-write; web-share; screen-wake-lock"
        src="https://runtime.video.cloud.yandex.net/player/...?autoplay=1&mute=true"
    ></iframe>
  </div>
</div>
```

## Setting up the player startup options {#parameters}

Customize your player appearance and video playback using special parameters.

Add `parameter=value` pairs separated by `&` to the embed code URL after `?`:

```http
https://runtime.video.cloud.yandex.net/player/...?{param1=value1}&...&{paramN=valueN}
```

You can see the list of parameters and their possible values in the table below. If you do not specify the parameters, the player will start with default parameters.

#|

|| **Parameter:** | **Description:** ||
|| `allow_muted`  |
Auto video playback in mute mode at startup:

* `false`: Muted autoplay not allowed.
* `true`: Muted autoplay allowed.

The `allow_muted` parameter has priority over `autoplay`. If `allow_muted=false`, autoplay will take place only if it is possible with sound.
||
|| `autoplay` |
Auto video playback at startup:

* `0`: Auto playback off.
* `1`: Auto playback on.

The default value is `0`.

For the autoplay option to work correctly in all browsers, use the `autoplay=1` parameter together with `mute=1`.
||
|| `hidden` |
With this parameter, you can hide the player's interface elements. All of them are shown by default.

{% cut "List of interface elements" %}

* `*`: All interface elements.
* `contextMenu`: Context menu.
* `fullscreen`: Full screen toggle button.
* `live`: **Go back to live** button.
* `mobileSeekButtons`: Rewind and fast forward buttons in the mobile interface.
* `play`: Interface element displaying the **Play**, **Pause**, and **Repeat** buttons. It turns off play or pause when clicking the player.
* `playbackRate`: Playback rate.
* `poster`: Poster.
* `preloader`: Load indicator.
* `settings`: Settings button.
* `startScreen`: Start screen.
* `startScreenPlay`: Play button on start screen.
* `subtitlesToggle`: Subtitles toggle button.
* `timeline`: Timeline. It turns off rewinding and fast forwarding from the keyboard or by touching the sensor screen.
* `timelinePreview`: Preview on the timeline.
* `time`: Current playback time.
* `title`: Video title.
* `sound`: Mute button.
* `volumeSlider`: Volume slider.

{% endcut %}

To hide several interface elements, provide a string of comma-separated values, e.g., `hidden=startScreenPlay,play`.
||
|| `lang` |
Player interface language.

{% cut "List of languages" %}

* `ru`: Russian
* `en`: English
* `be`: Belarusian
* `id`: Indonesian
* `kk`: Kazakh
* `tr`: Turkish
* `tt`: Tatar
* `uk`: Ukrainian
* `uz`: Uzbek

{% endcut %}

If you do not specify the parameters or provide an unsupported value, the player interface language will be based on user data.
||
|| `loop` |
Playback looping:

* `false`: Playback looping off.
* `true`: Playback looping on.

The default value is `false`.
||
|| `mute` |
Mute at startup:

* `false`: Sound on.
* `true`: Sound off.

The default value is `false`.
||
||  `play_on_visible` |
Stopping playback if the player leaves the visible area and starting playback if the player is in it. The parameter affects both video content and ads. It can take the following values:

* `false`: Video is played back if the player leaves the visible area.
* `true`: Video is not played back if the player leaves the visible area.
* Player visibility ratio sufficient for playback. Specify this value as a decimal fraction with a period (`.`) for a delimiter.

The default value is `false`. When set to `true`, the visibility ratio is `0.5`.

{% note info %}

When set to `play_on_visible=true`, the `autoplay` parameter is ignored. The parameter only works in browsers that can accurately calculate player visibility.

{% endnote %}
||
||  `preload` |
Video preload:

* `false`: Video preload off.
* `true`: Video preload on.

The default value is `false`.

When set to `autoplay=1`, the `preload` parameter is ignored.
||
||  `volume`  |
Volume at startup.

The values range from `0` to `1` inclusive, e.g., `volume=0.5`.

If set to `mute=1`, the parameter is ignored.
||
|#

### Example {#example}

This example shows the video autoplay in muted mode:

```html
<iframe
    frameborder="0"
    scrolling="no"
    allowfullscreen
    allow="autoplay; fullscreen; encrypted-media; accelerometer; gyroscope; picture-in-picture; clipboard-write; web-share; screen-wake-lock"
    src="https://runtime.video.cloud.yandex.net/player/video/vplvmyqsxi7dlwndvb4y?autoplay=1&mute=true"
></iframe>
```

<iframe
    frameborder="0"
    scrolling="no"
    allowfullscreen
    allow="autoplay; fullscreen; encrypted-media; accelerometer; gyroscope; picture-in-picture; clipboard-write; web-share; screen-wake-lock"
    src="https://runtime.video.cloud.yandex.net/player/video/vplvmyqsxi7dlwndvb4y?autoplay=1&mute=true"
></iframe>