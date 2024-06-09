# Binding Classes

In this tutorial, we will delve into attribute binding in Vue.js 3, specifically focusing on the `class` attribute. We'll explore both static and dynamic class bindings and learn how to manipulate an element's classes based on application state. This tutorial assumes you have a basic understanding of Vue.js and its directives.

## Basic Static Class Binding

Let's begin by defining a static class in our Vue component. Static classes are always present on the HTML element and do not change.

### Step 1: Define a Class in the Style Block

First, define a new class in the `<style>` block:

```html
<style>
.underline {
    text-decoration: underline;
}
</style>
```

### Step 2: Apply the Class in the Template

Next, apply this class to an HTML element within the `<template>` block:

```html
<template>
  <h2 class="underline">Underlined Text</h2>
</template>
```

When you save and view this in the browser, the text should appear underlined, demonstrating the application of the static class.

## Dynamic Class Binding

Dynamic classes allow us to change the class applied to an element based on the application's state. This is where Vue's `v-bind` directive comes into play.

### Step 1: Define Data Properties

In your Vue component, define a data property to control the dynamic class:

```javascript
<script>
export default {
  data() {
    return {
      status: 'danger'
    }
  }
}
</script>
```

### Step 2: Bind the Class Attribute

Use the `v-bind` directive to bind the `status` property to the class attribute of an HTML element:

```html
<template>
  <h2 :class="status">Status Text</h2>
</template>
```

Now, when you view this in the browser, the class `danger` will be applied. Changing the `status` property to, for example, `success` will dynamically apply the `success` class.

## Combining Static and Dynamic Classes

You can combine both static and dynamic classes on the same element. This is useful for applying static styles that don't change alongside dynamic styles that do.

```html
<template>
  <h2 class="underline" :class="status">Status with Underline</h2>
</template>
```

This will apply both the `underline` class and the dynamic class specified by `status`.

## Conditional Class Binding

Vue allows for more advanced class binding using JavaScript expressions, such as the logical AND (`&&`) operator and ternary operator.

### Logical AND Operator

Define a new class in the `<style>` block:

```html
<style>
.promoted {
    font-style: italic;
}
</style>
```

Add a data property to control the condition:

```javascript
<script>
export default {
  data() {
    return {
      isPromoted: true
    }
  }
}
</script>
```

Use the logical AND operator to conditionally apply the `promoted` class:

```html
<template>
  <h2 :class="isPromoted && 'promoted'">Promoted Movie</h2>
</template>
```

If `isPromoted` is `true`, the `promoted` class will be applied. Otherwise, it won't.

### Ternary Operator

For more complex conditions, use the ternary operator. Define additional classes and data properties:

```html
<style>
.new {
    color: green;
}
.sold-out {
    color: red;
}
</style>
```

```javascript
<script>
export default {
  data() {
    return {
      isSoldOut: true
    }
  }
}
</script>
```

Use the ternary operator for conditional binding:

```html
<template>
  <h2 :class="isSoldOut ? 'sold-out' : 'new'">Conditional Movie</h2>
</template>
```

If `isSoldOut` is `true`, the `sold-out` class will be applied. Otherwise, the `new` class will be applied.

## Binding Classes with Arrays and Objects

### Using Arrays

You can bind multiple classes using an array. This is useful when you need to apply multiple classes dynamically.

```html
<template>
  <h2 :class="['new', isPromoted && 'promoted']">Newly Promoted Movie</h2>
</template>
```

If `isPromoted` is `true`, both `new` and `promoted` classes will be applied.

### Using Objects

Binding classes with an object allows for clearer conditional logic. Each key in the object is a class name, and the value is a boolean expression.

```html
<template>
  <h2 :class="{ promoted: isPromoted, 'sold-out': isSoldOut, new: !isSoldOut }">Object Conditional Movie</h2>
</template>
```

This example applies the `promoted` class if `isPromoted` is `true`, `sold-out` class if `isSoldOut` is `true`, and `new` class if `isSoldOut` is `false`.

## Conclusion

In this tutorial, we covered the basics of binding classes in Vue.js 3, including static and dynamic class bindings, conditional class bindings using logical and ternary operators, and advanced bindings using arrays and objects. This flexibility allows you to create highly dynamic and responsive UI elements based on the state of your application.

By understanding these techniques, you can effectively manage and manipulate classes in your Vue.js applications, leading to cleaner and more maintainable code.

```html
<template>
  <div>
    <h2 class="underline">Underlined Text</h2>
    <h2 :class="status">Status Text</h2>
    <h2 class="underline" :class="status">Status with Underline</h2>
    <h2 :class="isPromoted && 'promoted'">Promoted Movie</h2>
    <h2 :class="isSoldOut ? 'sold-out' : 'new'">Conditional Movie</h2>
    <h2 :class="['new', isPromoted && 'promoted']">Newly Promoted Movie</h2>
    <h2 :class="{ promoted: isPromoted, 'sold-out': isSoldOut, new: !isSoldOut }">Object Conditional Movie</h2>
  </div>
</template>

<script>
export default {
  data() {
    return {
      status: 'danger',
      isPromoted: true,
      isSoldOut: true
    }
  }
}
</script>

<style>
.underline {
    text-decoration: underline;
}
.promoted {
    font-style: italic;
}
.new {
    color: green;
}
.sold-out {
    color: red;
}
</style>
```

By following this tutorial, you should now have a solid understanding of how to bind classes in Vue.js 3.