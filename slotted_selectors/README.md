# Slotted selectors
From the [Vue official documentation](https://vuejs.org/api/sfc-css-features.html#slotted-selectors):

> By default, scoped styles do not affect contents rendered by <slot/>, as they are considered to be owned by the parent component passing them in. To explicitly target slot content, use the `:slotted` pseudo-class:

```vue
<style scoped>
:slotted(div) {
  color: red;
}
</style>
```

# Example
In this section, we will define the `slot` inside the `BaseChild` component and pass slot within the
`BaseParent` component.

## Define normal scoped style in child component
The slot we pass to the `BaseChild` component looks like below:

```vue
<template>
  <BaseChild>
    <span class="text-blue">Base Child Slots</span>
  </BaseChild>
</template>
```

The CSS definition inside the `BaseChild` component:
```css
<style scoped>
.text-blue {
  color: blue;
}
</style>
```

The slotted element does not get updated with the `text-blue` CSS definition since they are considered to be owned by the parent component passing them in. You can look at the DOM:

// insert image here

**Explanation**: The slotted element does not have the attribute `data-v-...` since it belongs to parent component.
The solution is to add `slotted` pseudo class to CSS definition of the child component:

```css
<style scoped>
:slotted(.text-blue) {
  color: blue;
}
</style>
```
It will make you slotted componets style. Let look at the DOM:

// insert slotted image here

**Explanation**: The slotted element have the attribute `data-v-...-s` then it can apply the CSS scoped from the child component.

## Priority between the slotted scoped style and parent scoped style

Suppose we also define the CSS definition `text-blue` inside the parent component. Which CSS definition gets applied?

```css
// inside the BaseParent.vue component
<style scoped>
.text-blue {
  color: red;
}
</style>
```

Surprised! The CSS definition from the parent component gets updated. Since both CSS definition are the same specificity, my hypothesis is the CSS definition of child component is mounted before the CSS definition of the parent component.

// insert image here

