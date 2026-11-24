# Module 04: Media

**Folder:** `04-media/`
**Level:** Beginner (with Advanced notes)
**Time:** 8 to 10 hours
**Writing style:** ASD-STE100 (Simplified Technical English)
**Prerequisites:** Modules 01, 02, and 03

---

## Module Overview

### Goal
Learn to add images, audio, video, embedded content, and graphics to a page. Make media that is fast, accessible, and responsive.

### What you learn
After this module, you can:
1. Add images with correct `alt`, size, and loading attributes.
2. Group media with a caption using `<figure>` and `<figcaption>`.
3. Give the correct image to each screen size (`srcset`, `sizes`, `<picture>`).
4. Add audio and video with controls, captions, and fallbacks.
5. Embed maps and videos with `<iframe>`.
6. Draw simple graphics with inline SVG.
7. Build a photo gallery page.

### The main idea of this module
Media makes a page richer. But media also makes a page **heavy** and **hard to use** if you do it wrong. For each media file, ask three questions:
1. **Does it have a text alternative?** (accessibility)
2. **Is the file as small as possible?** (speed)
3. **Does it work on all screen sizes?** (responsive design)

### Folder structure for this module
```
04-media/
├── lesson-01-images.md
├── lesson-02-figure-figcaption.md
├── lesson-03-responsive-images.md
├── lesson-04-audio-video.md
├── lesson-05-iframe-embeds.md
├── lesson-06-inline-svg.md
├── lesson-07-project-photo-gallery.md
├── examples/
├── exercises/
└── project/
```

---

# Lesson 1: Images

## 1.1 Learning objectives
After this lesson, you can:
- Add an image with `<img>`.
- Write good `alt` text.
- Set `width`, `height`, and `loading`.
- Choose the correct image file format.

## 1.2 The `<img>` element

`<img>` is a **void element**. It has no closing tag.

```html
<img src="images/cat.jpg" alt="A grey cat asleep on a red sofa" width="600" height="400" />
```

| Attribute | Job | Required? |
|-----------|-----|-----------|
| `src` | The path to the image file. | Yes |
| `alt` | The text alternative. | Yes |
| `width` | The width in pixels. | Strongly recommended |
| `height` | The height in pixels. | Strongly recommended |
| `loading` | `lazy` or `eager`. | Optional |
| `decoding` | `async`, `sync`, or `auto`. | Optional |

The `src` path follows the same rules as link paths (Module 03).

## 1.3 Write good `alt` text

The `alt` attribute is the text that replaces the image if the user cannot see it. Users who cannot see the image are:
- Screen reader users.
- Users with a slow connection or a broken image.
- Search engines.

### Rules for `alt`

1. **Describe the purpose**, not only the picture.
2. Keep it short. Write 1 sentence (about 125 characters or fewer).
3. Do not start with "Image of" or "Picture of". The screen reader already says "image".
4. If the image is a link or button, describe **where the link goes**.
5. If the image only decorates, use an empty `alt=""`.
6. If the image has text, write that text in `alt`.

| Image | Bad `alt` | Good `alt` |
|-------|-----------|------------|
| Photo of a team | `team` | `The five members of our design team at a meeting table` |
| Logo that links to home | `logo` | `Acme Company, go to home page` |
| Line decoration | `line` | `alt=""` (empty) |
| Chart | `chart` | `Bar chart: sales rose from 10 in January to 40 in June` |
| Missing `alt` | (no attribute) | Always write the attribute |

**Important:** `alt=""` (empty) and no `alt` are **not the same**. An empty `alt` tells the screen reader to skip the image. No `alt` makes the screen reader read the file name.

## 1.4 `width` and `height`

Always write `width` and `height`. The browser then reserves space before the image loads. This stops the page from jumping (**layout shift**).

```html
<img src="photo.jpg" alt="Mountain lake at sunrise" width="800" height="533" />
```

- Use the real pixel size of the file, or a size with the same **aspect ratio**.
- Use CSS to make the image flexible: `img { max-width: 100%; height: auto; }`

## 1.5 Lazy loading

```html
<img src="photo.jpg" alt="..." width="800" height="533" loading="lazy" />
```

| Value | Result |
|-------|--------|
| `lazy` | The browser loads the image when the user scrolls near it. |
| `eager` | The browser loads the image at once. This is the default. |

**Rule:** Use `loading="lazy"` for images **below the first screen**. Do not use it for the main image at the top of the page.

## 1.6 Image file formats

| Format | Best for | Notes |
|--------|----------|-------|
| **JPEG** (`.jpg`) | Photos | Small files. Lossy. No transparency. |
| **PNG** (`.png`) | Graphics with sharp edges, transparency | Larger files. Lossless. |
| **WebP** (`.webp`) | Photos and graphics | Smaller than JPEG and PNG. Wide support. |
| **AVIF** (`.avif`) | Photos and graphics | Often the smallest file. Good support in modern browsers. |
| **GIF** (`.gif`) | Short simple animations | Large files. Use video instead. |
| **SVG** (`.svg`) | Logos, icons, drawings | Scales without loss. Text-based. |

## 1.7 Good practice for image files

1. Use lowercase file names with hyphens: `mountain-lake.jpg`.
2. Resize the image **before** you upload. Do not use a 4000 px photo in a 400 px space.
3. Compress the image. Tools: Squoosh (`squoosh.app`), TinyPNG, ImageOptim.
4. Keep photos under 200 KB when possible.
5. Put images in an `images/` folder.

## 1.8 Try It

1. Make a folder `images/`. Put 3 photos in it.
2. Add each photo with `<img>`, `src`, `alt`, `width`, and `height`.
3. Add `loading="lazy"` to the second and third photo.
4. Break a `src` path on purpose. See what the browser shows (the `alt` text).
5. Use DevTools (Network tab, filter **Img**) to see the file size of each image.

## 1.9 Advanced Note

- **Cumulative Layout Shift (CLS):** `width` and `height` give the browser the aspect ratio before load. Modern browsers use them to calculate `aspect-ratio`. This is a Core Web Vitals metric.
- **Largest Contentful Paint (LCP):** The top image is often the LCP element. Do not lazy-load it. Use `fetchpriority="high"` to load it first.
  ```html
  <img src="hero.jpg" alt="..." width="1200" height="600" fetchpriority="high" />
  ```
