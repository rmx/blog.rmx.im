---
layout: post
title: "It started as an attempt to make the editor more user-friendly"
---

In our last blog post we mentionend that we were rewriting the editor. We have
rewritten it yet again since!

The initial motivation was to make the editor more user-friendly. We achieved
that with the first rewrite. However, we saw that Polymer is not really
suitable for web applications. So at some point we've rewritten the rendering
code to use [React][react].

<span class="center">
    <span class="shadow">
        ![img](/assets/encounters-collection.png)
    </span>
</span>

The underlying data structure remained the same. It has much more explicit
structure than before. Instead of writing more or less free form scripts,
you now enter number into input fields, select checkboxes, pick items from
dropdown menus and so on.

<figure class="supporting">
    <span class="shadow">
        ![img](/assets/aura-main-view.png)
    </span>
</figure>

The main aura editor for example is now much easier to use. As you see on the
left, to configure the basic aura properties, you don't need to write a single
line of code.

We've also recently enabled account registration in the new client. You can go
to [rmx.im/signup](https://rmx.im/signup) and create an account. The permission
system is not fully in place yet, you will not be able to create or modify
objects. But at least you'll get a feel for the editor. **Note: rmx.im currently
only works with Chrome Canary (Chrome 36 or later)**.

[react]: https://facebook.github.io/react/
