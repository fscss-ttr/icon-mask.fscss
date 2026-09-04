# icon-mask

**icon-mask** is a lightweight FSCSS-based library for SVG icon rendering using the CSS `mask-image` technique. It provides a collection of ready-to-use icon macros that render inline SVG icons purely through CSS — no `<img>` tags, no external icon fonts, no JS.

- **Color control:** `icon-color(color)` sets a CSS variable used by all icons, making it trivial to theme or override per-component.
- **Size control:** `icon-size(size)` sets the icon dimensions via a CSS variable with a sensible default of `24px`.
- **Base setup:** `icon-base(elem, size)` applies the shared mask properties — `mask-repeat`, `mask-position`, `mask-size`, `background-color`, and `display` — to any selector.
- **Icon macros:** 24 individual icon definitions including `icon-home`, `icon-chart`, `icon-settings`, `icon-users`, `icon-messages`, `icon-notifications`, `icon-calendar`, `icon-files`, `icon-tasks`, `icon-teams`, `icon-reports`, `icon-support`, `icon-inbox`, `icon-logout`, `icon-profile`, `icon-search`, `icon-filter`, `icon-download`, `icon-upload`, `icon-star`, `icon-clock`, `icon-alert`, `icon-menu`, and `icon-times`.
- **Pack macro:** `icon-pack()` outputs all icons and the base setup in a single call.
- **Dynamic shorthand:** `icon(name)` resolves any icon by name at compile time.

icon-mask is implemented entirely in FSCSS, following the same **FSCSS libraries logic** as libraries like [circle-progress](https://github.com/Figsh/Circle-progress.fscss) and [st-core](https://github.com/fscss-ttr/st-core.fscss).

## Installation

Include FSCSS v1.1.24 or higher, then import **icon-mask** via `@import`:

```
<script src="https://cdn.jsdelivr.net/npm/fscss@1.2.0/runtime.min.js" defer></script>
```

This (better)

```
@import(exec(_init icon-mask))
```

Or this

```
@import((*) from icon-mask)
```

The library supports FSCSS **1.1.24+**. Once imported, all `icon-*` macros are available in your stylesheet.

## Usage

### Quick setup with the full pack

```
@icon-pack()
```

This outputs the base `.icon` styles and all 24 icon classes in one call.

### Manual setup

```
@icon-base()
@icon-home()
@icon-chart()
@icon-settings()
```

### Theming

```
:root {
  @icon-color(#10b981)
  @icon-size(20px)
}
```

### Dynamic icon by name

```
@icon(home)
@icon(chart)
@icon(notifications)
```

This resolves to `@icon-home()`, `@icon-chart()`, `@icon-notifications()` at compile time.

### Custom selector

Each icon macro accepts an optional class override:

```
@icon-home(.nav-home)
@icon-chart(.sidebar-chart)
```

### Custom base element

```
@icon-base(.my-icon, 32px)
```

## Example

**https://hub.devtem.org/fscss-modules/example/dashboard.html**

```html
<script src="https://cdn.jsdelivr.net/npm/fscss@1.2.0/runtime.min.js" defer></script>
<style>
@import(exec(*) from icon-mask)

:root {
  @icon-color(#6366f1)
  @icon-size(24px)
}

@icon-pack()

.icon-lg {
  @icon-size(32px)
}

.icon-accent {
  @icon-color(#f43f5e)
}
</style>

<span class="icon icon-home"></span>
<span class="icon icon-chart"></span>
<span class="icon icon-notifications"></span>
<span class="icon icon-settings"></span>
<span class="icon icon-profile"></span>
```

All icons are pure CSS elements — no inner HTML required. Color and size are controlled entirely through CSS variables, making them trivial to override at any scope.

## Plugin Reference

| Macro | Output summary |
|---|---|
| `@icon-color(color)` | Sets `--f-icon-color` |
| `@icon-size(size)` | Sets `--f-icon-size` |
| `@icon-base(elem, size)` | Applies shared mask + display styles |
| `@icon-home(class)` | Home icon mask |
| `@icon-chart(class)` | Bar chart icon mask |
| `@icon-settings(class)` | Settings/gear icon mask |
| `@icon-users(class)` | Users icon mask |
| `@icon-messages(class)` | Chat bubble icon mask |
| `@icon-notifications(class)` | Bell icon mask |
| `@icon-calendar(class)` | Calendar icon mask |
| `@icon-files(class)` | Document icon mask |
| `@icon-tasks(class)` | Clipboard/tasks icon mask |
| `@icon-teams(class)` | Team/group icon mask |
| `@icon-reports(class)` | Report/chart doc icon mask |
| `@icon-support(class)` | Lifering/support icon mask |
| `@icon-inbox(class)` | Inbox icon mask |
| `@icon-logout(class)` | Logout/arrow icon mask |
| `@icon-profile(class)` | Single user icon mask |
| `@icon-search(class)` | Magnifier icon mask |
| `@icon-filter(class)` | Sliders/filter icon mask |
| `@icon-download(class)` | Download arrow icon mask |
| `@icon-upload(class)` | Upload arrow icon mask |
| `@icon-star(class)` | Star icon mask |
| `@icon-clock(class)` | Clock icon mask |
| `@icon-alert(class)` | Triangle alert icon mask |
| `@icon-menu(class)` | Hamburger menu icon mask |
| `@icon-times(class)` | Close/X icon mask |
| `@icon-pack()` | All of the above in one call |
| `@icon(name)` | Dynamic icon by name |

## License

icon-mask is open source and free to use under the MIT License.