- **`decoding="async"`:** The browser decodes the image off the main thread. This can improve smoothness.
- **`crossorigin`:** Use it when you load images from another origin for use with canvas, or with CORS.
- **`referrerpolicy`:** Controls the `Referer` header for the image request.
- **`longdesc`:** An old attribute for long descriptions. Do not use it. Put the long description in the page text or use `aria-describedby`.
- **`ismap` and `usemap`:** Old methods for clickable image areas (`<map>` and `<area>`). Prefer separate links or SVG.
- **Image CDNs:** Services such as Cloudinary and imgix resize and convert images by URL. Use them in large projects.
- **Metadata:** Photos can have EXIF data (for example GPS location). Remove it before you publish.
- **Color profile:** Use sRGB for web images.
- **CSS `object-fit`:** Use `object-fit: cover` to fill a box without a stretched image.

## 1.10 Exercises

1. Write good `alt` text for: (a) a photo of your desk, (b) a company logo that links to the home page, (c) a decorative line.
2. Find the error: `<img src="Photo 1.JPG">`. List 3 problems.
3. Make a page with one large image at the top (no `lazy`) and 4 images below (with `lazy`).
4. Compress one photo with Squoosh. Write the file size before and after.
5. **Advanced:** Add `fetchpriority="high"` to the top image. Use Lighthouse. Check the LCP and CLS results.

## 1.11 Check your understanding
- Why is `alt` required?
- What is the difference between `alt=""` and no `alt`?
- Why do we write `width` and `height`?
- When do you not use `loading="lazy"`?

---

# Lesson 2: `<figure>` and `<figcaption>`

## 2.1 Learning objectives
After this lesson, you can:
- Group media with a caption.
- Tell `alt` text from a caption.
- Use `<figure>` for content other than images.

## 2.2 The elements

- `<figure>` holds self-contained content, such as an image, a diagram, a code block, or a quote.
- `<figcaption>` gives a caption for the `<figure>`.

```html
<figure>
  <img src="images/lake.jpg" alt="A calm lake with mountains behind it" width="800" height="533" />
  <figcaption>Lake Louise, Canada, at sunrise. Photo taken in June 2025.</figcaption>
</figure>
```

## 2.3 Rules

1. `<figcaption>` must be the **first** or the **last** child of `<figure>`.
2. A `<figure>` has only **one** `<figcaption>`.
3. The content must be related to the main text, but it can be moved (for example to an appendix) without changing the meaning.
4. `<figure>` is a block element.

## 2.4 `alt` and `<figcaption>` are different

| | `alt` | `<figcaption>` |
|---|---|---|
| Who sees it? | Users who cannot see the image | All users |
| Job | Replaces the image | Adds information |
| Where is it? | In the `<img>` tag | In the `<figure>` |

**Do not repeat the same text.** If the caption already describes the image fully, use a short `alt`.

## 2.5 Other uses of `<figure>`

```html
<!-- Code -->
<figure>
  <pre><code>console.log("Hello");</code></pre>
  <figcaption>Listing 1: A simple JavaScript statement.</figcaption>
</figure>

<!-- Quote -->
<figure>
  <blockquote><p>Simplicity is the ultimate sophistication.</p></blockquote>
  <figcaption>— Leonardo da Vinci</figcaption>
</figure>

<!-- Several images in one figure -->
<figure>
  <img src="before.jpg" alt="The room before painting" width="400" height="300" />
  <img src="after.jpg" alt="The room after painting" width="400" height="300" />
  <figcaption>Left: before. Right: after.</figcaption>
</figure>
```

## 2.6 Try It

1. Put 3 of your images in `<figure>` elements with captions.
2. Make a `<figure>` with a code block and a caption.
3. Make a `<figure>` with two images and one caption.
4. Look at the Accessibility tree in DevTools. Find the figure and its name.

## 2.7 Advanced Note

- **Accessible name:** A browser uses `<figcaption>` as the accessible name of `<figure>`. Screen readers can announce it.
- **`role="figure"`:** Not needed on `<figure>`. Only use it if you must give a non-`<figure>` element this role.
- **Do not use `<figure>` for decoration or page layout.** Only use it for content that is referenced in the text.
- **Numbering:** Use CSS counters to number figures automatically (`Figure 1`, `Figure 2`).
- **`<picture>` inside `<figure>`:** You can put `<picture>` in `<figure>` (see Lesson 3).
- **Captions for tables:** Tables have their own `<caption>` element (Module 05).

## 2.8 Exercises

1. Write a `<figure>` for a chart. Write a short `alt` and a detailed caption.
2. Find the error:
   ```html
   <figure>
     <img src="a.jpg" alt="A">
     <p>Text</p>
     <figcaption>Caption</figcaption>
     <figcaption>Second caption</figcaption>
   </figure>
   ```
3. Make a `<figure>` for a poem with `<pre>` and a caption with the author.
4. **Advanced:** Add CSS counters to number all figures on a page.

## 2.9 Check your understanding
- What does `<figcaption>` do?
- Where can you put `<figcaption>` in a `<figure>`?
- What is the difference between `alt` and a caption?

---

# Lesson 3: Responsive Images - `srcset`, `sizes`, and `<picture>`

## 3.1 Learning objectives
After this lesson, you can:
- Explain why one image file is not enough.
- Use `srcset` with `w` descriptors and `sizes`.
- Use `srcset` with `x` descriptors.
- Use `<picture>` for art direction and format choice.

## 3.2 The problem

- A phone screen is small. A large image wastes data.
- A high-density screen (Retina) needs more pixels.
- A wide screen needs a large image.

If you give one file to all devices, some devices get a file that is too big, and some get a file that is too small.

## 3.3 `srcset` with width descriptors (`w`)

Give the browser a list of files. Tell it the **width of each file**. The browser then picks the best file.

```html
<img
  src="images/photo-800.jpg"
  srcset="images/photo-400.jpg 400w,
          images/photo-800.jpg 800w,
          images/photo-1600.jpg 1600w"
  sizes="(min-width: 900px) 800px, 100vw"
  alt="A wooden boat on a quiet beach"
  width="800"
  height="533"
/>
```

