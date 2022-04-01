# og-verticals

Patches Remix to correctly handle Open Graph verticals. This was submitted as [PR#2497](https://github.com/remix-run/remix/pull/2497).

According to the [Open Graph spec](https://ogp.me/#types) you can have "verticals" that have a prefix other than `og:`. These verticals have a prefix that matches the value specified in `og:type` up until the first period.

For example, there is a vertical of "music". Within "music" you can have an `og:type` of "music.song".

When you specify `og:type` of "music.song" you can now have additional meta elements that are prefixed with `music:` (not `og:`) that must also use "property" instead of "name".

For example, this is valid:

```html
<title>Baby's Got Back</title>
<meta property="og:type" content="music.song" />
<meta property="music:musician" content="Sir Mix-a-Lot" />
<meta property="music:album" content="Mack Daddy" />
```

But currently, Remix renders the two "music" meta elements as `name`.

```html
<meta name="music:musician" content="Sir Mix-a-Lot" />
<meta name="music:album" content="Mack Daddy" />
```

## Production issue

I have a real-life example of this bug. My blogging engine uses an `og:type` of "article" and erroneously renders this in production. (see https://donavon.com/blog/remix-locale)

```html
<meta property="og:type" content="article" />
<meta name="article:published_time" content="2022-03-25T00:00:00.000Z" />
```

With this patch, it will render correctly as:

```html
<meta property="og:type" content="article" />
<meta property="article:published_time" content="2022-03-25T00:00:00.000Z" />
```
