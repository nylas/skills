---
title: Email-Safe HTML
section: template
---

## Email-Safe HTML

- **Layout:** tables, with `role="presentation"` on every layout table. Don't use flexbox, grid, or `position`.
- **Styles:** inline on every element. A `<style>` block is fine for a mobile media query.
- **Width:** about 600 to 700px for the content, collapsing to full width on small screens.
- **Preheader:** a hidden `<div>` right after `<body>`. It's the preview line in the inbox.
- **Buttons:** a table cell with a background color, holding a padded `<a>`. Never use `<button>`.
- **Backgrounds and corners:** Gmail drops CSS gradients, and Outlook for Windows ignores rounded corners. Set a solid `bgcolor` behind any gradient.
- **Images:** use absolute `https://` URLs on a host that allows cross-origin loading, with `alt` text and an explicit `width`.
- **Long values:** set `word-break: break-word` on cells that hold titles, names, or email addresses, and `break-all` on bare URLs.
- **Fonts:** if you use a web font, list `Helvetica, Arial, sans-serif` after it.
- **Never:** JavaScript, forms, iframes, or video.

**Copy and subjects.**
- **Headline:** say what happened in a few words.
- **Body:** say what the reader needs, then what they can do.
- **Subjects** are templates too, so guard their variables. Gmail threads emails with the same subject, so include something specific, such as the meeting title.