| Part | Meaning |
|------|---------|
| `src` | The fallback file for old browsers. |
| `srcset` | The list of files. `400w` means the file is 400 pixels wide. |
| `sizes` | How wide the image will be on the page (in CSS pixels). |

### How to read `sizes`
`sizes="(min-width: 900px) 800px, 100vw"` means:
- If the window is 900 px or wider, the image is 800 px wide.
- Otherwise, the image is 100% of the window width (`100vw`).

The browser uses `sizes`, the screen density, and the `srcset` list to choose a file. **You tell the browser the size. The browser makes the choice.**

## 3.4 `srcset` with density descriptors (`x`)

Use `x` descriptors when the image has a **fixed display size** (for example a logo).

```html
<img
  src="logo-200.png"
  srcset="logo-200.png 1x, logo-400.png 2x, logo-600.png 3x"
  alt="Acme Company"
  width="200"
  height="60"
/>
```

- `1x` = standard screen.
- `2x` = high-density screen.
- Do not mix `w` and `x` in one `srcset`.

## 3.5 The `<picture>` element

`<picture>` gives **you** control. It has `<source>` elements and one `<img>`.

### Use 1: Format choice

```html
<picture>
  <source srcset="photo.avif" type="image/avif" />
  <source srcset="photo.webp" type="image/webp" />
  <img src="photo.jpg" alt="A red fox in snow" width="800" height="533" />
</picture>
```

The browser uses the **first** `<source>` that it supports. The `<img>` is the fallback and is **required**.

### Use 2: Art direction

Art direction means a **different crop** for different screens.

```html
<picture>
  <source media="(min-width: 900px)" srcset="hero-wide.jpg" />
  <source media="(min-width: 500px)" srcset="hero-medium.jpg" />
  <img src="hero-narrow.jpg" alt="A runner on a mountain path" width="600" height="600" />
</picture>
```

On a wide screen, the browser shows a wide crop. On a phone, it shows a close crop.

## 3.6 When to use what

| Need | Use |
|------|-----|
| Same image, different sizes | `srcset` + `sizes` (`w`) |
| Fixed-size image, high-density screens | `srcset` (`x`) |
| New formats with fallback | `<picture>` + `type` |
| Different crop for different screens | `<picture>` + `media` |

## 3.7 Try It

1. Make 3 sizes of one photo: 400 px, 800 px, 1600 px wide. Use Squoosh.
2. Write an `<img>` with `srcset` and `sizes`.
3. Open DevTools > Network. Change the window width. Reload. See which file loads.
4. Export a WebP version. Write a `<picture>` with a WebP source and a JPEG fallback.
5. Make an art direction example with two crops.

## 3.8 Advanced Note

- **`currentSrc`:** In the Console, type `document.querySelector('img').currentSrc` to see the chosen file.
- **Cache effects:** If the browser already has a large file in its cache, it can use it instead of a smaller one.
- **Responsive and CSS:** `sizes` uses CSS pixels and media conditions. Match it to your CSS layout. A wrong `sizes` value makes the browser choose a wrong file.
- **`sizes` default:** If you omit `sizes`, the browser uses `100vw`. This often loads files that are too big.
- **Preload:** For the LCP image, use `<link rel="preload" as="image" imagesrcset="..." imagesizes="...">`.
- **Build tools:** Use a build step (for example `sharp`, Eleventy Image, Astro Image) to make all sizes and formats automatically.
- **`<picture>` and CSS:** Style the `<img>` inside `<picture>`. Do not style `<picture>` for image size.
- **`<source>` attributes:** `srcset`, `sizes`, `type`, `media`, `width`, `height`.
- **Background images:** CSS backgrounds use `image-set()` for the same purpose.

## 3.9 Exercises

1. Write `sizes` for an image that is 100% wide on phones, 50% wide from 600 px, and 400 px wide from 1200 px.
2. Write a `<picture>` with AVIF, WebP, and JPEG.
3. Explain when you use `<picture>` and not `srcset`.
4. Find the error: `<picture><source srcset="a.webp"></picture>`
5. **Advanced:** Use a script (Node.js with `sharp`) to make 3 sizes and 2 formats from one source image.

## 3.10 Check your understanding
- What does `sizes` tell the browser?
- What does the `w` in `800w` mean?
- Which element do you need inside `<picture>` for the fallback?
- What is art direction?

---

# Lesson 4: Audio and Video

## 4.1 Learning objectives
After this lesson, you can:
- Add audio with `<audio>`.
- Add video with `<video>`.
- Give fallback formats and captions.
- Follow rules for autoplay and accessibility.

## 4.2 The `<audio>` element

```html
<audio controls>
  <source src="audio/podcast.mp3" type="audio/mpeg" />
  <source src="audio/podcast.ogg" type="audio/ogg" />
  <p>Your browser does not support audio. <a href="audio/podcast.mp3">Download the MP3</a>.</p>
</audio>
```

| Attribute | Job |
|-----------|-----|
| `controls` | Shows the play, pause, and volume controls. |
| `autoplay` | Starts to play at once. **Avoid.** |
| `loop` | Plays again and again. |
| `muted` | Starts silent. |
| `preload` | `none`, `metadata`, or `auto`. Hints to the browser how much to load. |
| `src` | The file (use if you have only one format). |

**Important:** If you omit `controls`, the user sees nothing and cannot control the sound.

## 4.3 The `<video>` element

```html
<video controls width="640" height="360" poster="images/video-cover.jpg" preload="metadata">
  <source src="video/intro.webm" type="video/webm" />
  <source src="video/intro.mp4" type="video/mp4" />
  <track kind="captions" src="video/intro.en.vtt" srclang="en" label="English" default />
  <p>Your browser does not support video. <a href="video/intro.mp4">Download the video</a>.</p>
</video>
```

| Attribute | Job |
|-----------|-----|
| `controls` | Shows the controls. |
| `width`, `height` | The display size. |
| `poster` | An image to show before the video plays. |
| `preload` | `none`, `metadata`, `auto`. |
| `muted` | Starts silent. |
| `loop` | Plays again and again. |
| `autoplay` | Starts at once. Browsers allow it only for **muted** video. |
| `playsinline` | On iPhone, plays inside the page, not in full screen. |

