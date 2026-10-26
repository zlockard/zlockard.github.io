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

## Post boxes

All posts use the same boxed style in listings, including the first post on the
home page. To remove the box for an individual post, add this to its front matter:

```toml
hideBox = true
```

This removes the background, visible border, rounded corners, and shadow
in home, posts, and category/tag listings, including paginated pages. Padding,
alignment, and typography stay consistent with boxed posts. Omit `hideBox` or
set it to `false` to keep the normal box. Individual post pages are unaffected.

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

Below 1024px, `movietrailer` displays a keyboard-accessible, ticket-style
**Watch trailer** button below the movie's details. Opening it loads the YouTube
player inline, without autoplay or animation. **Hide trailer** removes the player
to stop playback; reopening loads a fresh player. On an initial mobile page load,
YouTube is not contacted until a trailer is opened.

On desktop, players load immediately beside the movie details, with no disclosure
button. Switching to the mobile layout collapses and unloads the players;
switching to desktop restores them without autoplay.

The player area immediately shows a static **Loading trailer...** status until
the iframe's load event fires. This reserves the video's space without animation;
it indicates iframe loading, not YouTube's subsequent video buffering. Reported
iframe errors display a retry instruction. There is no separate YouTube link.
Without JavaScript, a message explains that it is needed to watch trailers here.
Inline player loading, loading status, and breakpoint changes are handled by
`layouts/partials/extend_footer.html`; existing shortcode calls need no changes.

Movies have no visible feature-number labels. An **And then...** divider appears
before the second and subsequent movies within each `event`; parties do not
affect this sequence. Year,
runtime, and rating appear as small, bold-text chips with contrasting 2px borders,
with the director on a separate line.

All current movies use original, full-color SVG artwork in `static/posters/`,
not official film posters. Repeat screenings share the same artwork. Each
design shows an illustrated case on the left and a VHS
cassette partly slid out to the right, with vertically stacked reel windows.
Sleeve fronts use an approximately 7.4:4.1 height-to-width ratio, excluding the
perspective bevel.
The covers use restrained, abstract, non-graphic movie-specific motifs. Layouts
vary between artwork-first compositions, boxed lower titles, angled headings,
left/right-aligned titles, paired motifs, and staggered lettering, while the VHS
shape stays consistent. These do not use TMDB assets or require TMDB attribution.
Sleeves also mix saturated and pastel palettes with condensed, serif, monospace,
humanist, heavy sans-serif, and italic title treatments. Titles use system-font
stacks with generic fallbacks, without downloading fonts or changing the site's
typography.
To select artwork, add an optional `poster` to `moviesummary`. New movies without
this parameter retain the automatic title-and-year mockup:

```text
{{<moviesummary title="Movie Title" year="2027" length="90" poster="/posters/movie-title.jpg">}}
A short description of the movie.
{{</moviesummary>}}
```

Put local poster files under `static/posters/`. Poster images are lazy-loaded,
and the full movie title always remains readable beside the poster.

The optional `movietag` image (for example, `movietag="/events/bestof.png"`)
is centered directly above the summary text, independently of the poster and
movie details. Put local tag images under `static/`; they scale down to fit on
small screens.

Home and posts listings include right-aligned **Browse by year** links on the
same row as the left-aligned light/dark selector. On small screens the text label is hidden, keeping the selector and
year buttons on one row; extra years can scroll horizontally. Each link jumps to the
first event for that year on the appropriate existing pagination page; these
are not separate archive pages. Links are generated from published event posts
(including drafts when enabled), skip informational/season-divider posts, and
update automatically when pagination changes.

An event can mix parties and movies in any order. Party rendering belongs
to `party`, and movie layout belongs to `movie`, so the container
does not need to know what kind of event it holds. This also keeps Markdown
rendering separate from trusted shortcode HTML without enabling raw HTML in
the site's Markdown configuration.

Use `event` for all event containers. The old `movienight` alias has been removed.

Preview drafts and future events with `.\test.cmd`. Build published posts,
including future events, with `.\build.cmd`.

## Theme development

The backyard-drive-in layout keeps the original white/light-gray and charcoal
palettes, with neutral headings and accents. Headings and trailer buttons inherit
the original body system-font stack; no font downloads are needed. Arrival dates and times still
come from the post's `title`, not its publication timestamp. There are no theme
animations, press scaling, fades, or smooth scrolling.

For a season break, use `hideBox = true`, `hideTitle = true`, and
`hideMeta = true` in the post's front matter, then use the existing `rawhtml`
shortcode:

```text
{{<rawhtml>}}
<div class="season-divider">
  <p class="season-divider-label">That's a wrap</p>
  <h2>Previous Nights 2026</h2>
</div>
{{</rawhtml>}}
```

This is presentation only: it does not change sorting or automatically group
events by year.

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

Movie details and trailers sit side by side on desktop and stack below 1024px.
Trailers use a 560px-wide cell, constrained to the available content width when
stacked, and keep a 16:9 aspect ratio. Card padding cannot crop them. Responsive
sizing and the mobile disclosure work without JavaScript; loading the inline
player requires it. The same 1023.98px media query drives CSS and player loading.

After changing CSS, increment `params.assets.styleSheetVersion` in `hugo.toml`
to invalidate cached stylesheets. Keep the PaperMod license and CSS attribution
when editing the vendored theme. Upstream updates must be reviewed selectively,
because copying the full theme back in would restore removed features.
