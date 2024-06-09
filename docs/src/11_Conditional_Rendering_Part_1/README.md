# Conditional Rendering - 1

## Introduction

When developing Vue.js applications, it is often necessary to show or hide certain HTML elements based on specific conditions. Vue.js provides a straightforward way to handle conditional rendering with the use of directives. In this tutorial, we will explore three primary directives for conditional rendering: `v-if`, `v-else`, and `v-else-if`. We will discuss the `v-show` directive in the next tutorial. Let's begin by understanding these directives through a simple example.

## Conditional Rendering with `v-if`, `v-else`, and `v-else-if`

### Example Scenario

Consider a scenario where we have a variable `num` that can be 0, a positive number, a negative number, or NaN (not a number). We want to conditionally display different messages based on the value of this variable.

### Step 1: Initial Setup

First, we need to set up our Vue.js application with the necessary data property. Let's add a new data property `num` and initialize it to 0.

```javascript
<template>
  <div id="app">
    <!-- Conditionally render based on the value of num -->
    <h2 v-if="num === 0">The number is zero</h2>
    <h2 v-else>The number is not zero</h2>
  </div>
</template>

<script>
export default {
  data() {
    return {
      num: 0
    };
  }
};
</script>
```

In the above code, we use the `v-if` directive to check if `num` is zero. If the condition is true, the first `<h2>` element is rendered. Otherwise, the second `<h2>` element is displayed using the `v-else` directive.

### Step 2: Adding More Conditions

To handle more conditions, we need to introduce the `v-else-if` directive. Let's extend our example to display messages for positive numbers, negative numbers, and NaN.

```javascript
<template>
  <div id="app">
    <h2 v-if="num === 0">The number is zero</h2>
    <h2 v-else-if="num < 0">The number is negative</h2>
    <h2 v-else-if="num > 0">The number is positive</h2>
    <h2 v-else>The number is not a number</h2>
  </div>
</template>

<script>
export default {
  data() {
    return {
      num: 0
    };
  }
};
</script>
```

Now, our template includes additional `<h2>` elements with `v-else-if` directives to check if `num` is negative or positive. The final `v-else` directive catches any other case, such as `num` being NaN.

### Step 3: Validating the Example

To ensure our conditional rendering works as expected, we can manually change the value of `num` and observe the displayed messages:

- If `num` is 5: "The number is positive"
- If `num` is -5: "The number is negative"
- If `num` is 0: "The number is zero"
- If `num` is NaN: "The number is not a number"

### Step 4: Multiple Elements with the Same Condition

There might be cases where we need to conditionally render multiple elements based on the same condition. Instead of repeating the condition on each element, we can use a `<template>` tag to act as an invisible wrapper.

First, add a new data property `display` and set it to `true`. Then, conditionally render multiple elements within a `<template>` tag.

```javascript
<template>
  <div id="app">
    <template v-if="display">
      <h2>Vishwas</h2>
      <h2>Code Evolution</h2>
      <h2>Vue.js</h2>
    </template>
  </div>
</template>

<script>
export default {
  data() {
    return {
      display: true,
      num: 0
    };
  }
};
</script>
```

In this example, the `<template>` tag allows us to conditionally render multiple elements without introducing an extra `<div>` in the DOM. This can be particularly useful for maintaining the layout and avoiding unnecessary wrappers.

## Conclusion

In this tutorial, we explored the `v-if`, `v-else`, and `v-else-if` directives for conditional rendering in Vue.js. We also discussed how to conditionally render multiple elements using the `<template>` tag. Understanding these directives is crucial for efficiently managing the display logic in your Vue.js applications. Stay tuned for the next tutorial, where we will dive into the `v-show` directive for conditional rendering.

### Code Summary

Here's the complete code used in this tutorial for reference:

```javascript
<template>
  <div id="app">
    <h2 v-if="num === 0">The number is zero</h2>
    <h2 v-else-if="num < 0">The number is negative</h2>
    <h2 v-else-if="num > 0">The number is positive</h2>
    <h2 v-else>The number is not a number</h2>

    <template v-if="display">
      <h2>Vishwas</h2>
      <h2>Code Evolution</h2>
      <h2>Vue.js</h2>
    </template>
  </div>
</template>

<script>
export default {
  data() {
    return {
      num: 0,
      display: true
    };
  }
};
</script>
```

By following these steps, you can effectively manage conditional rendering in your Vue.js applications.