## 4.4 File formats

### Audio

| Format | MIME type | Notes |
|--------|-----------|-------|
| MP3 | `audio/mpeg` | Works everywhere. |
| AAC / M4A | `audio/mp4` | Good quality. Wide support. |
| OGG (Vorbis/Opus) | `audio/ogg` | Open format. |
| WAV | `audio/wav` | Large file. Not compressed. |

### Video

| Format | MIME type | Notes |
|--------|-----------|-------|
| MP4 (H.264) | `video/mp4` | Works everywhere. Best default. |
| WebM (VP9 / AV1) | `video/webm` | Smaller file. Open format. |

**Practical rule:** Provide **MP4 (H.264)**. Add **WebM** for smaller files if you can.

## 4.5 Captions and transcripts: `<track>`

`<track>` adds text tracks to audio or video.

```html
<track kind="captions" src="captions-en.vtt" srclang="en" label="English" default />
<track kind="subtitles" src="subs-fr.vtt" srclang="fr" label="Français" />
<track kind="descriptions" src="desc-en.vtt" srclang="en" label="Audio description" />
```

| `kind` | Use |
|--------|-----|
| `captions` | Speech and important sounds, for deaf or hard-of-hearing users. |
| `subtitles` | A translation of the speech. |
| `descriptions` | A text description of the visual content. |
| `chapters` | Chapter titles for navigation. |

### A simple WebVTT file (`captions-en.vtt`)

```
WEBVTT

00:00:01.000 --> 00:00:04.000
Welcome to the HTML course.

00:00:04.500 --> 00:00:08.000
In this video, we learn about media.
```

## 4.6 Accessibility rules for media

1. **Do not autoplay** sound. If you must autoplay, use `muted` and give a pause control.
2. Always give **controls**.
3. Give **captions** for all video with speech.
4. Give a **transcript** (a full text version) for audio and video.
5. Do not use media that flashes more than 3 times in 1 second.
6. Make sure that users can use the controls with a keyboard.

## 4.7 Try It

1. Add an audio file with 2 sources and a fallback link.
2. Add a short video with `controls`, `poster`, and `preload="metadata"`.
3. Write a `.vtt` caption file with 3 lines. Add it with `<track>`.
4. Write a transcript under the video in a `<details>` element.
5. Test the controls with the keyboard (`Tab`, `Space`, arrow keys).

## 4.8 Advanced Note

- **Autoplay policy:** Chrome and Safari block autoplay of sound. They allow `muted autoplay` (and `playsinline` on iOS). Users can allow it per site.
- **Streaming:** For long videos, use adaptive streaming (HLS or MPEG-DASH) with a service (for example Mux, Cloudflare Stream) or a player library. A plain `<video>` with MP4 downloads the file in one stream.
- **Range requests:** For seeking, the server must support HTTP range requests (`206 Partial Content`).
- **JavaScript API:** `HTMLMediaElement` gives `play()`, `pause()`, `currentTime`, `volume`, `playbackRate`, and events (`ended`, `timeupdate`, `loadedmetadata`).
  ```js
  const v = document.querySelector('video');
  v.addEventListener('ended', () => console.log('Done'));
  ```
- **Preload choices:** Use `preload="none"` for pages with many videos. Use `metadata` for a single video.
- **Picture-in-picture:** Controlled with `disablePictureInPicture` and the PiP API.
- **`controlslist`:** In Chromium, `controlslist="nodownload"` hides the download button. It is not a security feature.
- **Codecs in `type`:** `type='video/mp4; codecs="avc1.42E01E, mp4a.40.2"'` helps the browser to skip unsupported files quickly.
- **Web Audio API:** Use for advanced audio (effects, synthesis). It is not part of this course.
- **Copyright:** Use only media that you made, or have a license to use. Look for Creative Commons or public-domain sources.
- **File size:** Compress video with HandBrake or FFmpeg. Example: `ffmpeg -i in.mov -c:v libx264 -crf 23 -c:a aac out.mp4`

## 4.9 Exercises

1. Write an `<audio>` element with MP3 and OGG sources and a download link.
2. Write a `<video>` element with a poster, captions, and a fallback.
3. Write a WebVTT file with 5 captions for a 20-second video.
4. List 3 accessibility problems in `<video autoplay loop src="a.mp4"></video>`.
5. **Advanced:** Write JavaScript that adds a custom play/pause button. Use the `play()` and `pause()` methods.

## 4.10 Check your understanding
- What does `controls` do?
- Which video format works in all browsers?
- What is `<track>` for?
- Why is autoplay with sound a problem?

---

# Lesson 5: `<iframe>` Embeds

## 5.1 Learning objectives
After this lesson, you can:
- Embed another page with `<iframe>`.
- Embed a map and a YouTube video.
- Use `title`, `loading`, `sandbox`, and `allow`.
- Know the security risks.

## 5.2 The `<iframe>` element

`<iframe>` shows another web page **inside** your page.

```html
<iframe src="https://example.com" title="Example website" width="600" height="400"></iframe>
```

| Attribute | Job |
|-----------|-----|
| `src` | The URL of the page to embed. |
| `title` | **Required for accessibility.** Describes the content. |
| `width`, `height` | The size. |
| `loading="lazy"` | Loads the frame when it is near the viewport. |
| `allow` | Permissions (for example `fullscreen`, `camera`). |
| `allowfullscreen` | Lets the content go full screen. |
| `sandbox` | Limits what the embedded page can do. |
| `referrerpolicy` | Controls the `Referer` header. |

## 5.3 Embed a YouTube video

1. Open the video on YouTube.
2. Click **Share > Embed**.
3. Copy the code.

```html
<iframe
  width="560"
  height="315"
  src="https://www.youtube.com/embed/VIDEO_ID"
  title="HTML tutorial for beginners"
  loading="lazy"
  allow="accelerometer; encrypted-media; gyroscope; picture-in-picture; web-share"
  allowfullscreen
  referrerpolicy="strict-origin-when-cross-origin"
></iframe>
```

- Replace `VIDEO_ID` with the real ID.
- For more privacy, use `https://www.youtube-nocookie.com/embed/VIDEO_ID`.

