# Why a CTA Click Can Fire When Safari Video Controls Are Clicked

Safari renders native video controls outside the page's normal DOM. When a video is wrapped in, or sits underneath, a clickable CTA element, taps on Safari's play, pause, volume, or timeline controls can still be interpreted as a click on that CTA.

This happens because the browser's native media-control layer does not always prevent the surrounding element from receiving the resulting click. The event can therefore bubble to the CTA's click handler or activate the CTA's link, even though the user intended only to control the video.

## Avoid it

- Do not place a native `<video controls>` element inside an anchor or other clickable CTA container.
- Keep the video and CTA as separate sibling elements.
- If the CTA must be nearby, attach its handler only to a dedicated button/link instead of a shared parent.
- For analytics, ignore click events whose target is the video element or its container when appropriate.

Native control behavior differs between browsers, so test media interactions in Safari on the intended device.

