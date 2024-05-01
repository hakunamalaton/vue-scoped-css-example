# Introduction
This repository explains the `scoped CSS` in Vue with intuitive examples
References on Vue official documentation: https://vuejs.org/api/sfc-css-features.html#scoped-css

There is one example for each section:
- Child Component Root Elements
- Deep Selectors
- Slotted Selectors
- Global Selectors
- Mixing Local and Global Styles
- [Bonus] Scoped Style Tips

You can directly test on the [Vue Playgroud](https://play.vuejs.org/#eNp9kUFLwzAUx7/KM5cqzBXR0+gGKgP1oKKCl1xG99ZlpklIXuag9Lv7krK5w9it7//7v/SXthP3zo23EcVEVKH2yhEEpOhm0qjWWU/QgccV9LDytoWCq4U00tTWBII2NDBN/LJ4Qq0tfFuvlxfFlTRVORzHB/FA2Dq9IOQJoFrfzLouL/d9VfKUU2VcJNhet3aJeioFcymgZFiVR/tiJCjw61eqGW+CNWzepX0pats6pdG/OVKsJ8UEMklswXa/LzkjH3G0z+s11j8n8k3YpUyKd48B/RalODBa+AZpwPPPV9zx8wGyfdTcPgM/MFgdk+NQe4hmydpHvWz7nL+/Ms1XmO8ITdhfKommZp/7UvA/eTxz9X/d2/Fd3pOmF/0fEx+nNQ==).

## Child Component Root Elements
From Vue documentation:

> With scoped, the parent component's styles will not leak into child components. However, a child component's root node will be affected by both the parent's scoped CSS and the child's scoped CSS. This is by design so that the parent can style the child root element for layout purposes.

The example will help you understand the sentence `However, a child component's root node will be affected by both the parent's scoped CSS and the child's scoped CSS` easily.

### The Example
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

Inside the `BaseChild.vue` component, we use `text-red` CSS definition at the **root node**. The root node
of the component is the outest level block of a component. A component can have multiple root nodes. For
the related documentation, please reach it at [Attribute Inheritance on Multiple Root Nodes](https://vuejs.org/guide/components/attrs.html#attribute-inheritance-on-multiple-root-nodes).

### The result
The `BaseChild.vue` component applies the `text-red` CSS definition. The reason is by design of the Vue team so that **the parent can style the child root element for layout purposes**.

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