## 5.4 Embed a map

1. Open Google Maps (or OpenStreetMap).
2. Click **Share > Embed a map**.
3. Copy the code.

```html
<iframe
  src="https://www.openstreetmap.org/export/embed.html?bbox=77.2%2C28.6%2C77.3%2C28.7&amp;layer=mapnik"
  title="Map of central Delhi"
  width="600"
  height="400"
  loading="lazy"
></iframe>
```

Add a normal text link to the same location. Not all users can use a map.

## 5.5 Make an iframe responsive

```css
.video-wrap { aspect-ratio: 16 / 9; }
.video-wrap iframe { width: 100%; height: 100%; border: 0; }
```

```html
<div class="video-wrap">
  <iframe src="..." title="..." loading="lazy" allowfullscreen></iframe>
</div>
```

## 5.6 Security

An embedded page is **third-party content**. It can track users, or can be unsafe. Use these rules:

1. Embed only sites that you trust.
2. Use `sandbox` for unknown content.
3. Use `loading="lazy"`.
4. Use `title`.
5. Check that the site allows embedding. Some sites block it with `X-Frame-Options` or `Content-Security-Policy: frame-ancestors`.

### `sandbox`

```html
<iframe src="untrusted.html" sandbox title="Untrusted demo"></iframe>
<iframe src="demo.html" sandbox="allow-scripts allow-same-origin" title="Demo"></iframe>
```

An empty `sandbox` blocks scripts, forms, popups, and more. Add values to allow only what you need.

| Value | Allows |
|-------|--------|
| `allow-scripts` | JavaScript |
| `allow-forms` | Form submission |
| `allow-popups` | Popups and new tabs |
| `allow-same-origin` | Treat the content as same-origin |
| `allow-downloads` | Downloads |

**Warning:** `allow-scripts` and `allow-same-origin` together on the **same-origin** content remove the sandbox. Do not use them together for content from your own origin that you do not control.

## 5.7 Try It

1. Embed a YouTube video with `title` and `loading="lazy"`.
2. Embed a map. Add a text link to the same place.
3. Try to embed `https://www.google.com`. See the error. In DevTools > Console, find the reason.
4. Add `sandbox` to an embed. See what stops working.
5. Make the video responsive with `aspect-ratio`.

## 5.8 Advanced Note

- **`postMessage`:** Use `window.postMessage` to send data between a page and its iframe, across origins.
- **`srcdoc`:** `<iframe srcdoc="<p>Hello</p>">` embeds inline HTML. Useful for code demos.
- **Permissions Policy:** The `allow` attribute uses Permissions Policy. Example: `allow="geolocation 'none'"`. You can also set the HTTP header `Permissions-Policy`.
- **Clickjacking:** Attackers can embed your page in a hidden iframe. Protect your site with `X-Frame-Options: DENY` or `Content-Security-Policy: frame-ancestors 'self'`.
- **Performance:** An iframe loads a full page. A YouTube embed can load more than 500 KB. Use a **facade**: show a thumbnail, and load the iframe when the user clicks. The `lite-youtube-embed` library does this.
- **`credentialless` and `csp` attributes:** New, with limited support. Not used in this course.
- **Accessibility:** Keyboard focus can become trapped in an iframe. Test with the `Tab` key.
- **`<embed>` and `<object>`:** Older elements for plugins and PDFs. Use `<iframe>` or a link instead. Browsers have removed plugins.
- **SEO:** Search engines do not count iframe content as part of your page.

## 5.9 Exercises

1. Write an `<iframe>` for a YouTube video with all good practice attributes.
2. Write the correct `title` for a map of your city.
3. Explain why a site can refuse to be embedded.
4. Find 3 problems: `<iframe src="http://unknown-site.test"></iframe>`
5. **Advanced:** Make a "click to load" facade for a YouTube video. Use a thumbnail and a button. Load the iframe with JavaScript on click.

## 5.10 Check your understanding
- What does `<iframe>` do?
- Why must an iframe have a `title`?
- What does `sandbox` do?
- Why can a site refuse to be embedded?

---

# Lesson 6: Inline SVG Basics

## 6.1 Learning objectives
After this lesson, you can:
- Explain what SVG is.
- Write simple shapes in inline SVG.
- Make SVG accessible.
- Choose between `<img>` and inline SVG.

## 6.2 What is SVG?

**SVG** = Scalable Vector Graphics. It is an XML-based format. It describes shapes with **math**, not pixels.

- It stays sharp at any size.
- File sizes are small for simple graphics.
- You can style it with CSS and control it with JavaScript.
- Use it for logos, icons, charts, and illustrations. Do not use it for photos.

## 6.3 Three ways to use SVG

| Method | Example | CSS/JS control | Cached | Use for |
|--------|---------|----------------|--------|---------|
| `<img>` | `<img src="logo.svg" alt="...">` | No | Yes | Logos, illustrations |
| CSS background | `background: url(a.svg)` | No | Yes | Decoration |
| **Inline** | `<svg>...</svg>` in HTML | **Yes** | No | Icons, charts, animated graphics |

## 6.4 Your first inline SVG

```html
<svg width="200" height="200" viewBox="0 0 200 200" role="img" aria-labelledby="title1 desc1">
  <title id="title1">A blue circle</title>
  <desc id="desc1">A blue circle with a dark border on a light background.</desc>
  <rect width="200" height="200" fill="#eef" />
  <circle cx="100" cy="100" r="60" fill="#3b82f6" stroke="#1e3a8a" stroke-width="4" />
</svg>
```

## 6.5 The coordinate system

- The origin `(0, 0)` is at the **top-left**.
- `x` goes **right**. `y` goes **down**.
- `viewBox="min-x min-y width height"` sets the internal coordinate system. The graphic then scales to the `width` and `height` of the element.

```
(0,0) ───────────► x
  │
  │
  ▼
  y
```

## 6.6 Basic shapes

