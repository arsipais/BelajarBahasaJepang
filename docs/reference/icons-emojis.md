## icon: material/emoticon-happy-outline

# Icons, Emojis

One of the best features of Material for MkDocs is the possibility to use [more
than 10,000 icons][icon search] and thousands of emojis in your project
documentation with practically zero additional effort. Moreover, [custom icons
can be added] and used in `mkdocs.yml`, documents and templates.

[icon search]: #search
[custom icons can be added]: ../setup/changing-the-logo-and-icons.md#additional-icons

## Search

<div class="mdx-iconsearch" data-mdx-component="iconsearch">
  <input
    class="md-input md-input--stretch mdx-iconsearch__input"
    placeholder="Search the icon and emoji database"
    data-mdx-component="iconsearch-query"
  />
  <div class="mdx-iconsearch-result" data-mdx-component="iconsearch-result">
    <select
      class="mdx-iconsearch-result__select"
      data-mdx-component="iconsearch-select"
    >
      <option value="all" selected>All</option>
      <option value="icons">Icons</option>
      <option value="emojis">Emojis</option>
    </select>
    <div class="mdx-iconsearch-result__meta"></div>
    <ol class="mdx-iconsearch-result__list"></ol>
  </div>
</div>
<small>
  :octicons-light-bulb-16:
  **Tip:** Enter some keywords to find icons and emojis and click on the
  shortcode to copy it to your clipboard.
</small>

## Configuration

This configuration enables the use of icons and emojis by using simple
shortcodes which can be discovered through the [icon search]. Add the following
lines to `mkdocs.yml`:

```yaml
markdown_extensions:
  - attr_list
  - pymdownx.emoji:
      emoji_index: !!python/name:material.extensions.emoji.twemoji
      emoji_generator: !!python/name:material.extensions.emoji.to_svg
```

The following icon sets are bundled with Material for MkDocs:

- :material-material-design: – [Material Design][Material Design]
- :fontawesome-brands-font-awesome: – [FontAwesome][FontAwesome]
- :octicons-mark-github-16: – [Octicons][Octicons]
- :simple-simpleicons: – [Simple Icons][Simple Icons]

See additional configuration options:

- [Attribute Lists][Attribute Lists]
- [Emoji][Emoji]
- [Emoji with custom icons][Emoji with custom icons]

## Usage

### Using emojis

Emojis can be integrated in Markdown by putting the shortcode of the emoji
between two colons. If you're using [Twemoji] (recommended), you can look up
the shortcodes at [Emojipedia]:

```title="emoji"
:smile:
```

\<div class="result" markdown\>

:smile:

\</div\>
[Twemoji]: https://github.com/jdecked/twemoji
[Emojipedia]: https://emojipedia.org/twitter/

### Using icons

When [Emoji][Emoji] is enabled, icons can be used similar to emojis, by referencing
a valid path to any icon bundled with the theme, which are located in the
[`.icons`][custom icons] directory, and replacing `/` with `-`:

```title="icon"
:fontawesome-regular-face-laugh-wink:
```

\<div class="result" markdown\>

:fontawesome-regular-face-laugh-wink:

\</div\>

#### with colors

When [Attribute Lists][Attribute Lists] is enabled, custom CSS classes can be added to icons by
suffixing the icon with a special syntax. While HTML allows to use [inline
styles][inline styles], it's always recommended to add an [additional style sheet][additional style sheet] and move
declarations into dedicated CSS classes:

\<style\>
.youtube {
color: \#EE0F0F;
}
\</style\>

\=== ":octicons-file-code-16: `docs/stylesheets/extra.css`"

````
``` css
.youtube {
  color: #EE0F0F;
}
```
````

\=== ":octicons-file-code-16: `mkdocs.yml`"

````
``` yaml
extra_css:
  - stylesheets/extra.css
```
````

After applying the customization, add the CSS class to the icon shortcode:

```markdown title="Icon with color"
:fontawesome-brands-youtube:{ .youtube }
```

