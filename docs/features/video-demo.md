# Video Demo

Watch these walkthroughs to see Product in action. All recordings are available locally in the `docs/assets/videos/` directory.

!!! note "Adding your own videos"
    Place `.mp4` files in `docs/assets/videos/` and reference them with the embed code shown below. Videos are served as static assets — no external hosting required.

---

## Quickstart Walkthrough

This 3-minute overview covers creating your first workspace, running a pipeline, and inspecting the results.

<div class="video-wrapper" markdown>
<video
  controls
  width="100%"
  style="border-radius: 8px; box-shadow: 0 4px 24px rgba(0,0,0,.25); max-width: 800px; display: block; margin: 1rem auto;"
  poster="../assets/images/hero.png"
>
  <source src="../assets/videos/quickstart.mp4" type="video/mp4">
  <p>Your browser does not support HTML5 video. <a href="../assets/videos/quickstart.mp4">Download the video</a> instead.</p>
</video>
</div>

**What you'll see:**

1. Logging in and creating a workspace
2. Importing a sample dataset from S3
3. Running the built-in validation pipeline
4. Reviewing results in the analytics dashboard

---

## Pipeline Configuration Deep-Dive

A 6-minute walkthrough covering advanced pipeline configuration, including multi-step transforms, conditional branching, and error handling strategies.

<div class="video-wrapper" markdown>
<video
  controls
  width="100%"
  style="border-radius: 8px; box-shadow: 0 4px 24px rgba(0,0,0,.25); max-width: 800px; display: block; margin: 1rem auto;"
  poster="../assets/images/feature.png"
>
  <source src="../assets/videos/pipeline-config.mp4" type="video/mp4">
  <p>Your browser does not support HTML5 video. <a href="../assets/videos/pipeline-config.mp4">Download the video</a> instead.</p>
</video>
</div>

**Topics covered:**

- Writing multi-step pipeline YAML
- Using environment variable interpolation
- Configuring retries and dead-letter queues
- Connecting a Slack webhook for failure alerts

---

## How to Embed a Local Video

Copy this snippet into any Markdown page and adjust the `src` path:

```html
<video
  controls
  width="100%"
  style="border-radius: 8px; max-width: 800px; display: block; margin: 1rem auto;"
  poster="path/to/thumbnail.png"
>
  <source src="path/to/your-video.mp4" type="video/mp4">
  Your browser does not support HTML5 video.
</video>
```

### Path Reference Guide

| Page location | Video in `assets/videos/` | Correct `src` |
|---------------|---------------------------|---------------|
| `docs/index.md` | `quickstart.mp4` | `assets/videos/quickstart.mp4` |
| `docs/features/video-demo.md` | `quickstart.mp4` | `../assets/videos/quickstart.mp4` |
| `docs/getting-started/index.md` | `quickstart.mp4` | `../assets/videos/quickstart.mp4` |

!!! tip "Thumbnail / poster frame"
    The `poster` attribute sets the image shown before the user hits play. Point it at any PNG or JPG in your assets folder.

---

## Supported Formats

| Format | Extension | Notes |
|--------|-----------|-------|
| MPEG-4 | `.mp4` | Best compatibility — recommended |
| WebM | `.webm` | Smaller file size, modern browsers only |
| OGG | `.ogv` | Legacy fallback |

For maximum browser compatibility, provide both MP4 and WebM sources:

```html
<video controls width="100%">
  <source src="../assets/videos/demo.webm" type="video/webm">
  <source src="../assets/videos/demo.mp4"  type="video/mp4">
  Your browser does not support HTML5 video.
</video>
```

---

!!! info "PDF export and videos"
    When this page is exported to PDF via `mkdocs build`, video embeds are replaced by the poster image with a caption noting the original file path. This is handled automatically by the `mkdocs-with-pdf` plugin.