| Element | Main attributes | Example |
|---------|-----------------|---------|
| `<rect>` | `x`, `y`, `width`, `height`, `rx` (rounded corners) | `<rect x="10" y="10" width="80" height="50" rx="8" />` |
| `<circle>` | `cx`, `cy`, `r` | `<circle cx="50" cy="50" r="30" />` |
| `<ellipse>` | `cx`, `cy`, `rx`, `ry` | `<ellipse cx="50" cy="50" rx="40" ry="20" />` |
| `<line>` | `x1`, `y1`, `x2`, `y2` | `<line x1="0" y1="0" x2="100" y2="100" stroke="black" />` |
| `<polygon>` | `points` | `<polygon points="50,5 95,95 5,95" />` |
| `<polyline>` | `points` | `<polyline points="0,0 50,50 100,0" fill="none" stroke="black" />` |
| `<path>` | `d` (path data) | `<path d="M10 10 L90 10 L50 80 Z" />` |
| `<text>` | `x`, `y` | `<text x="10" y="30">Hello</text>` |

### Style attributes

| Attribute | Job |
|-----------|-----|
| `fill` | The inside color. |
| `stroke` | The outline color. |
| `stroke-width` | The outline width. |
| `opacity` | Transparency from 0 to 1. |

## 6.7 Path commands (basic)

| Command | Meaning |
|---------|---------|
| `M x y` | Move to a point. |
| `L x y` | Draw a line to a point. |
| `H x` | Draw a horizontal line. |
| `V y` | Draw a vertical line. |
| `Z` | Close the path. |
| Lowercase (for example `l`) | The same, but with **relative** coordinates. |

Example: a triangle.
```html
<svg width="100" height="100" viewBox="0 0 100 100" aria-hidden="true">
  <path d="M50 10 L90 90 L10 90 Z" fill="orange" />
</svg>
```

## 6.8 Make SVG accessible

| Case | Method |
|------|--------|
| The SVG has meaning | Add `role="img"` and a `<title>`. Link with `aria-labelledby`. |
| The SVG is decoration | Add `aria-hidden="true"`. |
| The SVG is an icon in a button with text | Use `aria-hidden="true"` on the SVG. The button text gives the name. |
| The SVG is an icon-only button | Put the label on the `<button>` with `aria-label`. |

```html
<button type="button" aria-label="Close">
  <svg width="16" height="16" viewBox="0 0 16 16" aria-hidden="true" focusable="false">
    <path d="M2 2 L14 14 M14 2 L2 14" stroke="currentColor" stroke-width="2" />
  </svg>
</button>
```

## 6.9 Style SVG with CSS

Use `currentColor` so that the icon uses the text color.

```css
.icon { width: 1.5rem; height: 1.5rem; fill: currentColor; }
.icon:hover { fill: crimson; }
```

## 6.10 Try It

1. Draw a house: a `<rect>` for the walls, a `<polygon>` for the roof, a `<rect>` for the door.
2. Draw a smiley face with `<circle>`, `<path>`, and `<ellipse>`.
3. Change `width` and `height` on the `<svg>` element. See that the drawing scales.
4. Make a "close" icon. Put it in a button with `aria-label`.
5. Change the color with CSS (`fill: currentColor`).

## 6.11 Advanced Note

- **`viewBox` and `preserveAspectRatio`:** `preserveAspectRatio` controls how the graphic fits in its box. Default: `xMidYMid meet`.
- **`<symbol>` and `<use>`:** Define an icon once. Use it many times.
  ```html
  <svg style="display:none">
    <symbol id="icon-star" viewBox="0 0 24 24">
      <path d="M12 2l3 7h7l-5.5 4.5L18 21l-6-4-6 4 1.5-7.5L2 9h7z" />
    </symbol>
  </svg>

  <svg class="icon" aria-hidden="true"><use href="#icon-star" /></svg>
  ```
- **Gradients and filters:** `<linearGradient>`, `<radialGradient>`, `<filter>`, `<clipPath>`, and `<mask>` give rich effects.
- **Animation:** Animate SVG with CSS (`@keyframes`, `transform`, `stroke-dashoffset`) or JavaScript. SMIL animation is old and not advised. Respect `prefers-reduced-motion`.
- **Optimize:** Use SVGO (`npx svgo file.svg`) to remove extra data.
- **Security:** An SVG file can contain `<script>`. Do not accept SVG uploads from unknown users without cleaning. SVG in `<img>` does not run scripts. Inline SVG does.
- **Path arcs and curves:** `C` (cubic Bézier), `Q` (quadratic), and `A` (arc) commands make curves. Design tools (Figma, Inkscape) export paths for you.
- **Charts:** Libraries such as D3 and Chart.js (canvas) make charts. You can also hand-write simple charts in SVG.
- **Namespace:** Inline SVG in HTML5 does not need `xmlns`. A separate `.svg` file does: `xmlns="http://www.w3.org/2000/svg"`.
- **Text in SVG:** SVG `<text>` does not wrap lines automatically.

## 6.12 Exercises

1. Draw a traffic light with 3 circles.
2. Write an accessible SVG with `role="img"`, `<title>`, and `<desc>`.
3. Make a bar chart of 4 values with `<rect>` elements. Add labels with `<text>`.
4. Make an icon with `<symbol>` and use it 3 times with `<use>`.
5. **Advanced:** Optimize an SVG with SVGO. Write the size before and after. Add a CSS hover animation.

## 6.13 Check your understanding
- What does SVG mean?
- Where is the origin `(0, 0)` in SVG?
- What does `viewBox` do?
- When do you use `aria-hidden="true"` on an SVG?

---

# Lesson 7: Module Project - Photo Gallery Page

## 7.1 Project goal
Build a photo gallery page. Use correct, accessible, and fast media.

## 7.2 Content plan

| Part | Content | Elements to use |
|------|---------|-----------------|
| Header | Gallery name and `<nav>` | `<header>`, `<h1>`, `<nav>` |
| Hero | One large photo at the top | `<picture>` or `<img>` with `srcset` |
| Gallery | At least 8 photos with captions | `<figure>`, `<figcaption>`, `<img>` |
| Media section | One video or audio, with captions or a transcript | `<video>` or `<audio>`, `<track>` |
| Map | An embedded map of where the photos were taken | `<iframe>` |
| Icon | At least 2 inline SVG icons (for example a camera) | `<svg>` |
| Footer | Credit and copyright | `<footer>` |

## 7.3 Project folder

