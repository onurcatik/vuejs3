# Conditional List Rendering

In this tutorial, we will delve into the process of conditionally rendering a list of elements in Vue.js 3. This is an essential skill for dynamically displaying data based on specific conditions. We will also discuss some best practices and common pitfalls to avoid when working with conditional rendering in Vue.js.

## Objective

Our goal is to render elements from an array based on a condition. Specifically, we will display only certain items from an array, using Vue.js directives. We will explore the correct way to use `v-for` and `v-if` together, ensuring that our implementation adheres to Vue.js best practices.

## Prerequisites

Before proceeding, ensure you have a basic understanding of:

- Vue.js 3 setup
- List rendering using the `v-for` directive
- Conditional rendering using the `v-if` directive

## Example Scenario

Consider an array of names. We aim to display only the name "Bruce" in the user interface.

```javascript
export default {
  data() {
    return {
      names: ['Bruce', 'Clark', 'Diana']
    }
  }
}
```

## Initial Approach

A straightforward method to conditionally render the name "Bruce" might involve combining `v-for` and `v-if` directly in the same element.

```html
<template>
  <div>
    <h2 v-for="(name, index) in names" :key="index" v-if="name === 'Bruce'">
      {{ name }}
    </h2>
  </div>
</template>
```

### Explanation

- `v-for="(name, index) in names"`: Iterates over the `names` array.
- `:key="index"`: Provides a unique key for each element (necessary for efficient rendering).
- `v-if="name === 'Bruce'"`: Conditionally renders the `h2` element if the name is "Bruce".

### Issue with Combining `v-for` and `v-if`

However, combining `v-for` and `v-if` in this manner is discouraged. Vue.js evaluates the `v-if` expression before the `v-for` directive. At the point of evaluation, the `name` alias from `v-for` does not exist, leading to potential errors and unexpected behavior.

### Recommended Approach

Vue.js recommends using computed properties to filter the array before rendering. Alternatively, we can use a `<template>` tag to separate the `v-for` and `v-if` directives.

## Solution Using Computed Properties

Computed properties are a powerful feature in Vue.js that allow us to define reactive properties. These properties automatically update when their dependencies change.

### Step 1: Define a Computed Property

We will create a computed property to filter the `names` array.

```javascript
export default {
  data() {
    return {
      names: ['Bruce', 'Clark', 'Diana']
    }
  },
  computed: {
    filteredNames() {
      return this.names.filter(name => name === 'Bruce');
    }
  }
}
```

### Step 2: Use the Computed Property in the Template

Update the template to use the computed property.

```html
<template>
  <div>
    <h2 v-for="(name, index) in filteredNames" :key="index">
      {{ name }}
    </h2>
  </div>
</template>
```

This approach is clean and efficient, adhering to Vue.js best practices.

## Alternative Solution Using `<template>` Tag

If using computed properties is not preferable for some reason, an alternative solution involves using the `<template>` tag to separate `v-for` and `v-if`.

### Step 1: Update the Template

We will use a `<template>` tag for the `v-for` directive and move the `v-if` directive to an inner element.

```html
<template>
  <div>
    <template v-for="(name, index) in names" :key="index">
      <h2 v-if="name === 'Bruce'">
        {{ name }}
      </h2>
    </template>
  </div>
</template>
```

### Explanation

- `<template v-for="(name, index) in names" :key="index">`: The `<template>` tag is used to iterate over the `names` array without rendering any HTML element.
- `<h2 v-if="name === 'Bruce'">`: The `v-if` directive is applied to the `h2` element, ensuring that only elements with the name "Bruce" are rendered.

## Conclusion

In this tutorial, we explored how to conditionally render a list of elements in Vue.js 3. We learned why combining `v-for` and `v-if` directly is discouraged and demonstrated two solutions: using computed properties and using the `<template>` tag. By following these best practices, we can ensure efficient and error-free rendering in our Vue.js applications.

In the next tutorial, we will start learning about methods in Vue.js. Stay tuned for more advanced topics.

```javascript
export default {
  data() {
    return {
      names: ['Bruce', 'Clark', 'Diana']
    }
  },
  computed: {
    filteredNames() {
      return this.names.filter(name => name === 'Bruce');
    }
  }
}
```

```html
<template>
  <div>
    <h2 v-for="(name, index) in filteredNames" :key="index">
      {{ name }}
    </h2>
  </div>
</template>
```

```html
<template>
  <div>
    <template v-for="(name, index) in names" :key="index">
      <h2 v-if="name === 'Bruce'">
        {{ name }}
      </h2>
    </template>
  </div>
</template>
```
