# Binding Text

## Introduction

In this tutorial, we will discuss how to bind text from the script block to the template block in Vue.js. This is a fundamental aspect of data-driven web applications where the content displayed in the browser needs to dynamically change based on the application state. We will explore two main methods for text binding in Vue.js: the mustache syntax and the `v-text` directive.

## Single File Components Recap

In the previous tutorial, we covered single file components in Vue.js. A single file component typically includes three sections:

1. **Template Block**: Defines the HTML structure.
2. **Script Block**: Contains the data and logic for the template block.
3. **Style Block**: Contains the styles for the component.

The script block is responsible for providing the data and the logic that the template block uses to render the UI. 

## Binding Text from Script to Template

### Static Text Example

Consider the following example where we have static text in our template:

```html
<template>
  <div>Hello Vishwas</div>
</template>

<script>
export default {
  name: 'App'
}
</script>
```

When you save this file and view it in the browser, you will see the text "Hello Vishwas". However, this text is static and cannot change based on the application state.

### Dynamic Text Binding with Mustache Syntax

To create a dynamic UI, we need to bind data from the script block to the template block. This is done using the mustache syntax, which consists of double curly braces `{{ }}`. Here is how you can bind a property from the data object to the template:

```html
<template>
  <div>{{ greet }} {{ name }}</div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      greet: 'Hello',
      name: 'Vishwas'
    }
  }
}
</script>
```

In this example:
- The `greet` property is set to "Hello".
- The `name` property is set to "Vishwas".

When you save this file and view it in the browser, you will see "Hello Vishwas". The mustache syntax `{{ greet }} {{ name }}` dynamically inserts the values of `greet` and `name` properties into the HTML.

### Updating Bound Data

The mustache syntax allows the template to dynamically update when the data properties change. For example, if you change the `name` property to "Batman":

```html
<template>
  <div>{{ greet }} {{ name }}</div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      greet: 'Hello',
      name: 'Batman'
    }
  }
}
</script>
```

The displayed text will automatically update to "Hello Batman".

### Using the `v-text` Directive

Vue.js provides another way to bind text using the `v-text` directive. This directive replaces the entire text content of an HTML element with the value of a specified data property.

Example:

```html
<template>
  <div v-text="channel"></div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      channel: 'Code Evolution'
    }
  }
}
</script>
```

In this case, the `div` element will display "Code Evolution".

#### Limitation of `v-text`

The `v-text` directive replaces the entire content of the HTML element. Therefore, it cannot be used to concatenate static and dynamic text within the same element. For instance, the following code will result in an error:

```html
<template>
  <div>
    Hello
    <span v-text="name"></span>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      name: 'Batman'
    }
  }
}
</script>
```

The above code will not work as expected because `v-text` will overwrite the entire content of the `span` element.

### Summary

In Vue.js, there are two primary ways to bind text:

1. **Mustache Syntax**: `{{ }}`
   - Can be used for partial or full text content within an HTML element.
   - Automatically updates the UI when the bound data property changes.
   - Preferred for its flexibility and slightly better performance.

2. **`v-text` Directive**: `v-text="property"`
   - Replaces the entire text content of an HTML element.
   - Useful for simple text bindings but less flexible than mustache syntax.

Both methods are important to understand, although the mustache syntax is more commonly used in practice. 

## Conclusion

This tutorial covered the basics of binding text in Vue.js using both mustache syntax and the `v-text` directive. Understanding these concepts is crucial for building dynamic and responsive web applications. In the next tutorial, we will explore another powerful Vue.js directive that is frequently used in real-world applications.

By mastering these techniques, you will be well on your way to creating dynamic, data-driven user interfaces with Vue.js.