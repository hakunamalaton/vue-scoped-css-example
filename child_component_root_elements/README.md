# Child Component Root Elements
From Vue documentation:

> With scoped, the parent component's styles will not leak into child components. However, a child component's root node will be affected by both the parent's scoped CSS and the child's scoped CSS. This is by design so that the parent can style the child's root element for layout purposes.

The example will help you understand the sentence `However, a child component's root node will be affected by both the parent's scoped CSS and the child's scoped CSS` easily.

## The Example
Inside `child_component_root_elements` folder, there are two components:
- `BaseParent.vue`
- `BaseChild.vue`

The `BaseParent.vue` component imports and uses the `BaseChild.vue` component. So we can say the `BaseParent.vue` is the parent component, and the `BaseChild.vue` is the child component.

Inside the `BaseParent.vue` component, we define the `text-red` scoped CSS like below:

```CSS
// inside BaseParent.vue
<style scoped>
.text-red {
  color: red;
}
</style>
```
### Example 1
Inside the `BaseChild.vue` component, we use `text-red` CSS definition at the **root node**. The root node
of the component is the outest level block of a component. A component can have multiple root nodes. For
the related documentation, please reach it at [Attribute Inheritance on Multiple Root Nodes](https://vuejs.org/guide/components/attrs.html#attribute-inheritance-on-multiple-root-nodes).

### The result 1
The `BaseChild.vue` component applies the `text-red` CSS definition. The reason is by the design of the Vue team so that **the parent can style the child root element for layout purposes**.
<img width="930" alt="Screenshot 2024-05-02 at 00 57 02" src="https://github.com/hakunamalaton/vue-scoped-css-example/assets/84494783/9d601ff7-540d-4ff4-adaa-df3068d397fc">

You can try add the outer level `div` inside the `BaseChild.vue` like this:

```VueJS
<script setup></script>

<template>
  <div>
    <div class="text-red">Base Child Component</div>
  </div>
</template>
```

The `Base Child Component` text does not apply the `text-red` CSS definition since it is not the root node of the `BaseChild.vue` anymore.

### Example 2
In this example, we are going to test the priority between the CSS definition inside the parent component
and the child component.
We define another CSS definition `text-blue` inside the child component `BaseChild.vue`. These classes
`text-red` and `blue-text` are applied to the `BaseChild.vue` component root node.

### The result 2
The `BaseChild.vue` component applies the `text-red` CSS definition. Therefore, the CSS definition from
the parent component takes higher precedence.
<img width="995" alt="Screenshot 2024-05-03 at 01 14 02" src="https://github.com/hakunamalaton/vue-scoped-css-example/assets/106505755/b618ea3a-4c93-4fd8-a89b-574b36d62b70">