```
project/
├── index.html
├── images/
│   ├── hero-800.jpg
│   ├── hero-1600.jpg
│   ├── photo-01.jpg
│   └── ...
├── media/
│   ├── intro.mp4
│   └── captions-en.vtt
└── README.md
```

## 7.4 Requirements

### Level 1: Beginner (required)
- [ ] Full HTML boilerplate, with a clear `<title>`.
- [ ] At least 8 images with clear, correct `alt` text.
- [ ] All images have `width` and `height`.
- [ ] Images below the first screen use `loading="lazy"`.
- [ ] The top image does **not** use `loading="lazy"`.
- [ ] Each gallery image is in a `<figure>` with a `<figcaption>`.
- [ ] At least one `<video>` or `<audio>` with `controls` and a fallback.
- [ ] At least one inline SVG with an accessible name, or `aria-hidden="true"` if decorative.
- [ ] One `<iframe>` with a `title` and `loading="lazy"`.
- [ ] No image is larger than 300 KB.
- [ ] All file names are lowercase, with hyphens.
- [ ] You have the right to use all photos, audio, and video. Credit the source.

### Level 2: Intermediate (recommended)
- [ ] Hero image with `srcset` and `sizes` (at least 2 sizes).
- [ ] One image with `<picture>` and a WebP source with a JPEG fallback.
- [ ] A `<track>` with captions, or a full transcript.
- [ ] A text link next to the map.
- [ ] Validate the page with `https://validator.w3.org`. Fix all errors.

### Level 3: Advanced (optional)
- [ ] Use CSS Grid to make the gallery responsive (`grid-template-columns: repeat(auto-fit, minmax(250px, 1fr))`).
- [ ] Use `aspect-ratio` and `object-fit: cover` for equal thumbnails.
- [ ] Use an SVG sprite with `<symbol>` and `<use>`.
- [ ] Use a "click to load" facade for an embedded video.
- [ ] Get a Lighthouse score of 90 or more for Performance and 100 for Accessibility.

## 7.5 Steps

1. Choose a theme: travel, food, pets, nature, your city, your art.
2. Collect or make 8 or more photos. Check the license.
3. Resize and compress the photos. Make 2 sizes of the hero image.
4. Write the alt text and captions on paper first.
5. Build the page structure: header, hero, gallery, media, map, footer.
6. Add the gallery with `<figure>` elements.
7. Add the video or audio, the map, and the SVG icons.
8. Test: use the keyboard, DevTools Network (file sizes), and a screen reader if you can.
9. Validate and run Lighthouse.
10. Write `README.md`. List the image credits.
11. Commit and push:
    ```bash
    git add .
    git commit -m "Add Module 04 photo gallery"
    git push
    ```

## 7.6 Starter template

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>My Photo Gallery</title>
  </head>
  <body>
    <header>
      <h1>
        <svg width="24" height="24" viewBox="0 0 24 24" aria-hidden="true" focusable="false">
          <rect x="2" y="6" width="20" height="14" rx="2" fill="currentColor" />
          <circle cx="12" cy="13" r="4" fill="white" />
        </svg>
        My Photo Gallery
      </h1>
      <nav aria-label="Main">
        <ul>
          <li><a href="#gallery">Gallery</a></li>
          <li><a href="#video">Video</a></li>
          <li><a href="#map">Map</a></li>
        </ul>
      </nav>
    </header>

    <main>
      <!-- Hero: no lazy loading -->
      <img
        src="images/hero-800.jpg"
        srcset="images/hero-800.jpg 800w, images/hero-1600.jpg 1600w"
        sizes="100vw"
        alt="Describe the hero image here"
        width="1600"
        height="900"
        fetchpriority="high"
      />

      <!-- Gallery -->
      <section id="gallery">
        <h2>Gallery</h2>
        <figure>
          <img src="images/photo-01.jpg" alt="Describe photo 1" width="600" height="400" loading="lazy" />
          <figcaption>Caption for photo 1. Photo: Your Name.</figcaption>
        </figure>
        <!-- Add 7 or more figures -->
      </section>

      <!-- Video -->
      <section id="video">
        <h2>Video</h2>
        <video controls width="640" height="360" preload="metadata" poster="images/video-poster.jpg">
          <source src="media/intro.mp4" type="video/mp4" />
          <track kind="captions" src="media/captions-en.vtt" srclang="en" label="English" default />
          <p>Your browser does not support video. <a href="media/intro.mp4">Download the video (MP4)</a>.</p>
        </video>
      </section>

      <!-- Map -->
      <section id="map">
        <h2>Where I took these photos</h2>
        <iframe
          src="PASTE-MAP-EMBED-URL"
          title="Map of the places where the photos were taken"
          width="600"
          height="400"
          loading="lazy"
        ></iframe>
        <p><a href="PASTE-MAP-LINK" target="_blank" rel="noopener noreferrer">Open the map in a new tab</a></p>
      </section>
    </main>

    <footer>
      <p><small>&copy; 2026 Your Name. Photos by Your Name.</small></p>
    </footer>
  </body>
