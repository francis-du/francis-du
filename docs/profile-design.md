# Profile artwork and previews

The profile uses local SVG artwork and GitHub's own Markdown layout. The main introduction, project descriptions and links remain selectable text. Project sections stack vertically so the descriptions stay readable on a phone.

`assets/francis-banner.svg`, `assets/wcode-card.svg` and `assets/maris-card.svg` are the light defaults. Each has a `-dark.svg` partner selected by `<picture>`. The SVGs contain a title and description, use system fonts, and load no scripts or external resources. Keep the project names large; put detailed copy in the README rather than inside an image.

GitHub documents this image pattern in its [writing quickstart](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/quickstart-for-writing-on-github#adding-an-image-to-suit-your-visitors). Its [Markdown API](https://docs.github.com/en/rest/markdown/markdown) provides the actual sanitized rendering:

```sh
gh api --method POST /markdown \
  -f mode=gfm \
  -f context=francis-du/francis-du \
  -F text=@README.md
```

## Captured on GitHub

These are screenshots of the actual README on GitHub at [df2312e](https://github.com/francis-du/francis-du/tree/df2312eb5c8a2661bc2fedc24bdbd9923d4b6d3a), captured on 2026-10-02 in Chrome. The crop contains the rendered README; no substitute website stylesheet was applied.

The review covered 320, 390, 768 and 1440 px viewports in both light and dark mode. All three images loaded and selected the correct theme, body text was 16 px, the README had no horizontal overflow, and the Chinese disclosure opened with the keyboard. GitHub's surrounding repository controls are outside these crops.

### Desktop · light

1440 px viewport, 838 px README.

![Actual GitHub README in light mode on desktop](previews/profile-light-1440.png)

### Desktop · dark

1440 px viewport, 838 px README.

![Actual GitHub README in dark mode on desktop](previews/profile-dark-1440.png)

### Phone · light

390 px viewport, 324 px README.

![Actual GitHub README in light mode on a phone](previews/profile-light-390.png)

### Phone · dark

390 px viewport, 324 px README.

![Actual GitHub README in dark mode on a phone](previews/profile-dark-390.png)

## Content and automation

Keep the existing `personal-profile`, `featured-projects` and `beyond-code` region markers. They identify hand-maintained sections. Only public projects are linked; Maris retains its development status. Writing links introduce the products and do not promise a release that has not been published.

The contribution-snake workflow publishes generated artwork to its separate `output` branch. It must not force-push `master`: a scheduled run can otherwise overwrite another session's newer profile changes.
