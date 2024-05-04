# Deep Selectors
We want to style nested elements within a child component, but the CSS is defined in the parent component. How can we achieve this?

## Example
The `BaseChild.vue` component's template has a text with two wrappers:
```VueJS
<div class="base-child-wrapper-1">
  <div class="base-child-wrapper-2">
    <div class="text-green">
      Base Child Component
    </div>
  </div>
</div>
```
If you define the CSS within the `BaseParent.vue` like this:
```VueJS
<style scoped>
.base-child-wrapper-1 .base-child-wrapper-2 .text-green {
  color: green;
}
</style>
```
The CSS definition will not effect to the child component. Since the generate CSS is:
```CSS
<style>
.base-child-wrapper-1 .base-child-wrapper-2 .text-green[data-v-abczyx] {
  color: green;
}
</style>
```
But the DOM of the child component looks like:
```HTML
<div class="base-child-wrapper-1" data-v-abcxyz="">
  <div class="base-child-wrapper-2">
    <div class="text-green">
      Base Child Component
    </div>
  </div>
</div>
```
The expect CSS definition should be like:
```CSS
<style>
.base-child-wrapper-1[data-v-abczyx] .base-child-wrapper-2 .text-green {
  color: green;
}
</style>
```
From the Vue official documentation, the [:deep](https://vuejs.org/api/sfc-css-features.html#deep-selectors) pseudo class may help.

Try fixing the CSS scoped definition inside the parent component:
```CSS
<style scoped>
.base-child-wrapper-1 :deep(.base-child-wrapper-2 .text-green) {
  color: green;
}
</style>
```
The CSS effect should work as expected. For the simply, you can just add `:deep` pseudo class to the target
nested class:

```CSS
<style scoped>
.base-child-wrapper-1 :deep(.text-green) {
  color: green;
}
</style>
```