\<div class="result" markdown\>

:fontawesome-brands-youtube:{ .youtube }

\</div\>

#### with animations

Similar to adding [colors][colors], it's just as easy to add [animations][animations] to icons by
using an [additional style sheet][additional style sheet], defining a `@keyframes` rule and adding a
dedicated CSS class to the icon:

\=== ":octicons-file-code-16: `docs/stylesheets/extra.css`"

````
``` css
@keyframes heart {
  0%, 40%, 80%, 100% {
    transform: scale(1);
  }
  20%, 60% {
    transform: scale(1.15);
  }
}
.heart {
  animation: heart 1000ms infinite;
}
```
````

\=== ":octicons-file-code-16: `mkdocs.yml`"

````
``` yaml
extra_css:
  - stylesheets/extra.css
```
````

After applying the customization, add the CSS class to the icon shortcode:

```markdown title="Icon with animation"
:octicons-heart-fill-24:{ .heart }
```

\<div class="result" markdown\>

:octicons-heart-fill-24:{ .mdx-heart }

\</div\>

### Icons, emojis in sidebars :smile:

With the help of the [built-in typeset plugin][built-in typeset plugin], you can use icons and emojis
in headings, which will then be rendered in the sidebars. The plugin preserves
Markdown and HTML formatting.

## Customization

### Using icons in templates

When you're [extending the theme][extending the theme] with partials or blocks, you can simply
reference any icon that's [bundled with the theme][icon search] with Jinja's
[`include`][include] function and wrap it with the `.twemoji` CSS class:

```html
<span class="twemoji">
  {% include ".icons/fontawesome/brands/youtube.svg" %}
</span>
```

1.  Enter a few keywords to find the perfect icon using our [icon search] and
    click on the shortcode to copy it to your clipboard:

    \<div class="mdx-iconsearch" data-mdx-component="iconsearch"\>
    \<input class="md-input md-input--stretch mdx-iconsearch\_\_input" placeholder="Search icon" data-mdx-component="iconsearch-query" value="brands youtube" /\>
    \<div class="mdx-iconsearch-result" data-mdx-component="iconsearch-result" data-mdx-mode="file"\>
    \<div class="mdx-iconsearch-result\_\_meta"\>\</div\>
    \<ol class="mdx-iconsearch-result\_\_list"\>\</ol\>
    \</div\>
    \</div\>

This is exactly what Material for MkDocs does in its templates.

```

```

[material design]: https://pictogrammers.com/library/mdi/
[fontawesome]: https://fontawesome.com/search?m=free
[octicons]: https://octicons.github.com/
[simple icons]: https://simpleicons.org/
[attribute lists]: https://www.google.com/search?q=../setup/extensions/python-markdown.md%23attribute-lists
[emoji]: https://www.google.com/search?q=../setup/extensions/python-markdown-extensions.md%23emoji
[emoji with custom icons]: https://www.google.com/search?q=../setup/extensions/python-markdown-extensions.md%23%2Bpymdownx.emoji.options.custom_icons
[emoji]: ../setup/extensions/python-markdown-extensions.md#emoji
[custom icons]: https://github.com/squidfunk/mkdocs-material/tree/master/material/templates/.icons
[attribute lists]: ../setup/extensions/python-markdown.md#attribute-lists
[inline styles]: https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/style
[additional style sheet]: https://www.google.com/search?q=../customization.md%23additional-css
[colors]: https://www.google.com/search?q=%23with-colors
[animations]: https://developer.mozilla.org/en-US/docs/Web/CSS/animation
[built-in typeset plugin]: https://www.google.com/search?q=../plugins/typeset.md
[extending the theme]: https://www.google.com/search?q=../customization.md%23extending-the-theme
[include]: https://jinja.palletsprojects.com/en/2.11.x/templates/#include
[extending the theme]: ../customization.md#extending-the-theme
[include]: https://jinja.palletsprojects.com/en/2.11.x/templates/#include