</html>
```

## 7.7 Self-check list

1. Does each image have a correct `alt` that describes its purpose?
2. Do all images have `width` and `height`?
3. Is the top image not lazy-loaded, and are the others lazy-loaded?
4. Does each `<figure>` have one `<figcaption>`?
5. Does the video have `controls`, a fallback, and captions or a transcript?
6. Does the `<iframe>` have a `title`?
7. Is each decorative SVG hidden with `aria-hidden="true"`?
8. Are all files small? Check DevTools > Network.
9. Does the validator show 0 errors?
10. Did you credit the sources?

## 7.8 Grading guide (self-assessment)

| Area | Points |
|------|--------|
| Correct `alt` text and captions | 20 |
| Correct image attributes (`width`, `height`, `loading`) | 15 |
| Responsive images (`srcset`, `sizes`, `<picture>`) | 15 |
| Audio/video with controls, fallback, captions | 15 |
| `<iframe>` and inline SVG, accessible | 10 |
| Small file sizes | 10 |
| Validator shows 0 errors | 5 |
| Git commits, README, credits | 10 |
| **Total** | **100** |

A score of 80 or more means you are ready for Module 05.

---

# Module 04 Review

## Final quiz

**Questions**

1. What is the difference between `alt=""` and no `alt` attribute?
2. Why do you write `width` and `height` on an image?
3. When do you not use `loading="lazy"`?
4. What is the difference between `alt` text and `<figcaption>`?
5. What does `sizes` tell the browser?
6. When do you use `<picture>` and not `srcset`?
7. Which attribute adds a play button and a volume bar to a video?
8. What is `<track>` used for?
9. Why must an `<iframe>` have a `title`?
10. Where is the origin `(0, 0)` in SVG? Which way does `y` go?

**Answers**

1. `alt=""` tells assistive tools to skip a decorative image. No `alt` makes a screen reader read the file name or URL.
2. The browser reserves space before the image loads. This stops layout shift.
3. For the image at the top of the page (above the fold), that the user sees first.
4. `alt` replaces the image for users who cannot see it. `<figcaption>` adds visible information for all users.
5. How wide the image will be in the layout, so that the browser can choose the best file from `srcset`.
6. When you need art direction (a different crop) or a choice of file format (AVIF, WebP, JPEG).
7. `controls`.
8. To add captions, subtitles, descriptions, or chapters to audio or video.
9. Screen reader users use the title to know what the frame contains.
10. At the top-left. `y` goes down.

## Common mistakes

| Mistake | Fix |
|---------|-----|
| No `alt` attribute | Always write `alt`. Use `alt=""` for decoration. |
| `alt="image of ..."` | Remove "image of". Describe the purpose. |
| No `width` and `height` | Add both. Use CSS `height: auto`. |
| 4000 px photo in a small space | Resize and compress first. |
| `loading="lazy"` on the top image | Remove it. Use `fetchpriority="high"`. |
| Caption and `alt` are the same | Write different text for each. |
| `<figcaption>` in the middle of `<figure>` | Put it first or last. |
| `<picture>` with no `<img>` | `<img>` is required. |
| `sizes` missing with `w` descriptors | Add `sizes`. The default is `100vw`. |
| Video with `autoplay` and sound | Remove `autoplay`, or add `muted` and controls. |
| Video with no captions | Add `<track kind="captions">` or a transcript. |
| `<iframe>` with no `title` | Add a clear `title`. |
| Embedding unknown sites | Use `sandbox` or do not embed. |
| Decorative SVG read by screen readers | Add `aria-hidden="true"`. |
| GIF for animation | Use `<video muted loop autoplay playsinline>`. |
| Use media without a license | Use your own media or media with a free license. |

## Glossary

| Term | Definition |
|------|------------|
| Alt text | A text alternative for an image. |
| Art direction | A different image crop for different screen sizes. |
| Aspect ratio | The relation between width and height. |
| Caption | Visible text that explains a figure or gives the speech in a video. |
| Codec | A program that compresses and decompresses audio or video. |
| Embed | To put content from another source inside your page. |
| Fallback | Content that shows when a feature is not supported. |
| Lazy loading | A delay in loading a resource until the user needs it. |
| Layout shift | A sudden movement of page content while the page loads. |
| Lossy | A compression that removes some data. |
| Poster | An image that shows before a video plays. |
| Sandbox | A set of limits on what embedded content can do. |
| `srcset` | A list of image files for the browser to choose from. |
| SVG | Scalable Vector Graphics. An image format based on shapes. |
| Transcript | A full text version of audio or video. |
| `viewBox` | The internal coordinate system of an SVG. |
| WebVTT | A text file format for captions and subtitles. |

## Module 04 progress checklist (copy to `PROGRESS.md`)

```markdown
## Module 04: Media
- [ ] Lesson 1: Images
- [ ] Lesson 2: figure and figcaption
- [ ] Lesson 3: Responsive images
- [ ] Lesson 4: Audio and video
- [ ] Lesson 5: iframe embeds
- [ ] Lesson 6: Inline SVG basics
- [ ] Lesson 7: Photo gallery project
- [ ] Final quiz (8/10 or more)
- [ ] All images compressed and with alt text
- [ ] Page validated with W3C
- [ ] Lighthouse accessibility check done
- [ ] Project pushed to GitHub
```

## Cheat sheet: Module 04

```html
<!-- Image -->
<img src="a.jpg" alt="Description" width="600" height="400" loading="lazy" />

<!-- Figure -->
<figure>
  <img src="a.jpg" alt="Short description" width="600" height="400" />
  <figcaption>Visible caption</figcaption>
</figure>

<!-- Responsive: same image, many sizes -->
<img src="a-800.jpg"
     srcset="a-400.jpg 400w, a-800.jpg 800w, a-1600.jpg 1600w"
     sizes="(min-width: 900px) 800px, 100vw"
     alt="..." width="800" height="533" />

<!-- Picture: format choice / art direction -->
<picture>
  <source srcset="a.avif" type="image/avif" />
  <source srcset="a.webp" type="image/webp" />
  <source media="(min-width: 900px)" srcset="a-wide.jpg" />
  <img src="a.jpg" alt="..." width="800" height="533" />
</picture>

<!-- Audio and video -->
<audio controls>
  <source src="a.mp3" type="audio/mpeg" />
</audio>
<video controls width="640" height="360" poster="p.jpg" preload="metadata">
  <source src="v.mp4" type="video/mp4" />
  <track kind="captions" src="c.vtt" srclang="en" label="English" default />
</video>

<!-- iframe -->
<iframe src="..." title="Clear description" loading="lazy" width="560" height="315"></iframe>

<!-- Inline SVG -->
<svg width="100" height="100" viewBox="0 0 100 100" role="img" aria-labelledby="t">
  <title id="t">Blue circle</title>
  <circle cx="50" cy="50" r="40" fill="royalblue" />
</svg>
```

| Format | Best for |
|--------|----------|
| JPEG | Photos |
| PNG | Sharp graphics, transparency |
| WebP / AVIF | Smaller photos and graphics |
| SVG | Logos, icons, drawings |
| MP4 (H.264) | Video, all browsers |
| MP3 | Audio, all browsers |

## Next module
Go to **Module 05: Tables**. You learn table structure, `<thead>`, `<tbody>`, `<tfoot>`, `colspan`, `rowspan`, and accessible tables.
