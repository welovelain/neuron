---
tags: [custom-head-recipe]
---

# Using Tailwind CSS classes

Neuron provides [Semantic UI](https://fomantic-ui.com/) already, however you can use other CSS toolkits as well. [Tailwind](https://tailwindcss.com/) in particular is a note-worthy one as it allows you to style elements using pre-defined *semantically defined* classes. 

First, activate Tailwind using [`twind/shim`](https://twind.dev/docs/modules/twind_shim.html), in your `head.html` (see [[Custom JavaScript and CSS]]):

```html
<!-- 
cf. https://github.com/tw-in-js/twind/discussions/161#discussioncomment-535632
-->
<script crossorigin="anonymous" src="https://cdn.jsdelivr.net/combine/npm/twind/twind.umd.min.js,npm/twind/observe/observe.umd.min.js"></script>
<script type="text/javascript">
   twind.setup(
    {
      mode: 'silent',  // Behave well with semantic UI classes
      preflight: () => {
        return {
           // Custom styles based on selectors go here (use the selector in Markdown; see below)
           ".my-highlight": twind.apply("bg-yellow-100 text-green-500 font-bold p-2"
        }
      }
    }
  );
  twindObserve.observe(document.documentElement)
</script>
<!-- End of Twind script -->
```

That's it; now you can use any of the Tailwind CSS classes in your Markdown files. Here's an example:

```markdown
## Highlights of the day:

:::{.rounded .shadow-2xl .border-2 .border-solid .border-pink-400 .text-xl .mb-4}
- Drank a [new]{.my-highlight} type of *coffee*
- Hacked a new feature to my pet project
- Enjoyed doing nothing in particular
:::

Random bits:
- These are not styled like the above div.
```

## Live example

See https://www.srid.ca/now (the pink box)
