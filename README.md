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
{{< event >}}
{{< party title="Game Night" >}}
Bring a **favorite game** to share.

- Games start at 8 PM.
- [See the details](https://example.com).
{{< /party >}}
{{< /event >}}
```

For a heading-only party, leave the `party` body empty. Omit its `title` for a
body-only party. Each party can have its own heading, and an event can contain
multiple parties. Events work in post
listings and on the individual post page.

## Movie nights

A movie night is simply an event containing movies. Each `movie` provides its
own table layout, using `moviesummary` and an optional `movietrailer`:

```text
{{< event >}}
{{< movie >}}
{{< moviesummary title="Movie Title" year="2027" length="90" >}}
A short description of the movie.
{{< /moviesummary >}}
{{< movietrailer YOUTUBE_VIDEO_ID >}}
{{< /movie >}}
{{< /event >}}
```

An event can mix parties and movies in any order. Party rendering belongs
to `party`, and movie layout belongs to `movie`, so the container
does not need to know what kind of event it holds. This also keeps Markdown
rendering separate from trusted shortcode HTML without enabling raw HTML in
the site's Markdown configuration.

The `movienight` shortcode remains a compatibility alias for `event`; new posts
should use `event`.

Preview drafts and future events with `.\test.cmd`. Build published posts,
including future events, with `.\build.cmd`.
