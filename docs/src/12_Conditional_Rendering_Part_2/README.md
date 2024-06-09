# Conditional Rendering - 2

In this tutorial, we will delve into the `v-show` directive in Vue.js, a powerful tool for conditionally displaying HTML elements. This tutorial follows the previous exploration of `v-if`, `v-else-if`, and `v-else` directives, providing a detailed comparison between `v-show` and `v-if` directives and explaining the use cases for each.

## Understanding `v-show`

The `v-show` directive in Vue.js is used to conditionally display an HTML element based on the evaluation of a JavaScript expression. If the expression evaluates to `true`, the element will be visible; if it evaluates to `false`, the element will be hidden. Unlike `v-if`, `v-show` does not add or remove the element from the DOM; instead, it toggles the element's `display` CSS property.

### Example of `v-show`

Consider the following example:

```html
<template>
  <div>
    <h2 v-show="showElement">Using v-show</h2>
    <button @click="toggleElement">Toggle Element</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      showElement: true
    };
  },
  methods: {
    toggleElement() {
      this.showElement = !this.showElement;
    }
  }
};
</script>
```

In this example, the `h2` element is conditionally displayed using the `v-show` directive. The `showElement` data property is bound to `v-show`, and a button toggles its value between `true` and `false`.

### Behavior of `v-show`

When `showElement` is `true`, the `h2` element is visible. When `showElement` is `false`, the `h2` element is hidden by setting its `display` CSS property to `none`. Importantly, the element remains in the DOM regardless of its visibility.

### Difference between `v-show` and `v-if`

To understand the differences between `v-show` and `v-if`, let’s consider another example:

```html
<template>
  <div>
    <h2 v-show="showElement">Using v-show</h2>
    <h2 v-if="showElement">Using v-if</h2>
    <button @click="toggleElement">Toggle Element</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      showElement: true
    };
  },
  methods: {
    toggleElement() {
      this.showElement = !this.showElement;
    }
  }
};
</script>
```

When `showElement` is set to `true`, both `h2` elements will be displayed. Upon toggling `showElement` to `false`:

- The `v-show` element remains in the DOM but is hidden (its `display` property is set to `none`).
- The `v-if` element is completely removed from the DOM.

### Inspecting the DOM

Inspecting the DOM when `showElement` is `false` will reveal the following:

- The element with `v-show` is present but hidden:

  ```html
  <h2 style="display: none;">Using v-show</h2>
  ```

- The element with `v-if` is not present in the DOM:

  ```html
  <!-- The `v-if` element is not rendered in the DOM -->
  ```

### When to Use `v-show` vs `v-if`

The choice between `v-show` and `v-if` depends on the specific use case:

- **Use `v-show`** when you need to toggle the visibility of an element frequently. Since `v-show` does not remove the element from the DOM, it avoids the cost of re-rendering the element.
- **Use `v-if`** when the condition is unlikely to change frequently during runtime. `v-if` is more appropriate for cases where you do not want the element in the DOM if the condition is false, as it completely removes the element and its associated listeners and data bindings.

### Summary

The `v-show` directive offers a way to conditionally display elements without removing them from the DOM, enhancing performance for elements that need to be frequently toggled. Conversely, `v-if` is suitable for elements that should be completely removed from the DOM when not needed. Understanding the nuances between these directives is crucial for optimizing your Vue.js applications.

In conclusion, Vue.js provides four primary directives for conditional rendering:

- `v-if`
- `v-else-if`
- `v-else`
- `v-show`

Each serves a specific purpose, allowing you to manage the DOM efficiently and tailor the user interface to various conditions dynamically. Remembering how each directive works and their appropriate use cases will significantly enhance your development process.

In the next tutorial, we will explore rendering a list of elements in Vue.js, continuing to build on our understanding of Vue's core concepts.
