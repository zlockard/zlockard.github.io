# Event posts

All events, including movie nights, use the same `event` container and date-card
styling. There is no event type parameter: the content determines what appears
inside the event.

Create a draft using the event archetype:

```powershell
hugo new content --kind event posts\2027-6-12.md
```

Set the post's `title` to the date and time displayed on its card, update `date`,
and set `draft = false` when ready to publish. Keep the post under `content/posts`
so it appears alongside movie nights.

```toml
+++
title = 'Saturday, June 12th (8:00PM)'
date = 2027-06-12T20:00:00-07:00
draft = false
+++
```

The `event` container takes no title or type parameters. Titles belong to its
content objects: use the optional `title` on `party` for a party heading, or
the existing `title` on `moviesummary` for a movie name.

## Parties

A `party` contains an optional title and a Markdown description. Its title,
content alignment, and spacing use the same layout and styles as `moviesummary`:

```text
{{<event>}}
{{<party title="Game Night">}}
Bring a **favorite game** to share.

- Games start at 8 PM.
- [See the details](https://example.com).
{{</party>}}
{{</event>}}
```

For a heading-only party, leave the `party` body empty. Omit its `title` for a
body-only party. Each party can have its own heading, and an event can contain
multiple parties. Events work in post
listings and on the individual post page.

To opt into orange lettering with a black outline, set the party's `titleclass`
to `text-orange-outline`:

```text
{{<party title="Halloween Party!" titleclass="text-orange-outline">}}
{{</party>}}
```

The class uses 24px, extra-bold lettering with an orange fill and a 2px black outline,
preserving the title's left alignment. Omit `titleclass` for the normal title
style. The CSS class can also be reused on other text elements.

## Movie nights

A movie night is simply an event containing movies. Each `movie` provides its
own table layout, using `moviesummary` and an optional `movietrailer`:

```text
{{<event>}}
{{<movie>}}
{{<moviesummary title="Movie Title" year="2027" length="90">}}
A short description of the movie.
{{</moviesummary>}}
{{<movietrailer YOUTUBE_VIDEO_ID>}}
{{</movie>}}
{{</event>}}
```

An event can mix parties and movies in any order. Party rendering belongs
to `party`, and movie layout belongs to `movie`, so the container
does not need to know what kind of event it holds. This also keeps Markdown
rendering separate from trusted shortcode HTML without enabling raw HTML in
the site's Markdown configuration.

Use `event` for all event containers. The old `movienight` alias has been removed.

Preview drafts and future events with `.\test.cmd`. Build published posts,
including future events, with `.\build.cmd`.

## Theme development

This site uses a deliberately slimmed-down local copy of PaperMod in
`themes/PaperMod2`, not the full upstream feature set.

- Event shortcodes and their shared wrapper live in `layouts/`.
- Page/list templates and shared header, footer, metadata, and asset loading
  live in `themes/PaperMod2/layouts/`.
- Event-specific styling and responsive movie/trailer rules live in
  `themes/PaperMod2/assets/css/extended/custom.css`.
- General layout and Markdown styles live in the theme's `css/common/` directory.
- English UI strings live in `themes/PaperMod2/i18n/en.yaml`.

The retained theme supports event listings, individual posts, pagination,
categories/tags, RSS, metadata for link previews and search engines, dark mode,
and scroll-to-top navigation. Search, archives, profile/home-info modes, social
icons, sharing buttons, comments, cover-image UI, table of contents, post-to-post
navigation, edit/canonical footer links, code-copy buttons, Chroma stylesheets,
unused theme shortcodes, and non-English translations have been removed.
Generic Markdown typography and image rendering are still supported.

Movie cells stack below 1024px. Trailer dimensions remain 560 by 315px at
viewports at least 560px wide, and 90vw by 50.625vw below that breakpoint.
These rules work without JavaScript. CSS viewport units account for classic
scrollbars, so small-screen trailers can be slightly narrower than the old
JavaScript sizing. CSS also uses fractional dimensions and viewport breakpoints
instead of the previous JavaScript's integer rounding.

After changing CSS, increment `params.assets.styleSheetVersion` in `hugo.toml`
to invalidate cached stylesheets. Keep the PaperMod license and CSS attribution
when editing the vendored theme. Upstream updates must be reviewed selectively,
because copying the full theme back in would restore removed features.
