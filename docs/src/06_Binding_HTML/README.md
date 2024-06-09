# Binding HTML

## Introduction
In this tutorial, we will explore how to bind HTML content in Vue.js 3 using the `v-html` directive. This is particularly useful when dealing with rich text editors or any scenario where you need to render raw HTML content in the user interface (UI). It is important to understand the differences between the `mustache` syntax, `v-text`, and `v-html` directives, especially concerning security implications.

## Understanding Data Binding in Vue.js
### Mustache Syntax and `v-text` Directive
In Vue.js, data binding to the UI is commonly done using the `mustache` syntax (`{{ }}`) or the `v-text` directive. Both of these methods interpret the bound data as plain text, which means any HTML tags within the data will be rendered as text, not as HTML elements.

### Example
Consider the following Vue component:
```vue
<template>
  <div>
    <p>{{ channel }}</p>
    <p v-text="channel"></p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      channel: '<b>Code Evolution</b>'
    }
  }
}
</script>
```
In this example, the `channel` property contains a string with HTML bold tags. However, when using `{{ channel }}` or `v-text="channel"`, the output will display the HTML tags as plain text:
```
<b>Code Evolution</b>
<b>Code Evolution</b>
```

## Rendering HTML with `v-html`
To render the `channel` property as HTML, we use the `v-html` directive. This directive interprets the bound data as HTML, allowing the tags to be rendered correctly.

### Example
Modify the previous example to use `v-html`:
```vue
<template>
  <div>
    <p v-html="channel"></p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      channel: '<b>Code Evolution</b>'
    }
  }
}
</script>
```
With `v-html`, the output will correctly render the HTML:
**Code Evolution**

### Important Security Consideration
Using `v-html` comes with significant security risks, particularly related to Cross-Site Scripting (XSS) attacks. Only use `v-html` with trusted content, as rendering content from untrusted sources can make your application vulnerable.

### Security Warning Example
Consider the following scenario where an untrusted content is rendered:
```vue
<template>
  <div>
    <p v-html="hack"></p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      hack: '<a href="#" onclick="alert(\'You have been hacked!\')">Win a prize</a>'
    }
  }
}
</script>
```
In this example, the `hack` property contains a malicious script. When the rendered link is clicked, it triggers an alert with a potentially alarming message:
```
Win a prize
```
Clicking on "Win a prize" will display an alert: "You have been hacked!"

### Mitigating Security Risks
To mitigate security risks:
1. **Sanitize HTML**: Ensure that any HTML content is sanitized before rendering it with `v-html`. Libraries such as [DOMPurify](https://github.com/cure53/DOMPurify) can be used to clean the HTML content.
2. **Limit Usage**: Use `v-html` sparingly and only when absolutely necessary. Avoid using it with content from untrusted sources.

### Example with Sanitization
Using DOMPurify to sanitize HTML content:
```vue
<template>
  <div>
    <p v-html="safeHtml"></p>
  </div>
</template>

<script>
import DOMPurify from 'dompurify';

export default {
  data() {
    return {
      rawHtml: '<a href="#" onclick="alert(\'You have been hacked!\')">Win a prize</a>'
    }
  },
  computed: {
    safeHtml() {
      return DOMPurify.sanitize(this.rawHtml);
    }
  }
}
</script>
```
In this example, the raw HTML is sanitized before being rendered, reducing the risk of XSS attacks.

## Conclusion
Using the `v-html` directive in Vue.js 3 allows for rendering HTML content in the UI. While it is a powerful feature, it must be used with caution to avoid security vulnerabilities. Always sanitize untrusted content and prefer using safer alternatives when possible. Understanding and applying these practices ensures that your Vue.js applications remain secure and reliable.